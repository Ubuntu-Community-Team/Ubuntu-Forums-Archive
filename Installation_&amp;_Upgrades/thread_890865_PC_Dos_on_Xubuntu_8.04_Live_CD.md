---
title: "PC Dos on Xubuntu 8.04 Live CD?"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by R2Khimself on 2008-08-15
Hey guys, somehow I really messed up my system so i burned a Xubuntu 8.04 i386 to a disc to install.  Anyways, I popped in the cd, changed my boot options to cd/dvd and for some reason, I get this:

[I][B]PC Dos...

Preparing to start your computer
*and then some IBM crap*

MSCDEX Version 2.25
Drive D: Driver MSCD001 unit 0

*some more IBM identifier crap*
Mous driver installed successfully
A:\>[/B][/I]

So I'm not real sure what the problem is.  I can't boot from the hard disk because, well..there's nothing on it! lol.  Don't worry, I performed a backup a few months back.  If anybody has seen this before and knows a work around, that'd be great!

Thanks in advance!

---

### Post by mikewhatever on 2008-08-15
Tow questions:
1. How much RAM do you have?
2. Have you burned the CD as image or as data? See the link for reference -> [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by R2Khimself on 2008-08-15
I only have 256RAM (this is an alternate download, too) and i burned it as data.  Now that you mention it, that could be my problem.  What do you think?

---

### Post by Too Late on 2008-08-15
You must burn it as an image. Now you have burned that as data and somehow managed to make that disc bootable. :D

Every burning software has a feature called "Burn an image" or something like that. Use that and then select the .iso image file.

---

### Post by mikewhatever on 2008-08-15
> **R2Khimself said:**
> I only have 256RAM (this is an alternate download, too) and i burned it as data.  Now that you mention it, that could be my problem.  What do you think?

256 of RAM should be fine, but the data disk will not boot. Follow the guide I linked to and reburn the iso.

---

