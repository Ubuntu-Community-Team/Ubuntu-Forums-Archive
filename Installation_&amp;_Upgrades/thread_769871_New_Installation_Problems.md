---
title: "New Installation Problems"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Ry123 on 2008-04-26
When the installer hit the "install the base system" step it popped up with a series of errors and informed me that the installation failed. This was the first couple...


debootstrap warning file:///cdrom/pool/main/f/fribidi/libfribidi0_0.10.9-1i386.deb was corrupt

warning: couldn't download package libfribidi0

file:///cdrom/pool/main/g/gcc-4.2/gcc-4.2-base_4.2.3-2ubuntu7_i386.deb was corrupt

warning: couldn't dowload package gcc-4.2-base

etc, etc, etc several more errors and warnings


Does this mean that the files on the install cd are corrupt?  I created it from a ubuntu site at OSU.  I am a novice and in need of a rescue.  What are my next steps?  Many thanks for your help!

---

### Post by geeree on 2008-04-26
> **Ry123 said:**
> Does this mean that the files on the install cd are corrupt?

Possibly. Presuming that this is the LiveCD, on the menu that pops up when you boot the CD there is an option that lets you check the CD for defects. Select that and complete the check. If there is a defect, post back with the report. 

Hope this helps.
Girish.

---

### Post by Ry123 on 2008-04-26
thanks the integrity check failed.  The message is:

The ./pool/main/h/hplip/hplip-data_2.8.2-Oubuntu8_all.deb file failed the MD5 checkusm verification. Your CD-ROM or this file may have been corrupted.

---

### Post by Spunner on 2008-06-04
I am using the Hardy server CD, installed a couple of times, and decided to reinstall (changing partitions - no data yet, so no loss)

Then I got the "...../coreutils_6.10-3ubuntu2_i386.deb was corrupt" and a whole bunch more if I continue..

Then, I did the integrity check several times, no problem...

I'll just keep retrying until it works.

---

### Post by Spunner on 2008-06-04
Worked fine next try... (same CD, never even ejected it) go figure.

---

### Post by jermal on 2008-08-23
> **Spunner said:**
> I am using the Hardy server CD, installed a couple of times, and decided to reinstall (changing partitions - no data yet, so no loss)

Then I got the "...../coreutils_6.10-3ubuntu2_i386.deb was corrupt" and a whole bunch more if I continue..

Then, I did the integrity check several times, no problem...

I'll just keep retrying until it works.


I have a similar problem, or same but other packages. Integrity check ok but the installation is complaining that there are corrupt packages ... so far no luck when trying again to install.....

I have downloaded the server installation iso again - but same fault???

---

### Post by jermal on 2008-08-24
After trying several times with two different cd:s where I first got integrity check OK several times but corrupt packages when I tried to install - I got NOK on the integrity check.

After rerunning the integrity check I got OK again and finally it installed OK also :) after maybe the 12th time :(

Must have been something with my cd-reader????

---

