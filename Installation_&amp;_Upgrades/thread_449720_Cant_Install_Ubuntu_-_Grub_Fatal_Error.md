---
title: "Cant Install Ubuntu - Grub Fatal Error"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by Tippmann5150 on 2007-05-20
First off, sorry. i am pretty bad with linux and ubuntu. I had Wubi on my laptop for a while and loved it, but my laptop is old, and I wanted to put ubuntu on my desktop. I downloaded the live CD, and when it was 94% installed, an error came up saying that there was a fatal error installing GRUB.

My system has a Pentium 4 2.6GHz processor, 480MB RAM, Windows XP SP2, a new MAXTOR 160GB internal hard drive, which I partitioned off with a section intended to put ubuntu on, and the rest for extra space for windows, the original 40GB drive (which I use to boot).

Im not sure what other infor to give right now, so let me know and ill get it

Thanks a million!

---

### Post by ntetreau on 2007-05-20
What is the exact error you get?

Nic

---

### Post by TheGuru on 2007-06-12
I just got the exact same error. At 94% of the Feisty Fawn installation process using a CD that I ordered from this site and successfully installed on a different PC an error simply saying that there was a Fatal Error installing GRUB. No more, no less.

I had XP Pro installed on an NTFS partition, an ext3 partition for Ubuntu and a different NTFS partition for documents etc. When I ran the installer, all I did was change the install location to the ext3 partition and the setup formatted it, then I left all the other settings at default.

I'm about to retry the install.

UPDATE:

It worked the second time. I used the same settings for install, and i formatted the ext3 partition again. Upon first boot of Ubuntu it performed an error check of the hard drive and fixed several errors.

---

### Post by ciuci on 2007-10-31
i am getting the exact same error!! i tried installing it a million times!! each time the same thing!! can anyone rescue me??

---

### Post by ciuci on 2007-10-31
> **ciuci said:**
> i am getting the exact same error!! i tried installing it a million times!! each time the same thing!! can anyone rescue me??

i was referring to the 7.10 version!

---

### Post by ciuci on 2007-10-31
> Executing 'grub-install (hd0)' failed.

This is a fatal error.
this is exactly what the error says ... i tried installing it once again, just to see the exact error text ... hope it helps those who want to help!

---

### Post by ciuci on 2007-11-01
heloooooooooo, is there anyone here?

---

### Post by traderpats on 2007-11-01
It would probably help if you posted your current setup.  That is, what drives you have and their locations i.e. internal, usb, and such, current OS etc.

---

### Post by ciuci on 2007-11-02
here are screenshots of the partitioning tables of my two hard drives... on hda1 i have Windows Vista installed! ... both hd's are local internal IDE drives ... most common thing a HD can be :)

---

### Post by spaccount on 2007-11-07
Hi,
[INDENT]I had the same problem! I tried installing gutsy last night, and am stuck at the last stage with a  *grub installation failure*. I'm trying to install this on a Dell Inspiron 6400 laptop. It is already loaded with XP. I had partitioned the disk before installing xp to make space for ubuntu. So this is how it looks.

[INDENT]
1. Primary Partition: 10GB - Windows XP 
2. Primary Partition: 6 GB - This is where I'm trying to install ubuntu, I do this by manually selecting the drive.
3. Extended Partition: This spans the rest of the harddisk and has been split into 4 logical drives[/INDENT]

I checked the Advanced screen for Grub install, there the field is populated with: hd0

Even after multiple install failures, I'm able to boot back into WindowsXP, which kind of makes sense as Grub could not install at all!

a. Any ideas? 
b. Also, do I need to restart the install from scratch to come to the Grub screen, or is there a way to skip to the last screen?
c. Perhaps some terminal commands?

[/INDENT]

Thanks!

---

### Post by Bashed on 2007-11-08
Same problem here (alternative DVD x64)

I have Vista x64 on sda1, sda2 is 1GB meant for swap and sda3 is 10GB meant for linux / partition (root).  The regular DVD install doesn't even boot at all due to my modern nvidia video card (many replicated this problem too with nvidia laptops/desktops).

---

### Post by Scottydahotty61 on 2007-11-08
yo im getting this same problem
im trying to install gutsy gibbon (7.10).
i have three partitions of my drive, one that is like 70 GB for my windows xp, one that is around 15 GB for Ubuntu, and one that is 1 GB and is a linux swap partition. 
ive mainly had help from one of my friends at school, but he doesnt know what to do about this fatal error by the grub installer. 
ive tried going to advanced settings and changing the (hd0) to (sda1) which is the actual name of my windows partition
but that didnt work
i need help

---

### Post by mrcoffee09 on 2007-11-17
I've got the same one, i just need the command to make the partition of my hard drive the default boot, i dont care if i cant load windows.

---

### Post by jken146 on 2007-11-17
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Hope this helps!

---

