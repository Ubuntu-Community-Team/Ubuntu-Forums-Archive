---
title: "Installed Ubuntu 12.04, but will not start without flash drive used to instal it"
date: 2012-05-24
forum: Installation &amp; Upgrades
---

### Post by liquidxlax on 2012-05-24
Hello, I have recently installed ubuntu 12.04 on my netbook and i'm currently using it right now.

Yet i'm having a problem with the start up and had a problem with installing it.

Since my netbook does not have a cd drive, i had to turn my flash drive in to a boot drive

Initially i used something that was suggested by many to help make a boot drive called 
unetbootin-windows-575.exe which did not work.

Then i found something called XBOOT which worked and allowed me to instal ubuntu. Yet whenever i turn on my netbook without the flash drive plugged in the screen just blinks with a single underscore in the top left corner.

After the netbook has booted the netbook works fine without it.  It seems as if my netbook uses XBOOT to start up on my flash drive.

My question is what can i do so that i will not have to use the flash drive?

thanks :)  total newbie to linux of any sort

---

### Post by oldfred on 2012-05-24
You need to install grub2's boot loader to the MBR of your drive. Some computers promote flash drives to sda and grub normally defaults to sda on the auto installs.

To find drive with Ubuntu, check for ext4 partitions:
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
sudo update-grub

But grub also remembers where to reinstall and 
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions


[]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive")

---

### Post by liquidxlax on 2012-05-25
can you give me a link to the grub2 bootloader, because i can't find one. 

How would i open it when it is installed?

---

### Post by darkod on 2012-05-25
You don't "open" it like you do with standard programs. It's called bootloader because it sits on the master boot record of the hdd and does the boot process.

When booting your computer without the usb stick, it calls the bootloader on the hdd automatically, in this case grub2.

Expect booting from the hdd, which is standard BIOS setting, you don't need to do anything.

First see if it installed correctly on the hdd, because now it's only on the usb stick. You can see that by trying to boot with the stick.

---

### Post by kc1di on 2012-05-25
Think you should be able to fix it with boot repair which you can get from here:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by liquidxlax on 2012-05-25
> **kc1di said:**
> Think you should be able to fix it with boot repair which you can get from here:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


worked after i figured out that cnt+alt+t was the terminal. fail booted once then booted properly. 

Thank you very much

---

### Post by kc1di on 2012-05-25
Your Welcome - I keep a cd with boot repair around just in case.
Works pretty good. 
enjoy ;)

---

