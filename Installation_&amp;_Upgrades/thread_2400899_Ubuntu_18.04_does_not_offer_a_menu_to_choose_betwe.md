---
title: "Ubuntu 18.04 does not offer a menu to choose between 2 OSes"
date: 2018-09-11
forum: Installation &amp; Upgrades
---

### Post by skaiser on 2018-09-11
Hello all,
I  have installed Ubuntu 18.04 on a second disk beneath Ubuntu 16.04. Now the machine boots only to 16.04. I have installed an Nvidia grafic card and do not see the menu, - only when I unplug the HDMI cable (there is still a vga cable present) can I see the menu and choose what I want.
My grub.cfg looks so:
search.fs_uuid 0fb470a4-cc74-43bb-8cd4-0595dda4fcf5 root hd1,msdos7 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
the uuid is of the 18.04 disk, can I replace it with the uuid of my 16.04, and is there a possibity to see the menu whithout unplugging the HDMI cable?
Thanks 
Siegfried

---

### Post by ajgreeny on 2018-09-11
Best to see full details of where you are at present so go to **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by skaiser on 2018-09-12
Hello, 
thanks for the answer, but the problem is different, it shows the menu on vga screen, but not in my grafic screen whith nvidia grafic card. I have posted already a more detailed post.

---

### Post by ajgreeny on 2018-09-12
Please do not start duplicate threads even if you use a different title. It is confusing for all including you and dilutes the forum's ability to help. 
[https://ubuntuforums.org/showthread.php?t=2400804](https://ubuntuforums.org/showthread.php?t=2400804)
Closed

---

