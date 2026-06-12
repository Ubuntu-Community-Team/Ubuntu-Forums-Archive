---
title: "Install Ubuntu in second partition"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by NEOLLE on 2008-09-11
Hello All,
 
I want to install Ubuntu in my old PC with the following specs 
   [LIST]
[INDENT][*]Pentium 4
[*]256MB RAM
[*]40G HD partitioned
[*]Drive C - 20G NTFS
[*]Drive D - 20G FAT32
[*]Windows XP[/INDENT]
[/LIST]

I got an official Ubunto installer last year and I used it in my installation. My problem is that the installation takes forever. It takes 10 to 15 mins to show a single form. The farthest part of the installation I reached was reading the file systems. After that it hangs. The installation won't finish.
  
I'm aware that Linux won't install in an NTFS disk, so I was thinking if it is possible to install Linux in my drive D which is in FAT32.

I don't want to remove my Windows XP since I have project that requires MS Windows. I want to have dual boot capability where I can choose which OS I want upon booting.

Your help will be greatly appreciated.:KS

---

### Post by loell on 2008-09-11
yes that's more or less expected on gnome livecd install,

try installing **Xubuntu** instead :)

---

### Post by Bucky Ball on 2008-09-11
I would suggest you download the alternate install cd of the newest version, Hardy 8.04. A more lightweight version of Ubuntu, mentioned in the last post, Xubuntu is probably a good option seeing as you have small amount of RAM (Xubuntu 8.04, alternate installer, *not* desktop).

[http://www.xubuntu.org/](http://www.xubuntu.org/)

You can install app and packages once you are up and running. Trying to install with the desktop version is no doubt your problem as this is chewing up your resources with it GUI (pretty colours and interface).

Ubuntu needs to be installed on an EXT3 partition and needs EXT3 Swap partition also, both of which you could create on 10GB of your 20GB FAT32 drive when you get to the section of the installation concerning partitioning your drives. 

Word of warning - good idea to back up any valuable data before embarking on this journey and remember - the Windoze partition will be the first one on the first disk (usually) and should be easy to identify as it will be marked 'NTFS'. Keep away from that one and you should be fine. That partition will probably be something like 'sda1' as far as the Ubuntu partitioner is concerned.

Here is an installation guide for the alternate cd, one of many pages conerning this topic:

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

Good luck and post back with any probs. :)

---

### Post by NEOLLE on 2008-09-11
Thanks for your replies. I'll try Xubuntu. :KS

---

