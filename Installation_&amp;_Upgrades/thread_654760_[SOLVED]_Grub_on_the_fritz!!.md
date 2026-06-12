---
title: "[SOLVED] Grub on the fritz!!"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by baylorbear on 2007-12-31
I installed Ubuntu to my second hard drive -- on which I had previously established a ntfs partition and wanted to use the remainder for Ubuntu.

HD0 is Vista all the way... 
HD1, 1 is where Ubuntu was supposed to live.

Install worked OK, and I clicked "Advanced" just before clicking INSTALL and set Grub to install to HD1.  

I did this because I didn't want GRUB overwriting the MBR because of all the horror stories I've heard about trying to get it to load Vista properly.

End result?  Windows works fine because it doesn't know Ubuntu is installed.  But I can't get into Ubuntu for the life of me...

I tried following these directions:  [http://www.thorsten-lux.de/files/wiki.html](http://www.thorsten-lux.de/files/wiki.html)

But my new "Linux" option in the Windows Boot Manager yields nothing but a blinking cursor...

I tried setting my second hdd as the primary booting drive in CMOS and I DO get the Grub loader, but the option for Vista provides yet another blinking cursor (no hdd activity)... and the option to load Ubuntu just gives an "Error 22:  Partition Not Found."

You guys got any suggestions?

I want to have my Vista hard drive remain largely unchanged... simply wanted to have the Windows Boot Manager to link to GRUB or directly to Ubuntu.

---

### Post by PmDematagoda on 2007-12-31
Edit the entry for Ubuntu so that "root" is:-
```
root      (hd1,0)
```
Then press "B".

---

### Post by logos34 on 2007-12-31
> **PmDematagoda said:**
> Edit the entry for Ubuntu so that "root" is:-
```
root      (hd1,0)
```
Then press "B".

no, I think it's **(hd0,1)** that baylorbear wants...If the ubuntu partition is on the second partition after the NTFS one:
> 
I installed Ubuntu to my second hard drive -- on which I had previously established a ntfs partition and wanted to use the remainder for Ubuntu.

then menu.lst lists (hd1,1), and he says he installed grub on (hd1), i.e. the mbr.  But he's changed the Bios boot order to directly boot the ubuntu drive, so it is now (hd0), and the root would be (hd0,1)

---

### Post by baylorbear on 2007-12-31
Thanks very much for your reply!  

I attempted your suggestion and got:
Error 17: Cannot mount selected partition.

Any thoughts?

---

### Post by baylorbear on 2007-12-31
> **logos34 said:**
> no, I think it's **(hd0,1)** that baylorbear wants...If the ubuntu partition is on the second partition after the NTFS one:


then menu.lst lists (hd1,1), and he says he installed grub on (hd1), i.e. the mbr.  But he's changed the Bios boot order to directly boot the ubuntu drive, so it is now (hd0), and the root would be (hd0,1)

Nice point... lemme give that one a try!!  I will respond momentarily!

---

### Post by baylorbear on 2007-12-31
> **logos34 said:**
> no, I think it's **(hd0,1)** that baylorbear wants...If the ubuntu partition is on the second partition after the NTFS one:


then menu.lst lists (hd1,1), and he says he installed grub on (hd1), i.e. the mbr.  But he's changed the Bios boot order to directly boot the ubuntu drive, so it is now (hd0), and the root would be (hd0,1)

Absolutely beautiful!  This worked without any problems.  When I applied the same thinking to the Windows Vista grub entry, it also loaded Windows just fine.

NOW -- If I may pose two questions...

1)  After I selected "E" to edit the entries in Grub, it did not save those changes.  I assume I will have to manually make the corrections from within Ubuntu... but how?

2)  I had previously attempted to add a second line item in the Windows Boot Manager called "Ubuntu."  This line item still exists but does not work.  I followed these instructions:  [http://www.thorsten-lux.de/files/wiki.html](http://www.thorsten-lux.de/files/wiki.html)  making use of BCDEDIT in Windows Vista.  How do I delete the line item I created here so that when I select VISTA from grub, it doesn't bring me to the Windows Boot Manager screen every time?

THANKS A TON!!!  I was growing very frustrated!

---

### Post by logos34 on 2007-12-31
1) to make the changes permanent:

gksudo gedit /boot/grub/menu.lst

change the 'groot' line and ubuntu 'root' lines

also, you need to edit /boot/grub/device.map

---

### Post by logos34 on 2007-12-31
2) I don't run vista so not sure how to do that from command line. 

Get [EasyBCD]("http://neosmart.net/dl.php?id=1")--makes editing boot manager a cinch.

---

### Post by baylorbear on 2007-12-31
> **logos34 said:**
> 1) to make the changes permanent:

gksudo gedit /boot/grub/menu.lst

change the 'groot' line and ubuntu 'root' lines

also, you need to edit /boot/grub/device.map

I'm looking at device.map right now... and am unsure of what changes I need to make...
Presently it reads:
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

Should I change this to:
(hd0)	/dev/sdb
(hd1)	/dev/sda
(hd2)	/dev/sdc

Additionally -- what is the benefit to this edit?  What would be the possible errors caused by NOT editing this file?

And lastly -- is there like a "thanks" button in the forums I can click to give credit?

---

### Post by logos34 on 2007-12-31
actually, if you're able to boot vista from grub as it is and the only problem is that extra boot manager screen, don't change anything.  if it ain't broke...

click the little star icon next to 'quote' lower right.

---

