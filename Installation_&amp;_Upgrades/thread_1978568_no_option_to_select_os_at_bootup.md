---
title: "no option to select os at bootup"
date: 2012-05-12
forum: Installation &amp; Upgrades
---

### Post by Philbe on 2012-05-12
When i boot my computer it boots straight into windows 7. I have installed Ubuntu 12.04 on my laptop the only way i can boot into Ubuntu is to press f12 at boot up and select the usb drive from there i have a option to select windows or Ubuntu is there a way to create a boot menu without having the usb disk connected to have a option upon starting the computer?

Thank you for your time I hope i am not duplicating a question i have not being able to find a simular question. 
Again thanks for you time :)

-Phil

---

### Post by wilee-nilee on 2012-05-12
Sounds like the Ubuntu bootloader, grub, was put in the usb drives mbr. Download this link in Ubuntu or from a Ubuntu live cd extract it to your desktop and run this command and post the results.txt

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by klompa on 2012-05-13
Hi this is the same as what is happening to mine but I have 3 hdd 1 for window,  1 for storage and 1 for ubuntu and installed from a live cd.  I have had the previous version of ubuntu installed and boot menu working so i don't know whats up.

I hope I uploaded the result.txt alright.

cheers for any help.

---

### Post by darkod on 2012-05-13
> **klompa said:**
> Hi this is the same as what is happening to mine but I have 3 hdd 1 for window,  1 for storage and 1 for ubuntu and installed from a live cd.  I have had the previous version of ubuntu installed and boot menu working so i don't know whats up.

I hope I uploaded the result.txt alright.

cheers for any help.

It looks good. Select in BIOS to boot from /dev/sdb, the second disk, as first option. That's where grub2 is and what you should boot first. All of your disks are 500GB so you might have problems telling them apart in BIOS, but you will get there if you try them one by one, if all else fails.

Also, on /dev/sda1 you have some /grldr files that shouldn't be there. I wonder if this is part of some old bootloader and what could be creating your confusion.

Otherwise all looks good and you should be getting the correct grub2 boot menu.

To the OP, all you have to do is boot ubuntu using the bootloader on the usb stick once, with F12 like you are doing it, then open terminal and run:
sudo fdisk -l (small L)

That will list your disks and partitions. Note which disk is your hdd (for example it should be /dev/sda) and which your usb (like /dev/sdb).
Once you know which is your hdd, simply run:
sudo grub-install /dev/sdX (replacing the X with the correct letter).

That will install the bootloader on the MBR of your internal disk. After that you should be OK booting without the usb.

---

### Post by klompa on 2012-05-13
Cheers mate that worked just switched the hdd boot priority.   As for the /grldr file I have tried mint 12 and ubuntu 11.something they must of put the boot loader their and got left when i did the boot repair for windows.

thanks again

Steve

---

