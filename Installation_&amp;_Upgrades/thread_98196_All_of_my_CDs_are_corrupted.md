---
title: "All of my CDs are corrupted"
date: 2005-12-02
forum: Installation &amp; Upgrades
---

### Post by Sirin on 2005-12-02
Hello. My 5.10 CDs just came in today (after two months of waiting). I put my install CD in. I run the integrity test on the CD. It fails. Then I run the test on a second CD, and that one fails too. Then after running 10 CDs on the test with all of them failing the tests, I try 10 more. They all fail. So I tried the rest that came in with the box. NONE of them passed the test. So here I am, with a whole box of CDs that don't work. :(

Does Canonical test their discs before shipping them?

---

### Post by leezer3 on 2005-12-02
Sounds much more likely to me that your CD drive is fubared.
Can you post a make, model & age please.
You may need to use some of the drive tuning parameters on install, but I don't know them offhand :cool: 

-Leezer-

---

### Post by Sirin on 2005-12-02
[QUOTE=leezer3]Can you post a make, model & age please.[/QUOTE]

MAKE: Acer
MODEL: AcerPower F2
AGE: AUGUST 2004

---

### Post by Sirin on 2005-12-03
If you need the CD drive info:

MODEL: LITE-ON CD-ROM LTN-572T
MANUFACTURER: Standard CD-ROM drives (I don't know why it says this...)
AGE: Mid-2004 Range

---

### Post by xmastree on 2005-12-03
Can you run md5sum on them?

---

### Post by Nevermore on 2005-12-03
i had the same problem a few weeks ago.
it gradually builded up until messed the partition table of my hdd and i had to format all and reinstall.
IT WAS A DEFECTIVE dimm module.
test your memory asap and for at least 3 hours in loop.
mine started to fail only after 40min was on, and at first were just a couple bits wrong, then builds up over time until a few memory location were faulty (this prevented me to install stuffs with big cabs, decript big files, use isos, and install the KERNEL)
it gave problems only when warm..
check ur mem asap and if u find a defective module dispose it.
cheers

guess what, i have a liteon also, and it works GREAT after disposing the defective ram module, just i had to switch from ubuntu to xubuntu.

---

### Post by pibulian on 2005-12-03
Today I received 5 CD 5.10 from Shipit, all 5 failed installation, all failed MD5 sums, all same 2 error:
.\install\netboot\pxelinux.cfg\default 
.\install\netboot\pxelinux.0

any help?

---

### Post by bwog on 2005-12-03
It seems unlikely that all those CDs are corrupted. Some users benefit from special bootparameters, such as dma on. The bootparameters are found on the install CD with help keys F1 to F8.

Quoting from this forum:

 FWIW there's a slightly simpler option: boot the installer with 'install cdrom-detect/cdrom_hdparm=-d1'.

---

### Post by fulano on 2005-12-08
> Today I received 5 CD 5.10 from Shipit, all 5 failed installation, all failed MD5 > sums, all same 2 error:
> .\install\netboot\pxelinux.cfg\default
> .\install\netboot\pxelinux.0

> any help?


I have the same problem as pibulian.  I downloaded 
ubuntu-5.10-install-i386.iso and the md5sum checked out ok.  When I 
attempted to install, I got checksum errors.  I unpacked the iso file and
ran md5sum against md5sum.txt and got errors on these two files:

md5sum: ./install/netboot/pxelinux.cfg/default: No such file or directory
./install/netboot/pxelinux.cfg/default: FAILED open or read
./install/netboot/pxelinux.0: FAILED

I think I saw somewhere that these were symbolic links ?  If so, I'm 
speculating that either the links didn't get created during install or md5sum
didn't follow them during the check.  These two files are zero length
when I unpack them.  Anyone know what's going on ?

---

### Post by GreenTomato on 2005-12-08
I also ran the md5 check and those two files failed...

.\install\netboot\pxelinux.cfg\default
.\install\netboot\pxelinux.0

Could it be that the md5 numbers in the file are just wrong?

---

### Post by psaulnier on 2005-12-08
Can someone explain to me exactly how to perform an integrity test on a CD? I haven't been able to find anything on the subject.

---

### Post by GreenTomato on 2005-12-08
I used this program (it doesn't require an install btw)

[http://md5summer.org/](http://md5summer.org/)

pick your cd drive, click "verify sums", choose the .txt file in the root of the cd, then the dialog box that pops up click ok or yes or whatever it is.

(there may be an easier way, but i don't know what that is)

---

