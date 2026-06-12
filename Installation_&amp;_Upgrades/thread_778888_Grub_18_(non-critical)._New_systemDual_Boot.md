---
title: "Grub 18 (non-critical). New system/Dual Boot"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by neoprimal on 2008-05-02
Hey all, I'm new to the community though I have lurked for a few years :). I've played with Ubuntu since v.6.xx, more so every time it gets to a newer version. 7.10 I had almost permanently in Virtual environments for practice. Heron is the first version I've actually decided to Dual boot alongside my mainstream OS which is Vista Ultimate 64. That as it is, I'm still VERY new and I require a bit more hand holding than the typical linux user. Please don't assume that I know commands and where to find them, I won't get all puffy if you consider me kindergarten. 

The situation at hand is the infamous Grub 18 error, however my own case is not so typical.

This is the second time I've installed Heron on this PC as I utterly messed up my last install by downloaded KDE4. (This back story may or may not be necessary, but I tend to be detailed so please be patient with me please). 

The first install went perfectly. There were never, absolutely 0 Error 18 messages no matter how many times I'd rebooted. When I realized I'd goofed and needed a do-over, I did what any typical Windows user would do, I formatted the drive that Linux was on and start over. Because of my success with the first install, I figured formatting wiped out grub completely and that I'd have a fresh start. 

For the most part, this seemed to be the case until upon a random reboot I got error 18. It wasn't typical however because of 2 things. 

Firstly, as I mentioned before, I never got it the first time I had the OS installed, and take into consideration that I had MANY reboots...installing wireless drivers, my video card drivers and settings panels, etc, all of which required reboots and I never had a single error 18. 
Secondly, they're seemingly non-critical...meaning for some odd reason I don't get them every time. I can go 2 or 3 reboots and have 1, or have none for quite some time, but for the most part after I do have 1 and reboot again, grub loads fine. 

From what I've read, generally people get stuck on it and either have to load the live CD or attempt some sort of recovery.

What I've done?

Well, nothing yet...just a bit of research, most of which has pointed to this being some kind of bios limit problem (drive bigger than the bios can handle, so start over and create a small /boot partition before the others) - however my system is brand new. I have an Abit IP35 Pro board, 4gb Ram, Nvidia 8800GT and 2TB of hard drive space spread out over AHCI Sata 2 drives. 

Linux is restricted (I hope) to using a single Sata 150 120gb drive, I thought about partitioning it and mounting areas myself, but figured guided setup would handle anything better than I possiby could, especially as this is really my first REAL go. God forbid I set it up and grub can't do it's thing automatically, then I'd be totally lost.
I REALLY don't think it's the bios limit thing though, more so because of the fact (through logic and evidence) that it worked so perfectly initially. Sure it could be luck, but wow I'd have to be REALLY lucky to get through that many reboots without a single error.

Is there a possibility that grub has snuck into another area in order to detect my other OSes? Or is there some other behavior of Grub that I'm not aware of? And that somehow this other grub is affecting the currently installed version? My menu file 'seems' pretty lean, I don't see how it could mess up. If you need me to post any messages or settings please let me know. I'd really appreciate some help on this. And again please be patient with me....I notice members of the Linux community tend to send newbies off to tutorials and how-tos assuming they haven't investigated. 

Thanks.

P.S

Here's my grub menu, jic.

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=704c98c9-f82f-4bf2-ae8a-9ad437792ba5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=704c98c9-f82f-4bf2-ae8a-9ad437792ba5 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
#title		Windows XP Professional x64 Edition
#root		(hd1,0)
#savedefault
#makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
#chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
#title		Windows XP Professional x64 Edition
#root		(hd3,0)
#savedefault
#makeactive
#map		(hd0) (hd3)
#map		(hd3) (hd0)
#chainloader	+1

---

### Post by dstew on 2008-05-02
The error is unlikely to be the old BIOS cylinder limit. It is possible that error 18 might occur if your hard drive was too big for your BIOS (I think bigger that 137 GB) but you would probably get it every time.

My guess is that during the formatting process when you removed your old KDE system that there are some weak formatting marks on the disk. So maybe sometimes you get lucky, and the BIOS is happy other times maybe not.

It might be worth looking at the disk with a repair program. There is the Linux fsck utility. You should run if from a Live CD boot, so the hard disk that is troublesome can remain unmounted. Check on your disk device names with```
sudo fdisk -l
```To use fsck to check and repair your Ubuntu system, the command would be```
sudo fsck -a /dev/sdc1
```if /dev/sdc1 is the name of your Ubuntu partition, as shown by the fdisk output.

If there are any partition table issues, the program testdisk can help with that. You can install it using the synaptic package manager, in the System --> Accessories menu. I think you will have to enable the Universe repository first (Synaptic settings menu).

There are a lot of other ideas about the "modern" grub 18 errors on [Herman's excellent grub page]("http://users.bigpond.net.au/hermanzone/p15.htm"). Look down near the bottom to see his cumulated wisdom on this error.

---

### Post by neoprimal on 2008-05-02
Thanks much. I'll check what you've said out.

---

