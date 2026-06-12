---
title: "I have no Operating System now due to partitioning problems! PLEASE HELP!"
date: 2006-04-23
forum: Installation &amp; Upgrades
---

### Post by michaelzhao on 2006-04-23
I did a very stupid thing this morning. I went to Partition Magic and decided to install a new Operating System. So, I decided to install Ubuntu Linux 5.10. So, I made the new partition and set the new Linux partition as a primary partition! 

This is the biggest mistake I have ever made in my computing experience. I tried installing Ubuntu, but it is not detecting the new Linux partition I made. So I gave up and tried restarting Windows MCE. However, because I set the new Linux ext 2 partition as a primary partition. I can't even load up Windows! What should I do? I can't get into any partition. I can't load up an operating system. Also I can't install Ubuntu!

As a reference, I have the Ubuntu Live CD. That might help. 

PS: I really don't want to reformat my computer. I should have all the files backed up, but I don't. My second major mistake. I have vital files on that computer that I cannot afford to lose.

---

### Post by dermotti on 2006-04-23
Does grub load up?

---

### Post by marcos89 on 2006-04-23
well, what I would do is to boot up the Ubuntu LiveCD open up a terminal and run:


mkdir windows
sudo mount -t vfat /dev/hda1 windows/
sudo nautilus windows/

i think the password is   "ubuntu" for the livecd, i dont remember.
and there you will be able to browse all of your files :-)

---

### Post by Sef on 2006-04-23
Do you have access to another computer? If so, download these three rescue disks, one of them should help you.

[http://trinityhome.org/trk/]("http://trinityhome.org/trk/")

[http://www.ultimatebootcd.com/index.html]("http://www.ultimatebootcd.com/index.html")

[http://sysresccd.org/Main_Page]("http://sysresccd.org/Main_Page")


> I went to Partition Magic

Don't use Partition Magic.  It and Linux don't get along well.  Use the partitioner on the install disk.

---

### Post by michaelzhao on 2006-04-23
Okay, I do have access to another computer. So I am going to download the 3 rescue disks. 

As for installing GRUB. I cannot do that because I don't even have a partition to install GRUB to. 

As for you Marcos89. That is most excellent you can do that. However, I was wondering if I could actual edit the partition table within Linux so I can actuallly boot up Windows once more.

---

### Post by Toon81 on 2006-04-23
> Don't use Partition Magic. It and Linux don't get along well. Use the partitioner on the install disk.

I've tried installing three different Linuxes so far, namely: Mandrake 10 (currently called Mandriva), Fedora Core 1, and Ubuntu, and all three had excellent partitioning tools. In fact, all partition problems I have ever had were results of my using PM. I second Sef wholeheartedly.

What I sometimes do is partition my disks from Windows XP with its built-in partitioner and then format them with the installer, that seems to work fine as well.

---

### Post by RavenOfOdin on 2006-04-24
I tried using Partition Magic on XP and it absolutely sucked . . .

---

### Post by microthorne on 2006-04-25
Hi,

I'm assuming you have access to a second system as you are online posting in the forums.  If you have access to a CD Burner, you could try downloading a 'gparted' liveCD.  It starts up xwindows with a partitioner which might allow you to fix your issue.

Gparted Home Page:
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Gparted ISOs:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

GParted Screenshots:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

HTH, Good luck!
-Thorne

---

### Post by Sef on 2006-04-26
Here's one to recover lost data and partitions.

[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

---

### Post by matelot on 2006-04-26
[QUOTE=Toon81]... What I sometimes do is partition my disks from Windows XP with its built-in partitioner and then format them with the installer, that seems to work fine as well.[/QUOTE]

Can XP partition itself from its own single partition? I've a 160Gb HDD single partition. I've downloaded *gparted* for use later, but would be interested in what XP can do to itself. Looking under *Disk Management* I didn't seem to think so. I'd like to be wrong on this occasion... :mrgreen:

---

### Post by Sef on 2006-04-27
> Can XP partition itself from its own single partition?

You can't partition a mounted partition.  Hence you couldn't use XP to partition itself.

GParted or QtParted could partition your hard drive though.

---

### Post by frodon on 2006-04-27
**michaelzhao**, your problem is just that after a failed ubuntu installation and if you reach at least the partition step the boot sector is put on the linux partition and because the install failed this partition is unusable and therefore you get this error when you start your computer.
The solution is quite simple, boot again on the ubuntu install cd and go to the partition step, edit your windows partition manually, put the boot sector on it then save & quit, and all should be like before you began to install ubuntu.
[IMG]http://users.bigpond.net.au/hermanzone/p3/9ntfs.gif[/IMG]
[IMG]http://users.bigpond.net.au/hermanzone/p3/10ntfs.gif[/IMG]

---

### Post by kyle_charest on 2006-04-27
hi if you have a windows cd, i would reformat your hard drive and use the partioner through microsoft while installing, and from there you can sut-up your partitions. I had to reformat and reinstall windows reciently due to a few bad clusters. but everything is working with boot up, buy my problem is that kubuntu freezes after login...oh well

---

