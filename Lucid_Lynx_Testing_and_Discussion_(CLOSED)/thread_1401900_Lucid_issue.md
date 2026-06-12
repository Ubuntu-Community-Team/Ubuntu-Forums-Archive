---
title: "Lucid issue"
date: 2010-02-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by wyomingpat on 2010-02-08
Could not register this as a Lucid bug as I could not jump through all the hoops.

Been running with Lucid fine until Yesterday Feb 7th. I am running the latest Alpha release. When I rebooted yesterday after the daily update I noticed I had lost all my desktop shortcuts. Then I checked further and my Documents and Downloads folders had disappeared too. Checked the trash and they were not there but solme old files I had deleted over the week were.

This is kind of alarming even in an alpha release as my home folder is on a separate partition to prevent corruption. I then resorted to my backup produced with archive manager that is on a USB drive - cannot unpack, unexpected end of file.

Any comments please?

---

### Post by dabl on 2010-02-08
> **wyomingpat said:**
> 
Any comments please?

1. There is a forum for Lucid Lynx here:

[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)


2. While it may seem "serious" from a user's perspective, in an Alpha version it may be a trivial, even deliberate, breakage from the developer's perspective.  There is no expectation that anyone would be using an Alpha version for anything other than testing the version.

---

### Post by howefield on 2010-02-08
> **wyomingpat said:**
> Could not register this as a Lucid bug as I could not jump through all the hoops.

Couldn't or wouldn't ? 

> Been running with Lucid fine until Yesterday Feb 7th. I am running the latest Alpha release. When I rebooted yesterday after the daily update I noticed I had lost all my desktop shortcuts. Then I checked further and my Documents and Downloads folders had disappeared too. Checked the trash and they were not there but solme old files I had deleted over the week were.

This is kind of alarming even in an alpha release as my home folder is on a separate partition to prevent corruption. I then resorted to my backup produced with archive manager that is on a USB drive - cannot unpack, unexpected end of file.

Any comments please?

Nothing is alarming when it comes to Alpha software. If you don't get breakage, it's a bonus. But it has to be expected.

The best solution is to have a robust backup strategy, whether running alpha or otherwise. The lack of that seems to be the failure here.

---

### Post by darkod on 2010-02-08
> **wyomingpat said:**
> I am running the latest Alpha release. 

Also to add to the previous post, there is no such thing as latest Alpha release.
Yes, there are stages like Alpha 1, 2 and 3, but images are made available every few days so you can't say you have the "latest" release. Check and there is a newer image already.

---

### Post by overdrank on 2010-02-08
Moved to Lucid Lynx Testing and Discussion

---

### Post by phillw on 2010-02-08
> **wyomingpat said:**
> Could not register this as a Lucid bug as I could not jump through all the hoops.

Been running with Lucid fine until Yesterday Feb 7th. I am running the latest Alpha release. When I rebooted yesterday after the daily update I noticed I had lost all my desktop shortcuts. Then I checked further and my Documents and Downloads folders had disappeared too. Checked the trash and they were not there but solme old files I had deleted over the week were.

This is kind of alarming even in an alpha release as my home folder is on a separate partition to prevent corruption. I then resorted to my backup produced with archive manager that is on a USB drive - cannot unpack, unexpected end of file.

Any comments please?

As your home folder is on a seperate partition, it could be as simple as 10.04 alpha not mounting it. - That'd give you no desktop icons, etc.

Have a look into that, before you start worrying yourself. Places is a good area to start.

As a note of caution, that has been raised. When running 10.04, it is safer to rsync your /home over to 10.04 and then unmount your /home partition immediately afterwards.

Yes, so you have to rsync back and forth, but it's no big deal & keeps you /home safe :-)

Regards,

Phill.

---

### Post by kansasnoob on 2010-02-08
I have a separate /home and no problems here.

Other (minor) problems - yes, but no disappearing /home.

---

### Post by VMC on 2010-02-08
> **phillw said:**
> As your home folder is on a seperate partition, it could be as simple as 10.04 alpha not mounting it. ...If it couldn't mount it how could he login? Your login is based off of your "/home" folder, or in this case partition.

---

