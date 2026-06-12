---
title: "Making Windows partitions available to Ubuntu"
date: 2006-04-09
forum: Installation &amp; Upgrades
---

### Post by walterius on 2006-04-09
Hi! I am new to Ubuntu (just installed it last night) and Linux. I am also an old Windows hand. I have a multiboot Windows system consisting of five partitions, and I want to make three of them available in Ubuntu (Windows ME, Windows 2000 Pro, and My Documents).

I had the partition numbers available to me briefly when I was installing Linux, but no longer have them. I cannot find them in Windows or Partition Magic.

How can I find them so I can mount them (sudo, etc.) in Linux?

Many thanks. P.S.: so far, I love Ubuntu! :p 

Walterius

---

### Post by renzokuken on 2006-04-09
have a look in System -> Administration -> Disks

that should tell you the partition numbers. you can also mount them here by creating a folder in /media for each partition and mounting them to that point.

if you want the partitions to mount on boot, then you will have to edit your fstab file ( /etc/fstab )

search the forums for a guide on this, they can explain it much easier than i can

---

### Post by RRS on 2006-04-09
System>Administrations>Disks>Partitions

This will list all the patitions on your hard drive. By clicking thru the list you'll be able to view the properties of each.

Edit: Gotta learn to type faster :)

---

### Post by Bartender on 2006-04-09
walterius -
I'm guessing you have at least 3 different file systems on your HDD - FAT32 (Me), NTFS (W2K), and ext3 (Ubuntu).
You do know about the limitations, right?  You can't just go mucking about inside of an NTFS file system from within Linux.  I'm not sure of the exact line in the sand.  I think that with some tweaking you can *see* your NTFS-based files, but you don't want to try writing to them.

Oh, yeah, Welcome to Linux!!

---

### Post by walterius on 2006-04-09
Thank you all! You are most helpful! :KS 

Here are my Windows partitions, all are FAT32:

Windows ME *
Windows 2000 (MSFT Office XP) *
Windows 2000 (MSFT Office 2000)
Windows 2000 (MSFT Office 97)
My Documents *

and the two Linux partitions

* These are the ones I want to access in Ubuntu.

I will use what you have told me and post again when I have succeeded (or crashed and burned).

Walterius :p

---

### Post by renzokuken on 2006-04-09
is "My Documents" a part of Windows ME or Windows 2000 (MSFT Office XP)?

if it is on the same partition as either of these installations then there is no real need to mount it seperately. Mounting a windows harddrive makes it possible to see EVERYTHING on that drive so access to My Documents will simply be a case of navigating through a few of you Windows folders

---

### Post by walterius on 2006-04-09
The My Documents partition is just that: Windows sees it as a separate HDD. I set it up that way--gives all OS's the same access to the same documents.

Walterius :confused:

---

### Post by walterius on 2006-04-09
Following the instructions in "Installing Ubuntu," I got all five Windows partitions visible in Ubuntu.

I named their Ubuntu folders after their partition numbers: windowsa1, windowsb5, etc. However, I don't like that. I want to name them after their Windows functions: WINME, WINNT, O2000, O97, and MYDOCS. How can I do that? I can't find anything on renaming folders. In fact, is there anything good to read on file management? Most of it remains a mystery to me.

Walterius :confused:

---

### Post by Papa-san on 2006-04-11
[QUOTE=renzokuken]

if you want the partitions to mount on boot, then you will have to edit your fstab file ( /etc/fstab )

search the forums for a guide on this, they can explain it much easier than i can[/QUOTE]

This thread was a result of my search of the forums...
Was wondering if you could explain the steps of editing the fstab file to a nOOb who has a habit of doing these things wrong...

Thanks!

Oh, I should say that XP is on c:/ drive. My D:/ drive has some XP overflow, and the partition that contains Ubuntu. (As well as swap partition.) None of the guides I have seen go there...

---

### Post by aysiu on 2006-04-11
[QUOTE=Papa-san]
Was wondering if you could explain the steps of editing the fstab file to a nOOb who has a habit of doing these things wrong...[/QUOTE] First, where you enter commands:

Ubuntu: Applications > Accessories > Terminal
Kubuntu: KMenu > System > Konsole

Guides:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by walterius on 2006-04-16
It's solved. See this thread:

[http://www.ubuntuforums.org/showthread.php?t=160094](http://www.ubuntuforums.org/showthread.php?t=160094)

Many thanks to all. :D

---

