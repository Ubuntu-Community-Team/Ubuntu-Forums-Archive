---
title: "Lost MBR with Ubuntu 7.04 installation"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by dudemanguy333 on 2007-06-07
I recently installed Ubuntu 7.04 after having 6.11 and WinXP in dual boot, with a shared FAT32, for a while. My computer has always been oddly buggy, so I wasn't all that surprised when it wouldn't let me simply update from 6.11 automatically. I downloaded the installer, and reformatted my old partition of 6.11 and installed 7.04.

When I then booted my computer, GRUB skipped the step where it asks which drive to boot off of. I thought that was odd, too, but probably not a big deal. What really got me worried was when the shared FAT32 wouldn't mount. In fact, the computer had no idea it was even there. I did a little research on the topic, and found that the Master Boot Record was most likely destroyed with the installation of 7.04. Someone mentioned something about using the XP cd to repair the Windows partition, so I tried that and it didn't work. That would be fine, except now I can't even boot off of Ubuntu, because that cd wiped my MBR again or something. Is there anything I can try to recover some data? I would play with some stuff that I found elsewhere, but I'm afraid of damaging things further.

---

### Post by mckinneycm on 2007-06-07
You might just want to start from scratch. How important is the data that's on the system?

---

### Post by dudemanguy333 on 2007-06-07
The stuff is of enough importance that I wouldn't mind working a bit to try to recover it, yet it's not the end of the world if it isn't recovered.

---

### Post by myoungf1 on 2007-06-07
First of all is the windows partition still in place?  From the Windows CD go to the Repair part of the CD after booting up and choose, I think, MiniNT.  Next, if you haven't done so already, do a chkdsk /r and then chkdsk /f.  Next try to do a fixmbr.  Doing that in that precise order should fix any Windows MBR problems that occur.  After you do that you will need to reinstall grub, can get that from searching the forums, to get grub back on both the windows partition and the ubuntu partition.

---

### Post by jettapup on 2007-06-07
If you have access to a win 98 start up disk,  boot off of it and then
c:\fdisk /mbr This got my windows partition back after I hosed my Ubuntu partition.and got into a continous grub failure error 22 loop.
JettaPup

---

### Post by logos34 on 2007-06-07
The easiest thing to do is restore grub to the mbr, then if you can boot into ubuntu at least you'll have a functioning OS.  If this is a single hard disk dual boot setup, just boot from the Ubuntu LiveCD, go to the destop and open a terminal and type:

sudo grub
root (hd0,x)      where x = the the # of the root partition minus 1 (grub starts counting from 0)
setup (hd0)  
quit

---

### Post by dudemanguy333 on 2007-06-07
Hrm, no dice. The situation is that there is seemingly nothing in place, and if I were to go and set up partitions, it would just say that there is a sinlge corrupt partition. Doing chkdsk /r said that there were one or more unrecoverable errors on the disk.

I've seen people make reference software that is able to recover files and the likes. I'd assume something like this would be applicable to this situation? And does anyone know why this would happen, and how to avoid it in the future (besides more thorough backing-up)?

---

### Post by dudemanguy333 on 2007-06-07
to Jettapup: I don't have 98 install cd :(

to logos34: Recovering the files takes the priority at the moment. I can always just reinstall everything, and it's no big trouble, but I don't want to damage the filesystem further.

---

### Post by myoungf1 on 2007-06-07
> **dudemanguy333 said:**
> Hrm, no dice. The situation is that there is seemingly nothing in place, and if I were to go and set up partitions, it would just say that there is a sinlge corrupt partition. Doing chkdsk /r said that there were one or more unrecoverable errors on the disk.

I've seen people make reference software that is able to recover files and the likes. I'd assume something like this would be applicable to this situation? And does anyone know why this would happen, and how to avoid it in the future (besides more thorough backing-up)?

As far as why their are unrecoverable errors on the disk that could be due to many reasons, Ubuntu install was corrupt, viruses, etc.  And yes there are programs out there to do a disk recovery but the free ones are worthless and the shareware ones only tell you what the problem is and its not cheap to get a good recovery program.  It does look like you will need to get a recovery software program.  Start with ZDNet and see what they have in the ways of disk recovery, sorry I can't give you a specific name but its been awhile since I have looked for such a program.  Also more thorough backing up of any pc is always a good idea especially if you have programs and files that you don't want to lose in cases like these.

---

### Post by logos34 on 2007-06-07
After reinstall, if if you still can't access that fat32, you might consider gettting [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").

I've run it from a number of utility cds including [SystemRescueCD]("http://www.sysresccd.org/Main_Page")

---

### Post by myoungf1 on 2007-06-07
Take a look at the following link;

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

This has some good documentation on the different options of chkdsk for win xp and could be worth a try before trying to do a full recovery of the windows partition.  Also have you tried to reinstall grub first to see if that works?

Edit:  Also for the future you might try Ultimate Boot CD [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) so if you ever run into this problem in the future you will have something readily available to help you recover you windows.

---

### Post by alex2035 on 2007-06-07
I got same problem couple of times, due to the fact that I was trying different distros (they where all writing Grubs or LILOs on top of each other).
I made myself a CD from a Win98 boot disk image (the CD thinks its a floppy, never mind) and boot from there  to a DOS prompt, type fdisk /mbr and you are done (forget XP console, it doesnt help much). Your Windoze would be up and running, fix then your linux or whatever.;)

---

### Post by dudemanguy333 on 2007-06-07
Just a follow up,

Thanks for all the suggestions! I was able to use testdisk through the SystemRescueCD very easily, and from there I was able to remake the FAT32 and NFTS partition. The NFTS was too damaged to boot form, so I created a third partition of the Ubuntu that I no longer needed. I wiped it and installed windows on it, then booted and recovered files with Active@ File Recovery. It was surprisingly easy actually. From now on, I'm being more careful about backing up before messing with OSes. ;)

---

### Post by praxis22 on 2007-06-10
Try Paragon Partition Manager 8 pro (widows app)

It understands Linux file systems, and has support for swap2, ext2, ext3 & ReiserFS, and can recover partitions, etc. You'd have to buy it, but it all depends how much your data is worth.

---

