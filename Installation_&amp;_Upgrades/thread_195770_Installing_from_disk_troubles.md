---
title: "Installing from disk troubles"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by oedipuss on 2006-06-13
Hello

I've tried installing ubuntu 6.06 on an old laptop, on which the cd is broken. 
Presumably this can be done following [this guide]("https://wiki.ubuntu.com/Installation/FromHardDriveWithFloppies") from the official ubuntu wiki . 

So far I've copied the image to the laptop's disk, dd'ed the image to a partition and copied 'vmlinuz' and 'initrd.gz' from that partition's /casper/ directory to my primary partition (which will be root).

When trying to boot though, using a grub boot disk, I'm entering the kernel /vmlinuz command as I see it in the cd's /isolinux/isolinux.cfg file, ie : ```


 kernel /vmlinuz  append   boot=casper initrd=/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
```

ommitting quiet and splash to see what's happening.
It then tries to mount a cdrom, I think, because sometimes when it detects the drive, it produces a series of CDROM not accessible or such =( 
When the drive isn't detected the installation stops , and drops me to a shell.. 

How could I make the script look for the cd in /dev/hda3 instead of the (broken) cdrom ? (that's where the image is dumped, it is mountable as a cd) According to the above guide it should normally ask me what the cdrom device is , in case it doesn't find one..

Thanks

---

