---
title: "Question about installing windows 7"
date: 2012-01-04
forum: Installation &amp; Upgrades
---

### Post by davidq25 on 2012-01-04
Hi, I have Ubuntu installed on my laptop, but I wanted to install Windows 7 alongside Ubuntu.
While trying to install Windows 7 from a CD, I got an error along the  lines of: "Windows 7 cannot be installed on disc 0 partition 1". What's  the problem? How can I solve this?
 
Thanks for the help

---

### Post by fantab on 2012-01-04
> **davidq25 said:**
> Hi, I have Ubuntu installed on my laptop, but I wanted to install Windows 7 alongside Ubuntu.
While trying to install Windows 7 from a CD, I got an error along the  lines of: "Windows 7 cannot be installed on disc 0 partition 1". What's  the problem? How can I solve this?
 
Thanks for the help

Windows, by default tries to install itself on the first partition and since you have Ubuntu on it you get this error. Also the Ubuntu partition has ext4 or ext3 or any other Linux specific  file system which windows does not recognize.

If you have an option to reinstall Ubuntu, I suggest that you install Windows first and then install Ubuntu. This scheme is a better option when dual booting with windows.

[**See this **]("http://members.iinet.net.au/%7Eherman546/index.html")for more instructions on Dual Boot with windows.

---

### Post by davidq25 on 2012-01-10
> **fantab said:**
> Windows, by default tries to install itself on the first partition and since you have Ubuntu on it you get this error. Also the Ubuntu partition has ext4 or ext3 or any other Linux specific  file system which windows does not recognize.

If you have an option to reinstall Ubuntu, I suggest that you install Windows first and then install Ubuntu. This scheme is a better option when dual booting with windows.

[**See this **]("http://members.iinet.net.au/%7Eherman546/index.html")for more instructions on Dual Boot with windows.

How can I just install Windows and remove Ubuntu?

---

### Post by fantab on 2012-01-11
> **davidq25 said:**
> How can I just install Windows and remove Ubuntu?

Since you have running UBUNTU and if you cannot do without WINDOWS, then I recommend DUAL BOOT.
Just follow the steps and you will be fine. 


[LIST]
[*]BACK UP your important DATA.
[*]Download and Create a [**GParted Live CD**]("http://gparted.sourceforge.net/livecd.php"). You should boot it at start up, just as you would boot OS Installation Disk. After that you should find out what PARTITION TABLE is there on HDD. It should be DOS. If it is not then DELETE all the Partitions and CHANGE  the Partition Table to DOS.
[*]Create your partitions on HDD as you prefer. Format the Partitions and exit.
[*]INSTALL WINDOWS.
[*]INSTALL UBUNTU. Remember you should INSTALL GRUB to /dev/sda only.
[/LIST]

---

### Post by Mark Phelps on 2012-01-12
> **davidq25 said:**
> How can I just install Windows and remove Ubuntu?

If you don't want to dual-boot, then just boot from an Ubuntu desktop CD, and choose Try Ubuntu.

Once the desktop loads, use DASH to find Disk Utility and launch that.

Use that to remove all the partitions.

Then, when you reboot with the Win7 DVD, it should install without problems.

---

### Post by darkod on 2012-01-12
> **fantab said:**
> Windows, by default tries to install itself on the first partition and since you have Ubuntu on it you get this error. Also the Ubuntu partition has ext4 or ext3 or any other Linux specific  file system which windows does not recognize.

If you have an option to reinstall Ubuntu, I suggest that you install Windows first and then install Ubuntu. This scheme is a better option when dual booting with windows.

[**See this **]("http://members.iinet.net.au/%7Eherman546/index.html")for more instructions on Dual Boot with windows.

Even windows is not that dumb. You can select to install to what ever partition you want.

Did you create a ntfs partition for windows first? Or you simply tried to install it to your linux partition in which case of course it will fail.

It doesn't have to be the first partition but it does need to be ntfs and primary partition.

You need to create unpartitioned space and then create one ntfs partition from it. Then run the windows installer and just select to install on that partition.

---

