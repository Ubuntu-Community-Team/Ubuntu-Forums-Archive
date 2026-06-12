---
title: "Missing BOOTMGR after installation"
date: 2011-07-07
forum: Installation &amp; Upgrades
---

### Post by h3now on 2011-07-07
Hello guys, about two days ago I decided that I wanted to at least give linux a try (I'm a windows user so far...). Then I saw this distro called ubuntu, wich allegedly didn't needed me to know anything about linux to use it. I followed the steps in the website ([http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)), burned a CD and started the installation... everything went as expected, and at some point ubuntu said something like "everthing is installed now... restart your computer to continue". 
  And so I did, but then I got a message saying "BOOTMGR missing. Press ctrl-alt-del to restart."
  Now I can't even use windows anymore! (I'm writing from my friend's laptop ^^)... I quickly looked over some threads in the forum with resembled my problem, but as I already pointed out I'm not a linux guy, and therefore I didn't quite understood the solutions and everything.

At this very moment I'm re-installing my whole windows OS and I'm cautious if I'll try to install ubuntu again from the cd. Maybe someone in the forums can point out what I did wrong (if it was actually my fault) cuz I really wanna try it!

-------------------------------------------------------
INSTALLATION:
Did everything the website told me to, I installed it alongside with windows (or at least tried to =[ ).
One important thing to point out is that at the part wich ubuntu asks me where to install it, ad there's a dropdown menu for me to choose it, the only option wich showed up was my pendrive. When I noticed that, I clicked at the "return" button and removed my pendrive from the usb entrance. After that I went back to that page and now it showed only my 160GB harddrive. Since that was the one wich I intended to install ubuntu anyway (not the 1TB one), I just chose it and went on with the installation.

SPECS:
Motherboard: Asus P5VD2-X
Processor: Pentium D 3.00 GHz
Graphics card: NVIDA 9800 GT
Two hard drives:
    160 GB - Windows and Linux 
    1 TB - Media and files, shared by the OS's

Hope this is enough info to solve my problem... thank's in advance guys, looking forward to become another ubuntu user.

---

### Post by Theredbaron1834 on 2011-07-07
Well, it seems grub didn't install right. :(

"You can try to reinstall again. 
Or, you can boot up the live disk again, and do what this thread says.
http://ubuntuforums.org/showthread.php?t=224351"
Is what I would have said if you hadn't started reinstalling windows allready. Windows was still there, but it's bootloader BOOTMGR was gone.

If you want to try again, next time when you click install alongside windows, at the bottom of the screen there will be something like "install bootloader where". Make sure it is on your default drive, IE the one that is the same size as the drive you are installing too.

And, don't worry. It isn't often this hard. I too was a *dows user in till, about 2 years ago. Did what you did, for a week, then deleted windows alltogether. A much better OS then any of the new windows.

---

### Post by oldfred on 2011-07-07
Theredbaron1834's link is for grub legacy. Since 9.10 Ubuntu has been using grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Before jumping in and reinstalling you can ask for help and you may just need some minor repairs. But we do like to spend days and days fixing things when you can reinstall Ubuntu in about an hour. Of course that only works well on new installs or for those who do have good backups.

You mentioned a large drive also, you might want to read this advice:
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate them from drive to drive.

---

### Post by Theredbaron1834 on 2011-07-07
O, right, Oldfred is right. Forgot that it was shipped with Grub2.

---

### Post by h3now on 2011-07-07
Now I installed ubuntu via windows installer... this time it worked! Actually I`m replying from ubuntu
:)

---

### Post by Theredbaron1834 on 2011-07-07
Well, that works too. Hope you have fun with it.

---

### Post by Blasphemist on 2011-07-07
For anyone that reads this and would like screen by screen instruction, I'll refer you to this site by Herman. [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

This describes in depth dual boot installations, and nearly all related questions. 

I started with win 7 and added Ubuntu. A few versions of Ubuntu later I did what's called a clean upgrade, an upgrade from CD. I now have built a USB with many distro's and recovery utilities on it using this. [http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

I now have on my hard drive win 7 (only it's space has been shrunk), Ubuntu natty and oneiric, kubuntu, xubuntu, Fedora 15, openSUSE and Debian. I didn't use herman's site while installing but did use it to get my head straight prior to some of the installs. I did at different times get the grub and grub rescue prompts instead of successful boots and used the Grub2 documentation to troubleshoot.

---

### Post by Theredbaron1834 on 2011-07-08
Yeah, that is what I use. I keep gparted, Dr. Web antivirus, Ubuntu, hirens, and a windows install on it. Great for when I happen upon trouble like this, ie when it happens to friends and family. Also, just in case I mess something up myself. :)

---

