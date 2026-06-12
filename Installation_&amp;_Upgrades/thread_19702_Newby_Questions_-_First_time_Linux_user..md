---
title: "Newby Questions - First time Linux user."
date: 2005-03-13
forum: Installation &amp; Upgrades
---

### Post by inphase on 2005-03-13
I installed Ubuntu version 4.10 onto a clean hard drive (d) a Seagate 10G IDE separate from my existing Win 2000 on a Seagate 20G IDE drive (c). I insalled the GRUB partioning as it seems like a good idea to be able to boot for either system. 

The installation went well and I like the feel of Ubuntu. 
Why can't I see the 'c' drive from within Ubuntu?
How do I install the internal modem? Dial up 56k v90 When I do a 'locate' modem from the network installation, it says it cannot find a modem, please check to see if the modem is connected etc.....

The other problems started when I boot with win 2000. It seems to take forever to boot and when it's finally done, everthing works properly except window explorer, which is unbearably slow (seems to hang) 
I can see the 'd' drive in explorer but cannot access it. After a while when I go to task manager, it says "not responding" and I have to end task.

My aim is to get all my documents and files to Ubuntu and eventually do away with windows compleatly. 
I realize that I have a lot of reading and studing to do as at this point I have no knowledge of Linux distrobutions, but I really want to go that route.

Thanks in advance for any assistance.
John.

---

### Post by Buffalo Soldier on 2005-03-13
Welcome to Ubuntu and GNU/Linux.

GRUB is a bootloader, not a partition type :)

To "*see*" drive **C** you need to mount it. How to do it? Feel free to read [How to mount Windows partition (NTFS) on boot-up, and allow all users to read only?](http://ubuntuguide.org/#automountntfs) at UbuntuGuide.org

Windows 2000 uses NTFS as its filesystem. And I assume you've chosed EXT3  filesystem for Ubuntu. For the time being, Linux is only able to read NTFS filesystem but not write to it. And Windows are not able to read or write to EXT3 filesystem. (I think there are some third-party software that you can use, but maybe some else can guide you about that)

---

### Post by inphase on 2005-03-13
[QUOTE=Buffalo Soldier]Welcome to Ubuntu and GNU/Linux.

GRUB is a bootloader, not a partition type :)

To "*see*" drive **C** you need to mount it. How to do it? Feel free to read [How to mount Windows partition (NTFS) on boot-up, and allow all users to read only?](http://ubuntuguide.org/#automountntfs) at UbuntuGuide.org

Windows 2000 uses NTFS as its filesystem. And I assume you've chosed EXT3  filesystem for Ubuntu. For the time being, Linux is only able to read NTFS filesystem but not write to it. And Windows are not able to read or write to EXT3 filesystem. (I think there are some third-party software that you can use, but maybe some else can guide you about that)[/QUOTE]
 Thanks, as I said, "I have a lot of reading to do" !!!!

---

