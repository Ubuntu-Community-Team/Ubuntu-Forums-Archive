---
title: "Fresh Install doesn't recognise HDD"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by Ivchenko on 2010-10-25
Hi, I'm trying to install Ubuntu 10.10 from a USB stick but neither the install nor the LiveCD will recognise my Hard Disk Drive.  They only recognise the USB stick and report that install cannot proceed without at least 2.6GB freespace (of which of course there isn't on the USB stick).

I've installed Ubuntu on a couple of systems before but this is the most advanced and I'm certainly no expert.  It's an ASUS P6X58D-E mobo with two WD600GB SATA3 HDD's setup in RAID1 configuration.  It's already running W7Ultimate x64 OK on it's own 150GB partition.  Of course I can't even run gparted from the LiveCD to repartition.

I suspect the problem is the RAID config, but not sure what to do... Anyone any ideas or experienced this before?  I'm at a dead-end

---

### Post by sikander3786 on 2010-10-25
Try no dmraid parameter from F6 menu on the initial boot screen. See here.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

Sometimes, removing the package dmraid solves the problem.

```
sudo apt-get remove dmraid
```

If none of these work, how many Sata controllers are there on your motherboard? Does it have a Marvell Sata Controller?

---

### Post by ronparent on 2010-10-25
Removing dmraid won't solve your problem if you have 'fakeraid' drives in your system. The problem most likely has to do with the 6Mb/sec SATA ports. You may have to search to find if this has been resolved.

---

### Post by Ivchenko on 2010-10-26
Thanks - I've tried removing dmraid pkg and it didn't help.

Yes the two RAID1 drives are SATA 6Gb/s on a Marvell 88SE9128 controller.  (The board has a further 6 unused SATA@3Gb/s on the Intel ICH10R Southbridge).

I've googled and forumed many things but to no avail yet... Is this a known problem with the Marvell controller or RAID1?

---

### Post by dino99 on 2010-10-26
[http://ubuntuforums.org/showthread.php?t=877552](http://ubuntuforums.org/showthread.php?t=877552)

[https://launchpad.net/ubuntu/+bugs?field.searchtext=RAID&orderby=-date_last_updated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://launchpad.net/ubuntu/+bugs?field.searchtext=RAID&orderby=-date_last_updated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

---

### Post by Ivchenko on 2010-10-26
many thanks for the pointers dino - now i know what better to search for as the cause of my problems, it seems as though i've stumbled into a minefield.

i normally don't mind getting my hands dirty, but setting up fakeraid looks traumatic and potentially disruptive to my existing (and painless) Win7 installation and still uncertain whether it will cure my problem!

---

### Post by psusi on 2010-10-26
> **Ivchenko said:**
> i normally don't mind getting my hands dirty, but setting up fakeraid looks traumatic and potentially disruptive to my existing (and painless) Win7 installation and still uncertain whether it will cure my problem!

Umm... you already HAVE a fakeraid.

The problem seems to be that your fancy new 6gbps sata ports don't don't yet have a working driver.

---

### Post by ronparent on 2010-10-26
I would advise deferring a 10.10 install to the raid and filing a bug report. There is no point doing anything to disrupt your working win7 setup and risking data loss just to install 10.10 as a trial. Meanwhile have you tried 10.04 LTS?

If anyone can post a meaningful solution that doesn't mess up what you have you should certainly listen.

---

### Post by ronparent on 2010-10-26
Someone else with a similar problem wants to see your bug report. What shall I tell them? Link to other post:

[http://ubuntuforums.org/showthread.php?t=1606075](http://ubuntuforums.org/showthread.php?t=1606075)

---

