---
title: "Installation Problems"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by TriZz on 2007-04-27
Hey all, it's been awhile since I've given Ubuntu a try -- but I've been reading nothing but good things lately, so I thought I'd try to give it another go.

But I sure am having one hell of a time trying to get this working.  Perhaps you can help?

Here's the scenario:

Fiesty Fawn 7.04 x86
AMD Anthlon 64 3400+
Nvidia GeForce 6800
1GB of RAM

Currently running Windows Vista Ultimate Edition.  I've used the Windows partitioner in to create the second partition on the drive.  It's a simple partition (as opposed to dynamic which I hear Ubuntu hates).

This is a custom machine, built it myself -- so it's not a name brand.

Ok.  Here's what's happening:

I load the CD and I get the options to show up just fine.  These options are to start/install Unbuntu; start/install in safe graphics mode; check CD for errors; run memtest; boot from first hard disk

When I try to boot in the first or second options, I get a black screen.  At one point, the screen acts like it's going to do something, but shortly after that the "activity" light on my CD drive stops blinking.

Any input would be fantastic as I'd love to dual boot this machine and get my hands a bit dirty...

Thanks,
TriZz

---

### Post by tripkip on 2007-04-27
> **TriZz said:**
> Hey all, it's been awhile since I've given Ubuntu a try -- but I've been reading nothing but good things lately, so I thought I'd try to give it another go.

But I sure am having one hell of a time trying to get this working.  Perhaps you can help?

Here's the scenario:

Fiesty Fawn 7.04 x86
AMD Anthlon 64 3400+
Nvidia GeForce 6800
1GB of RAM

Currently running Windows Vista Ultimate Edition.  I've used the Windows partitioner in to create the second partition on the drive.  It's a simple partition (as opposed to dynamic which I hear Ubuntu hates).

This is a custom machine, built it myself -- so it's not a name brand.

Ok.  Here's what's happening:

I load the CD and I get the options to show up just fine.  These options are to start/install Unbuntu; start/install in safe graphics mode; check CD for errors; run memtest; boot from first hard disk

When I try to boot in the first or second options, I get a black screen.  At one point, the screen acts like it's going to do something, but shortly after that the "activity" light on my CD drive stops blinking.

Any input would be fantastic as I'd love to dual boot this machine and get my hands a bit dirty...

Thanks,
TriZz

Hi, I have exact the same problem!!
First I tried 6.06 then 7.04, both successless :(
There is no usb inserted, cd is burned at low speeds and for the 7.04 i have a2b159599b69cea51371eee1ec5feda6 for md5.
How to solve this problem ? Or is there no possibility to install linux on the prepared Ext3 en Swap partitions true windows?

Plz help!!

---

### Post by SteveSch on 2007-05-04
I have the same problem. Tried 7.04 and the previous version, in safe mode and normal mode. the screen just goes blank and the computer hangs. Very disappointing for a first linux try, and that for one that claims to be easy to install...

Computer: AMD 64 X2 3800+, 1GB Kingston RAM, ATI Express 850 pro (Asus), Seagate Baracuda 300GB

greetz

---

### Post by wydaho on 2007-05-14
I had very similar problems until I ran the install in expert mode and with "acpi=off" added to the boot command line.  The install then went fine.  Details are on a thread I submitted a few days ago. If you want to read more search on "install fails ati".

Please post a reply if this helps.

Wydaho

---

