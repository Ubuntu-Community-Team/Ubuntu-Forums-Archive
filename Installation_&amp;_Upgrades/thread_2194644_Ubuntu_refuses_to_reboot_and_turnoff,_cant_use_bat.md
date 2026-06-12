---
title: "Ubuntu refuses to reboot and turnoff, cant use battery."
date: 2013-12-19
forum: Installation &amp; Upgrades
---

### Post by cube10025 on 2013-12-19
ASUS Republic of Gamers G750JW 

I have tried to install Ubuntu 12.04 a few times. I believe there is a problem with my Hard Drive, it comes with a preinstalled windows 8 and a recovery partition. I cant stand windows 8 and want Ubuntu instead! So I deleted all the partition on the disk. The disk was GPT but I converted it to MBR.

I manage to install Ubuntu but after I install all the updates Ubuntu refuses to reboot or turnoff, I must pull the plug to turn the computer off, and sometimes Ubuntu cant use the battery. Also the installer cant detect Windows installation so I cant choose "install Ubuntu along Windows" the installer shows all the disk as unallocated.
I have tried converting to GPT back to MBR the other way around nothing works...

What is the beast way to deal with GPT disk? Seems I have tried all things...

---

### Post by tfrue on 2013-12-20
I believe that most new Window's computers come with UEFI, which has caused problems with the Linux installations but like always there is a fix. There are several things you can do, so let's being.

Since you already deleted the Window's partitions, you might as well format the drive and format it as a Linux drive and use GRUB. Aside's from that, you will have to decide if you want to keep EFI boot, or give it the boot and go old school. I haven't had to deal with EFI, but I have read some articles over it and I'm glad I haven't had to, but here is a link to getting Ubuntu installed on a computer that supports EFI and it will probably do a lot better of a job at helping you than I can. I would say go the extra mile and keep the EFI boot because who doesn't want the extra security and benefits of new technology.

So click [here]("https://help.ubuntu.com/community/UEFI").

It may also help to update to 13.10, but give that a try first if you want to stick with 12.04

---

### Post by cube10025 on 2013-12-21
Thanks for the answer, I am not to good with EFI GRUP etc, Ubuntu is able to use the battery now at least no problems yet. I notice even if I used gdisk and fix part to remove the GPT,  the Ubuntu installer warns that it detect GPT anyway. So I used HDShredder to wipe the harddrive took 3 hours but it solved the problems with the GPT. Still Ubuntu cant reboot or turnoff but it works better with the hardware i believe, and the installer can now detect windows installations not that I want them... I removed the boot options in BIOS and let Ubuntu use default when I re installed Ubuntu...

---

### Post by cube10025 on 2013-12-22
I installed 13.10 and it works perfect! Thanks for the advice!!!

---

### Post by tfrue on 2013-12-22
No problem friend! You have a great day and don't forget to mark this post as solved.

Chris

---

