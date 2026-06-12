---
title: "Installed grub 2 over my windows boot sector"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by nickajeglin on 2010-07-08
Then I accidentally messed up with testdisk and wiped out the backup one too. Here's the relevant part of my bootscript results: 
```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 318767303 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM
```

Right, so anyways, should I just use a windows cd to fixmbr? The only reason I ask is because I'm afraid that when I do that it will torch my grub 2 stuff.

---

### Post by ebin on 2010-07-08
When I install windows after Ubuntu, or do something wipe out my MBR I've found the [super grub disk]("http://www.supergrubdisk.org/") is the easiest way to correct the problem.

---

### Post by drs305 on 2010-07-08
This link should provide the solution to your problem:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

---

### Post by Grenage on 2010-07-08
I'd agree with the above.  I've always reinstalled grub from a live CD and run a grub-update.

---

### Post by oldfred on 2010-07-08
From the windows tools fixMBR overwrites the grub in the MBR and then you can only boot windows.
the windows command if the testdisk procedure does not work is fixBOOT as that rewrites the boot sector in the partition PBR.

---

### Post by nickajeglin on 2010-07-08
Drs305: I already did that, I just messed it up and wiped out the backup sector as well.

And I did get the supergrub disk just in case I mess this up. :p Can it write windows compatible boot sectors? In any case I'll definitely try out fixboot instead of fixmbr, since that fixmbr sounds like what I was afraid of, whereas fixboot sounds right. Thanks oldfred.

---

### Post by Ibidem on 2010-07-08
I'd try grub4dos, to load ntldr.  [http://diddy.boot-land.net/grub4dos/Grub4dos.htm](http://diddy.boot-land.net/grub4dos/Grub4dos.htm)
But that's just me...
If you do that, I suggest installing grub4dos to sda1 eventually (I presume that's the Windows partition).
If you can boot grub4dos to a command prompt, run this:

find --set-root /ntldr 
		chainloader /ntldr 		

Which loads xp.

I'd say to use syslinux to load grub4dos the first time.

Alternatively, use Super Grub Disk.

---

### Post by nickajeglin on 2010-07-09
Thanks oldfred, fixboot works like a charm.

---

