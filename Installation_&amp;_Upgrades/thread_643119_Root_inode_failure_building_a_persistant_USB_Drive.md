---
title: "Root inode failure building a persistant USB Drive"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by rchille on 2007-12-17
Hello all,

I bought a 4GB Pen drive ([http://reviews.cnet.com/usb-flash-drives/pny-attach-usb-flash/4505-3240_7-31753262.html](http://reviews.cnet.com/usb-flash-drives/pny-attach-usb-flash/4505-3240_7-31753262.html))  Friday with the intent of installing 7.10 Gutsy on it.

I was following these directions here:
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

I made it through the install with out much trouble (I did have to install lilo on it as the noted at the bottom to make it bootable). The final product has all the functionally of a normal gutsy livecd, but additionally it should have a persistent mode via casper.

When I try to boot from the persistent option I get and error that says I have a root inode failure on my casper partition and it dumps me into ash.

The strange thing is if I plug the drive into my computer I can see and access both partitions and a e2fsck comes up clean (no bad sectors or corrections)

I can boot the drive as if it was a CD and everything looks good too (and can read partitions fine too). It only seems to be a problem when trying to boot into the persistent mode. 

Any suggestions?

---

### Post by rchille on 2007-12-17
As usual, I stumbled upon something interesting only after I posted my question :(

This is from Herman from elsewhere in the forums: [http://ubuntuforums.org/showthread.php?t=611763&highlight=casper&page=3](http://ubuntuforums.org/showthread.php?t=611763&highlight=casper&page=3)

> 

 Hello tech9,
Quote:
Thanks for attaching the files I need. I do realize that it is best to get everything from the repositories, but I am behind a proxy... I think that may have something to do with it. I have already installed ntlmaps so that I can still run sudo atp-get
Okay, sorry about that, I wanted to put that message there though, mainly for other people who may also be reading this thread. I don't want to be setting a bad example that others might follow, hence the warning.
Quote:
well, my qustion now is I see the the linux boot file is named completely different in 710 than in 704 . The name of 710 boot file is ldlinux.sys and 704 is syslinux.cfg.
I extracted the two files syslinux.cfg & isolinux.txt in the root of my USB drive.
Is there something that I am missing?
when I try to boot the stick, I receive an error message saying "Error loading operating system.
Did you install syslinux to the MBR of the flash drive or to the first sector or the ubuntu710 partition?

Quote from the how-to,
Quote:
12 Remove and Re-insert your flash drive
13 Back at the terminal, type apt-get update
14 Type apt-get install syslinux mtools
15 Type syslinux -sf /dev/sdx1
That would install syslinux to the first sector of the ubuntu710 partition, to install syslinux to the MBR of the USB disk, you would need to do,
15 (b) Type syslinux -sf /dev/sdx
Code:

syslinux -sf /dev/sdx

Actually, with my own particular USB setup, I didn't run into that problem because I made mine a little different. Mine has Super Grub Disk for USB in the first partition and installed to the flash drive's MBR and the ubuntu and casper-rw partitions are after that. I edited Super Grub Disk for USB's menu.lst to chainload syslinux in the first sector of the flash drive's ubuntu partition.
I also added lines in my regular (internal hard drive's) Ubuntu's GRUB menu to chainload either the MBR of the USB, (Super Grub DIsk for USB), or the second partition in the USB, syslinux, which boots ubuntu in the USB.

Anyway, tech9, just try installing syslinux to MBR as well as to the partition of your USB flash drive and see if it works then.

Or try chainloading the USB's first partition from your installed GRUB and that should work too.

EDIT: I just re-tried this myself and the advice about installing Syslinux to MBR is incorrect, you will get this, "syslinux: this doesn't look like a valid FAT filesystem".
As the how-to suggests, you can install LiLo to MBR in the USBdisk instead, (or GRUB, or Super Grub Disk like I did.)

Will that help you or did I guess wrong about what your problem might be?

Regards, Herman 


The part that interest me is:
> 
Did you install syslinux to the MBR of the flash drive or to the first sector or the ubuntu710 partition?

Quote from the how-to,
Quote:
12 Remove and Re-insert your flash drive
13 Back at the terminal, type apt-get update
14 Type apt-get install syslinux mtools
15 Type syslinux -sf /dev/sdx1
That would install syslinux to the first sector of the ubuntu710 partition, to install syslinux to the MBR of the USB disk, you would need to do,
15 (b) Type syslinux -sf /dev/sdx

```

syslinux -sf /dev/sdx

```


Anyone think this might be my trouble as well? Sadly my drive is at home so I have no way to test right now.

---

