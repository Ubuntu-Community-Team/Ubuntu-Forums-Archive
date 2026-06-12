---
title: "Dual Boot with XP and Ubuntu Help..."
date: 2011-04-18
forum: Installation &amp; Upgrades
---

### Post by Sicksorrow on 2011-04-18
Ok I have two HDD's in my PC one has Win XP (it was first) 

The other is a blank NTFS. There are no files on it.

I want to install Ubuntu on the blank one, but I haven't found any clear answers to my questions.

I have used WUBI and installed inside of Win XP and Decided I liked it alot...

But my questions are simple (I think)

If I install Ubuntu on the blank HDD will I need a bootmanager?

If I decide that I want to change hard disks like for example: Taking out my Ubuntu HDD and putting it in another PC will I mess up my pc?

How do I go about installing ubuntu?

Especially when I get to the install ubuntu from live cd it ask what drive do you want the bootloader to be installed on?

---

### Post by Hedgehog1 on 2011-04-19
> **Sicksorrow said:**
> Ok I have two HDD's in my PC one has Win XP (it was first) 

The other is a blank NTFS. There are no files on it.

I want to install Ubuntu on the blank one, but I haven't found any clear answers to my questions.

I have used WUBI and installed inside of Win XP and Decided I liked it alot...

But my questions are simple (I think)

If I install Ubuntu on the blank HDD will I need a bootmanager?

If I decide that I want to change hard disks like for example: Taking out my Ubuntu HDD and putting it in another PC will I mess up my pc?

How do I go about installing ubuntu?

Especially when I get to the install ubuntu from live cd it ask what drive do you want the bootloader to be installed on?

There are a couple of choice open to you.

One option is the 'complete isolation' method of installs.  In this option, you would install Ubuntu on the  second drive (/dev/sdb) and install the bootloader on the same drive (/dev/sdb).  To boot Ubuntu, you would have to use the bios to select that 2nd hard drive to boot from. You could then take the hard drive to another PC and run Ubuntu on it (you may have to change video drivers if their cards don't use the same video drivers).

The 'complete isolation' means Windows stays untouched on the first drive, and Ubuntu stays untouched on the 2nd drive.

The thing is - this method wastes a lot of disk space.

Another option is 'common boot drive, common data drive'

In this option, you would install Ubuntu as a true dual boot on the first drive (and use grub to select Windows or Ubuntu). Then both OSs would share data on the second NTFS drive.

The second option is what I run.  Windows 7 & Ubuntu on /dev/sda,
and common data on /dev/sdb as a single NTFS partition.  Here is what my /dev/sda drive looks like:

[IMG]http://img834.imageshack.us/img834/8480/gpartedpartitiontable.png[/IMG]

Hope this helps a little.

***The Hedge***

:KS

---

