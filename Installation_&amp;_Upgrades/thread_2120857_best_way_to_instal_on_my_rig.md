---
title: "best way to instal on my rig"
date: 2013-02-27
forum: Installation &amp; Upgrades
---

### Post by yon2501 on 2013-02-27
ok so im familiar with the usual way to dual boot a computer, however my rig is a little special and need some advice on the best way to do this.

currently i have windows 7 on a 30GB SSD with junction points leading to a 1TB HDD then i also have a 1.5TB Media drive.

Idealy I'd like to have ubuntu running on the 30GB SSD and move the windows install to the 1TB on a partition but I dont know how the junction points would act with that since they were set up for 2 seperate physical drives, and if at all possible I'd like to avoid having to reinstall windows.

the other obvious option I see is to install ubuntu on the 1TB but id prefer to have it on the SSD since I'll be using ubuntu as my primary OS and windows basically just for gaming.

Any advice Would be great, thanks.

PS. I'd like to keep the windows install as a separate partition so my program files and user directory are kept separate from the rest of the installation.

---

### Post by dino99 on 2013-02-27
there is nothing special with your rig   ):P

you are the boss on board  :p do it as you feel  ;)

---

### Post by oldfred on 2013-02-28
I do not know junction points in Windows 7, is that like links in Linux where a location is not really what it is. I use links for all my data in my hard drive back to my /home in my 30GB / (root) partition in my 60GB SSD.

You have to decide what you want to do with Windows. I might think you want the SSD for gaming. But Ubuntu boots & loads applications (first time) really quick with the SSD. But Linux is good about caching activity in RAM so reloading thing is not always faster.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

