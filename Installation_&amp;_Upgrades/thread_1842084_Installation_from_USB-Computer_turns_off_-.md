---
title: "Installation from USB-Computer turns off -"
date: 2011-09-10
forum: Installation &amp; Upgrades
---

### Post by farmerjohn73 on 2011-09-10
Hi all,

I have an old desktop.  378 MBRam, Celeron 2.4ghz.  I got new IDE hard disk today.  I dont have CDrom on it.  I have only USB drives.  I partitioned it through winxp using Easeus Partition Manager and created ext2 partion and a swap partition (also ext2).

I made a bootable USB for 10.04 from my linux laptop through Startup disk  creator.  I changed the bios of my desktop to boot from USB HDD and booted the desktop.  The real problem started here.  The First screen of Ubuntu appeared and all of a sudden the system got turned off itself.  I tried many times, but the same thing happens again and again either at the first screen or second screen showing UBUNTU title.  But it is not going any further or the computer turns off itself.

I tried changing the USB Ports.  But no use.

If I remove the USB and boot, system boots normally to win xp.

I tried deleting the partitions and booted again.  But the system turns off itself again.

I can't understand what is the problem.

please help.

 I want to install ubuntu through USB to dual boot with winxp and ubuntu.

How do I solve this problem?

---

### Post by farmerjohn73 on 2011-09-13
No one read this post?  somebody pls help??

---

### Post by varunendra on 2011-09-14
Can you boot some other live cd? For example DSL or Clonezilla or Slax? Although all of them are linux based, DSL is a minimal desktop OS and clonezilla is meant for creating disk/partition images. If you don't have XP installation cd, try booting clonezilla live and create a backup image of your XP partition. In case something goes wrong with XP too, you can restore it from this image.

After that, I'd suggest to pull everything off the motherboard of the computer, even the CPU if you doubt it. Then re-seat only essential cables/parts that are necessary to boot up the computer, that is - CPU, RAM, and power cable internally, and mains power cable, VGA cable, keyboard and the USB drive from the outside. This will eliminate the chance of any other attached device causing the trouble.

If the problem stays the same way, I'll doubt your graphics or a faulty RAM. There may be other issues though.

If it boots successfully this way, I'll doubt other attached devices or their connections, including the hard drive itself. However, it may also be a case of a weak power supply, especially the 5V supply, if the USB drive is a hard drive drawring power from the USB.

---

### Post by mörgæs on 2011-09-14
Before going into surgery I would recommend booting Lubuntu rather than Ubuntu. The computer does not have enough memory for Ubuntu.

You can use DSL for a quick test, but don't install it. It has been abandoned for several years.

---

### Post by farmerjohn73 on 2011-09-26
> **varunendra said:**
> Can you boot some other live cd? For example DSL or Clonezilla or Slax? Although all of them are linux based, DSL is a minimal desktop OS and clonezilla is meant for creating disk/partition images. If you don't have XP installation cd, try booting clonezilla live and create a backup image of your XP partition. In case something goes wrong with XP too, you can restore it from this image.

After that, I'd suggest to pull everything off the motherboard of the computer, even the CPU if you doubt it. Then re-seat only essential cables/parts that are necessary to boot up the computer, that is - CPU, RAM, and power cable internally, and mains power cable, VGA cable, keyboard and the USB drive from the outside. This will eliminate the chance of any other attached device causing the trouble.

If the problem stays the same way, I'll doubt your graphics or a faulty RAM. There may be other issues though.

If it boots successfully this way, I'll doubt other attached devices or their connections, including the hard drive itself. However, it may also be a case of a weak power supply, especially the 5V supply, if the USB drive is a hard drive drawring power from the USB.


Thank you for valuable steps to trouble shooting.  I thought it was a problem of over heat.  I removed the side door, kept a table fan beside the CPU and tried installing ubuntu.  It was successful.  But even when I use USB drive for copying large files like 2.5 GB, sometimes its getting turned off. Otherwise it is working well.

When I talked to a hardware expert, he said may be USB is getting short circuit try using USB ports that are placed behind the CPU.

I didnt try this.  But if I use the system without the USB, it is working well, though I didnt check it fully.

Unfortunately, I dont have a CD Drive,  that's gone long back !

---

