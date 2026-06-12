---
title: "uninstall ubuntu"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by liveinbox on 2009-12-02
does anyone know how to safely and fully remove ubuntu 9.10 from my system with ubuntu being the only os on the system.

thank you.

---

### Post by u.b.u.n.t.u on 2009-12-02
> **liveinbox said:**
> does anyone know how to safely and fully remove ubuntu 9.10 from my system with ubuntu being the only os on the system.

thank you.

Is the following correct? You have a HDD with Ubuntu on it, nothing else, nothing of value, and you want to remove Ubuntu.

You can simply format the HDD if all you want is a blank HDD. A format would erase EVERYTHING.

---

### Post by liveinbox on 2009-12-02
> **u.b.u.n.t.u said:**
> Is the following correct? You have a HDD with Ubuntu on it, nothing else, nothing of value, and you want to remove Ubuntu.

You can simply format the HDD if all you want is a blank HDD. A format would erase EVERYTHING.


Yes all I have is ubuntu on the drive, however, I want to revert to my original drive settings, that being the ntfs and fat32 (whatever it means) and their sizes before ubuntu was installed in order to ready my system for windows xp pro. 

 I did try to format the drive 3 times.  What I did was use a usb 2.0 to IDE/SATA cable to view the drive on my pc.  right clicked and format.  But before formatting it, nothing showed up in any of the partitions (nfts and fat32).

To my surprise, ubuntu was still intact, password settings and all even the apps that were open showed up as if nothing happened.

---

### Post by darkod on 2009-12-02
You can do the NTFS formatting with the XP installer. When you start the install it will show you your drive and the partitions. It can't recognize ubuntu filesystem but it will be able to see the partitions. You can just format them then as NTFS and select where you want XP installed.

As for the sizes, you can't revert to the same sizes automatically unless you used the same size partition for ubuntu. In that case when you format them as NTFS it will be like before. Or you can delete all partitions and create the sizes you want manually.

All of this with the XP installer.

If you still want to format before starting the XP install, boot with ubuntu cd, select Try Ubuntu option and open Gparted. There you can format/delete/create the partitions. If swap is mounted use right-click swapoff to unmount it. The other partition should be unmounted in Try Ubuntu option.

---

### Post by u.b.u.n.t.u on 2009-12-02
As darkod said, the XP CD is the best way to ready a hard drive for XP installation. The same is also true for Windows 7.

The quickest way is a quick format of the entire HDD by the XP CD to NTFS and then create the partitions you want.

Unless there exists a particular pressing need to have a FAT32 partition for XP, such really is rather redundant today.

NTFS replaced FAT32 as the Windows file system.

More info:

[http://en.wikipedia.org/wiki/NTFS](http://en.wikipedia.org/wiki/NTFS)

Also when you see FAT referred to, they mean FAT16, which was the file system prior to FAT32.

Ubuntu 9.10 uses ext4 as the file system. A leading edge file system for linux.

---

### Post by liveinbox on 2009-12-02
> **u.b.u.n.t.u said:**
> As darkod said, the XP CD is the best way to ready a hard drive for XP installation. The same is also true for Windows 7.

The quickest way is a quick format of the entire HDD by the XP CD to NTFS and then create the partitions you want.

Unless there exists a particular pressing need to have a FAT32 partition for XP, such really is rather redundant today.

NTFS replaced FAT32 as the Windows file system.

More info:

[http://en.wikipedia.org/wiki/NTFS](http://en.wikipedia.org/wiki/NTFS)

Also when you see FAT referred to, they mean FAT16, which was the file system prior to FAT32.

Ubuntu 9.10 uses ext4 as the file system. A leading edge file system for linux.


Oh, when I got the usb 2.0 to ide/sata cable to save my data to my external drive, I saw fat32 with nfts and thought it was suppose to be there as a default and necessary for xp.  I'm learning here.

So just to recap and clarify: to remove ubuntu, and have the right partitions intact, and install xp without difficulty I can restart my computer with the windows xp pro. 4 or 5 installation cds and forget about the process after that because the cd will take care of formatting the drive to ntfs (don't need fat32) and I can start using xp pro. once installation is through.

hopefully I didn't forget anything

---

### Post by darkod on 2009-12-02
Yes, something like that. First of all, XP is on one CD so you are confusing me with mentioning 4 or 5 CDs.

Start your computer with the CD inside, it will start XP installer, you can format your current partitions as NTFS if you wish to keep their size as they are. Then specify where you want XP installed, on which partition. In fact, you can format just that one where XP will be installed at that time.

You can format the other partitions later from the working XP.

---

### Post by u.b.u.n.t.u on 2009-12-02
> **liveinbox said:**
> Oh, when I got the usb 2.0 to ide/sata cable to save my data to my external drive, I saw fat32

What devise was using FAT32? A modern HDD for Windows uses NTFS. Some usb pens use FAT32.


> **liveinbox said:**
> So just to recap and clarify: to remove ubuntu, and have the right partitions intact

As I stated, it is easier to "quick format" the entire HDD and then create your partitions than to individually modify each partition, but either approach will work.

Make sure you have backed up ALL data before formatting. Verify that a backup has integrity ... that the data actually exists and is accessible.

---

### Post by liveinbox on 2009-12-02
> **darkod said:**
> Yes, something like that. First of all, XP is on one CD so you are confusing me with mentioning 4 or 5 CDs.

Start your computer with the CD inside, it will start XP installer, you can format your current partitions as NTFS if you wish to keep their size as they are. Then specify where you want XP installed, on which partition. In fact, you can format just that one where XP will be installed at that time.

You can format the other partitions later from the working XP.


about the cd: someone told me about windows xp installation cds, there being 4 or 5 of them.  I'll trust that there is one.  maybe it's something else.

ok...I will get the cd (xp pro.) and do what's been suggested and hope it works.  thanks for this help.

I'll just go with the one partion of ntfs taking up 100% of my 60GB drive and install xp on there.

---

### Post by darkod on 2009-12-02
Maybe what they had in mind was that there are different versions. XP Home, XP Pro, XP Media Centre, etc. Otherwise it fits on one CD.

---

### Post by u.b.u.n.t.u on 2009-12-02
> **liveinbox said:**
> about the cd: someone told me about windows xp installation cds, there being 4 or 5 of them.

I read what darkod posted. He is correct in what he has written.

---

### Post by liveinbox on 2009-12-05
> **u.b.u.n.t.u said:**
> I read what darkod posted. He is correct in what he has written.


thanks for the help with removing ubuntu.  I have windows xp installed now but have one more hurdle: internet not working maybe the attachment may hint at a problem you might now how to fix.  thanks again.

---

### Post by darkod on 2009-12-05
You need drivers for all those components that have the yellow mark. Welcome to Windows XP.

---

### Post by liveinbox on 2009-12-05
> **darkod said:**
> You need drivers for all those components that have the yellow mark. Welcome to Windows XP.

I know this a ubuntu forum--would you be able to point me in the right direction or a great forum designed that supports such enquiries.

I really am a semi-novice if not a novice in computer know-how.

---

### Post by darkod on 2009-12-05
If you have branded machine, like Dell, HP, etc then check the model number on any stickers on it, and go to their website, look for Support section and try to find them there.
If you have custom built machine, then you have to look them up component by component, which will be difficult if you don't know their models.

Or just install Ubuntu as only OS. :) Unless you REALLY, REALLY need XP.

---

### Post by liveinbox on 2009-12-05
Or just install Ubuntu as only OS. :) Unless you REALLY, REALLY need XP.[/quote]

I would have stayed with ubuntu alone but I couldn't install the program I need most: "Revit Architecture 2009".  even with "wine" it didn't work and soon after that I lost my sound so I decided to revert to xp.  didn't really want to...ubuntu's alright.

I think I'm at the site I need to be to download drivers but it all seems mess to me, but my thinking is all the info I need is on it so I'll just read away. thanks.

also would you happen to know any good, reputable forums specifically for ibm's (lenovo) or internet problems in general.  thanks.

---

### Post by u.b.u.n.t.u on 2009-12-05
> **liveinbox said:**
> I know this a ubuntu forum--would you be able to point me in the right direction or a great forum designed that supports such enquiries.

I really am a semi-novice if not a novice in computer know-how.

Your mainboard came with a set of drivers on a CD, find and install. If for whatever reason you don't have such, then check the mainboard manufacturers website for applicable downloads.

Make sure you update XP to SP3.

---

### Post by u.b.u.n.t.u on 2009-12-05
> **darkod said:**
> Or just install Ubuntu as only OS. :) Unless you REALLY, REALLY need XP.

XP is fast becoming obsolete. On compatible hardware Ubuntu is a good alternative.

If you need windows programs and are likely to do so in the future, then Windows 7 and a new computer are in order. Ignore the Microsoft minimum specs and treat their "recommended" specs as the true minimum.

---

### Post by liveinbox on 2009-12-05
unfortunately I did not get a driver cd with my laptop.

but for sure in the future I plan on getting the latest in os and laptop tech, but for now I'm alright with
the os I have and the laptop (IBM R51) is alright.

I didn't find much problems in the 2 days I used it, but even with "wine" I couldn't install needed software: Revit Architecture 2009. and the sound stopped working after a while.

but a great os it's interesting.

I hate downloading these drivers: I have 4 more left from the attached photo..."1394 Net Adapter" isn't able to upgrade from the lenovo drivers etc. webpage

and "ethernet controller, netowork controller, and unknown device" remain in the yellow question and exclamation status

although out of place with this downloading-internet-driver issue, any further suggestions

(if I had $4000 I would invest in  elite thinkpad w700ds but in the future)

---

### Post by u.b.u.n.t.u on 2009-12-05
Find the mainboard manufacturer. If it isn't badged then go to their website and download the drivers set for the mainboard. Obviously this only works for Windows.

---

