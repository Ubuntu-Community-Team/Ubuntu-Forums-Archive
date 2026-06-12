---
title: "external hard drive questions"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by tim.is.awesome on 2008-11-26
i have a few questions.


1. if i have ubuntu installed on an external hard drive, and it is plugged in when the computer is off, if i turn on the computer with it plugged will it start up ubuntu without the BIOS setup or anything? and when it is unplugged from the computer, it will start up windows.  (i tried to word that as easily as possible)


2. if ubuntu is installed on the external hard drive. can i still use the hard drive on windows?


thank you ahead of time.

---

### Post by caljohnsmith on 2008-11-26
> **tim.is.awesome]1. if i have ubuntu installed on an external hard drive, and it is plugged in when the computer is off, if i turn on the computer with it plugged will it start up ubuntu without the BIOS setup or anything? and when it is unplugged from the computer, it will start up windows. (i tried to word that as easily as possible)[/QUOTE]
To do that you would have to make sure Grub gets installed to the MBR (Master Boot Record) of the external drive, and also you would have to set your BIOS so that the external drive is first in the BIOS boot order said:**
> 2. if ubuntu is installed on the external hard drive. can i still use the hard drive on windows?
Yes, in Windows you can use either of the following programs to access ext3 paritions:

ext2fsd program: [http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)
ext2ifs: [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

Or if you set up a shared NTFS/FAT partition between Ubuntu and Windows, no extra software is necessary. Good luck and let us know how it goes.

---

### Post by zwygart on 2008-11-26
1. If your BIOS is setted to Yes, if not you will have to set up the setup.:)

The BIOS is what makes your computer boot. Essentially it keeps the date and time. Also it decide which drive to boot from. This mean the BIOS has a list off drives to boot and it tries one by it one until one works. If your external harddrive is before your internal harddrive in the list, it will boot from. If not, it will boot your Windows. If your exterenal is first in the list but not plugged, then it is unbootable and the BIOS will continue in his list until Windows.

Resume : If you don't know what a BIOS is, make some research. To make it easy, your external drive should be before your internal. May be it is, so your happy, may be it's not so change it. 

2. You can access windows partition from Ubuntu. You CANNOT access ubuntu partition from Windows (except you install the program like caljohnsmith  suggested). You will be able to boot Windows.

If you want to be able to use your external harddrive from windows, I suggest you partition it in a FAT partition where you put the files you want to share and another partition ext? where Ubuntu is. 

If you don't understand me and want to install Ubuntu then paste the output off 
```
sudo fdisk -l
```
from a linux terminal (on LiveCD or something) and your drive plugged in.

Hope this helps.

To copy from a terminal : select the text
press CTRL + SHIFT + C
In the post press CTRL + V

---

### Post by tim.is.awesome on 2008-11-27
thank you guys. :)

---

### Post by Pumalite on 2008-11-27
After your installation is finished and before rebooting; edit your external drive's menu.lst and make 'groot' and 'root' (hd0,0)
(When you boot your USB; that drive will be considered the first drive)

---

### Post by tim.is.awesome on 2008-11-28
OH GOD! i messed up bad. now when i start up my computer it shows the dual boot screen. I DONT WANT DUAL BOOT. i already got yelled at for that. how do i get rid of this and fix it? now i cant start my computer without the external hard drive plugged in. AND i cant start ubuntu. wtf?!? i need help bad.

---

### Post by caljohnsmith on 2008-11-28
OK, you don't have to panic, your problem should be easy to fix. How about booting your Live CD, open a terminal (Applications > Accessories > Terminal), and do:
```
sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
```
That will install a Windows MBR (Master Boot Record) to your internal sda drive so you should be able to boot straight into Windows if your external drive is unplugged. Then to install Grub to the MBR of your external drive:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Then when you start up your computer, if you set your BIOS to boot the external drive, you should get Ubuntu; if your external drive is unplugged and you set your BIOS to boot the internal Windows drive, you should boot straight into Windows as you did before. Give it a shot and let me know how it goes.

---

### Post by tim.is.awesome on 2008-11-28
i did everything you have said in the codes.(thank you by the way) now it says: 

Probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$ 


should i wait? or is it already done

---

### Post by caljohnsmith on 2008-11-28
Once you do the "sudo grub", after it is done "probing devices" you should get the "grub>" prompt and can do the rest of the grub commands. Did you get that far? How about posting the output of all those commands.

---

### Post by tim.is.awesome on 2008-11-28
ok. i know what i did. i thought that it was still "probing all devices" when its been done this entire time :D


and this is what i got at the end:

```

ubuntu@ubuntu:~$ sudo apt-get install syslinux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
syslinux is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 141 not upgraded.
ubuntu@ubuntu:~$ sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 records in
0+1 records out
404 bytes (404 B) copied, 0.0252842 s, 16.0 kB/s
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$

```

---

### Post by tim.is.awesome on 2008-11-29
i got everything working fine except for one thing: automatically starting up ubuntu or windows.


when i start up my computer and go to BIOS, i set my external hard drive first then internal second. but when i save and exit it and the computer starts back up, it says some thing like 
```
GRUB
ERROR 18

``` or something like that. what does this mean and why does it do this?

---

### Post by caljohnsmith on 2008-11-29
A Grub error 18 typically happens when you have a BIOS that can't access anything on your HDD past either 8.5 GB or 137 GB, depending on how old the BIOS is. The best way to fix that problem is to reinstall Ubuntu, but create a ~200 MB ext partition at the very beginning of the drive, and then when you go through the Ubuntu installation, set the mount point on that partition as "/boot". That way all of Ubuntu's boot files will be at the beginning of the drive and within reach of your BIOS. How about trying that and let me know how it goes.

---

