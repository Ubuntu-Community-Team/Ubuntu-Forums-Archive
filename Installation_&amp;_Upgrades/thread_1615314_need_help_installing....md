---
title: "need help installing..."
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by ilovechi23 on 2010-11-06
Hi guys, I've always been a fan of Linux and decided to run it on my laptop. But I ran into a problem. When I started the installation I did side by side... well my daughter starting pressing keys while I wasnt looking and the installation wasnt complete. When I tried to reinstall it didnt give me the side by side option only use entire disk or partition the disk. That's where I'm lost at. Ive attached a screenshot so you can see the allocate screen. Thanks in advance. Oh and still wanted to run it side by side also.

---

### Post by P4man on 2010-11-06
Is the 11GB the partition you wanted to install ubuntu on? 
Either way, I dont like it that it doesnt tell how much free space you have on your main partition and that sda3 would be ntfs. If that is where you tried installing ubuntu on, it cant be ntfs.

May I suggest booting windows and running chkdsk /f. Maybe something went wrong resizing the windows partition.

---

### Post by ilovechi23 on 2010-11-06
I don't know where it was installing to... I had did the memory slide when selecting side by side... and when I did chkdsk /f but it flashes so fast I can't see nothing... i guess this is kinda bad

---

### Post by P4man on 2010-11-06
in windows, open a terminal (cmd.exe) and type in 

chkdsk c: /f /r

It will probably tell you it cant do it now and ask you to do it on the next boot. Confirm that and reboot.

Also verify in storage management (or is that disk management) if windows see the three partitions and if you can ready any of them. I suspect the 11GB will be unreadable, but thats probably okay.

---

### Post by ilovechi23 on 2010-11-07
So I did the chkdsk and after two hours it was done. Then I checked the disk management and it shows my c: saying its healthy and two other partitions that are healty also. One partition is 1.46GB and 10.24GB for the other partition. So now what?

---

### Post by sikander3786 on 2010-11-07
> **ilovechi23 said:**
> So I did the chkdsk and after two hours it was done. Then I checked the disk management and it shows my c: saying its healthy and two other partitions that are healty also. One partition is 1.46GB and 10.24GB for the other partition. So now what?
So if Windows is working just fine, its time to install Ubuntu. But you'll need to do a bit of manual partitioning this time. You'll need to delete sda3, the 10.24GB partition and split it into 2 partitions manually from the Ubuntu installer.

Delete sda3.

On the unallocated space, click Add and allocate it 8GB space (or whatever space you can afford, the maximum possible), Filesystem=ext4, and set the mount point as '/'. It will hold the base install, your home folder and all the necessary boot files.

On the remaining unallocated space, click Add and allocate all of the space to a Swap partition. Filesystem=Swap.

You don't need to change any other settings. Just go on with the installer and Grub should see Windows 7 just fine for dual booting.

---

### Post by ilovechi23 on 2010-11-07
Ok I'm gonna try in the morning and let you know

---

### Post by ilovechi23 on 2010-11-07
Hey just a quick update ... I woke up and did all the steps and got it installed successfully side by side. Thanks for all the help guys

---

