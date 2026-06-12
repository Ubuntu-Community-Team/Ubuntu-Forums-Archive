---
title: "Complete Linux Noob problem"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by gvansly1 on 2008-07-11
Hi, Complete noob here...I'm trying to istall Ubuntu (64bit) on a system that already has a dual boot Vista/XP. Vista and XP are on a seperate SATA drive while I'm trying to install Ubuntu on a seperate IDE drive. The drive has been formatted using the NTFS file system. I used a windows based program called Easy BCD that allows multiple Operating Sytems to be booted using the Windows Boot Manager.
When I boot up, my options are Vista/XP/Neo Smart Linux.
When I select the Linux option I get the following:

Unrecognized Partition Table For Drive 80
Please Rebuild It Using A MicrosoftCompatible FDISK Tool**(Err=23)**
Current C/H/S = 16383/240/63 (Hd0,0)
File System Type is NTFS Partition Type 0x7
Config file /NST/menu.lst
find--set-root--ignore floppies /boot/grub/menu.lst

Can someone with patience please assist me in getting this resolved. I'm looking forward to learing/using the linux O.S.

---

### Post by VMC on 2008-07-11
> **gvansly1 said:**
> Hi, Complete noob here...I'm trying to istall Ubuntu (64bit) on a system that already has a dual boot Vista/XP. Vista and XP are on a seperate SATA drive while I'm trying to install Ubuntu on a seperate IDE drive. The drive has been formatted using the NTFS file system. I used a windows based program called Easy BCD that allows multiple Operating Sytems to be booted using the Windows Boot Manager.
When I boot up, my options are Vista/XP/Neo Smart Linux.
When I select the Linux option I get the following:

[COLOR="Red"]Unrecognized Partition Table For Drive 80[/COLOR]
Please Rebuild It Using A MicrosoftCompatible FDISK Tool**(Err=23)**
Current C/H/S = 16383/240/63 (Hd0,0)
File System Type is NTFS Partition Type 0x7
Config file /NST/menu.lst
find--set-root--ignore floppies /boot/grub/menu.lst

Can someone with patience please assist me in getting this resolved. I'm looking forward to learing/using the linux O.S.

I'm not sure I understand how you installed ubuntu. We'll get to that in a moment. First EasyBCD can boot Linux partitions, you need to read their info on how to map for Linux. It's in there docs. I used it once. I prefer Grub, it can handle all your needs. Now back to your drive setup. I've heard of several people having trouble with mixing SATA and PATA drives, which your doing. Lets see how things stack up for the monent though.

Boot using the ubunt livecd. Then go to "Applications > Accessories > Terminal"

From the Terminal a DOS like box will open. Then the following exactly as I have listed:

```
sudo fdisk -l
```

That way we can see how your drives are ordered.

---

### Post by gvansly1 on 2008-07-11
VMC,

Hey thanks for the reply, however I don't have the livecd... I burned an ISO from the download site.....and there is no Applications-Accessories-Terminal.....option available per your reply.

Good news though....I finally got it to work by deleting the Grub and Linux options from the Easy BCD Windows application, then reinstalled Ubuntu from the ISO burned Disc, however this time around I changed the Boot Drive sequence in the BIOS so that the drive that I wanted Ubuntu installed on was the first boot drive....I then "manually configured" the Partition Step of the Ubuntu installation process (Step 5), deleted the listed partition, created a new one as "/", installed the software.....rebooted (using the new boot sequence) The GRUB installer started and my options are now Linux or windows, when I select windows the Windows boot loader starts (using the setup from Easy BCD) and my options are Vista/XPPro....

Therefore I'm a happy camper.....Thanks for your timely response...This is my first experience with Linux OS and will probably have more posts....

---

### Post by Bakon Jarser on 2008-07-11
Glad you got it working.  Just so you know, that .iso you burned is the livecd.  It's called that because you can run ubuntu from it without installing it to a hard drive.

---

### Post by Sealbhach on 2008-07-11
Nice one.

It's a good idea, if you're doing a manual partition, to create two partitions:

/ (root) - about 12GB should do.

/home - as much space as you like

+ a small swap partition (about 2x your ram)

That way, if you want to upgrade, you don't have to start all over again... everything in your /home folder (documents,files, settings) will remain after you have upgraded.


.

---

### Post by gvansly1 on 2008-07-12
Thanks Bakon, did not know this, I assume then I would be able to somehow run it parallel to a Windows installation to resolve issues?


Great idea Sealbhach.....I did not do that however, I just installed it, so I will reinstall as instructed. Is the (swap) preceeded with the /

---

### Post by Sealbhach on 2008-07-12
> **gvansly1 said:**
> 

Great idea Sealbhach.....I did not do that however, I just installed it, so I will reinstall as instructed. Is the (swap) preceeded with the /

No, it's just called "swap" and the partition type is also "swap".

The / and /home partitions should be "ext3".


.

---

### Post by gvansly1 on 2008-07-12
Sealbhach,

Thanks again will do as instructed, also how do I get Ubunt to recognize my thumbdrive?

---

