---
title: "Installation Doubts"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by Faltzer on 2007-10-13
I'm on Step 4 of Ubuntu 7.04 installation, and I'm having troubles deciding what I should do.


I have Windows XP Media Center Edition installed on Drive C:\, and so, when it reaches the Partition part, here is what I see:

[http://i22.tinypic.com/vharf5.png](http://i22.tinypic.com/vharf5.png)

A preview of what I see.

---

### Post by PmDematagoda on 2007-10-13
Does the whole drive belong to XP?

---

### Post by Faltzer on 2007-10-13
I'm not sure how to answer that question, really. Drive C:\ is using Media Center Edition, on the C:\WIndows folder, and I have an extra drive which is for SYSTEM RECOVERY.


So, I'm not really sure how to answer this correctly.

---

### Post by PmDematagoda on 2007-10-13
You may have to resize the drive, goto the manual partition setup and post what you see.

---

### Post by Faltzer on 2007-10-13
Alright, this is what I see in Manual:

[http://i20.tinypic.com/semus1.png](http://i20.tinypic.com/semus1.png)

---

### Post by PmDematagoda on 2007-10-13
Ok, so as I know it, you need:-

About 100Mb for the /boot partition which is in ext3 format

How much RAM do you have?

About 2Gb for the / partition which is also in ext3 format

The remaining space for the /home partition which will also be for in ext3 format.

But before we make the partitions, tell us how much RAM you have.

---

### Post by novaheat on 2007-10-13
You'll want to re-size the main NTFS partition (/dev/sda1, judging from your screenshot). Looks to me like there's plenty of space there, so you'll have a lot of room for Ubuntu. PmDematagoda's already posted some pretty good guidelines for space reqs.

---

### Post by Faltzer on 2007-10-14
I have 384MB RAM. But wouldn't creating a new partition erase all of the ones I already have? Wouldn't that erase data? I don't want to mess up anything, so how would I do this without removing anything?

---

### Post by Faltzer on 2007-10-14
Okay, how do I resize? And how would I go to accomplishing all of these so complicated tasks? I'm getting a headache just by looking at all of this.

---

