---
title: "Grub - Installing XP (dual boot) on non-first partition?"
date: 2006-12-17
forum: Installation &amp; Upgrades
---

### Post by fisherman783 on 2006-12-17
I currently have Ubuntu on hda1 (and2, swap).  I have taken some space at the end of the hard drive for hda3 and would like to install XP on it.  I think I'm pretty familiar now with grub and partitions.  The one thing I can't figure out how to do is get XP to install on the non-first partition.


As I install XP from the CD, it goes through the initial startup procedure, then reboots.  On boot, the computer says that no operating system is available.  Since the Windows booter is on the MBR, I restored Grub from hda1 onto the MBR.  If I remember the XP installation procedure correctly, it now needs to do some kind of follow-up boot, which I can't get it to do through Grub.

The relevant section of my menu.lst, as advised by several now-forgotten (but helpful) guides:
```
title Microsoft Windows XP Home Edition
rootnoverify	(hd0,2)
map (hd0,2) (hd0,0)
map (hd0,0) (hd0,2)
makeactive
chainloader +1

title Windows CD Boot
map (hd0,0) (hd0,2)
map (hd0,2) (hd0,0)
chainloader (cd)+1
```

The top entry should get a working XP installation to boot with no problems.  In this installation limbo state, it generates the same errors as when Windows had the MBR (disk error, no operating system installed, etc.)

I gathered from my research that I would need something like the bottom entry for the follow-up boot from CD, but that doesn't seem to work.  I get error 23 - error parsing number.  Since it seems to be balking at "(cd)" I've tried using (cd0) instead (since I've seen that used too), but with the same result.  Can anyone help me figure out what to do?

---

### Post by confused57 on 2006-12-17
The mapping lines are only for Windows being on a 2nd hard drive, you could try an entry similar to your first one without the map lines:

title Microsoft Windows XP Home Edition
rootnoverify	(hd0,2)
makeactive
chainloader +1

May or may not work, Windows usually needs to be on a partition before any other OS.

---

### Post by bulldog on 2006-12-17
You have to modify the boot.ini file and point it to the right partition.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Windows_Booting_errors](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Windows_Booting_errors)

---

### Post by fisherman783 on 2006-12-17
> **bulldog said:**
> You have to modify the boot.ini file and point it to the right partition.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Windows_Booting_errors](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Windows_Booting_errors)

Thanks for the tip, but the boot.ini file indicates the correct partition (3).

This may be wrong, but... as I'm getting a better feel for the situation, I think what's probably happening is that the Windows installation CD, upon boot, looks on partition 1 for a partially completed XP installation.  If it finds one, it continues stage 2 of the installation (which looks like a Windows-styled installation screen).  Otherwise, it asks if you want to boot from the CD to start stage 1 of the installation (which happens in a DOS-style screen and is much shorter).  The re-mapping should take care of fooling the CD into looking in the correct partition and continuing installation, but how do I then tell Grub to boot from CD...?

---

### Post by bulldog on 2006-12-17
Remapping is only useful if you have windows installed on a second disk instead of the first.
It has no function with partitions so better erase it.

I'm not sure if I understand what you're saying about booting ubuntu from a cd........can you clarify why you want to do so?

---

### Post by Herman on 2006-12-17
With  a reasonably modern computer, you need to set the boot order in your CMOS (BIOS) to get your computer to boot from a CD.
                          BIOS page (boot sequence).......................................[BIOS Page]("http://www.users.bigpond.net.au/hermanzone/p1.htm")

There are a lot of diffeerent kinds of Windows, and a lot of different kinds of Windows install CDs. A few might be able to install on a non-first partition. I'm not sure.

I do know that once installed, you can move that partition to the other end of the disk or the middle of the disk or anywhere, as long as it retains the same partition number, it won't know the difference. (At least with my computers thats' what happens).
You can also have Windows on any Primary partition, 1,2,3, or 4, as long as boot.ini has the right partition  number, you can boot Windows with Grub.

I'm not sure aboout the actual installing part. It depends what kind of CD you have. I hope it works for you without too much trouble.

Regards, Herman :D

---

### Post by Juan Largo on 2006-12-17
fisherman783 -

I'm not much of an Ubuntu expert, but I think I know Windows fairly well.  I've installed Windows XP several times on a non-first partition in a dual-boot setup when the other OS is another Windows OS.  However, most of the literature I've been reading on a dual-boot Windows/Linux installation advises to install Windows first and THEN Linux.  Is there a particular reason that you wish to do it the other way around?

One possible way to install XP with Ubuntu aleady installed is to use a reliable partitioning tool like Acronis Disk Director Suite to resize and move the existing Linux partitions toward the end of the disk and create an NTFS partition at the beginning.  Then use the XP installation disk to install XP on the first partition, where it is happy.  Then re-install Ubuntu and Grub by overwiting / (root) without overwriting your existing /home partition, thereby saving your existing Ubuntu software, documents, and settings.

Just a suggestion...

---

### Post by fisherman783 on 2006-12-17
Thank you for the replies, everyone!

> **bulldog said:**
> I'm not sure if I understand what you're saying about booting ubuntu from a cd........can you clarify why you want to do so?
I should have been more verbose - the installation CD in question is the Windows installation CD.  I was trying to get Grub to boot it after re-mapping the partitions, in order to fool the silly old Windows installer...

> **bulldog said:**
> Remapping is only useful if you have windows installed on a second disk instead of the first.
It has no function with partitions so better erase it.
...but it doesn't sound like that's an option after all.

> **Juan Largo said:**
> Is there a particular reason that you wish to do it the other way around?
The reason I want to do it this way is because I currently have Ubuntu on partitions 1 and 2; Iwanted to avoid having to move all my data and update configuration files, and also to learn something in the process.  :)

> **Juan Largo said:**
> most of the literature I've been reading on a dual-boot Windows/Linux installation advises to install Windows first and THEN Linux.
Yes, I've read this too.  I posted my question because I only found one procedure telling how to install Windows on a non-first partition - the one I tried - and Grub didn't seem to like it.

> **Juan Largo said:**
> One possible way to install XP with Ubuntu aleady installed is to use a reliable partitioning tool like Acronis Disk Director Suite to resize and move the existing Linux partitions toward the end of the disk and create an NTFS partition at the beginning.  Then use the XP installation disk to install XP on the first partition, where it is happy.  Then re-install Ubuntu and Grub by overwiting / (root) without overwriting your existing /home partition, thereby saving your existing Ubuntu software, documents, and settings.
Unless anyone comes up with any other leads,  I'm going to have to do something like this.  It's just going to be a little tedious.

---

### Post by louieb on 2006-12-18
Sounds like this is a case of if its not broke tweak it. You might try this to get grub to boot your XP install CD. [http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB](http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB)

---

