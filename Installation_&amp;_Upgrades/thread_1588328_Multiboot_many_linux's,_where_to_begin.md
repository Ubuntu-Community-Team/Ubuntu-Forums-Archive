---
title: "Multiboot many linux's, where to begin?"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by xenosaga01 on 2010-10-04
Hi, I am new to using Linux. I want to try multiple copies of Linux at the same time. I also plan on keeping my windows. I have 2 harddisk drives. A 500gb for my Windows, and a 180gb drive for the linux installations. The first version of Linux I intend to install is Ubuntu 10.04.1 desktop 64bit. The second is Debian 5.05 64bit. I was wondering if someone could first tell me how I should make my partition on the hdd for the multiboot?

---

### Post by andrewthomas on 2010-10-04
It might be easier to install Debian first, then Ubuntu using the side-by-side option.

---

### Post by oldfred on 2010-10-04
I put my data into a common /data partition and mount it into each install. (I created script from history of manually doing it first time). I create several 20-25GB system partitions and if just upgrading will copy settings from /home but do not share /home at all. You do have to decide which system will be the "master" and have its grub controlling boot. With 2 drives you could have different boot loaders in each drive, but I like to have the boot loader in a drive boot a system on that drive so each drive can be booted just incase the other fails.

Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments by Morgan Hall
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions (post #5) of data linking from above blog, based on more from comments 
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

If sharing with window you will also want a shared NTFS partition for firefox profile, thunderbird profile and other data you may also want in windows. Then all your bookmarks & emails will be the same in every system including windows.

---

### Post by snowpine on 2010-10-04
You can install VirtualBox and test multiple distros at the same time, each in its own window. :)

---

### Post by xenosaga01 on 2010-10-04
I dont want any of them to share resources. I just want to have them all installed along side eachother, and be able to have a bootmenu that I can select which OS I want to boot at start.

---

### Post by xenosaga01 on 2010-10-08
is there any way to make Windows see my vista and all the linux OS's. I only want 1 menu to select what I want to boot at startup. grub is a bit scary for me. I had a bad experience with it in the past.

---

### Post by snowpine on 2010-10-08
> **xenosaga01 said:**
> is there any way to make Windows see my vista and all the linux OS's. I only want 1 menu to select what I want to boot at startup. grub is a bit scary for me. I had a bad experience with it in the past.

Ubuntu now uses the GRUB2 bootloader, which has many improvements over GRUB. I suggest conquering your fear if you want to have a pleasant Ubuntu experience. Or, use VirtualBox as I suggested above. :)

---

### Post by andrewthomas on 2010-10-08
> **snowpine said:**
> Ubuntu now uses the GRUB2 bootloader, which has many improvements over GRUB. I suggest conquering your fear if you want to have a pleasant Ubuntu experience. Or, use VirtualBox as I suggested above. :)
+1 grub2 is pretty solid

---

### Post by zpliang on 2010-10-08
> **xenosaga01 said:**
> Hi, I am new to using Linux. I want to try multiple copies of Linux at the same time. I also plan on keeping my windows. I have 2 harddisk drives. A 500gb for my Windows, and a 180gb drive for the linux installations. The first version of Linux I intend to install is Ubuntu 10.04.1 desktop 64bit. The second is Debian 5.05 64bit. I was wondering if someone could first tell me how I should make my partition on the hdd for the multiboot?

I suggest the following tech path:[LIST=1]
[*] Make one of your flash disk bootable. Maybe Gparted live is suitable for you. try your favorite bootloader on your flash drive.
[*] Choose any friendly-to-you boot loader. I use grub4dos(just grldr+menu.lst in fact). Old-fashioned, and simple grammar, reversible. Good for multi-boot without overwriting windows MBR.
[*] Try booting a smallest linux system from vmlinuz and initrd.gz on windows partition without installing anything. Try chainloading to your windows boot loader so that you can always go back. Try booting to your recovery partition if any.
[*] GPartEd live can modify partitions while keeping data. 
[*] When install, try to leave a small partition for vmlinuz's and initrd's. use "root=" kernel argument to boot your system.
[*] Puppy linux can live in a few files and doesn't hurt anything in windows. You may want to try it. (Before that I have never seen a word processor start up in a blink!:lolflag:)
[*] *something I don't know*
[/LIST]

---

