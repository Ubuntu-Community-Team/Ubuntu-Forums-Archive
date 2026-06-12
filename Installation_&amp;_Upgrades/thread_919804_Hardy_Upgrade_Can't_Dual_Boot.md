---
title: "Hardy Upgrade Can't Dual Boot"
date: 2008-09-14
forum: Installation &amp; Upgrades
---

### Post by Macrosystems on 2008-09-14
First off, I apologize if this is the wrong section/forum/format.
I recently installed Ubuntu on my laptop. I was dual booting Windows XP and Gutsy Gibbon for a while, but decided to upgrade to Hardy Heron this morning. Everything seemed fine until I restarted and grub no long listed XP. I tried changing menu.lst, but when I try and boot XP it loads the stupid ThinkVantage Rescue and Recovery software. What to I do? I can still access the files from ubuntu but I cant boot windows. 

In case it helps, the laptop is IBM Thinkpad T61p.

Thanks it

---

### Post by sjbaugh on 2008-09-14
I am not an expert, but it may help to look at the partitions that are actually installed on your machine. You can get Gparted from the repositories or its website (use Google!). Gparted is a graphical utility but you need to start it from a terminal using sudo. If in doubt don't do it and BE VERY CAREFUL and don't change anything unless you know what you are doing as you could completely toast your system!

Steve

---

### Post by Sef on 2008-09-14
>               **Re: Hardy Upgrade Can't Dual Boot**
 I am not an expert, but it may help to look at the partitions that are actually installed on your machine. You can get Gparted from the repositories or its website (use Google!). Gparted is a graphical utility but you need to start it from a terminal using sudo. If in doubt don't do it and BE VERY CAREFUL and don't change anything unless you know what you are doing as you could completely toast your system!

Steve     To look at your partitions do this, which is much safer:

Applications > Accessories > Terminal

paste or type in this code:

```
sudo fdisk -l
```small L;  paste the results here.

---

### Post by Macrosystems on 2008-09-14
Thanks Sef,
I think the problem is that the upgrade removed IBMs rescue and recovery partition. The thinkpad laptops comes with the recovery software on a seperate partition which is no longer there. But I still don't understand why I can't boot XP.

sudo fdisk -l returns:
/dev/sda1               1       26129   209881161    7  HPFS/NTFS
/dev/sda2   *       38156       38913     6085800   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3           26130       37661    92630790   83  Linux
/dev/sda4           37662       38155     3968055    5  Extended
/dev/sda5           37662       38155     3968023+  82  Linux swap / Solaris

Thanks

---

### Post by caljohnsmith on 2008-09-15
When you are in Ubuntu, try this:
```
gksudo gedit /boot/grub/menu.lst
```
Find your Windows entry in that file, and change it to:
```
title  Windows
root   (hd0,0)
makeactive
chainloader +1
```
That should work, but let me know how it goes.

---

### Post by Sef on 2008-09-15
> Thanks Sef,
I think the problem is that the upgrade removed IBMs rescue and recovery partition. The thinkpad laptops comes with the recovery software on a seperate partition which is no longer there. But I still don't understand why I can't boot XP.
I wanted to make sure that you still had XP on your system.

> Partition 2 does not end on cylinder boundary.

See if [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") will resolve that problem.

---

