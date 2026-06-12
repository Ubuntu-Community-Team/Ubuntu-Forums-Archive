---
title: "[SOLVED] triple boot XP/hardy/Vista"
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by karatekid on 2008-07-16
i recently  installed ubuntu on my pc in a dual boot with XP
then i installed vista in to another partition. As expected Grub had been wiped out and i could boot into Xp or Vista only.
then after reading on several sites i tried restoring the grub using the live CD.

i executed the following commands
```

grub
root (hd0,7)
setup(hd0,0)
quit
exit

```

everything looked fine.
however when i rebooted grub was loaded as usual and i came across the boot menu that was there when  it was dual boot(XP/hardy).
when i selected windows  Xp professional the screen showed
```

Starting 
stage 2.....

```
and then it came back to the boot menu without booting even XP
as such now vista is nowhere to be seen in the boot menu.the entry corresponding to XP doesn't work and i can only boot into Ubuntu.


here are my partition tables

```

sudo fdisk -l
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49734972

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1315    10562706    c  W95 FAT32 (LBA)   
/dev/sda2            1316        9993    69706035    f  W95 Ext'd (LBA)
/dev/sda3            9994       10011      144585    c  W95 FAT32 (LBA)
/dev/sda5            1316        4963    29302528+   b  W95 FAT32
/dev/sda6            4964        7576    20988891    b  W95 FAT32
/dev/sda7            7577        9026    11647093+   7  HPFS/NTFS
/dev/sda8            9027        9862     6715138+  83  Linux
/dev/sda9            9863        9993     1052226   82  Linux swap / Solaris


```

---

### Post by logos34 on 2008-07-16
Edit: sda1 is XP (C:\)  and sda7 is Vista (can't install the latter on anything but ntfs)

You might have to resort to restoring the vista bootloader to the mbr with the vista dvd, then get [EasyBCD]("http://neosmart.net/wiki/display/EBCD/Linux") so you use windows to dual boot ubuntu

---

### Post by Herman on 2008-07-16
Oh my gosh! 

What site has advised you to install GRUB to (hd0,0)?  :shock:!!!
```
grub
root (hd0,7)
[COLOR=Red]**setup(hd0,0)**[/COLOR]
quit
exit
``` You have installed GRUB to your Windows XP boot sector!
You should have installed GRUB to your first hard disk's MBR and not the XP boot sector.
```
grub
root (hd0,7)
[COLOR=Sienna]**setup(hd0)**[/COLOR]
quit
exit
```You can easily repair your Windows XP boot sector in lots of different ways, one way is to boot your Windows XP Installation CD to a [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") and use the FIXBOOT command.
It's also possible to restore the boot sector from it's backup from Ubuntu, refer to this link if you need to do it that way, [When the bootsector is not the same as its backup]("http://users.bigpond.net.au/hermanzone/p10.htm#differences_between_the_bootsector_and_its_backup") - FAT32.

You will need to fix your Windows XP boot sector before you'll be able to boot Windows regardless of what boot loader or boot manager you use.

---

### Post by logos34 on 2008-07-16
> setup(hd0,0)

Wow, how did I miss that?  I'm up way too late...

I'm glad you came along, Herman!

How's it going?

---

### Post by Herman on 2008-07-16
:) Good logos34, I'm well. Nice to see you here. :)
You are doing a good job. Sorry for barging in like this.  It's easy to miss little things like an extra '0' once in a while. You might have picked it up given a little more time.

---

### Post by karatekid on 2008-07-16
i did try to use 
fixboot c:
and fixmbr
however when i rebooted my system it just displayed "disk error"(grub was not there anymore) and did not boot.
then i tried reinstalling XP .when the files were copied and the system rebooted,again i got the same message.
after this  i tried the same thing with vista and again that same message
"disk error".
finally i booted off the ubuntu live cd and again followed steps i did earlier to restore grub.now i'm back at the same situation, grub loada but only ubuntu runs

---

### Post by Herman on 2008-07-16
It could be that when you installed Vista, that Vista has installed it's boot loader in your XP operating system and modified your Windows XP boot sector to point to it.
If you have a BCD folder in your Windows XP partition, that's probably what has happened, (without your permission or even your knowledge). Maybe you need to fix it with Vista recovery commands now instead. Refer to this article, [Installing Vista]("http://www.multibooters.co.uk/installing.html").

That means probably you need to Vista Recovery Console or whatever the equivalent is in Vista language, and run the appropriate command, (sorry, I can't remember it right now, but I think there's just one command for fixing Vista's boot manager and it does everything, I'm not sure.
Here is another useful link in case you don't have a Vista Installation CD, you can get a repair CD from here: [Windows Vista Recovery Disc Download]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") - Neosmart.net, thanks lswest for the link. Thanks for the download to Computer Guru, of NeoSmart Technologies (the developer of [EasyBCD]("http://neosmart.net/dl.php?id=1")).
That's what I think you'll probably need to do anyway, I might be wrong because I don't use Vista myself so I haven't tried those things out. Probably you should check with someone else first.
Maybe someone else with Vista can confirm this or help out by giving you some further pointers.
Regards, Herman :)

---

### Post by Mark Phelps on 2008-07-16
I have a multi-boot machine with Linux and Windows partitions and what Herman says is correct.  

GRUB wiped out the Windows MBR stuff, so you will have to restore your Vista boot loader first.  Of course, that will wipe out GRUB in the process, but once you get back into the Windows loader and confirm it works, restore GRUB -- but this time, to the first Linux partition, not to the MBR of the drive.

I have mine set up that way and it works great.

---

### Post by karatekid on 2008-07-16
i did try to restore windows vista bootloader using the vista DVD.
however it did not work.
Even windowsXP would not re-install.
finally  i used a partition manager to set a small 100mb partition as active(as well as primary) and installed XP in some other drive(with boot files in the 100mb small drive).
after this i edited the boot.ini file  to boot to my old windows installation and finally i was able get back to my old windows installation

---

### Post by Herman on 2008-07-16
> GRUB wiped out **[COLOR=Red]the Windows MBR stuff[/COLOR]**, so you will have to restore your Vista boot loader first. Of course, that will wipe out GRUB in the process, but once you get back into the Windows loader and confirm it works, restore GRUB -- but this time, to the first Linux partition, not to the MBR of the drive.
That's mostly right, except there's no such thing as a 'Windows MBR'. The MBR is not part of the Windows operating system. Even if you only have Windows and no other operating systems in a hard disk, the MBR is a stand-alone item, quite separate from any operating system partition. 
There's an MBR in the first sector of every formatted hard disk, and by convention, no partitions's first sector begins until after the fisrt track, at sector number 63. :)

The boot sector, however, (not to be confused with a MBR), is the first sector of a partition and could be said to belong to an operating system which is installed in that partition. :)

It might sound like I'm ranting, but it's very important to clearly define those two different locations becsue otherwise more people might be confused and install GRUB to their Windows boot sector, where it doesn't belong. (Often (hd0,0), but may vary in different computers depending on the partition arrangement, presence or not of a 'recovery partition' and so on).

It's quite safe and good to install GRUB to (hd0), which would be the first hard disk's MBR, where GRUB will be able to function as both the boot manager for other boot loaders in the computer, and also the boot loader for Ubuntu.
It's a good idea to (optionally) install GRUB to the first sector ('boot sector') of your Ubuntu partition.

If you didn't want to touch your hard disk's MBR when you install Ubuntu, you can install GRUB to the Ubuntu partition's boot sector (first sector of the partition), and install [EasyBCD]("http://neosmart.net/wiki/display/EBCD/Linux") in Windows XP or Vista. Easy BCD will then boot Ubuntu. (As logos34 suggested). Easy BCD is very good software as far as I know, but the last time I checked, it was free but it wasn't 'open source'. Apart from that, Easy BCD is a great choice for dual booters. Computer Guru, (the developer of [EasyBCD]("http://neosmart.net/dl.php?id=1")) seems like a great guy and is very hard working and helpful to Ubuntu users.

GRUB is an open source boot loader and boot manager. 
I hope that most people understand what 'open source' means so they can make an informed decision about which they prefer. 
There is certinaly no reason to fear installing GNU/GRUB to MBR. 

Regards, Herman :)

---

### Post by karatekid on 2008-07-17
i would also like to thanx Herman for his page
**Illustrated Dual Boot site-Install Ubuntu**
 i think in my case installing Grub on my Windows partition has caused some really bad problems. i am unable to boot from my windows partition .
whenever i  set my windows partition as active the computer just pops up with error message 
"disk error"
"press any  key to restart":(
is there any way to  correct this error without formatting my windows partition.

---

### Post by Herman on 2008-07-17
Here's a link to another website, [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm")
That website has free boot CDs you can download the will at least get your Windows XP to boot up. The CDs contain their own copy of with NTLDR and the other vital Windows booting files, so they bypass the MBR, and the boot sector, and NTLRD, (the Windows Loader), and boot.ini and NTdetect.com.
You should be able to at least boot Windows XP with one of those.
I'm not sure about Vista.
I was hoping the  [Windows Vista Recovery Disc]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") would fix that for you. Did you try it? 
What happened if anything?
Unfortunately I have to go now and will be away for a few days, but I'll be back. I hope you'll be able to get more help from someone in the meantime if you still need it.
Regards, Herman :)

---

### Post by Herman on 2008-07-17
:-k Hmmm, 
I wonder if there might be a spare Vista boot sector in the Vista partition we could move with 'dd' commands and I wonder if that would work, it seems like it might be worth a try.
Also, the backup boot sector is in the last sector of an NTFS formatted partition.
TestDisk can be used to restore it (to the Vista boot sector first), so there's two ideas that might be worth a try.

---

### Post by karatekid on 2008-07-20
finally i have been able to get a susseccful triple boot with Vista bootmanager as my bootloader.
i had to create a 100mb partition and set it as active and now all my boot files(for vista bootloader) reside in this  drive and not my windows partition.
But still one problem exists.
if i boot into XP from the bootloader menu everything works fine but if i try to boot directly my windows partition(using super grub) the error message pops up
"disk error".

---

### Post by karatekid on 2008-07-29
solved
perhaps i had damaged the filesystem on c: drive.
i booted using the gparted live cd and repaired the filesystem on my windows partition.now everything works fine

---

