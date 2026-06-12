---
title: "What does 'Kernal Panic Not Syncing' mean?"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by Melbourne Guy on 2008-04-02
I was interested in seeing what Ubuntu would do and if it really could replace Win Xp so I am attempting to boot from the CD to get an overview.

But all I get is the initial Ubuntu screen then this message pops up

MP-Bios bug 8254 timer not connected to IO-APIC Kernal Panic - not Syncing: IO-APIC Timer doesnt work boot with APIC=debug and send report then try booting with the 'noapic' option

Some details I am loading form a CD supplied from EPOCH Labs in Melbourne so the disk is probably OK the Desktop PC is as follows;
ASUS M2N-MX SE Motherboard, AMD Athlon 64 dual processor, 2 Gig of mem, SATA Maxtor hard drive , SATA Pioneer DVR212.

Win XP is loaded on this PC and seems to run ok (as good as Windows gets of course)

I would love to see what UBUNTU 7.10 looks like does everybody run into these kind of problems? One of the posts went into a few pages of technical detail to give a 'fix' for this problem with the proviso that you had to do this EACH TIME you made updates to the Kernal?

It seems to me that if it was Windows there would be a 'patch' that would be downloaded 'once'.

Is there anybody out there who could give me a hint if there is a  premanent solution? 
Frustrated non user

---

### Post by dstew on 2008-04-02
The first thing to check is the CD integrity (if the boot gets that far). If the CD is OK, you probably have a problem with the CD linux kernel interacting with your hardware. You can try the Alternate Install CD, which uses a text-based installer. Or, you can try kernel parameters.

To use Live CD kernel parameters, press F6 at the opening menu. It looks like your problem may be with the interrupt processor, so try these parameters:```
noapic
nolapic
```If that works, you can install and see if Ubuntu boots OK. Often, the kernel parameters are needed for the Live CD, but not for the installed Ubuntu system. If they are needed, however, you can put them in the boot statements in the /boot/grub/menu.lst file to make a permanent fix.

---

### Post by enjoy777 on 2008-04-05
> **dstew said:**
> The first thing to check is the CD integrity (if the boot gets that far). If the CD is OK, you probably have a problem with the CD linux kernel interacting with your hardware. You can try the Alternate Install CD, which uses a text-based installer. Or, you can try kernel parameters.[quote]

I have the same problem what Melbourne Guy wrote. I try to install Ubuntu 7.10 and now Kubuntu 8.04 beta but in both of the installers I have got this error. Bot ISO file I download from ubuntu.com and kubuntu.com.

To use Live CD kernel parameters, press F6 at the opening menu. It looks like your problem may be with the interrupt processor, so try these parameters:```
noapic
nolapic
``` 

Yes I set noapic parameter and installation for kbuntu works good. But after installation I try to boot my new kubuntu from HD but I have got above error. I would like to know how to add noapic parameter to bootloader when I can go inside files on my HD. The last step what I can see is my GRUB menu. When I start with one of GRUB option the error apears.

---

### Post by dstew on 2008-04-05
> I would like to know how to add noapic parameter to bootloader when I can go inside files on my HDThe simplest way is to edit the /boot/grub/menu.lst file. First, use the grub edit function to put the boot option on the command line, so you can get into your Ubuntu system. Highlight the Ubuntu OS you want to boot at the grub menu, but do not press 'enter', press 'e' instead. Then, highlight the kernel line, press 'e', and add the boot parameter to the line. Press 'enter', then 'b' to boot. Once Ubuntu is started, you need to edit your menu.lst file to make the change permanent. To do that, open the file in the gedit text editor: ```
gksudo gedit /boot/grub/menu.lst
```Find the line below the **## ## Start Default Options ##** separator near the top that starts with **#kopt**. At the end of the line, add the boot option you want. Do not uncomment the line (leave the # at the beginning). Then, save the file. On a command line, enter```
sudo update-grub
```That should take care of it. Reboot to see if it works.

---

