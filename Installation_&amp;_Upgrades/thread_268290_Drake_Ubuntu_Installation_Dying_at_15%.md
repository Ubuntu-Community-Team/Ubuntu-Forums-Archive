---
title: "Drake Ubuntu Installation Dying at 15%"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by ada5011 on 2006-09-29
I was attempting to install Ubuntu-Dapper Drake via the ShipIt CD and going to the live CD install.  I successfully partitioned my hard drive into an ~15 GB NTFS partition for my root and an ~729 MB Linux-Swap for the swap.

I then click install, and at 15% it just dies.  I have the reformat box checked for the swap (though not necessary) and its just not working.

Any ideas?

Dell Inspiron 9300
1.73 GHz Pentium M
80 GB HD
1 GB SDRAM

---

### Post by aysiu on 2006-09-29
Bum disc.

Yes, I know it's an *official* Ubuntu ShipIt CD--still could be a bum disc.

Bum discs happen sometimes when the CD is burnt too quickly. I burn at 4x just to be safe.

---

### Post by morphodone on 2006-09-29
> **ada5011 said:**
> I successfully partitioned my hard drive into an ~15 GB NTFS partition for my root and an ~729 MB Linux-Swap for the swap.


Are you sure about that filesystem?

---

### Post by ada5011 on 2006-09-29
So wait...I have to get another one and wait another month to get it?

This is depressing.

---

### Post by ada5011 on 2006-09-29
> **morphodone said:**
> Are you sure about that filesystem?

Should I not do NFTS?

---

### Post by aysiu on 2006-09-29
@ morphodone, I'm assuming that / overwrote the NTFS partition and made it Ext3. Maybe ada5011 just doesn't understand what happened.

@ada5011, I'm just proposing a possible explanation. Every time I've heard of or experienced Ubuntu "dying" or freezing at a particular part of the installation, it's from one of three things:

1. A bum CD
2. Not enough RAM
3. Faulty hardware

How much RAM do you have?

---

### Post by morphodone on 2006-09-29
> **ada5011 said:**
> Should I not do NFTS?

Nope, you should use ext3 or reiserfs...

P.S. You can download the version of ubuntu and burn the iso image
if your disc is bad as suggested.

[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

---

### Post by ada5011 on 2006-09-29
Oooh...that didn't happen.  When I clicked reformat for the NTFS partition, it actually reformatted it as an NTFS....so I should have it as EXT3??  

And 1 GB

---

### Post by morphodone on 2006-09-29
> **ada5011 said:**
> Oooh...that didn't happen.  When I clicked reformat for the NTFS partition, it actually reformatted it as an NTFS....so I should have it as EXT3??  

And 1 GB

Are you using the live cd to format the drive?  If so I don't think NTFS should even be an option.  I thought you might have formatted that drive
in windows.

The root partition should be at least 5 GB or so.  512 MB to 1024 MB for swap.  these are rough figures of course.

p.s. where are you aysiu - not sure I'm going help him figure this out

---

### Post by Sef on 2006-09-29
> Oooh...that didn't happen. When I clicked reformat for the NTFS partition, it actually reformatted it as an NTFS....so I should have it as EXT3??


Yes, format as ext3 or reiserfs.  Ext3 is the default.  Linux can read, but not write to NTFS because it is a proprietary Microsoft format.

> And 1 GB

1 gb ram is more than enough.  Are you going to do some gaming, video, or other usage will takes up a lot of ram?  If yes, then make ur swap 2 gb.  If not, 1 gb swap will be enough.  If you just basically do email, word processing, and internet, you may not even need a swap partition at all.

---

### Post by ada5011 on 2006-09-30
It's done :)  All I needed was the EXT3 format.  I have 14.59 GB for the root and ~729 MB for the swap.

Mainly I'm going to be doing programming, internet, and minor graphics on linux.

---

### Post by morphodone on 2006-09-30
> **ada5011 said:**
> It's done :)  All I needed was the EXT3 format.  I have 14.59 GB for the root and ~729 MB for the swap.

Mainly I'm going to be doing programming, internet, and minor graphics on linux.

excellent

---

