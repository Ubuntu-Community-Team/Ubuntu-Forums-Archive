---
title: "Help with USB stick process"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by pete_m on 2010-05-15
I'm an EEE PC user planning an imminent move Ubuntu Karmic to  Lucid  .  .
in the hope of performance improvements and the benefit of tying in to a fresh LTS release.
I'm hoping to use USB creator to be able to try things out on other computers - and to proselytise the Open Source/ Ubuntu alterative.

I've put some work into my existing Ubuntu install based on 9.10 karmic nbr2 and am very happy with the results - full credit and thanks to all . .

First screenshots - more soon - of my work in progress at
[http://www.youtube.com/watch?v=YoI4wRVVjBs](http://www.youtube.com/watch?v=YoI4wRVVjBs)

I'm still comparitively new to Linux so any observations and guidance will be much appreciated ..

I've been using remastersys to create iso images and these have run successfully in 
VirtualBox. 

My Lucid iso does not run in VirtualBox (yet ?! ) so I haven't yet tried to put it on a stick.  .
tho' perhaps this only a VBox issue . .
 i've read about a patched kernel that addresses the issue. and a hint to disable AdvancedPowerControlManagement( or something )  in the VM.
Any ideas how to do that ?

In the meantime I have successfully used USB-creator with the EB4 netbook variant which is based on Debian Sid and it ran fast and stable for a day.

This was on the second attempt after reading of a hint that one should not( yet ? ) ask for persistent storage . .

Does anyone know what is the state of play here . . both for karmic and lucid ?

I've come across and installed live-helper but i'm not sure exactly what it is & how to use it. 

Again any observations and guidance will be much appreciated.


Thanks

---

### Post by oldfred on 2010-05-16
There seem to be multiple ways to install to a USB flash drive. While the USB creator works and Ihave used it, I prefer two choices. One is to dedicate a USB flash to ISOs and directly boot as many as the flash will hold. Another is to have a full Ubuntu install on the flash (may require larger flash drive.

MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntuforums.org/showthread.php?t=1451184](http://ubuntuforums.org/showthread.php?t=1451184)
[http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback](http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback)

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

---

### Post by pete_m on 2010-05-17
Thank you Fred for those very useful links much appreciated.

It makes the prospect of working with multiple systems much less daunting.

If you have any observations as i embark on this they will be most welcome.

I'll try to get my stick equipped as per the tutorial with the lua scripting for auto-detecting isos or at least have the grub.conf version working. This should leave me with a stick that is a hybrid between the two choices you mention - choosing at grub time between the installed system( presently eb4) and a number of ISOs ( Masonux f'rinstance )

Presumably one can use these grub instructions to enable a similar multi-boot from ISO system on a main drive ( or other external drive). .

After a round of working with the present instructions and a 4Gb stick - leaving the present eb4 system( which I like ) and adding a number of ISOs . .

What I think I'll try for is a 16Gb stick  ( they seem to be keeping up or running ahead of Moore's Law for price and storage).

partitioned as 

sda FAT32 Main .. ISOs and current -file  only boots from ISOs - mounted as home when booting 'vanilla' or 'patched' . .

sdb ext2 'vanilla'
sdc ext2 'patched'

Union FS system for sdb & sdc - as per the original EEE PC Xandros scheme. This may be overkill given that one can always restore from vanilla ISO, but i think it  might be useful if when patching and one needs to correct a mistake or roll-back a stage, for the vanilla system to be physically present . .

the USB installed system on sdb/c will mount the FAT partition as home and will ( eventually ! ) be the GRUB default . .


sdx ext2 swap

I envisage such a stick being able to 'audition'  for a particular target computer.  .
Run Live images & choose a suitable iso

Install this to USB as vanilla . .make changes as needed( on patched)
Install patched to target system - we passed the audition !!

Best Regards.

---

### Post by oldfred on 2010-05-17
I will attach my grub config. Note that I had to for some reason use ISOs where everyone else used ISO, so I am not consistent with other instructions. My last entry for Dariks does not work, but all the other do. MC4GB is my microcenter 4GB USB flash.

/media/MC4GB/boot/grub/grub.cfg
```
menuentry "Ubuntu 10.04 64bit" {
    set isofile="/boot/ISOs/ubuntu-10.04-desktop-amd64.iso"
 
    loopback loop $isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu 9.10 64 bit" {
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

menuentry "Darik's Boot and Nuke" {
 loopback loop /boot/iso/dban-beta.2006042900_i386.iso
 linux (loop)/ISOLINUX/DBAN.BZI nuke="dwipe" silent --
}

```

---

### Post by pete_m on 2010-05-17
hi Fred,
Thanks for that .cfg file...

Do you have the lua scriptiing stuff happening ?
 Reckon it'd be worth the extra hassle ?

i'll let you know how I get on - currently grappling with disappeared nautilus desktop icons.

This happened after I installed a bunch of alternative WM's thinking that such a choice may be useful for the audition !

There's a thread about this phenomenon . . [http://ubuntuforums.org/showthread.php?t=1468771&page=2](http://ubuntuforums.org/showthread.php?t=1468771&page=2)2 in case you're interested and/or knowledgeable about that side of things . .

Best,,

---

