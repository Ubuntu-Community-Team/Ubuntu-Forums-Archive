---
title: "Can't get live usb to boot"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by EowynCarter on 2010-05-04
I'm trying to get a persistent live usb of ubuntu lucid, with usb creator.

When trying to boot, it will just display "boot error".
So I clean the USB key, re-installed everything. Still the same.

Then I try on laptop, and surprise, it works.
So i restored default on the desktop's BIOS. And updated BIOS.
No changes.

I'm kind of out of ideas there. So if anyone have a clue on what's going on.

---

### Post by unisubzero on 2010-05-04
I had the same problem with one of my 4Gig USB sticks (created with unetbootin tho). For some strange reason it didn&#8217;t wonted to boot from it (Zotac mobo) but after I took my second one it booted just fine. On Intel mobo both USB sticks boot just fine.

---

### Post by EowynCarter on 2010-05-04
I tried bought an other usb key yesterday, didn't booted either.
What bugs me is that it use to work.

Plus, I already used that key to boot ubuntu without problems.

---

### Post by EowynCarter on 2010-05-04
Ok, tried an other key, no dice.

I'm kinda baffled by all this. And i still can't install lucid on my PC. :-k

---

### Post by Skaperen on 2010-05-04
How are you creating the USB flash drive?  If all you want to do is install to another drive FROM a flash drive, maybe this will help.  If you have another Linux to create it with, you can download a special image I created from the Ubuntu ISO, and directly copy it raw to the flash drive using dd or any other basic copy tool.

```
http://slashusr.net/ubuntu/10.04/ubuntu-10.04-desktop-amd64.iso.img
```Change "amd64" to "i386" if you need the 32-bit version.  Note the different extension on the file name.  Once downloaded, you can copy with like this (assuming your flash drive is /dev/sdc ... change the name if different):

```
dd if=ubuntu-10.04-desktop-amd64.iso.img bs=1048576 of=/dev/sdc
```Be sure to copy to the whole drive, not a partition. ** IT WILL ERASE EVERYTHING ON THE TARGET DRIVE** so be careful.  This image file can also be used to burn a CD/DVD like the regular ISO, too (in case you only want to keep one copy around for space saving reasons).

---

### Post by EowynCarter on 2010-05-04
what's the differance between this and the .iso ?

---

### Post by Skaperen on 2010-05-04
The image I made is derived from the ISO by adding an MBR with a patched GRUB v0.97.  The kernel, initrd, and memory test program are appended to give them a linear reference.  The parts modified are either outside of the ISO filesystem part, or in the first 32K that is reserved.  So they are co-compatible.  There are netbook and kubuntu versions out there, too.

---

### Post by EowynCarter on 2010-05-05
Makes sense. I tried with the original iso yesterday, key looked empty. At that point the bios saw the key as "hard drive" rather than the usual "usb removable" 

I realised that I hadn't been bothered with sound cards. Hinting that internal sound card is still deactivated. Even though I told the BIOS to restore default settings...

---

### Post by EowynCarter on 2010-05-05
Mmmm, BIOS reseted, no dice.

I think I'm going to use the good old cd way.
What's weird...

I'll mail dell, maybe they'll have some clues. And if someone can fix the bios... 

Tanks for your help.

---

### Post by Skaperen on 2010-05-06
> **EowynCarter said:**
> Makes sense. I tried with the original iso yesterday, key looked empty. At that point the bios saw the key as "hard drive" rather than the usual "usb removable" 
The flash key is emulating a hard drive device, so that's what it sees.  Certain flash keys can emulate a CD/DVD drive, and there is a tool to put your own ISO in it (u3-tool.sourceforge.net).  But just because the data is an ISO does not make the device look different ... it's still a hard drive.  You could put an ISO on a real spinning hard drive and get the same effect.

Note that the special image I created modifies the ISO image to make it look like what is expected on a hard drive (without breaking what is expected on a CD/DVD).  It's a hybrid and can work either way.  The filesystem on the image is still an ISO, and it is still mounted by reference to the whole drive.  But the Casper system Ubuntu uses is smart enough to find it and mount it, anyway, so it works.

---

### Post by davethefan on 2010-05-15
Hi, Long time reader - first time poster.

I've recently had the same trouble with an 8GB Transcend on an IBM Thinkpad X30, and after hours of running around in circles, managed to boot without problems.

I used MBRWiz under windows to look at what partitions were on the drive, and it seemed that the geometry of the drive was corrupt - there were 4 partitions of various sizes, one of which was 400GB!

What I did was format the drive using [HP USB Disk Storage Format Tool]("http://files.extremeoverclocking.com/file.php?f=197") - this resets your drive to factory settings.

I then used Universal USB Installer to convert the ISO as normal, and it booted no problem.

Hope this helps somebody!
davethefan

---

