---
title: "GParted sees HDD as completely unallocated with Windows 7 installed"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by blahdieblah on 2009-11-19
Hi guys, I've installed Ubuntu before a few times, and I'd like to dual boot it on my Asus Eee PC with Windows 7. Recently, I've done a full reinstall of Windows and in the process I completely reformatted the drive. It now has a small system reserved partition for booting, the large 139GB partition for Windows itself, and a 20GB partition I made for Ubuntu to go onto. Upon booting into either Ubuntu 9.10 or Netbook Remix 9.10, it recognizes these two used partitions in the file browser, and I can see all of my files. However, neither GParted or Ubuntu Installer sees any of the partitions; it just lists it as unallocated. I'm booting off of an SD card that I used Unetbootin on, and I've re-loaded Ubuntu onto it a few times.

Does anyone know what I could do to fix my problem? Any help would be greatly appreciated.

---

### Post by Robertjm on 2009-11-20
Which version of GParted are you using? They just released a new version on 11/16. Download a LiveCD fromthem and give it a try!!

---

### Post by Mark Phelps on 2009-11-20
Also, unless someone has figured out how to fix this recently (and if they have, they haven't advertised it), the forum is chocked full of posts where people have been unsuccessful dual-booting with the Win7 2-partition scheme and Ubuntu 9.10 GRUB2.

If you really want to try this, be sure to use the Win7 Disk Management utility to free up space for your Ubuntu partitions.  Do NOT use GParted LiveCD or the Ubuntu installer.

Not trying to discourage you, just saying -- don't get your hopes up.

---

### Post by darkod on 2009-11-20
It worked for me "straight out of the box". And Karmic is my first try with Ubuntu. But I didn't do anything special so have no clue what to advise. :) I guess I was just lucky.
Here is my (short) story:
Successfully dual booting on my netbook, both win7 and 9.10 desktop are 32bit versions. I deleted all partitions and win7 installer created the 100MB boot partition. Installed 9.10 desktop after that, picked up everything by itself, no hick-up what so ever.
On my desktop I had vista and system and data partition. Actually booted with Gparted LiveCD to shrink my data partition to make some space. Next boot of vista run some disk checks but it booted fine and worked fine. Then I booted with win7 dvd, installed on the system partition over vista and in this situation it didn't create the 100MB. I think if you install on already existing partition it doesn't create it, according to what happened to me.
After that installed 9.10 desktop 64bit and again, it picked up everything by itself, working fine.

So it works with and without the 100MB, on two machines, both 32bit and 64bit version. It seems it just works. :)

PS. Even though new to ubuntu I used manual partitioning option, always want to create partitions myself. And didn't even touch the Advanced options, never knew they existed then. In a single drive setup just leave it alone (grub2). From reading here it seems many people actually make problems for themselves by trying to install grub2 on a partition and not the MBR wanting to keep windows MBR (have no clue why) and then somehow to chainload linux from windows bootloader.

---

### Post by blahdieblah on 2009-11-20
I looked in Ubuntu's Disk Utility and it sees absolutely everything about my hard drive. It's formatted with an MBR partition table, if that would make any difference. The problem seems to lie in GParted, because I know the Ubuntu Installer Partitioner uses it as well. If I was to download a new GParted and make a Live USB out of it, it wouldn't do me much good because I couldn't install Ubuntu anyways... I already have a 20GB partition ready for it to use, and making a new Live USB wouldn't help when I really should be updating GParted on my current USB.

Should I just run

```
sudo apt-get install gparted
```

on the Live USB? Does that work?

---

