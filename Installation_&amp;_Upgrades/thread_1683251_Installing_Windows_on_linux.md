---
title: "Installing Windows on linux"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by djonko on 2011-02-07
Hello,

I got a problem. Every cd I put in my laptop shows up blank, I tried other cd's to no avail.

If I right click on the cd/dvd drive and look at the properties, those are all unknown.

I run Ubuntu 10.10 Maverick Meerkat and I have no idea what to do.

Thanks

---

### Post by Mark Phelps on 2011-02-07
Try changing your BIOS to boot from the CD drive, and then insert a bootable CD (i.e., Ubuntu destkop or Windows installation CD).

If it still does not read the contents of the CD, that implies that your laptop CD drive is bad.

IF the machine is several years old, or if the drive has seen a lot of use, you could purchased one of the CDs used to clean the laser lens.  That can get dirty and stop the reading from working.

However, once you do get the PC to read the CD, realize that you can NOT install Windows inside Linux -- unless you're talking about using VirtualBox -- which I wouldn't recommend on a laptop because of limited resources.

---

### Post by ajgreeny on 2011-02-07
Windows is not clever enough to even know that a linux filesystem partition exists on your hard disk, and therefore will not be able to install.

Quite heartening to see M$ making life more difficult for themselves than it need be.

However you will need to use your live CD to run gparted, with which you can shrink your ubuntu partition to make either unallocated space, or an ntfs partition.  The windows install system will see either of those and allow you to install the OS.  However, after doing that you will need to restore grub or use another bootloader system to get back to booting ubuntu.

EDIT:  Sorry, I think I answered without reading your post properly.

---

### Post by djonko on 2011-02-07
I already changed the BIOS, problem still persists.

It reads the disk, but it says it's a blank disk. But when I put it into another computer it works just fine.

I want to do a clean install of Windows XP because I'm having horrible problems with the I855 bugs.

The problem isn't that my computer doesn't see the CD, it just doesn't see any files on it.

---

### Post by ajgreeny on 2011-02-07
Can you run a live ubuntu CD, or does that also not work?  If you can, it at least points to the fact that the drive can read CDs.  Going back to my previous post, I believe I have read where it was impossible to boot a windows install CD where there was no available hard disk partition, so it may be worth running gparted from ubuntu live CD as I suggested, and deleting the partitions on disk, or shrinking one of them if you need to keep files or OS intact.

---

### Post by djonko on 2011-02-07
I tried the cd with ubuntu on it, still says it's a blank cd.

---

### Post by IWantFroyo on 2011-02-07
How new is your optical drive? How much abuse has it went through?

---

### Post by stchman on 2011-02-07
> **djonko said:**
> Hello,

I got a problem. Every cd I put in my laptop shows up blank, I tried other cd's to no avail.

If I right click on the cd/dvd drive and look at the properties, those are all unknown.

I run Ubuntu 10.10 Maverick Meerkat and I have no idea what to do.

Thanks

There is a possibility that your optical drive on the laptop is faulty.

---

### Post by djonko on 2011-02-08
I think it has something to do with a faulty driver or something. Because I can burn a CD using Brasero, then it says there are files on it. As soon as I open the drive, close it again, it starts reading the disk. Then again it says it's a blank CD...

---

### Post by djonko on 2011-02-09
I think I found the problem. My ubuntu doesn't recognize ISO files. How do I fix this?

---

### Post by ajgreeny on 2011-02-09
> **djonko said:**
> I think I found the problem. My ubuntu doesn't recognize ISO files. How do I fix this?
What do you mean "doesn't recognise ISO files?  What iso file are you talking about, and what are you wanting to do with it?

---

### Post by djonko on 2011-02-10
I tried burning a cd with brasero to see if that works. That worked, I burned the cd.

But now, everytime I insert a cd into the drive, the drive disappears.

EDIT:
When I type Dmesg in terminal I get this;

77.724004] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
[   77.724031] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
[   77.724041] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
[   77.724051] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
[   80.607031] lib80211_crypt: registered algorithm 'WEP'
[  266.394635] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.394644] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.394651] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.394659] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.394672] end_request: I/O error, dev sr0, sector 0
[  266.394679] Buffer I/O error on device sr0, logical block 0
[  266.397981] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.397987] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.397993] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.398000] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.398011] end_request: I/O error, dev sr0, sector 0
[  266.398015] Buffer I/O error on device sr0, logical block 0
[  266.401284] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.401291] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.401298] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.401305] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  266.401316] end_request: I/O error, dev sr0, sector 0
[  266.401320] Buffer I/O error on device sr0, logical block 0
[  266.404692] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  266.404699] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[  266.404705] sr 1:0:0:0: [sr0]  Add. Sense: Logical block address out of range
[  266.404713] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00

---

### Post by dino99 on 2011-02-10
the drm legal security kick you out

---

### Post by djonko on 2011-02-10
Explain please..

---

### Post by djonko on 2011-02-10
No one? It would be nice if I could use my laptop properly again

---

### Post by ajgreeny on 2011-02-11
You still haven't told us what the iso file is that you are trying, or have already tried to burn to CD.

> the drm legal security kick you out 	means that the file or CD you're trying to copy/burn is protected by **d**igital** r**ights **m**anagement and you will not be able to do what you want.

---

### Post by djonko on 2011-02-11
A custom XP iso with drivers and stuff slipstreamed into it.

I burned a CD with this cd drive (the problematic one). That worked, the cd works fine on my moms pc, but when I put it back into the drive in this laptop, the Drive disappears in 'Places'

or it says the cd is blank. 

It's pretty random but that are the 2 things it does.

---

### Post by Mark Phelps on 2011-02-11
> **djonko said:**
> A custom XP iso with drivers and stuff slipstreamed into it.

I burned a CD with this cd drive (the problematic one). That worked, the cd works fine on my moms pc, but when I put it back into the drive in this laptop, the Drive disappears in 'Places'

or it says the cd is blank. 

It's pretty random but that are the 2 things it does.

That pretty much indicates a hardware problem with the optical drive.

Did you read my earlier post about using a drive cleaner CD?  If the drive has seen a lot of use, a $10 cleaning CD can work wonders.

---

### Post by ajgreeny on 2011-02-11
> **Mark Phelps said:**
> That pretty much indicates a hardware problem with the optical drive.

Did you read my earlier post about using a drive cleaner CD?  If the drive has seen a lot of use, a $10 cleaning CD can work wonders.
+1

Just get a new drive or give the one you have a good clean.  If it were me, I would try to get a new one; they're cheap enough these days, though as it's a laptop, it is perhaps less cheap and a bit more difficult.

---

