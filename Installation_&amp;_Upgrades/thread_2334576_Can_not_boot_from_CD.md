---
title: "Can not boot from CD"
date: 2016-08-20
forum: Installation &amp; Upgrades
---

### Post by Tommy_Atkins on 2016-08-20
All,

I have a System 76 Ratal machine running 14.04 with all updates applied. 
It reboots from the hard drive with no problems. I can not get it to recognize the new 16.04 CD (or any other CD for that matter) when it is placed in the machine.
After restarting the PC and doing the ctrl-s it shows the following:
LAN : IGAGE slot ooc8 v13g1
SATA : Port 3 ATAPI : HAS124 C : PORT 0 : Boot Drive
SATA : PORT 6G0 : St1oooDM003-1CH162 : PART 0 : BootDrite

If I run /select  the CD in the Line starting LAN It loads/runs  the DHCP Intel Boot Agent for a time gives an error No boot name received, reads in the disk and then eventually stops with no message.
With either of the other selected it may load the CD, making some reading noises and stops.

I have no idea how to give it a boot name or what is the matter. and would appreciate any help.

Tom Atkins

---

### Post by sudodus on 2016-08-22
Welcome to the Ubuntu Forums :-)

The Ubuntu iso files are too big for CD disks. They need a DVD disk. Or did you mean DVD, when you wrote CD?

-o-

- Did you check with md5sum that the iso file was downloaded correctly?

- How did you create the boot disk?

- When the computer is running: what can you see, when you insert the boot disk into the CD/DVD drive? Can you see directories and files, one single file or nothing at all?

---

### Post by Tommy_Atkins on 2016-08-22
It was a DVD. I did a checksum on the disk I created and it was OK. I did not do it on the one I purchased.
When the computer is running and I insert the DVD (which  is marked as a 16.04 LTS 32/64 install disk)
it shows as an ISO Image disk with a  boot folder and  a boot catalog.  Boot contains grub and iso folders.
The iso folder contains  two desktop 16.04 iso files one 32bit and the other 64 bit. Grub contains 4 folders and 
2  grub. files one . config and thee other .config.~  
 config contains
 # Put MultiDisk Folder on Desktop|$CD Desktop|/Desktop$ grub-mkrescue --output Ubuntu-16.04-desktop-i386-amd64.iso MultiDisk

# Derived from /boot/grub/loopback.cfg from ubuntu-16.04-desktop-i386.iso and ubuntu-16.04-desktop-amd64.iso


menuentry "Try Ubuntu without installing (32-bit)" {
    loopback iso /boot/iso/ubuntu-16.04-desktop-i386.iso
    linux   (iso)/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=/boot/iso/ubuntu-16.04-desktop-i386.iso quiet splash --
    initrd  (iso)/casper/initrd.lz
}
menuentry "Try Ubuntu without installing (64-bit)" {
    set gfxpayload=keep
    loopback iso /boot/iso/ubuntu-16.04-desktop-amd64.iso
    linux   (iso)/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=/boot/iso/ubuntu-16.04-desktop-amd64.iso quiet splash --
    initrd  (iso)/casper/initrd.lz
}
menuentry "Install Ubuntu (32-bit)" {
    loopback iso /boot/iso/ubuntu-16.04-desktop-i386.iso
    linux   (iso)/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity iso-scan/filename=/boot/iso/ubuntu-16.04-desktop-i386.iso quiet splash --
    initrd  (iso)/casper/initrd.lz
}
menuentry "Install Ubuntu (64-bit)" {
    loopback iso /boot/iso/ubuntu-16.04-desktop-amd64.iso
    linux   (iso)/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity iso-scan/filename=/boot/iso/ubuntu-16.04-desktop-amd64.iso quiet splash --
    initrd  (iso)/casper/initrd.lz
}
menuentry "Check disc for defects (32-bit)" {
    loopback iso /boot/iso/ubuntu-16.04-desktop-i386.iso
    linux   (iso)/casper/vmlinuz  boot=casper integrity-check iso-scan/filename=/boot/iso/ubuntu-16.04-desktop-i386.iso quiet splash --
    initrd  (iso)/casper/initrd.lz
}
menuentry "Check disc for defects (64-bit)" {
    loopback iso /boot/iso/ubuntu-16.04-desktop-amd64.iso
    linux   (iso)/casper/vmlinuz.efi  boot=casper integrity-check iso-scan/filename=/boot/iso/ubuntu-16.04-desktop-amd64.iso quiet splash --
    initrd  (iso)/casper/initrd.lz
}
menuentry "Test memory" {
    loopback iso /boot/iso/ubuntu-16.04-desktop-i386.iso
    linux16 (iso)/install/mt86plus
}

I did run the memory test from this disk for about 1 1/2  hours. No problems found.


Can I just reformat the disk, do a fresh install, and then restore from a copy of my /home directory?

I seems that it would be easier and less time consuming. 

Thanks for your help.

Tommy Atkins

---

### Post by sudodus on 2016-08-22
It is a grub and iso system. Such a system boots from 'mass storage devices' like hard disks drives and USB pendrives. But I am not sure that it was made to boot from a CD/DVD drive. I never tried that (maybe it works).

Where did you get that system (iso file or image file)? And what method did you use to install it into the DVD disk?

---

### Post by Tommy_Atkins on 2016-08-22
I downloaded the iso file from Ubuntu's WEB sit. I also purchased one on the internet.
When I first installed Linux I replaced the original Ubuntu Linux version  on my System 76 machine
with an ISO file from Ubuntu's WEB site for 14.04 LTS with no problem and have been running it for
 several years. The install was done from a DVD and runs booting from the Hard Drive.

Tommy Atkins

---

### Post by sudodus on 2016-08-23
I am sorry, but I am confused and do not understand what is your original problem.

- Does the installed system (in the internal drive) work correctly?
- or does the installed system (in the internal drive) work correctly, except that it cannot *read* from the DVD drive?
- or is the installed system bad and must be replaced?

-o-

- Why do you want to boot from the DVD - do you want to upgrade to a newer version of Ubuntu, or are there problems with the current installed system? Or are you curious and want to test something new?

- Is the problem, that you cannot *boot* from any of the DVD disks with Ubuntu? In that case, have you tried to boot another computer from these DVD disks?

It is quite common, that there are hardware problems with DVD drives, and if that is the case, you will probably have better luck, if you try to boot from a USB pendrive. See the following links,

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

There might also be problems with UEFI - for example that the DVD disk with grub and iso (described in post #3) can only boot in BIOS mode, and your computer is set to boot in UEFI mode. See the following link

[Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

---

### Post by Tommy_Atkins on 2016-08-23
I wanted to upgrade to the 16.04 LTS version of UBUNTU.
The results of running   [COLOR=#333333][FONT=UbuntuMono]test -d /sys/firmware/efi && echo efi || echo bios is bios.
I got this command from the ubuntu 
[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]"Test if running in UEFI mode" entry in the help.ubuntu.com file. 
  [/FONT][/COLOR]

---

### Post by sudodus on 2016-08-24
Running in BIOS mode should make it easier (than running in UEFI mode) :-)

1. ***Try to find out if the CD/DVD drive is working***.

- Can the installed system *read* these disks (that you are trying to boot from) in the CD/DVD drive?
- Have you tried to boot another computer from these DVD disks?

2. If you cannot be sure, but you suspect, that the CD/DVD drive is damaged, you can ***create a USB boot drive, and try to boot and install that way instead***. See the following links,

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

My favourite tool to create USB boot drives is [mkusb](https://help.ubuntu.com/community/mkusb) (because I made it ;-) ).

Edit: Try with Ubuntu version ***16.04.[COLOR="#0000ff"]1[/COLOR] LTS***, the first point release.

---

