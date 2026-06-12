---
title: "Installation Problem stuck at 46%"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by dmorris1 on 2007-12-10
I am trying install ubuntu 7.10 onto my computer. 

When ever i go to install, the computer gets stuck at 46% on scanning devices for the partitioner. I am not sure what is wrong. 

My computer is an AMD Athlon 64 FX-53 processor
and an MSI K8T Neo 2 main board. 

The hard drive is hooked up using IDE and is 200gb in size.

I am not sure what i am doing wrong or what i need to do. I've searched around the forums alot but all the tips don't seem to be working. I am not sure what do to.

---

### Post by Pumalite on 2007-12-10
If you are talking about the first option in the Live CD; you might need some boot parameters. Could also be a bad burn. But, here is a guide and a collection of parameters to try:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317
Good luck.

---

### Post by dmorris1 on 2007-12-10
i read through those links you gave me and im not quite sure which parameters i would need. 

I don't know if this helps at all either but the gparted partitioner can't recognize any disks. I just let it sit there for 15 minutes while it said scanning disks. I don't know if that helps clarify what my problem is.

---

### Post by Pumalite on 2007-12-10
Get Gparted Live CD. Boot from it and take a look.

---

### Post by dmorris1 on 2007-12-10
I got the gparted live cd and booted it. It recognizes my hard drive, and i was able to delete my old ntfs partition and replace it with a new ext3 partition. but Ubuntu itself still won't recognize the disk.

I am currently trying the alternate method by just using text. I am just wondering how long i should expect it to recognize my hardware?

Also as a side note, should i be using the Amd 64 bit live cd or the regular i386 live cd. I've tried both the 64 bit one doesn't boot and the i386 does, but im not sure if that is truly the disk i should be using.

---

### Post by Pumalite on 2007-12-10
I would choose what works.

---

### Post by dmorris1 on 2007-12-10
i rebooted the live cd of gparted and now it won't find any of my drives. Im totally lost on what to do. 

The live cd of ubuntu does recognize it in the Computer folder. so what is going on? why can i not partition it. Could it be some setting i have on the harddrive, im using cable select. Should i make it my primary device in my bios? anything

---

### Post by banda on 2008-01-26
@ dmorris1

hey .. you probably don't need a solution for this now, but i am going to give one anyway for the folks who land up here from google.

solution 1-
disable floppy disk in the BIOS. restart the computer
9 out of 10 times this would fix it, otherwise this may be a drive issue.. 

solution 2

if you have windows, boot into it, type cmd in start>run.  type chkdsk x: /f   

do this for each ntfs partition, replacing x with the drive letter each time


you could also use the windows cd to do the same if you don't have windows.


side note> since chdsk application is the property of microsoft, it cannot be included in ubuntu.

---

