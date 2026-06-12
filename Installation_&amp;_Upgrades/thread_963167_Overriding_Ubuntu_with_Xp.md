---
title: "Overriding Ubuntu with Xp"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by jgordon6633 on 2008-10-30
For some reason I can only find it the other way around.. people seem to think ubuntu is God's gift to earth.

Anyway, I have Ubuntu installed on a Dell D600, and i have a bootable copy of XP on a flash disk. ( for some reason my BIOS is locked, and I can't change the boot order, and i can select the drive by pressing f12, but it just loads Ubuntu)

How do I remove Ubuntu completely, but from within the system? 

I want a clean slate.

thank you.

---

### Post by Partyboi2 on 2008-10-30
If you are able to boot a ubuntu live cd then you can use gparted (System>Admin>Partition Editor) to delete your ubuntu partition. Then reinstall windows.

---

### Post by jgordon6633 on 2008-10-30
is a live cd just a copy of ubuntu on a cd? or do i have to order it from the linux wizard?

---

### Post by Partyboi2 on 2008-10-30
yes it is ubuntu on a cd. If you don't have a copy then an easier way is to use gparted live cd this is easier on bandwidth. You can get gparted live cd  from [[COLOR=Blue]here [/COLOR]]("http://gparted.sourceforge.net/livecd.php")

---

### Post by jgordon6633 on 2008-10-30
ok, i have booted from my installation CD, which of these options do I choose?

A. Install Ubuntu
B. Check CD for Defects
C. Test Memory
D. Boot from first hard disk

---

### Post by melojo on 2008-10-30
[http://qtparted.sourceforge.net/download.en.html](http://qtparted.sourceforge.net/download.en.html)
use this to delete the linux partition.

You can probably unlock your bios by moving the jumper pin on your motherboard, this should set your bios back to factory default.

---

### Post by Partyboi2 on 2008-10-30
> **jgordon6633 said:**
> ok, i have booted from my installation CD, which of these options do I choose?

A. Install Ubuntu
B. Check CD for Defects
C. Test Memory
D. Boot from first hard disk
Choose A and it should load to the ubuntu desktop where you can select gparted from System>Admin>Partition Editor

---

### Post by jgordon6633 on 2008-10-30
ok i forgot there was another option:

E. try Ubuntu without any changes to your desktops

I pressed it but my CD is f*cked up so i am making a new one. do I still choose A or E?

---

### Post by Partyboi2 on 2008-10-30
Use E instead of A

---

### Post by jgordon6633 on 2008-10-30
ok, i did what you recommended and removed the partitions, but I cant remove all. there are two left:

one is called 'linux-swap'
the other 'extended' and both are 1.44 Gig, but I have 147 Gig unallocated. When I try to boot w/o the live cd, I get 'error 18'

any ideas?

---

### Post by Partyboi2 on 2008-10-30
Start gparted again and right click on the swap partition and turn swap off, then delete it and then remove the extended.

---

