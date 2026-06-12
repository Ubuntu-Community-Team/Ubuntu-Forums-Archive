---
title: "Confusion with New Hard Drive"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by geovino on 2007-03-02
I just installed a WD 80GB sata hard drive today. First time I've added a new sata drive, and with this drive I see that you don't have master/slave anymore. So when I installed my live cd of 6.10 it saw the new 80gb drive and my 160gb Winxp drive. I selected the new 80gb drive to install Ubuntu and it smoothly installed. But when it rebooted it went to WinXP without showing a boot loader screen with the choice to go to Ubuntu or WinXP. So I rebooted went into the BIOS and went to boot sequence and see that the 80gb is and sda hd0 drive and WinXP is the sdb hd1 drive. So I selected the sda Ubuntu drive to boot first since the 160gb was selected before. When I rebooted WinXP came up again, didn't make a difference. Why would that happen? What happened to the bootloader? 

Do I have to go back in with the live cd and change the bootloader in the install section some way?

---

### Post by taurus on 2007-03-02
Did you install GRUB to /dev/hda (hd0)?

---

### Post by geovino on 2007-03-02
That is what I think happened. I assumed that my original 160gb was the hdd0 but after going back into WinXP and looking at disc management, the new 80gb became the hdd0 and the 160gb WinXP is now the hdd1 . So it looks like the bootloader was put in the new 80gb that Ubuntu is on and not the WinXP drive which is now hdd1. 

How do I correct this?

---

### Post by confused57 on 2007-03-02
> **geovino said:**
> That is what I think happened. I assumed that my original 160gb was the hdd0 but after going back into WinXP and looking at disc management, the new 80gb became the hdd0 and the 160gb WinXP is now the hdd1 . So it looks like the bootloader was put in the new 80gb that Ubuntu is on and not the WinXP drive which is now hdd1. 

How do I correct this?

The live cd can be used to install grub to your mbr:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

If you're able to get grub installed to your Ubuntu drive's mbr, you can add an entry to boot Windows, similar to what's described in this thread:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

While you're booted into the live cd, you might want to open a terminal(Applications--Accessories--Terminal), post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

Also, before you even do any of the above & have a spare cd-rw laying around, you might want to burn a copy of the Super Grub Disk(500 kb download):
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
see "Super Grub Disk" in the index, this site has excellent information about grub, mounting, etc...

---

### Post by geovino on 2007-03-03
Thanks for the info, but I solved the problem...

I went back into the BIOS and I saw that my changes to make the 80gb hd0 boot first was not selected as I thought. The 160gb hd1 was still in the first position. Once I changed the boot sequence to having the hd0 drive boot first (that's the one with grub installed to it) the bootloader came up and I was able to get into Ubuntu. And Winxp was displayed on the list.

Problem Solved :)

---

