---
title: "Multiple &quot;Live CD&quot; USB"
date: 2013-05-20
forum: Installation &amp; Upgrades
---

### Post by DigitalNoise on 2013-05-20
I've been banging my head against a wall for three solid days now on this issue, and I'm just not getting anywhere.  So, I figured I'd finally stop being stubborn and ask someone else...

What I'm trying to do seems - I think - to be fairly simple.  I've got 15 different "Live CD" ISO's that I'd like to place on a USB drive so that I can boot from it and try each one out to figure out which one I want to go with.  It'd be nice if I could just install from the USB once I've figured that out, but it's not necessary.

I've tried so many things that I've lost track, but the two most recent are:

**[INDENT]MultiBootUSB[/INDENT]**[INDENT][INDENT]This looks like it should do exactly what I want, but even after chosing "Install syslinux and copy all required files" it does not seem to actually install the bootloader correctly.[/INDENT][/INDENT]

**[INDENT]UNetbootin[/INDENT]**[INDENT][INDENT]This does extract and install the bootloader correctly, but it only supports one distro at a time.[/INDENT][/INDENT]

I know there can be some issues with the different "Live CDs" and how they handle the boot procedure, however, other than Arch, CrunchBang, Peppermint and Mint, all the desired ISO's are Ubuntu or derivatives, and all recent (13.04 & 12.04).

Any help? :-)

---

### Post by 2F4U on 2013-05-20
I found these two, which promise to do the trick (haven't tested it myself):

[http://www.makeuseof.com/tag/boot-multiple-live-cds-usb-disk-yumi-windows/](http://www.makeuseof.com/tag/boot-multiple-live-cds-usb-disk-yumi-windows/)
[http://www.howtogeek.com/howto/39747/how-to-boot-10-different-live-cds-from-1-usb-flash-drive/](http://www.howtogeek.com/howto/39747/how-to-boot-10-different-live-cds-from-1-usb-flash-drive/)

---

### Post by oldfred on 2013-05-20
Not all ISO can be booted with grub2's loopmount, but many can be. All the Ubuntu Desktop versions (not server nor alternative), gparted, Boot-Repair, Supergrub and Parted magic work as I have them all on one partition in a hard drive and on some flash drives.

I just install grub2 to the flash drive. Copy ISO into a /iso folder and modify grub.cfg (you have to create your own with just a grub install) to boot ISO. 

Once you install grub to flash drive it is identical to this.
       This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

      
 Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")
Label partition & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sda
[https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2](https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2)

Now older info, but some of the info I used.

 MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)

I can post my examples, but I think the examples in the threads above cover the issues. On my hard drive I have changed to a config file so every ISO update I do not have to edit 40_custom and run sudo update-grub.

If the distribution will loopmount, often finding the exact paths and parameters requires looking at the ISO and seeing what it uses in its boot files.

---

### Post by DigitalNoise on 2013-05-20
> **2F4U said:**
> I found these two, which promise to do the trick (haven't tested it myself):

[http://www.howtogeek.com/howto/39747/how-to-boot-10-different-live-cds-from-1-usb-flash-drive/](http://www.howtogeek.com/howto/39747/how-to-boot-10-different-live-cds-from-1-usb-flash-drive/)

I FINALLY got MultiSystem to install and work, and so far QEMU is showing that it's actually working correctly.  The Google Translate of the home page for MultiSystem sucks, and actually screws a few things up.  Their installation script didn't work for me, so I had to add the repository - but I had to manually at a sources.list file for them instead of using **sudo apt-add-repository**.  I'm not sure if that's because I'm using Linux Mint 15 at the moment, or if it's a failure to update the instructions.

I should probably write down what I actually had to do vs. what the translated page says before I forget.

---

### Post by DigitalNoise on 2013-05-20
I remember reading through some of these, but for some reason I could not get GRUB2 to install the bootloader in the MBR, despite following the instructions to the letter.

I've finally got MultiSystem working, though I had to jump through a bunch of hoops.  We'll see if that actually works for me - so far QEMU says it is.

---

### Post by DigitalNoise on 2013-05-20
And I spoke too soon.  I can get the USB drive that MultiSystem builds to boot under QEMU, but I cannot get it to boot at system start up - it just acts like nothing is there and goes to the GRUB2 menu on my harddisk.

I don't get it.  fdisk/GParted show the partition on the USB drive is bootable; GRUB2 is installed... but it just won't boot, despite chosing the device at boot time from the menu.  Something has to be missing.

---

### Post by oldfred on 2013-05-20
You can always post this if running another live install or Ubuntu.

       
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by C.S.Cameron on 2013-05-20
I have had very good luck with MultiBootUSB.
I was using a multiBoot thumbdrive  just today to install 13.04 to another thumb drive.

---

### Post by DigitalNoise on 2013-05-20
> **oldfred said:**
> You can always post this if running another live install or Ubuntu.

       
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Here you go: [http://paste2.org/hW54L7mc](http://paste2.org/hW54L7mc)

**/dev/sdc** is the USB drive.  I'm a n00b at reading this stuff, but it looks to me as if it says everything is ok - but that there's no bootloader installed on **/dev/sdc1**

---

### Post by DigitalNoise on 2013-05-20
> **C.S.Cameron said:**
> I have had very good luck with MultiBootUSB.
I was using a multiBoot thumbdrive  just today to install 13.04 to another thumb drive.

I wish I knew what the problem was. I had to go through all kinds of hoops to get it to install - the shell script wouldn't work for me (kept popping open the repository GUI); and then I couldn't automatically add the repository via add-apt-repository - kept getting a message that there was no valid JSON file there, so I ended up having to manually create a sources.list file for that, and then I was able to install it from there but... still can't seem to get it to do what I want it to do.

---

### Post by monkeybrain2012 on 2013-05-20
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

I have made many live usbs with multiple boot with this nifty tool. Only catch is that if you have multiple OSes only one can be made persistent, it seems.

---

### Post by DigitalNoise on 2013-05-20
> **monkeybrain2012 said:**
> [http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

I have made many live usbs with multiple boot with this nifty tool. Only catch is that if you have multiple OSes only one can be made persistent, it seems.

Yes, that would be the MultiBoot that I can't seem to get to work - it installs the OS's fine, but it can't seem to make the drive bootable for some reason.  Or at least that's what it looks like.  And there's essentially no documentation for it either - or at least none that I've been able to find in english.

---

### Post by C.S.Cameron on 2013-05-20
Are you using MultiBootUSB or MultiSystem?

MultiBootUSB can be obtained from here:

[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)

---

### Post by monkeybrain2012 on 2013-05-20
> **DigitalNoise said:**
> Yes, that would be the MultiBoot that I can't seem to get to work - it installs the OS's fine, but it can't seem to make the drive bootable for some reason.  Or at least that's what it looks like.  And there's essentially no documentation for it either - or at least none that I've been able to find in english.

What OSes are you putting in there? I have made multi boot usbs with Debian, *buntu, different flavours of Fedora and all work fine (except Fedora 18, if enable persistence then the live user see a screen asking for password so cannot get to the desktop)

You may be doing something wrong, because if you run the install script properly then you don't have to manually add the repo to the sources list. By the way which version of Ubuntu are you using? I haven't used it in 13.04 yet.

---

### Post by DigitalNoise on 2013-05-21
> **C.S.Cameron said:**
> Are you using MultiBootUSB or MultiSystem?

MultiBootUSB can be obtained from here:

[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)

MultiSystem, sorry.  I have MultiBootUSB, but had the same problem - couldn't/wouldn't read the boot loader from the USB.

---

### Post by DigitalNoise on 2013-05-21
> **monkeybrain2012 said:**
> What OSes are you putting in there? I have made multi boot usbs with Debian, *buntu, different flavours of Fedora and all work fine (except Fedora 18, if enable persistence then the live user see a screen asking for password so cannot get to the desktop)

You may be doing something wrong, because if you run the install script properly then you don't have to manually add the repo to the sources list. By the way which version of Ubuntu are you using? I haven't used it in 13.04 yet.

I'm currently using Linux Mint 15 RC 64-bit.  As I said, when I run the install script, it pops open the "Software Sources" application but gives no indication of what I'm supposed to do; when I close the application the script errors out with "xterm".  Now, this could be related to using Linux Mint, but since I can't get the Live USB to boot so I can try other distros, much less install them...

As for what I'm trying to put on the USB to boot from:

[LIST]
[*]archlinux-2013.05.01-dual.iso
[*]crunchbang-11-20130506-amd64.iso
[*]linuxmint-13-cinnamon-dvd-64bit.iso
[*]linuxmint-13-mate-dvd-64bit.iso
[*]linuxmint-13-xfce-dvd-64bit.iso
[*]linuxmint-14.1-cinnamon-dvd-64bit.iso
[*]linuxmint-14.1-mate-dvd-64bit.iso
[*]linuxmint-14-xfce-dvd-64bit.iso
[*]linuxmint-15-mate-dvd-64bit-rc.iso
[*]lubuntu-13.04-desktop-amd64.iso
[*]Peppermint-3-20121105-amd64.iso
[*]ubuntu-12.04.2-desktop-amd64.iso
[*]ubuntu-13.04-desktop-amd64.iso
[*]xubuntu-12.04.2-desktop-amd64.iso
[*]xubuntu-13.04-desktop-amd64.iso
[/LIST]

---

### Post by oldfred on 2013-05-21
I just add boot stanzas like this to grub.
This works for me, but I have my files in a gpt partitioned drive, so I have to add that insmod and I have nVidia so I have to add nomodeset. This particular entry is my hard drive hd2 and partition 4 (hd2,4).

```
menuentry "Ubuntu 13.04 Raring ISO 64bit" {
    set isofile="/iso/raring-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

```

---

### Post by DigitalNoise on 2013-05-22
> **oldfred said:**
> I just add boot stanzas like this to grub.
This works for me, but I have my files in a gpt partitioned drive, so I have to add that insmod and I have nVidia so I have to add nomodeset. This particular entry is my hard drive hd2 and partition 4 (hd2,4).

```
menuentry "Ubuntu 13.04 Raring ISO 64bit" {
    set isofile="/iso/raring-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

```

My grub.cfg file has entries like that.  It's more like whatever is supposed to be in the MBR of the USB device isn't actually there - I've done the whole sudo grub-install routine and pointed it at the right place, but when I boot and tell it to look at the USB... it doesn't find anything (apparently), so it skips it and goes on to my normal grub install that lets me boot into Linux or Windows.

---

### Post by sudodus on 2013-05-22
Maybe the problem is not the USB boot drive, but your computer.

1. Have you booted your computer from a unetbootin USB boot drive?

2. What computer is it? Is it a new one with Windows 7 or 8 and UEFI?

3. Or is it an old one, that cannot boot from USB?

4. Have you set the computer to look for USB before the internal HDD at boot?

5. Is there a hotkey to press, so that you get a meny of devices to boot from?

6. Or have you forgotten to install the boot-loader? If you use grub2, what I call the 'grub-n-iso' method, you install grub and the boot-loader to the USB drive, and then edit .../boot/grub/grub.cfg (on the USB drive) to fit your iso files.

---

### Post by DigitalNoise on 2013-05-22
1) Yes, that's how Linux Mint 15 RC 64 bit got installed (what I'm using now).

2) No - the motherboard is about 5 years old, the other OS is Windows 7 Ultimate 64-bit.

3) Boots from USB just fine, see #1

4) Yes.

5) Yes.

6) See my previous replies - I've installed grub to the USB drive multiple times; doesn't seem to do anything.  QEMU boots the USB drive, but in practice the system won't boot from it.  I suspect something is missing.

---

### Post by sudodus on 2013-05-22
Try if my special 'grub-n-iso' system with fake-pae is working. Yes I know it is not intended for your computer. But it was actually created on a 64-bit machine with an intel i5 cpu, and it should work there as well as anything between that and Pentium M. You can replace the lubuntu.iso and or rename another iso to second.iso and have it in the same directory, the top level directory in the first partition of the USB drive. See this link

[https://help.ubuntu.com/community/grub-n-iso](https://help.ubuntu.com/community/grub-n-iso)

If it works, you can make a similar drive, or edit the partitions (expand the first partition to fill your USB drive) to provide space for all your iso files.

And then edit .../boot/grub/grub.cfg (on the USB drive) to fit your iso files.

*Edit 1*: 'grub-n-iso-n-swap' allows for two CD size iso files.
*Edit 2*: This USB drive boots in a new computer only when you run it without UEFI (in CSM mode)

---

### Post by DigitalNoise on 2013-05-22
I ended up trying the procedure at the link below, and I can now boot from the USB stick and get the Easy2Boot menu.  Unfortunately now I'm getting an error message whenever I try to actually boot into any of the ISO's - same one every time "Error 30: Invalid Argument".

The really screwy thing is that when I boot the USB using QEMU, I can boot into any of the ISO's just fine.

[http://en.positon.org/post/The-ultimate-live-USB-MultiBoot-solution%3A-Easy2Boot](http://en.positon.org/post/The-ultimate-live-USB-MultiBoot-solution%3A-Easy2Boot)

---

### Post by sudodus on 2013-05-23
Now I *think* the problem is not booting, but that the iso files are not treated in a correct way. The text in what corresponds to grub.cfg (the menuentries) are not correctly addressing either the iso files themselves or the files in the filesystem inside the iso files.

-o-

If you try the 'grub-n-iso' method of post #21 and succeed, you have a method that you can use. The 'grub-n-iso' method clones an image to the USB pendrive, and it should be obvious if it works or not. I think it will work, and then you can inspect and use it as a template to make a multi-boot system.

---

### Post by sudodus on 2013-05-24
Look at the attached file. It shows corresponding menuentries in grub.cfg and iso files in a USB drive. The 'path' may vary depending on how you have mounted it,**[FONT=courier new] 'path'/boot/grub/grub.cfg[/FONT]**, for example [B][FONT=courier new]/media/grub-n-iso/boot/grub/grub.cfg
[/FONT][/B]
```

set timeout=10
set default=0

menuentry "Run Lubuntu ISO (from /lubuntu-13.04-desktop-i386.iso)" {
 loopback loop /lubuntu-13.04-desktop-i386.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/lubuntu-13.04-desktop-i386.iso splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "Run Ubuntu ISO (from /ubuntu-12.04.2-desktop-amd64.iso)" {
 loopback loop /ubuntu-12.04.2-desktop-amd64.iso
 linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=/ubuntu-12.04.2-desktop-amd64.iso splash --
 initrd (loop)/casper/initrd.lz
}

```

---

