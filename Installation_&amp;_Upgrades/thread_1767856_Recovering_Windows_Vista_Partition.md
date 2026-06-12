---
title: "Recovering Windows Vista Partition"
date: 2011-05-26
forum: Installation &amp; Upgrades
---

### Post by THE_An0mOLy! on 2011-05-26
Not sure if this is exactly the right section for this but here goes:

I recently accidentally corrupted my windows vista partition whilst trying to extend it via gparted under ubuntu 11.04 and then cancelling it shortly after starting. Resulting in me being unable to boot into vista (I don't have another copy of any windows OS so I'd really like not to have trashed this one :D)

Looking on gparted now my partition is Fat32(?) and apparently only has 36mb used =/

Any ideas anyone? ^^

Thanks in advance :D

---

### Post by ILoveYorkies on 2011-05-26
Hi,
 I'm afraid I can't help you too much but I have a suggestion that might help.  From here [http://en.wikipedia.org/wiki/List_of_live_CDs](http://en.wikipedia.org/wiki/List_of_live_CDs)
I have downloaded SystemRescueCD for myself but have not needed to use it yet but  the livecd boots for me that much I tried out. You could search for linux repair or rescue livecds for more info. Even download.com  has  info on Linux cds that rescue both Linux and Windows.  Type in the search box on download.com for free Windows repair or rescue cds.
Rescue and repair live CDs

 
[LIST]
[*][Billix]("http://en.wikipedia.org/wiki/Billix")  &#8211; a multiboot distribution and system administration toolkit with the  ability to install any of the included Linux distributions
[*][BootMed]("http://www.bootmed.com/") &#8211; a Live CD that was made to help those not familiar with Linux repair or recover their Windows Computer from a Live CD.
[*][Inquisitor]("http://en.wikipedia.org/wiki/Inquisitor_%28hardware_testing_software%29") &#8211; Linux-based hardware diagnostics, stress testing and benchmarking Live CD
[*][Parted Magic]("http://en.wikipedia.org/w/index.php?title=Parted_Magic&action=edit&redlink=1")
[*][RIP: (R)ecovery (I)s (P)ossible]("http://en.wikipedia.org/wiki/Recovery_Is_Possible") is a Linux-based CD with partition tool and network tools ([Samba]("http://en.wikipedia.org/wiki/Samba_%28software%29")), based on the 2.6.17 kernel.
[*][System Folder]("http://en.wikipedia.org/wiki/System_Folder") of [Mac OS]("http://en.wikipedia.org/wiki/Mac_OS") on a [CD]("http://en.wikipedia.org/wiki/Compact_Disc") or on a [floppy disk]("http://en.wikipedia.org/wiki/Floppy_disk") &#8211; works on any media readable by [68k]("http://en.wikipedia.org/wiki/68k") or [PowerPC]("http://en.wikipedia.org/wiki/PowerPC") Macintosh computers.
[*][SystemRescueCD]("http://en.wikipedia.org/wiki/SystemRescueCD") is a Linux-based CD with tools for Windows and Linux repairs, based on the 2.6 kernel.
[*][Trinity Rescue Kit]("http://en.wikipedia.org/wiki/Trinity_Rescue_Kit") &#8211; Mandriva Linux-based CD for use on a Windows or Linux-based system.
[/LIST]
Hope this helps.

---

### Post by THE_An0mOLy! on 2011-06-01
Just tried SystemRescue and BootMed (bootmed wouldnt even boot...) but I'm not sure if any of the others will help (although I'm going to try them all now anyway)... I';m just looking for a way to restore the partition back to how it was.. or at least a way of accessing the data that should be there =/

Forgive me if I'm missing something blatently obvious here but any help is greatly appreciated. :D

---

### Post by Quackers on 2011-06-01
If you boot from the Ubuntu live cd and choose "try Ubuntu" does it let you access the Windows data from the Places menu?

If you want to restore the partition as it was testdisk could be worth a try.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

For its use this is probably a better link
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

---

### Post by THE_An0mOLy! on 2011-06-01
I used testdisk and all it says was that the partition is FAT32 and practically empty... Would deleting the partition then trying to recover it help?

Edit - Just tried booting back into Ubuntu and now it says: "This is not a bootable disk. Please insert a bootable floppy and press any key to try again..."

I think I just broke it some more... somehow -.-

---

### Post by Quackers on 2011-06-01
I wouldn't have thought so.
Did you do the deeper search as shown in the second link?

---

### Post by THE_An0mOLy! on 2011-06-01
Yes I did, didn't come up with anything else. I'm booting into SystemRescueCD again now and I'll see if I can what those links say with testdisk :D

---

### Post by THE_An0mOLy! on 2011-06-09
[FONT="Courier New"]Okay so after using TestDisk under SystemRescueCD I successfully located all of the partitions and have tried as many configurations as I can in order to get the laptop to boot - the latest of which (while using TestDisk's own MBR code) did nothing for 4 of the options and the first merely rebooted the laptop =/

I've taken the drive out now and am running it and TestDisk on my new win7 PC (in the hope it will be faster, or at least less annoying to monitor).

Any ideas?[/FONT]

---

