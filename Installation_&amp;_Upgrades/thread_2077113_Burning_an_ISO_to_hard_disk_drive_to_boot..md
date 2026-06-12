---
title: "Burning an ISO to hard disk drive to boot."
date: 2012-10-27
forum: Installation &amp; Upgrades
---

### Post by Drop D on 2012-10-27
Hello all. 

I bought a Macbook Pro recently and have been using that nearly exclusively.  Without much use for my old Windows 7 netbook anymore, I decided to go back to Ubuntu.  One minor problem, though.  When I booted up Windows 7 on my netbook, I got a "BOOTMGR not found" error message.  Without thinking of it too much, I decided to completely forget Windows 7.  

On to the actual problem now; because I have no CD drive (netbook, mind you) I have no way of actually using an Ubuntu CD.  I am, however, in possession of a hard disk drive that can hold an ISO image.  

Is there a way I can burn an ISO image to a hard disk drive on my Mac so I can then boot from that drive on my netbook? 

If not, I will just buy or borrow a USB CD drive. I don't want to spend money, though! Thanks all.

---

### Post by oldfred on 2012-10-27
Bootmgr not found is an issue with the Widows partition. Usually Windows installs to two partitions and the first is just a hidden 100MB boot/repair partition that calls the bootmgr from the main partition. Have you tried f8 from BIOS screen to see if you can get into Windows repair console?

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

I do not know how from a MAC. And it may not be possible as Mac use an older UEFI boot not MBR.

But you can just install grub2's boot loader to a drive and use a simple grub.cfg menu entry to loop mount an ISO file directly.

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

### Post by RayChangTW on 2012-10-27
D

---

### Post by funicorn on 2012-10-28
Yes you can, but only for Ubuntu 12.04 Image and later. But burning an Image to a hard  disk drive is not a good idea, instead you'd better use a flash drive.

Just use *dd* to write the image file to the flash disk, then boot the computer from it. 
```

sudo dd if=Ubuntu.iso of=/dev/sdc bs=4M

```An alternative way is to write grub2 stage 1 to some hard drive, put the image file to some partition , then boot from the hard drive and then boot LIVE system from the image file. In this case it's not limited to 12.04 nor higher. You can use Ubuntu 10.04 for example. The basic syntax in grub2 cli to boot from an ISO file is 
```

set root=(hd1,X)
loopback loop /Ubuntu.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/Ubuntu.iso --noeject --
initrd (loop)/casper/initrd.lz
boot

```And to write grub2 state1 to some hard drive, you must have a copy of that and use *dd* again.

---

### Post by Androzani1 on 2012-10-28
> **Drop D said:**
> Hello all. 

On to the actual problem now; because I have no CD drive (netbook, mind you) I have no way of actually using an Ubuntu CD.  I am, however, in possession of a hard disk drive that can hold an ISO image.  

Is there a way I can burn an ISO image to a hard disk drive on my Mac so I can then boot from that drive on my netbook? 

If not, I will just buy or borrow a USB CD drive. I don't want to spend money, though! Thanks all.

I don't think a HDD is capable of booting from an ISO, so either try a flash drive if you have one or use your mate's CD drive.

---

