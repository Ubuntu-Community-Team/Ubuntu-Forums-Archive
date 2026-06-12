---
title: "Using grub 2 to boot an iso off hard drive"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by dan98 on 2010-07-21
I have a dual boot machine windows xp & Ubuntu 10.04. I want to use Grub 2 to boot an Ubuntu 8.04 32bit live cd image off my hard drive. I put a copy of the 8.04 iso in a new directory /boot/iso. I added the following lines to my grub.cfg.
 
menuentry [COLOR=#ff0000]"Ubuntu Live 8.04 32bit"[/COLOR] [COLOR=#7a0874]**{**[/COLOR]
loopback loop [COLOR=#000000]**/**[/COLOR]boot[COLOR=#000000]**/**[/COLOR]iso[COLOR=#000000]**/**[/COLOR]ubuntu804.iso linux [COLOR=#7a0874]**(**[/COLOR]loop[COLOR=#7a0874]**)**[/COLOR][COLOR=#000000]**/**[/COLOR]casper[COLOR=#000000]**/**[/COLOR]vmlinuz [COLOR=#007800]boot[/COLOR]=casper iso-scan[COLOR=#000000]**/**[/COLOR][COLOR=#007800]filename[/COLOR]=[COLOR=#000000]**/**[/COLOR]boot[COLOR=#000000]**/**[/COLOR]iso[COLOR=#000000]**/**[/COLOR]ubuntu804.iso noeject noprompt [COLOR=#660033]--[/COLOR]
initrd [COLOR=#7a0874]**(**[/COLOR]loop[COLOR=#7a0874]**)**[/COLOR][COLOR=#000000]**/**[/COLOR]casper[COLOR=#000000]**/**[/COLOR]initrd.lz
[COLOR=#7a0874]**}**[/COLOR]
 
my current error message is 
error: invalid file name 'boot=casper'.
 
Thanks in advance

---

### Post by drs305 on 2010-07-21
Here is one 

menuentry "Ubuntu Live 8.04 32bit" {
loopback loop (hd**X,Y**)/boot/iso/ubuntu804.iso 
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu804.iso noeject noprompt
initrd (loop)/casper/initrd.gz
}

---

### Post by oldfred on 2010-07-21
My loop mount of 9.04 uses initrd.gz and only the newer versions use initrd.lz. 

Not sure about 8.04 but I thought it was a change from gz to lz about version 9.10.

---

### Post by drs305 on 2010-07-21
*oldfred* is correct. I just mounted my hardy .iso and it is initrd.gz. I believe it changed to .lz in 9.10.

I've edited my previous post to reflect the older convention. Thanks *oldfred*

---

### Post by dan98 on 2010-07-22
I modified my grub.cfg and I still get the same error. I am testing this functionality in a Virtualbox machine. Here is some more information.
 
1. fdisk
root@user01-desktop:~# fdisk -l
Disk /dev/sda: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdd33dd33
Device Boot Start End Blocks Id System
/dev/sda1 * 1 780 6265318+ 7 HPFS/NTFS
/dev/sda2 781 1306 4218881 5 Extended
/dev/sda5 781 1279 4003840 83 Linux
/dev/sda6 1279 1306 214016 82 Linux swap / Solaris
root@user01-desktop:~#
 
2. the iso
root@user01-desktop:/boot/iso# ls -l
total 716748
-rw-r--r-- 1 user01 user01 733945856 2010-07-21 11:34 ubuntu804.iso
root@user01-desktop:/boot/iso#
 
3. some grub.cfg entries, Ubuntu 10.04 boots fine
 
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set e...
linux /boot/vmlinuz-2.6.32-23-generic root=UUID=e... ro quiet splash
initrd /boot/initrd.img-2.6.32-23-generic
}
 
 
menuentry "Ubuntu Live 8.04 32bit" {
loopback loop (hd0,5)/boot/iso/ubuntu804.iso
loopback (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu804.iso noeject noprompt initrd (loop)/casper/initrd.gz
}
 
Can someone make a Virtualbox machine with this working? Then it could be available for download. This is the beauty of open source. There are many posts in the forums with people trying to get this to work [http://ubuntuforums.org/showthread.php?t=1406889&highlight=boot+linux+iso+image+hard+drive](http://ubuntuforums.org/showthread.php?t=1406889&highlight=boot+linux+iso+image+hard+drive). 
 
One working example will answer all of the questions. According to this site [http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/](http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/) grml is required to boot an iso.

---

### Post by dan98 on 2010-07-22
With this grub 2 entry I made some progress.
 
menuentry "ubu804 ISO" {
loopback loop (hd0,5)/boot/iso/ubuntu804.iso
linux (loop)/casper/vmlinuz boot=casper
iso-scan/filename=/boot/iso/ubuntu804.iso noprompt
initrd (loop)/casper/initrd.gz
}
 
I made it to this prompt:
 
Busybox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
 
(initramfs) 
 
 
I can enter commands at this prompt. This grub.cfg entry is very similar to my other one except for linux loop instead of loopback and the noeject. Do you know what command I am missing? I am trying to boot all the way to the LiveCD gui.

---

### Post by drs305 on 2010-07-22
I've been playing with this for a good part of the day, experimenting with various iterations. So far with no luck. I takes me back a year or so when I was trying to determine the way to mount an Ubuntu ISO without any existing documentation.

A couple of observations that may help you. First, telling us that you were trying to do this in a VM is important. The menu entries provided in earlier posts are all for 'real' ISOs mounted on a normal system.

Secondly, you can check your (hd0,5) choice by using grub's tab complete feature. At the menu, press "c" to get to the Grub2 command line. From there, start typing your "loopback loop" line. When you have typed
> loopback loop (hd0,5)/
double-TAB and see if anything comes up. Unless you are running a 'saved' VM, I would suspect you will get no results. (On my machine, 0,5 is the swap).

Next, if you got no results, try (hd0,1)/ and I think you will find your /boot folder and contents. If so, use (hd0,1) for the entire line.

Finally, where I have been concentrating my attempts has been the 'linux' line. When I was experimenting on my real system, I usually ended up at the 'initramfs' point because of a problem with the 'linux' line. As I've said, I haven't found the proper combination to get past 'initramfs', but the entries after "linux (loop)/casper/vmlinuz' is where I suspect the problem lies. I don't think the first part of the line is the problem since after typing 'linux (loop)/casper/vm' a double-TAB will complete the *vmlinuz*.

Anyway, if I'd spent as much time on Google as I have playing with the VM I may have found a solution.  ;-)  Hopefully someone will post the solution for you.

---

### Post by dan98 on 2010-07-23
Thanks for looking into this for me. I also ended up at the 'initramfs' point with Ubuntu 8.04. I tried Ubuntu 10.04 and I get '(initiramfs) Unable to find a medium containing a live file system'. The VM is working the same as a physical machine.
 
I don't think 'Using grub 2 to boot an iso off hard drive' works. It sounds nice. Does anyone out there have this working? Should I try booting a livecd .iso file from a different distro?

---

### Post by oldfred on 2010-07-23
Without the VM I directly boot ISO from my flash drive with grub2. I have several versions of Ubuntu, gparted, system rescue and they all work. I do not know what change the VM should make.

---

### Post by dan98 on 2010-07-23
Thanks for the reply. drs305 and I can only make it to the initramfs prompt.
 
I have some questions for you.
1. Is your flash drive bootable? 
2. Are you booting a ubuntu .iso file? If I did an ls on your flash drive would I just see a few .iso files.
3. Has the .iso file been mounted or expanded into a folder?
4. Is your thumb drive formatted fat32?
5. Can you please post all or part of your grub.cfg file?
 
I can figure out the VM changes. So far I haven't seen any. I get the same results as drs305. I also can build everything on a clean no OS physical machine if needed.

---

### Post by oldfred on 2010-07-23
My Flash is FAT. I installed grub2 and manually edited the grub.cfg. Because it is grub I also have a full copies of scripts for emergency use in the root of the drive. All the Ubuntus, gparted, & system rescue boot. Dariks does not, and I have not tested all the rest so far.

Disk /dev/sdd: 4 GB, 4038612480 bytes
255 heads, 63 sectors/track, 491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdd1   *           1         492     3951958    b  FAT32


fred@fred-desktop:/media/MC4GB/boot/ISOs$ ls
fdfullcd.iso                miniLucid32.iso
gparted-live-0.5.2-1.iso    pmagic-4.8.iso
lupu-501.iso                systemrescuecd-x86-1.5.0.iso
maverick-desktop-amd64.iso  ubuntu-10.04-desktop-amd64.iso
miniKarmic32.iso            ubuntu-9.10-desktop-i386.iso

```
menuentry "Ubuntu 10.10 Maverick 64bit" {
    set isofile="/boot/ISOs/maverick-desktop-amd64.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 10.04 Lucid 64bit" {
    set isofile="/boot/ISOs/ubuntu-10.04-desktop-amd64.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 9.10 Karmic 64 bit" {
    set isofile="/boot/ISOs/ubuntu-9.10-desktop-amd64.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}

menuentry " " {
set root= 
}

menuentry "Ubuntu 9.10 32 bit" {
    set isofile="/boot/ISOs/ubuntu-9.10-desktop-i386.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 9.04 32 bit" {
    set isofile="/boot/ISOs/ubuntu-9.04-desktop-i386.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.gz
}

menuentry "Parted Magic" {
    set isofile="/boot/ISOs/pmagic-4.8.iso"

    loopback loop $isofile 
    linux (loop)/pmagic/bzImage iso_filename=$isofile edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rwnomce sleep=10 loglevel=0
    initrd (loop)/pmagic/initramfs
}

menuentry " " {
set root= 
}

menuentry "SystemRescueCd 1.5.0" {
 set isofile="/boot/ISOs/systemrescuecd-x86-1.5.0.iso"
 loopback loop $isofile 
 linux (loop)/isolinux/rescuecd isoloop=$isofile  
 initrd (loop)/isolinux/initram.igz
}

menuentry "Gparted live" {
  insmod loopback
  insmod iso9660
  set gfxpayload=800x600x16, 800x600
  set isofile="/boot/ISOs/gparted-live-0.5.2-1.iso"
  loopback loop $isofile
  linux (loop)/live/vmlinuz boot=live union=aufs noswap noprompt ip=frommedia toram=filesystem.squashfs findiso=$isofile
  initrd (loop)/live/initrd.img
}

menuentry "Ubuntu Mini 9.10 32 bit" {
    set isofile="/boot/ISOs/miniKarmic32.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.gz
}


menuentry " " {
set root= 
}

menuentry "Reboot" {
    reboot
}

menuentry "Halt" {
    halt
}

menuentry "Memory test (memtest86+)" {
 linux /boot/memtest86+.bin
}

Boot most up2date Lucid kernel on sdc7
menuentry "Lucid on sdc7" {
    set root=(hd1,7)
        linux /vmlinuz root=/dev/sdc7 ro quiet splash
        initrd /initrd.img
}


menuentry "Darik's Boot and Nuke" {
 loopback loop /boot/iso/dban-beta.2006042900_i386.iso
 linux (loop)/ISOLINUX/DBAN.BZI nuke="dwipe" silent --
}




```

---

### Post by Herman on 2010-07-23
I think we should be able to boot Ubuntu 9.04 and later from an .iso file on the hard drive or a USB, but I don't think it's possible to do it with earlier versions than 9.04, because I think the Live CD operating system needs to have built in support for  this kind of booting.

---

### Post by C.S.Cameron on 2010-07-23
If you look at how sundar_ima does it with MultiBootUSB, he manages to boot just about everything with grub2 but needs to expand some of the isos to do so. 
Herman is right, some pre grub2 distro's just won't boot from the iso position.

---

### Post by dan98 on 2010-07-23
I dropped the 8.04 iso. I won't try that one anymore. It is interesting that the .iso file needs to have built in support for this kind of booting. I boot many .iso files with my VM without any issues. I thought this functionality would be similar. I guess the VM cd/dvd emulation works a lot different than grub.
 
fat vs ext4
I created a 2 gig fat hard drive with one primary partition. I added it to my VM, it is (hd1,1). I created a iso dir off the root of my new fat drive and put my lucid .iso file in it. I created a new entry in grub.cfg for lucid on (hd1,1). I get different results. Now I get further into the boot process. My new error message is below.
 
Begin: Mounting root file system[ 9.026062] EXT4-fs (sda5): mounted filesystem with ordered data mode
Begin: Running /scripts/casper-premount ....
Done.
Done.
stdin :error 0
/init: line 7: can't open /dev/sr0: No medium found
/init: line 7: can't open /dev/sr0: No medium found <==This line keeps repeating ...
 
I would really like to boot the .iso off the hard drive. I will try booting it off a flash drive if I can't get this to work. Do you know of anyone booting .iso files from the hard drive?

---

### Post by oldfred on 2010-07-24
This entry worked for me:

menuentry "Ubuntu 10.10 Maverick 64bit" {
    set isofile="/boot/ISO/maverick-desktop-amd64.iso"
 
    loopback loop (hd0,5)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

I first tried directly using the current /ISO that I have in my /home but it is a link, I then tried the full link, then I created the ISO under boot.  None worked as I had the (hd0,5) in the set isofile "". I also forgot the momodeset the first time and it turned off my monitor which Lucid also did.
I boot sdc and the file is in sdc5.

---

### Post by dan98 on 2010-07-24
Thank you oldfred, drs305, C.S.Cameron, and Herman. oldfred THANK you for the working grub.cfg entry! 
 
I modified your entry for 10.04 and my hard drives.
 
menuentry "fat Ubuntu 10.04" {
set isofile="/iso/ubuntu1004.iso"
loopback loop (hd1,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
initrd (loop)/casper/initrd.lz
}
 
menuentry "ext4 Ubuntu 10.04" {
set isofile="/boot/iso/ubuntu1004.iso"
loopback loop (hd0,5)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
initrd (loop)/casper/initrd.lz
}
 
I booted into the 10.04 live cd from the .iso file on the fat partition. I also booted into the 10.04 live cd from the .iso file on the ext4 partition. Both of them boot all the way to the gui desktop without any errors or issues. All of this works in my Virtualbox virtual machine. I am running Virtualbox version 3.2.6 r63112. Now that all of the kinks are ironed out. I will port this to my physical machine.

---

### Post by Irregular Joe on 2010-10-26
I have not been able to place the iso file on an LVM volume.  Although following all instructions, I would only get the missing file error from the 20iso-scan script.

Although I could enter each grub2 command, and 'ls (sys-root)/' to see the file, and the kernel would load properly, for some reason, the iso-scan/filename would never be recognized if it resided on an LVM volume.  I tried 'insmod lvm', setting boot= and root=, with no success.

I was able to create a normal partition to hold the iso, and it finally worked, but I would much rather use an LVM volume for this, as I like the flexibility to move space around as needed that I get with LVM.

---

### Post by wouf-wouf on 2011-11-21
UP :KS
Hello Iregular Joe.
Did you found how boot ISO from an LVM part?
by :)

---

### Post by afuentes on 2011-12-21
bump!

yup, i would like to know this as well. LVM ftw! :guitar:

---

### Post by HeliusVonVeritas on 2013-03-20
> **dan98 said:**
> I have a dual boot machine windows xp & Ubuntu 10.04. I want to use Grub 2 to boot an Ubuntu 8.04 32bit live cd image off my hard drive. I put a copy of the 8.04 iso in a new directory /boot/iso. I added the following lines to my grub.cfg.
 
menuentry [COLOR=#ff0000]"Ubuntu Live 8.04 32bit"[/COLOR] [COLOR=#7a0874]**{**[/COLOR]
loopback loop [COLOR=#000000]**/**[/COLOR]boot[COLOR=#000000]**/**[/COLOR]iso[COLOR=#000000]**/**[/COLOR]ubuntu804.iso linux [COLOR=#7a0874]**(**[/COLOR]loop[COLOR=#7a0874]**)**[/COLOR][COLOR=#000000]**/**[/COLOR]casper[COLOR=#000000]**/**[/COLOR]vmlinuz [COLOR=#007800]boot[/COLOR]=casper iso-scan[COLOR=#000000]**/**[/COLOR][COLOR=#007800]filename[/COLOR]=[COLOR=#000000]**/**[/COLOR]boot[COLOR=#000000]**/**[/COLOR]iso[COLOR=#000000]**/**[/COLOR]ubuntu804.iso noeject noprompt [COLOR=#660033]--[/COLOR]
initrd [COLOR=#7a0874]**(**[/COLOR]loop[COLOR=#7a0874]**)**[/COLOR][COLOR=#000000]**/**[/COLOR]casper[COLOR=#000000]**/**[/COLOR]initrd.lz
[COLOR=#7a0874]**}**[/COLOR]
 
my current error message is 
error: invalid file name 'boot=casper'.
 
Thanks in advance

Mount the .iso with:

$ mkdir /media/iso
 $ mount -o loop /boot/iso/ubuntu804.iso /media/iso

Check the ISO content and look for the folder where "initrd.lz" and "vmlinuz" files are for your Ubuntu version, change every "/casper" appearance in the menuentry by the name of the folder where you found them.

(When it happened to me i had to substitute every "/casper" with "/install", and "initrd.lz" for "initrd.gz"  within Ubuntu 12.10 --Precise Pangolin--).

---

### Post by oldfred on 2013-03-20
Old thread with old info, Please do not post in really old threads. 
Thread closed.

Some newer info
 This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

