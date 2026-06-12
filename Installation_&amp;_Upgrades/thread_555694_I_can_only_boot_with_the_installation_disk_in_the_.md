---
title: "I can only boot with the installation disk in the cd/dvd drive"
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by kyfho23 on 2007-09-20
'lo, all
   After installing Kubuntu, I can only boot into the installed system on the hard drive with the installation disk in the cd/dvd drive. After the BIOS screen, the boot stops with a flashing cursor in the upper left corner-no splash screen, no text, just the cursor. The installation disks have worked before.
   I've tried the following so far:
   1) Reset the BIOS settings to defaults. (I'm on an Intel Core2Duo E6600).
   2) Completly formatting the drive, and installing on the clean disk.
   3) Using several different installation disk-a ShipIt Kubuntu 7.04 CD, a Kubuntu 7.04 DVD, and an Ubuntu 7.04 64-bit installation disk.
   4) Both activating and not activating popularity contest during the install.

   The problems started after I had installed, then removed, the Ubuntu 64-bit system. However, as I said, I've used FreeDos to format the drive since then, and reset the BIOS.
   I have my harddrive set up with a 50-Gig / partition, a 200 Gig /home partition, and a 264 Meg swapspace. 

   Any ideas?  Thanks in advance.

---

### Post by Pumalite on 2007-09-20
You probably have some garbage left in your hard drive. I would DBan the drive: [http://dban.sourceforge.net/](http://dban.sourceforge.net/), then use Gparted to make one large partition of your drive, format to ext3 if you want; then install>Guided>Use Entire Disk

---

### Post by kyfho23 on 2007-09-20
*sigh* 
do you think I can keep the separate /home partition?

---

### Post by Pumalite on 2007-09-20
You can back it up including 'Hidden Files', but you have to DBan your entire drive. Restore /home after a clean install.

---

### Post by kyfho23 on 2007-09-20
I'll let you know what happens. Downloading DBan and GParted now.BTW, love the quote!
CTW

---

### Post by Pumalite on 2007-09-20
Glad you like it. Nobody gets out of here alive!

---

### Post by dabl on 2007-09-20
> **kyfho23 said:**
> 'lo, all

 After the BIOS screen, the boot stops with a flashing cursor in the upper left corner-no splash screen, no text, just the cursor. 

 Any ideas?  Thanks in advance.

Actually, the original problem might be fixable with this approach:

[http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

:)

---

### Post by kyfho23 on 2007-09-20
just to keep everyone updated....
  i'm now getting messages about bad blocks....but i'm going to try dabl's idea before gparted.

also, FreeDos in the CD will also allow the system to boot.

more as it occurs...

ctw:confused:

---

### Post by Pumalite on 2007-09-20
You mean WTH.

---

### Post by kyfho23 on 2007-09-20
OK...having spent the afternoon on this...I finally tried the 'install & use guided partitioning for the whole disk" idea that mr. puma had suggested. <shrug> it worked.

best i can figure is that yes, there was some junk left from the 64-bit install.

and Puma...ctw are my initials, wth is how i was feeling.

i'm going to mark this off as one of those learning experiences :)

thanks for everyone who help, or even looked. one of the reasons i won't move away from ubuntu (or kubuntu) are these very support fora.

be well all.

ctw

---

### Post by Pumalite on 2007-09-20
Glad you got it working!

---

