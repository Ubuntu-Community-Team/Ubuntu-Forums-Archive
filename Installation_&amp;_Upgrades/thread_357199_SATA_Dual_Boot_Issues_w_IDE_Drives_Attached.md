---
title: "SATA Dual Boot Issues w/ IDE Drives Attached"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by Eric B on 2007-02-09
Original config.

1 SATA with windows xp
2 IDE drives that I use for storage and back up.

I partitioned my SATA drive to make room for Ubuntu last night and added Ubuntu to the drive successfully, but I left the default, hd0, for the boot loader. This did not work. The reason being is that despite telling my BIOS to boot from the SATA drive, it is still hd2. I reinstalled Ubuntu and chose hd2 for the boot loader. Reboot and I get the Grub screen. Cool, or so I thought. I get the old error 22 on Ubuntu and NTLDR is missing on xp.

I looked at the mappings and tried to tackle Windows first. 

root (hd2,0)
map (hd2) (hd0)
map (hd0) (hd2)

That looks right to me.
first partition on hd2 is windows. 

What is the problem here? 

I am thinking that maybe the boot loader thinks it is on hd0 once it comes up, but I tried 
sudo gedit /boot/grub/menu.lst and it came up with a blank doc, so I couldn't try that. Not that I am even sure it if would fix the problem.

Anyone have any ideas?

Most everything I find on this is with windows on the SATA and Ubuntu on the IDE, which works fine. That I can figure out,  but I wiped my IDE drive that I use for back up to do this. This is not a good thing.

---

### Post by mikewhatever on 2007-02-09
Shouldn't it be like this:
> title      Microsoft Windows 98SE
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
savedefault
makeactive
chainloader +1


or in your case 
> 
root (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)


---

### Post by Eric B on 2007-02-09
I think that was a typo in the post on my part. I would have to check later.

---

### Post by miseljt on 2007-02-09
Hope this helps.

[http://www.ubuntuforums.org/showthread.php?t=351022]("http://www.ubuntuforums.org/showthread.php?t=351022")

---

### Post by Eric B on 2007-02-09
I will give that a shot as well. I had thought about that, but I didn't want to do it because if I put the other drives back in, I figure that the will wind up being hd0 and hd1 and break my config.

Have you put your IDE drives back in?

---

### Post by confused57 on 2007-02-09
Is Windows on the first partition, and you installed Ubuntu to the second partition?  If so, you shouldn't have any problems getting your system to boot.  If you want to see your partition tables, boot up the live cd, open a terminal, enter:
```
sudo fdisk -l
```
The -l is a small "L"


Since Windows & Ubuntu are on the same drive, you don't need the mapping commands.
If you're getting a grub menu at startup, with just the SATA drive connected, make sure the entry to boot Ubuntu is highlighted, press "e" to edit, then change the root from (hd2,1) to root (hd0,1), if that doesn't work(which it should, if Ubuntu is on the 2nd partition), then root (hd1,1).  These changes are temporary, if you're able to boot, you can make it permanent in your /boot/grub/menu.lst.

If Windows is on a partition located after the Ubuntu partition, then booting Windows may be difficult.

```
sudo gedit /boot/grub/menu.lst
```
menu.lst is short for menu.list

---

### Post by Eric B on 2007-02-09
Windows is definitely on the first partition of the SATA drive with Ubuntu on the 2nd. 

Slow day at work, and I am anxious to get home and try to remedy this issue. Its making the day drag on.

---

### Post by Eric B on 2007-02-09
Well, I am home now, and same thing. I am editing the boot loader as I go. It doesn't think hd2,1 is a partition. That is funny since i installed the boot loader on hd2, otherwise i wouldnt be at the boot loader right now, and ubuntu is definitely on the 2nd partition.

Edit:

I fixed it. Despite the boot loader being on hd2, and the install being on hd2, etc. Once my system starts up and grub loads, it thinks that it is on hd0. I just changed it to hd0, and up it came, made the chages in menu.lst once in Ubuntu doing
sudo gedit /boot/grub/menu.lst
and changing all that said root hd2,x to hd0,x and remaking the map commands for the windows partition seeing as how i didn't need them because if the system now thinks its on hd0 after booting that stuff seems worthless.

---

