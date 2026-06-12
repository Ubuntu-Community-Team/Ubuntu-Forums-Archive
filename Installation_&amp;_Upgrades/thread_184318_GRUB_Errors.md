---
title: "GRUB Errors"
date: 2006-05-29
forum: Installation &amp; Upgrades
---

### Post by Rochcom on 2006-05-29
I am trying to install a dual boot setup with XP Pro. 

I have XP on physical drive 0 formatted with FAT32, one partititon (160 gig). 
Ubunto is installed on phsical drive 1 (40 gig) with the default two partitions, one for swap.

GRUB is installed on the second physcial drive. It starts correctly when booting from that drive but gives Error 15 (file not found) when attempting to boot any of the Ubuntu configurations.  It gives Error 13 (no executable found) when trying to boot XP.

I looked at a previous post from someone who has an identical setup working.

I used the GRUB built in editing function to confirm that the commands were identical to that user's configuration (except for the version numbers - he had an older version).  

Live CD version works fine. But I cannot boot the hard drive installation or Windows with GRUB. 

I am not sure what to do next.

---

### Post by Jose Catre-Vandis on 2006-05-29
Sounds like you have grub installed on the 1st drives mbr OK, but that grub can't find your ubuntu install correctly.

The second drive should be hdb and if you installed ubuntu on the first partition of hdb then it would be hdb1. in "grubspeak" this is (hd1,0) (although it might be different on you machine, depending on how ubuntu named your partitions. Check your menu.lst in /boot/grub/ to see that the boot listing is correct. Should read something like this:

> title		Ubuntu, kernel 2.6.15-23-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

Otherwise, try re-installing grub using a live CD to setup grub again. There is a good howto here somewhere.

---

### Post by Sutekh on 2006-05-29
You can try this wiki HOWTO too see if you can get GRUB working correctly.

[Ubuntu Wiki - Recovering Ubuntu After Installing Windows]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows")


If you are feeling adventurous, you can use the GRUB command line to try and boot something.  Press 'c' to get to it.

Try the root command and the <TAB> button```
root (hd0,<TAB>
```Are any ext2fs (type 0x83) partitions listed?  Try hd1,<TAB>, etc.

If you find some ext2fs partitions try completing the root command.  So say if (hd0,0) was an ext2fs partition.  The root partition is most likely to be (hd0,0) or (hd1,0).
```
root (hd0,0)
```Next step load the kernel
```
kernel (hd0,0)/boot/vmlinuz<TAB>
```and select the one you want, by typing a bit more and letting <TAB> complete the typing.  

Then try to load the initial ramdisc
```
initrd (hd0,0)/boot/initrd.img<TAB>
```and choose the same version as the kernel.

If all this works
```
boot
``` should finish the process.  

Good Luck!

---

### Post by Rochcom on 2006-05-30
Thanks for your replies.

Since posting, I reinstalled and this time installed GRUB both to the hard drive AND to a floppy.  Everything works fine from the floppy, but I have the same errors as before from the hard drive. Unfortunately, once booted into Ubuntu, the floppy appears, but it will not mount and is thus inaccessible, so I cannot exame the list file. Yike! I will check out the instructions mentioned.

---

### Post by blackweaver on 2006-05-31
had a similar problem; can't remeber the actual grub confgi but if you can boot with your live cd, mount your linux partition, go to the grub folder, am not sure of where it but on one of my linux partitions where i installed grub it might be located in the boot folder; anyway if you find it open the menu.lst file; that's where the boot config are located; i think sukeh has the right of it though; i had a similar problem and could not boot because all the kernels of my previous distros had supprt for my motherboard compiled into them while this kernel has support as a module; what partition is your linux installed? after booting, type fdisk -l if you have something lile /dev/hda5 that's (hd0,4) where hd0 will be hda, hd1: hdb and so on so that if your partition is /dev/hdc3 it must read (hd2,2); by the way in tour initial install did you install grub, if not your config  might be /vmlinuz not /boot/vmlinuz

---

