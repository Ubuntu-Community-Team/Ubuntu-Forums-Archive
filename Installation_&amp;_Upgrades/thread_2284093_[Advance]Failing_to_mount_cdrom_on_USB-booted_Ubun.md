---
title: "[Advance]Failing to mount /cdrom on USB-booted Ubuntu Server Installer"
date: 2015-06-27
forum: Installation &amp; Upgrades
---

### Post by Jesse_TeKrony on 2015-06-27
**Warning: To be able to help me here you will need extensive knowledge of how the Debian installer/initrd/grub2/shell scripting works. You have been warned.**

Now I already know what you are thinking, "Oh another guy tried using unetbootin or some other multiboot disk creator and now the installer can't find the disk" but my problem goes considerably deeper than that. First, some background:

For the last few years, I have manually created multiboot USB's using grub2. Essentially, you plug my USB in, and you get a nice grub menu of, for example, all variations Ubuntu 15.04 in both 32bit and 64bit. I am NOT mounting ISO's as a loopback device to do this, as I have tried that in the past and it is slow as hell. The way my multiboot USB works is by using a series of FAT32 partitions and a seemingly little-known casper kernel parameter called live-media. This paramter allows you to set the block device of the partition where the squashfs filesystem image is located, meaning the initramfs isn't confused by the several FAT32 partitions containing different versions of ubuntu. (As a side note you can do similar things with Fedora and Arch, that I have tested myself) Below is a currently working example (except for the Ubuntu Server entries, but that's what this post is about) of a grub.cfg file for Ubuntu 15.04 32 and 64 bit.

```
set timeout=999
set default=0
set gfxmode=auto

#I made a little function here so I don't have to repeat so much.
#I eventually want to add all major derivatives of Ubuntu and this will make that much easier.
#Usage: boot_casper <root label> <seed file>
function boot_casper {
    search --label --set --no-floppy $1
    echo ":: Booting ${chosen} on root ${root}..."
    
    #Different architectures have different names for the kernel
    echo ":: Loading kernel..."
    options=""
    if [ -f /casper/vmlinuz.efi ]; then
        #64bit Ubuntu desktop (works for Kubuntu, Xubuntu, etc)
        kernel=/casper/vmlinuz.efi
        options="${options} splash boot=casper"
    elif [ -f /casper/vmlinuz ]; then
        #32bit Ubuntu desktop
        kernel=/casper/vmlinuz
        options="${options} splash boot=casper"
    elif [ -f /install/vmlinuz ]; then
        #32/64bit Ubuntu server
        kernel=/install/vmlinuz
    fi
    options="${options} file=/cdrom/preseed/${2} live-media=/dev/disk/by-label/${1}"
    echo ":::: Kernel Path: ${kernel}"
    echo ":::: Kernel Options: ${options}"
    linux ${kernel} ${options}


    echo ":: Loading ramdisk..."
    if [ -f /casper/initrd.lz ]; then
        #Ubuntu desktop
        initrd=/casper/initrd.lz
    elif [ -f /install/initrd.gz ]; then
        #Ubuntu server
        initrd=/install/initrd.gz
    fi
    echo ":::: Initrd Path: ${initrd}"
    initrd ${initrd}
}


submenu "Ubuntu" {
    menuentry "Ubuntu 15.04 64bit" {
        boot_casper "ubu_1504_64" "ubuntu.seed"
    }
    menuentry "Ubuntu 15.04 32bit" {
        boot_casper "ubu_1504_32" "ubuntu.seed"
    }
    menuentry "Ubuntu Server 15.04 64bit" {
        boot_casper "usv_1504_64" "ubuntu-server.seed"
    }
    menuentry "Ubuntu Server 15.04 32bit" {
        boot_casper "usv_1504_32" "ubuntu-server.seed"
    }
}

```

Essentially I have a usb disk with several partitions with the following filesystem labels:
[LIST]
[*]BOOT (FAT32)(primary): Contains grub2's files
[*]ubu_1504_64 (FAT32)(logical): Contains the contents of the Ubuntu 15.04 Desktop 64bit ISO
[*]ubu_1504_32 (FAT32)(logical): Contains the contents of the Ubuntu 15.04 Desktop 32bit ISO
[*]usv_1504_64 (ext2)(logical): Contains the contents of the Ubuntu 15.04 Server 64bit ISO (This partition is ext2 because when I was troubleshooting I wondered if the symlinks that were lost when the ISO is copied to a FAT32 filesystem were important to the installer discovering the volume, turns out it made no difference)
[*]usv_1504_32 (FAT32)(logical): Contains the contents of the Ubuntu 15.04 Server 32bit ISO
[/LIST]

As mentioned earlier the Ubuntu Desktop entries boot just fine into the live environment. However, when I try booting in to the server installer, everything boots fine, but the installer fails to find the "cdrom" after configuring the keyboard etc. It appears that the installer doesn't care much for the live-media kernel parameter. From what I understand it doesn't use it at all as the the installer is running completely from the initrd. However, if I manually mount "/dev/disk/by-label/usv_1504_64" to "/cdrom" by switching to a different tty before the installer gets to the cdrom detection step, the installer continues along no problem and all is well with the world.

I didn't want to have to manually mount /cdrom everytime I install Ubuntu server, so I began looking into a way to modify the initrd to automatically mount the correct partition using the live-media kernel parameter. Reading the [Debian installer documentation]("http://d-i.alioth.debian.org/doc/internals/ch02.html#di-boot"), I found that scripts in "/lib/debian-installer-startup.d" are executed as the installer is being started. So, I created the following script:

```
#Mount live usb partition at /cdrom
for i in $(cat /proc/cmdline); do
        if [ $(echo ${i} | grep live-media) ]; then
                #To be safe; I have no idea when /cdrom is created in the install process
                if [ ! -d /cdrom ]; then
                        mkdir /cdrom
                fi
                #More or less copied from /init, see [here]("http://www.gnu.org/software/bash/manual/bashref.html#Shell-Parameter-Expansion") if you are unfamiliar with the syntax 
                partpath=${i#live-media=}
                mount ${partpath} /cdrom
        fi
done

```
I extracted the initrd to a temporary directory ([helpful instructions]("https://wiki.ubuntu.com/Initramfs")), added the script as "/lib/debian-installer-startup.d/S99live-media" **and marked it executable**. I am aware that if the script is not executable it will be sourced instead of executed. I then repackaged the intitrd, recompressed it, and copied it to the correct location in the usv_1504_64 partition. Once again everything booted fine, but when I switched to a different tty and check the root filesystem, I found the /cdrom had been created but was not mounted. If I execute the S99live-media script manually from the tty, it works perfectly, and the install will continue fine as it's precious /cdrom is in tact.

In short, it appears that something in the installer is umounting /cdrom after S99live-media is run. **Does anyone have an idea of how I can get this script to run at the correct time in the install process? Or if there is a better way of getting my partition mounted in the right place?**

As a final note, I eventually wrote a script to patch the initrd as I was doing it so much in my troubleshooting. For those who are interested, here is that script:

```
#!/bin/bash
#Usage: ./patch_livemedia.sh <initrd>
initrdpath=$(readlink -f "$1")
tempdir=$(mktemp -d)
mountscript="${tempdir}/initrdtemp/lib/debian-installer-startup.d/S99live-media"
mkdir ${tempdir}/initrdtemp
cd "${tempdir}/initrdtemp"
gzip -dc "${initrdpath}" | cpio -ivd
mv "${initrdpath}" "${initrdpath}.old"


cat > "${mountscript}" << 'EOF'
#Mount live usb partition at /cdrom
for i in $(cat /proc/cmdline); do
        if [ $(echo ${i} | grep live-media) ]; then
                if [ ! -d /cdrom ]; then
                        mkdir /cdrom
                fi
                partpath=${i#live-media=}
                mount ${partpath} /cdrom
        fi
done
EOF


chmod +x "${mountscript}"
find . | cpio -R root:root -o -H newc > "${tempdir}/initrd"
gzip "${tempdir}/initrd"
cp "${tempdir}/initrd.gz" "${initrdpath}"
rm -r "${tempdir}"

```
This script takes the location of the initrd file as a parameter, inserts my script into it, and replaces the old initrd leaving a backup behind.

*PS: I have done my best to correct most of my typos, but I am writing this late at night (after a long day of messing with shell scripts) so no guarantees. Sorry for any grammar crimes against humanity. Also, congrats on managing to read all of this. You did read all of this, right?*

---

### Post by dino99 on 2015-06-27
hello,
reading that thread makes me thinking to an app named 'multisystem' which i use and appreciate a lot. Are you talking about it ? and want it to be systemd compatible ?

My feeling is that thread needs to be exposed to devs (programming subforum / askubuntu) due to its high level. You can decide to change for 'programming subforum' by clicking the bottom left 'report post' message request box.

---

### Post by sudodus on 2015-06-27
Welcome to the Ubuntu Forums *Jesse_TeKrony* :-)

Interesting post! I see your problem, and I think it is the same as when booting via grub2 into an ISO file (which you are also referring to). I have no solution for multi-booting the Ubuntu server iso, the mini.iso and the Lubuntu alternate iso (with debian installers), while I have recently made a system to build (multi-) boot USB pendrives, that boot in (almost) all PCs. See the following posts (in the thread [One pendrive for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682"))

[Build your own single boot or multiboot pendrive for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682&p=13302278#post13302278")

[Create or download a portable system with a small footprint with a potential for isotesting]("http://ubuntuforums.org/showthread.php?t=2259682&p=13310634#post13310634")

[Manage the daily built iso files of your choice]("http://ubuntuforums.org/showthread.php?t=2259682&p=13310836#post13310836")

-o-

But one simple method works with all the Ubuntu debian installers since a few years ago, cloning/flashing/copying of the iso file directly to a USB pendrive. There was also the problem with mounting /cdrom until a few years ago, but it was solved also for the mini.iso (during Ubuntu 13.04 'Raring'). See [this link]("http://ubuntuforums.org/showthread.php?t=1958073&p=12847494#post12847494").

I use [mkusb (and text-mode mkusb-nox)]("https://help.ubuntu.com/community/mkusb") to wrap security around ***dd*** to clone/flash/copy the iso file directly to a USB pendrive, and I have found that it is very reliable. This means using the pendrive as a ***temporary*** device rather than a more or less static multiboot devic[I]e.

Edit:[/I] Of course, if you solve the problem with /cdrom, I would be very happy to use your solution :-)

---

### Post by Jesse_TeKrony on 2015-06-27
> **dino99 said:**
> [COLOR=#000000]hello,[/COLOR]
[COLOR=#000000]reading that thread makes me thinking to an app named 'multisystem' which i use and appreciate a lot. Are you talking about it ? and want it to be systemd compatible ?[/COLOR]

[COLOR=#000000]My feeling is that thread needs to be exposed to devs (programming subforum / askubuntu) due to its high level. You can decide to change for 'programming subforum' by clicking the bottom left 'report post' message request box.[/COLOR]
I thought about putting it in programming, but my question is kind of an awkward fit not matter where I put it. Everything else in programming is about python or something. XD I suppose I'll put the request in and let some mod decide. I am not using multisystem, as most utilities I have found for doing this don't quite do it how a like it (the OSS way: always build your own thing rather than using the 1000 other solutions :P ). systemd compatibility doesn't come into this at all as the Ubuntu Server installer never leaves initrd which uses the BusyBox init.

---

### Post by Jesse_TeKrony on 2015-06-27
> **sudodus said:**
> Welcome to the Ubuntu Forums *Jesse_TeKrony* :-)

Interesting post! I see your problem, and I think it is the same as when booting via grub2 into an ISO file (which you are also referring to). I have no solution for multi-booting the Ubuntu server iso, the mini.iso and the Lubuntu alternate iso (with debian installers), while I have recently made a system to build (multi-) boot USB pendrives, that boot in (almost) all PCs. See the following posts (in the thread [One pendrive for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682"))

[Build your own single boot or multiboot pendrive for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682&p=13302278#post13302278")

[Create or download a portable system with a small footprint with a potential for isotesting]("http://ubuntuforums.org/showthread.php?t=2259682&p=13310634#post13310634")

[Manage the daily built iso files of your choice]("http://ubuntuforums.org/showthread.php?t=2259682&p=13310836#post13310836")
Looks interesting. ^^

> **sudodus said:**
> 
But one simple method works with all the Ubuntu debian installers since a few years ago, cloning/flashing/copying of the iso file directly to a USB pendrive. There was also the problem with mounting /cdrom until a few years ago, but it was solved also for the mini.iso (during Ubuntu 13.04 'Raring'). See [this link]("http://ubuntuforums.org/showthread.php?t=1958073&p=12847494#post12847494").

I use [mkusb (and text-mode mkusb-nox)]("https://help.ubuntu.com/community/mkusb") to wrap security around ***dd*** to clone/flash/copy the iso file directly to a USB pendrive, and I have found that it is very reliable. This means using the pendrive as a ***temporary*** device rather than a more or less static multiboot devic[I]e.

Edit:[/I] Of course, if you solve the problem with /cdrom, I would be very happy to use your solution :-)
Yeah, I could use dd, but I want a monster multiboot drive. To be clear, I've used my method to have one drive with Ubuntu, Ubuntu Gnome, Kubuntu, Xubuntu, Lubuntu, Elementary OS, Clonezilla, Debian itself (anything that uses the Debian method of live boot works) along with Arch Linux and Fedora. It works perfectly for the ubuntu desktop ISO's. And my script does solve the /cdrom problem. I just need to figure out how to make it run at the right time in the install process.

In fact, I would be interested in writing a guide on using my method but as you can see I'm still working out the kinks myself. ^^

---

### Post by sudodus on 2015-06-27
With some luck, someone who reads this thread will come with a good tip to put the bits and pieces together for your 'monster multiboot drive', so good luck :-)

---

