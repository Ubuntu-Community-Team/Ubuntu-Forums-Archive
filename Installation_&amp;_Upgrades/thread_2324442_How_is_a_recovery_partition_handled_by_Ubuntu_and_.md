---
title: "How is a recovery partition handled by Ubuntu and Grub2 during and after installation"
date: 2016-05-13
forum: Installation &amp; Upgrades
---

### Post by mew4 on 2016-05-13
[COLOR=#111111][FONT=Ubuntu]I have an Acer Aspire 5332 computer and I&#8217;m running Windows Vista. I plan to install Ubuntu 16.04 manually through 'Something Else'. I want to delete Windows during the install but preserve its recovery partition (Acer's EISA Configuration). Then I want to create a root &#8217;/ &#8216; partition and a swap partition and select Grub's /dev/sda boot setting. I understand that with this setting Grub will recognise everything on my hard drive but will boot Ubuntu automatically by default. Is this correct?
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Also, I've seen screenshots of the Grub boot screen showing a Windows&#8217; recovery partition listed on the screen, and I was wondering how Grub and Ubuntu handle these partitions. For instance, upon start-up, will my computer go straight into Ubuntu's splash screen or the Grub boot screen (like a dual boot)?
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Finally, if the recovery partition is listed on the Grub boot screen, can it be accessed through this screen, although I'm assuming that the recovery partition doesn't have a Master Boot Record for Grub to over-write. And failing this option, will I still be able to access my recovery partition by using Acer's default keys 'Alt' and 'F10'? - I'm assuming that the Ubuntu/Grub install won't affect this function nor corrupt the Windows recovery software. But am I right in thinking this?
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]My install details will be as follows:-
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have a normal Motherboard Bios (Brand Acer V1.06 ) .
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The Acer recovery partition (PQ Service/EISA Configuration) contains a factory setting image of Vista.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]After deleting my Windows NTFS partition (Vista) during manual install (&#8217;Something Else&#8216;), my new partition table will be as follows:-
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]dev/sda1 - recovery partition
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]dev/sda2 - root &#8216;/&#8217; (EXT4)
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]dev/sda3 - swap
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Boot selection -
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]dev/sda (for the whole drive).[/FONT][/COLOR]

---

### Post by DuckHook on 2016-05-13
I haven't used Windows since the XP days and never had a recovery partition to deal with, so can't advise you as to the mechanics. However, what you are proposing sounds at least a little risky. I presume you want the Windows recovery partition around just in case. But if so, why take any chances at all? Why not just buy another SSD/HDD, swap out your Windows HDD, keep it somewhere safe, and install Ubuntu onto a clean disk with no possibility of inadvertently nuking your Windows investment?

---

### Post by yancek on 2016-05-13
You can boot the Recovery partition for windows directly from Grub if it is detected during  the install and a menuentry is created for it.  I've accessed this on a windows 7 machine but never had to go through the entire process so I don't know if it will work.  

If Ubuntu is the only OS installed, I don't think you will see a boot menu, it will boot automatically although you can change this.

> [COLOR=#111111][FONT=Ubuntu] the recovery partition doesn't have a Master Boot Record for Grub to over-write.[/FONT][/COLOR]

No partition has a master boot record.  This is a specific location (sector 1) on all harddrives outside any partitions.

If this is new to you, I would suggest reading some tutorials on dual-booting such as the one below:

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

