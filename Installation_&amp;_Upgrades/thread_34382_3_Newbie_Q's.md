---
title: "3 Newbie Q's?"
date: 2005-05-14
forum: Installation &amp; Upgrades
---

### Post by scaramonga on 2005-05-14
Newbie here.....so be gentle!...LOL

Installed Ubuntu and all ok apart from a couple of niggling things I need help with peeps?

When booting and I choose to select Windows XP........it wont boot and says missing 'ntdlr'..........now I know this is because windows is on my main SATA drive and its trying to boot from the same IDE drive Linux is on.........I have to go back to BIOS and change to boot from SCSI for it to work.  Linux is installed on my IDE drive. Any way of fixing this?

Is there also any way to access my Windows drives/folders from Linux.......and vice versa??...........seems no easy way of doing this??.........NTFS file system by the way!

Lastly.......LOL...........my screen resolution is fine on my LCD screen....but it wont let me select anything other than 60hz??..........I'd prefer 75!!

Sorry for the dribble.........I am new to this LOL.......

Many thx all!  :smile:

---

### Post by davidmigl on 2005-05-14
[QUOTE=scaramonga]Newbie here.....so be gentle!...LOL

Installed Ubuntu and all ok apart from a couple of niggling things I need help with peeps?

When booting and I choose to select Windows XP........it wont boot and says missing 'ntdlr'..........now I know this is because windows is on my main SATA drive and its trying to boot from the same IDE drive Linux is on.........I have to go back to BIOS and change to boot from SCSI for it to work.  Linux is installed on my IDE drive. Any way of fixing this?

Is there also any way to access my Windows drives/folders from Linux.......and vice versa??...........seems no easy way of doing this??.........NTFS file system by the way!

Lastly.......LOL...........my screen resolution is fine on my LCD screen....but it wont let me select anything other than 60hz??..........I'd prefer 75!!

Sorry for the dribble.........I am new to this LOL.......

Many thx all!  :smile:[/QUOTE]
 I am new, too, and I had many of these same problems as you.  Here is what I did.

~~~~~~~~~~~~~~~~~~~
1.  Similarly, I installed Ubuntu on a different IDE HDD alongside an existing Windows installation on another IDE HDD.  GRUB seems not to like windows.  Funny thing is, it gives you all these options for Ubuntu (safemode, memtest, normal, etc.) but only one for windows, although windows has options too (safemode, last known good config., etc.).  It's playing favorites here, I think :grin:.  The hatred goes on.  When I try to boot into windows with GRUB, it simply won't let me.  It freezes with this:

```
Booting "Microsoft Windows 2000 Professional"

root (hd1,0)
     Filesystem type unknown, partition type 0x?
savedefault
makeactive
chainloader +1
```

When you select a terminal, it also gives you a linux one and not windows.  GRUB is definitely trying to get you to abandon MS :grin:.

**-->** When the story's told, however, changing the BIOS boot order of the HDD is the only way I can get the machine to dual boot.  It works, so I'm happy.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
2. You can read but not write NTFS partitions in Linux.  Have a look   [ here](http://ubuntuguide.org/#mountunmountntfs) for some more info.  In windows, it's the same way.  Look [here](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm) for a windows app that can browse ext3 partitions.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
3. Look in [url=http://ubuntuforums.org/showthread.php?t=21984&page=2&pp=10&highlight=refresh+rate]this[/url thread, especially posts #'s 14 and 15
~~~~~~~~~~~~~~~

Glad to help!!

davidmigl

---

### Post by n21roadie on 2005-05-16
If i read you post correctly , you have wind*ws on your scsi drive, you changed the
bios boot sequence from C to SCSI,

Is your sata drive "C" and your scsi "D" , am i correct so far?,

I have a combined scsi and ide multi drives setup,and if this is any help , i had to remove the ide drive to install wind*ws and linux on to the scsi drive , because in the the bios the ide will be assigned C and more important your wind*ws boot files Ntdlr will be placed onto your ide drive ,so my solution was to partition the scsi drive ( 9.1GB )into three partitions,
(1)20MB fat hidden partition ,(2) 4.5GB ntfs,(3)4.5GB ex2,
Installed Wind*ws on the ntfs , and Linux on the ex2,   
I hope this will be of some help ?

---

