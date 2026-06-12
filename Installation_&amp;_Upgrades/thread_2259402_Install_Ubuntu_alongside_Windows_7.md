---
title: "Install Ubuntu alongside Windows 7"
date: 2015-01-04
forum: Installation &amp; Upgrades
---

### Post by virgilcaine232 on 2015-01-04
I'm trying to install Ubuntu alongside Windows 7, but the option for a dual boot installation does not show up as Windows 7 is not regognized by the ubuntu installer. I made sure the system boots in uefi mode and secure and fast boot should be turned off. I just ran boot-repair, but still no luck.
My boot-repair url is [http://paste.ubuntu.com/9670890/](http://paste.ubuntu.com/9670890/)

Any help would be greatly appreciated!

Thanks
v.caine

---

### Post by Impavidus on 2015-01-04
Although there are entries for Windows in the EFI partitions on both hard drives, there are no Windows partitions. So, there is no Windows installed on your computer.

---

### Post by yancek on 2015-01-04
So which boot option did you select when installing Ubuntu?  As indicated above, you have efi files for windows and Ubuntu on both your hard drives but no windows partitions.  You would be better off using the manual option in Ubuntu referred to as Something Else.  Is that what you did?  You've overwritten your windows partitions.  The link below is a tutorial on installing Ubuntu 14.04 and has a step be step using Something Else as an option.  Hope you have the windows installation medium if you still want windows.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by virgilcaine232 on 2015-01-04
Thank you for your replies! 

There is only one hard drive  installed in my computer. I ran the boot-rapair from a ubuntu live usb  drive. Windows 7 is still working perfectly fine.

I did not install ubuntu yet, because I am afraid I could loose my windows partition and I am not really familiar with the partitions needed for linux if I chose the manual installation, but I guess this is what I will have to do, right?

---

### Post by virgilcaine232 on 2015-01-04
I am sooo sorry! I just looked at the boot-repair protocol and found out that I had a typo in the link :sad:
The right address is [http://paste.ubuntu.com/9670899/](http://paste.ubuntu.com/9670899/)

I am very sorry about this and I hope you could maybe have a quick look at the right file...

---

### Post by yancek on 2015-01-04
You have windows installed in the master boot record and also have an efi partition with windows efi files.  That's a little weird as you should not have both.  You need to decide if you are going to use efi or mbr when installing Ubuntu.  The link below explains dual-booting windows with Ubuntu efi. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2015-01-04
Since drive is gpt and you have an efi partition, Windows is booting in UEFI mode. Not sure how or why you have a Windows boot loader in the gpt protective MBR. If you try to boot in BIOS mode it will read MBR and give a bootmgr missing error as it cannot boot in BIOS mode.

Use Windows own partition tools to shrink Windows and make room for Ubuntu. Reboot Windows immediately and let it run chkdsk and repair itself.

Links previously posted are good for installing.
You should make a complete backup of Windows and the efi partition. Then even the worst type of error has a way to recover from.

More links & info in the link in my signature.

---

### Post by virgilcaine232 on 2015-01-05
Do you think Windows 7 is not detected by ubuntu due to the Windows boot loader? Is there any way to get rid of it?

---

### Post by oldfred on 2015-01-05
The boot loader in the MBR is not seen nor used.

Is Windows hibernated?
Or it may just need a chkdsk. 
Even though my old XP would boot, I could not see it from Linux. After a chkdsk it booted a bit faster and then working in Ubuntu.

---

### Post by virgilcaine232 on 2015-01-07
Everything worked out fine! After manual partitioning and installation.   The Grub bootloader found the windows 7 installation and I am now able   to boot both systems!
Thank you for your help!

---

### Post by oldfred on 2015-01-07
Great. :)

Please change status to solved.

---

