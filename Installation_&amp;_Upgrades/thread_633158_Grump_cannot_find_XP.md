---
title: "Grump cannot find XP"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by majakarlsson on 2007-12-06
I think I have learned that i need to edit grubs menu.lst to make Windows XP available for booting. (when I installed Ubunty 7.10 Gutsy Gibbon I choose to keep XP, and was promised a dual-boot option, but all OS, commercial or free, seems to want to make it hard for us to switch back and forth).

It looks like this now:

*********
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d5f05a09-c52b-4170-8ab3-1628616d6b15 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d5f05a09-c52b-4170-8ab3-1628616d6b15 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

title Windows XP
root (hd0,1)
makeactive
chainloader +1 
***************

The windows XP option I wrote myself. However, I get some kind of "can't find" bla bla file- message when trying to boot windows.
(Note: it says "NTLDR missing", or something similar, it's in swedish on my computer)

I got gpartition, but the way it writes locations of partitions is different, not the hd0-way.


So how can I find out which hd-adress to write?
Or is it the right adress but the NTLDR-thing is another problem?
thanx

---

### Post by forestpixie on 2007-12-06
check the drive you need by running this in terminal, 

```
sudo fdisk -l
```

post it here if you need help

---

### Post by majakarlsson on 2007-12-06
thanx, ok i get the following response:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        6516    49253400    f  W95 Ext'd (LBA)
/dev/sda2   *        7198        7751     4188240    e  W95 FAT16 (LBA)
/dev/sda3            6517        7197     5148360   83  Linux
/dev/sda5               2        6478    48966088+   7  HPFS/NTFS
/dev/sda6            6479        6516      287248+  82  Linux swap / Solaris

So i understand it has to be one of the two first. But how does /dev/sda1 or sda2 translate into the menu.lst-file?

---

### Post by forestpixie on 2007-12-06
first number = drive, second number = partition, it looks like sda2 is the one which you  need that would be hd0,2, although it appears to be fat16? - or is it extended - I've got my stupid head on :)

---

### Post by majakarlsson on 2007-12-06
that one IS fat16, according to thefdisk-list anyway...

the strange thing is that in my menu.lst hd0,2 is the adress used for booting ubuntu... which works... doesn't that mean that 0,2 can not be correct for boting windows?

---

### Post by forestpixie on 2007-12-06
d'oh stupid me - count from zero - so 2nd partion first drive is hd0,1 - which doesn't work - I thought actuallly that xp had to go on ntfs, are you sure xp's not on sda5 which would be hd0,3

while I remember also - when you've added the xp boot to grub - I think the xp bit needs to be outside the automagic kernels list

---

### Post by MQMike on 2007-12-06
Looks like Windows is on (hd0,0)
And, yes, Windows should be outside the Automagic kernels list, either before the *** Begin line or after the *** End line.


How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

---

### Post by meierfra on 2007-12-06
> not on sda5 which would be hd0,3
????????? sda5 is (hd0,4)


> Looks like Windows is on (hd0,0)
????????? (hd0,0) (that is sda1) is an extended partition.

Try

title Windows XP
root (hd0,4)
chainloader +1 

(do not use "makeactive", grub is not able to activate  a logical partition)

But it probably will not work. Do you know which  partition is Windows: The 4GB fat 16 partition sda2 or  the 49GB NTFS  partition sda5? 

Did you used to have a another Windows partition which you deleted?

---

### Post by forestpixie on 2007-12-06
> ????????? sda5 is (hd0,4)

why would that be - would not hd0,4 be the swap aprtition or does there being extended partitions change the numbering?

---

### Post by meierfra on 2007-12-06
> does there being extended partitions change the numbering?

yes. Primary partition are numbered (hd0,1) through (hd0,3).
The first logical partition is always (hd0,4), regardless of the number of primary partitions.
(a logical partition is a partition sitting inside an an extended partition) 

The sda numbers work the same way, only that they start counting at 1. So the sda5 always is (hd0,4),  sda7 is  (hd0,6) and so on.

---

### Post by forestpixie on 2007-12-06
thanks - that's the new thing for today then :)

---

### Post by MQMike on 2007-12-06
Sorry about saying Windows is on (hd0,0).  Good gosh, what the heck am I thinking (or not thinking)!

There’s ways to get at this, of course.

First off, GParted Live CD would be great for seeing these partitions better, and actually seeing the organization of the start of the Extended and the succeeding Logicals.  You can even just simply use the GParted in Ubuntu.

Second, as a quick acid-test, it is sometimes helpful to run Super Grub Disk and ask it to boot Windows.  If it does, then you know you can (quite probably) solve this.

Third, to really see what BIOS (&GRUB) sees, the GRUB geometry command is hard to beat.  In Ubuntu, open a terminal, type sudo grub, get a GRUB prompt, grub>, then type
geometry (hd0)
(since you have just the one HDD).

Or, boot up, see the boot menu, interrupt it by pressing the “c” key, get a GRUB prompt, and manually try to boot Windows by typing various (hd0,y)’s until you hit one:

root (hd0,y)
chainloader  +1
boot

Keep trying until you hit the correct y.  Then edit menu.lst accordingly after you get it all booted and sorted.

That’s how I’d approach this sort of Where am I? and Where is Windows? issue.  Looks like there's only two candidates: y = 1, or y = 4.

GParted:   [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
Super Grub Disk, new site:  [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by lajevardi on 2007-12-10
same problem here guys,
I was playin with y! but I couldn't find the appropriate digit to boot windows. I still gettin' the "NTLDR is missing" error.
I have forced ubuntu to boot using this trick. but not working with windows.
I've used Windows Recovery, typing "fixmbr" and "fixboot". 
but still same problems again and again..

---

### Post by Pforrest on 2007-12-10
Look like Grub actually boot to the "wd" partition, however something has cause the OS to not continue boot, most likely are missing or damage files Ntldr-Ntdetect.com-Boot.ini 
If you have access to the "wd" partition try 
@1 manually copy & replace the files mention-You do back up the original first before replace them right?
@2 the solution from this site [http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm) will help some

---

### Post by lajevardi on 2007-12-11
thanks Pforrest for your reply,
I'm goin' to try this..

---

### Post by Skerit on 2007-12-17
When I installed Windows it DEMANDED I made a separate boot partition for the ntldr & boot.ini thing, and it HAD to be on one of my SATA drives.

Now, my regular IDE connectors are full (only have 1) so I'm using an extra IDE card, this one has my windows on it. 

I can get to the windows boot partition (on my SATA HD) but it's still saying it can't find NTLDR, even though it's RIGHT THERE!

---

### Post by lajevardi on 2008-03-02
I have done all I did for ubuntu 6.04 to install 7.10, there's no problem :D 
and Ubuntu rocks......

---

