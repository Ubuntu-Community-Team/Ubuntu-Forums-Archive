---
title: "USB Stick ISO Booter"
date: 2012-08-28
forum: Installation &amp; Upgrades
---

### Post by iaw4 on 2012-08-28
dear experts---

I would like to keep a couple of iso files on my USB stick and be able to boot into them, just as I am able to boot into them if they had been a CD-ROM.  I have seen YUMI.  Besides the irony that it is a windows program, it has the drawback that ISO selection and installation has to be done at USB copy creation time.  It is not dynamic.   I would much prefer a booter that could scan all existing *.iso files in the top directory of the USB drive, and then present me with a list of choices of OS that I can boot into.  any further OS installations thereafter would only require copying of their iso files into the USB stick.

does this exist?

regards,

/iaw

---

### Post by oldfred on 2012-08-28
Grub will loop mount the ISO, but you have to create your own menu in with grub.cfg. I just copied examples and updated to my newest ISO.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

There are several scripts that automate process.
These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

My system sees a flash drive as another hard drive, so these instructions also apply if that is the case.
This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by iaw4 on 2012-08-28
thanks, but not dynamic enough :-( .  it should read available ISOs at boot time, so that iso installation is copying a file and nothing else.  once I have to edit configuration files before reboot, it ain't the same thing.

I guess it doesn't exist (yet).

/iaw

---

### Post by oldfred on 2012-08-28
You now have an opportunity. 

Just write a script to scan ISO's and add them to grub.cfg or a liveimage.cfg that grub calls. The real issue becomes every ISO has different boot parameters, so you have to in effect have all the scripts rewritten like  the multi-boot scripts.

---

### Post by nariub on 2012-08-29
I did this, kinda 
I created a custom grub script
I still have to copy the iso (to a specific directory), and run update-grub which find the iso, and add it to the menu choices

I don't think it is quite as automated as the OP wants though.

---

### Post by iaw4 on 2012-08-30
indeed.  I mean something much more dynamic.  A setup that works without running grub or creating config files.  sort of like a chainloader that scans iso images, presents images, and then mounts them per user request.

it would be a lot more convenient.

/iaw

---

### Post by oldfred on 2012-08-30
While that would be nice, the issue is every ISO has different parameters. So you cannot mount them all the same.

While my Ubuntu entries are the same, and my server entry does not work as it is different from a desktop most other installs have files in different directories on the "CD" and need different parameters. If everyone did it the same then it might be possible.

```
# livecdimage.cfg
# Add this to 40_custom to load this file:
# menuentry 'Live ISOs' {
# configfile (hd2,4)/iso/livecdimage.cfg
#} 


menuentry "Uubuntu 12.10 Quantal ISO 64bit" {
    set isofile="/iso/quantal-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

menuentry "Uubuntu 12.04 Secure Remix ISO 64bit" {
    set isofile="/iso/ubuntu-secure-remix-12.04-64bits.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 12.04 Precise ISO 64bit" {
    set isofile="/iso/ubuntu-12.04-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 12.04 Precise Server ISO 64bit" {
    set isofile="/iso/ubuntu-12.04-server-i386.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
#    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile 
#    initrd (loop)/casper/initrd.lz
    linux (loop)/install/vmlinuz boot=file=/cdrom/preseed/ubuntu-server.seed iso-scan/filename=$isofile vga=788
    initrd (loop)/install/initrd.gz
#  kernel /install/vmlinuz
#  append  file=/cdrom/preseed/ubuntu-server.seed vga=788 initrd=/install/initrd.gz quiet --

}

menuentry "Ubuntu 12.04 Precise mini ISO 64bit" {
    set isofile="/iso/mini.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
#    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile 
#    initrd (loop)/casper/initrd.lz
    linux (loop)/vmlinuz iso-scan/filename=$isofile vga=788
    initrd (loop)/initrd.gz
#  kernel /install/vmlinuz
#  append  file=/cdrom/preseed/ubuntu-server.seed vga=788 initrd=/install/initrd.gz quiet --
}

menuentry "Try ms_lts_precise_r4 without installing" {
    set isofile="/iso/ms_lts_precise_r4.iso"
loopback loop (hd2,4)$isofile 
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=$isofile quiet splash --
    initrd    /casper/initrd.lz
}


menuentry "Fedora-17 ISO 64bit" {

    set isofile="/iso/Fedora-17-x86_64-Live-Desktop.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/isolinux/vmlinuz0 fromiso=$isofile root=live:$isofile rootfstype=auto ro liveimg  rhgb rd.luks=0 rd.md=0 rd.dm=0 
    initrd (loop)/isolinux/initrd0.img
}


menuentry "Kubuntu 11.04 Natty ISO 64bit" {

    set isofile="/iso/kubuntu-11.04-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

menuentry "Parted Magic (Boot ISO Image via Grub2) " {
    insmod part_gpt
    set isofile="/iso/pmagic_2012_05_30.iso"
    loopback loop (hd2,4)$isofile
    linux (loop)/pmagic/bzImage iso_filename=$isofile edd=off load_ramdisk=1 prompt_ramdisk=0 rw vga=normal loglevel=9 max_loop=256 vmalloc=256MiB
    initrd (loop)/pmagic/initrd.img
}

menuentry "gparted (Boot ISO Image via Grub2) " {
    insmod part_gpt
    set isofile="/iso/gparted-live-0.12.1-5.iso"
    loopback loop (hd2,4)$isofile
#    linux (loop)/live/vmlinuz live-media=iso=$isofile keyb=us gl_kbd=us gl_lang=en_US gl_numlk=off gl_batch boot=live union=aufs  #toram=filesystem.squashfs noswap noprompt vga=791
#        linux (loop)/live/vmlinuz fromiso=$isofile boot=live noswap
        linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt ip=frommedia findiso=$isofile toram=filesystem.squashfs
    initrd (loop)/live/initrd.img
}
# linux /workdir/vmlinuz fromiso=/dev/sda11/debian-live-6.0.3-i386-lxde-desktop.iso boot=live config BOOT_IMAGE=/live/vmlinuz

menuentry "Boot-Repair ISO 64bit " {
    insmod part_gpt
    set isofile="/iso/boot-repair-disk.iso"
    loopback loop (hd2,4)$isofile
    linux (loop)/live/vmlinuz2 boot=live config union=aufs noswap noprompt ip=frommedia findiso=$isofile toram=filesystem.squashfs
#    linux (loop)/live/vmlinuz2 boot=live config
    initrd (loop)/live/initrd2.img
}

menuentry "Rescatux" {
    recordfail
    insmod part_gpt
    insmod ext2
    set isofile="/iso/rescatux_cdrom_usb_hybrid_i386_486-amd64_0.30b4_sg2d.iso"
    loopback loop (hd2,4)$isofile
#    linux (loop)/casper/vmlinuz2 boot=live config fromiso=$isofile
    linux (loop)/casper/vmlinuz2 boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd2.lz
}

menuentry "SystemRescue CD on hard drive" {
              set root=(hd2,4)
              linux   /sysrcd/rescuecd subdir=sysrcd setkmap=us
              initrd  /sysrcd/initram.igz
} 


menuentry "Reboot" {
    reboot
}

menuentry "Halt" {
    halt
}

```

---

### Post by iaw4 on 2012-08-30
>  While that would be nice, the issue is every ISO has different parameters. So you cannot mount them all the same.

why not?  if my computer can boot the iso file if it were burned on a CD, my computer surely can do the same in principle from an iso file.  ok, it would be nicer if we could add command line arguments, and/or have some popular default choices (rescue, single-user, single-user readonly).

the whole grub2 system is outdated.  I am trying right now to transfer a linux system from one drive to another.  the filesystems are easy enough to cp (via -ax).  it is only grub that requires contortions.

OSX shows how to do it right.

you hold down the "ALT" key during boot time, and some ini bootloader scans all available partitions for operating systems.  then it presents a menu of what you can possibly boot.  done.  want to boot a new OS?  attach the hard drive that contains it, and it will simply show up on a list of choices.

now, linux does not have control over BIOSes, of course, but every linux grub-like boot loader could have a stage 1b minisystem, which is always executed first.  then, this stage 1b minisystem has some smarts.  if the user holds down a key---any key---it could scan for bootable systems.  once it presents a list, we would want the ability to enter optional boot parameters.  finally, it would start the real boot process.

grub complications, sooner or later, are a serious problem for non-experts.

/iaw

---

