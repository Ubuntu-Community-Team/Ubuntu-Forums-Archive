---
title: "Installing Ubuntu: Cannot pass prepare mount points screen"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by dark_ixion on 2006-10-26
I had Ubuntu 6.06 installed previously on my PC, and I've tried installing 6.10 but cannot.

At first, I booted up the CD, ran the installer, but when I get to the "Prepare mount points" screen, I get the error message "No root file system" when clicking next.  I've set it up as follows:
[FONT="Courier New"]
**Mount Point | Partition**
/media/hdb5 | Partition 5 Disc IDE/ATA 2 (Logical) [hdb5]
/media/hda1 | Partition 1 Disc IDE/ATA 1 (Primary) [hda1]
/media/hda2 | Partition 2 Disc IDE/ATA 1 (Primary) [hda2]
swap        | Partition 6 Disc IDE/ATA 1 (Logical) [hda6]
/           | Partition 5 Disc IDE/ATA 1 (Logical) [hda5][/FONT]

I thought that maybe the old version was screwing it up somehow, so I reformatted my partition (hda5) with ext3 and booted it up again, but get exactly the same problem.

It says: you must mount one partition on the root file system ("/") and you must choose at least one partition for use as swap space.

I've done both of these, and I've even checked the reformat box and removed the other 3 mount points in an attempt to get it accepting it, but it still comes up with the "No root file system" error at the bottom when I click on next.

What am I doing wrong?  I was able to install Ubuntu on this exact same partition previously.

Thanks

Thom

---

### Post by nick122147 on 2006-10-26
Hi, this happened to me too, must be a bug, a serious one.. I'm downloading the alternate install disc now, hope that works.

---

### Post by weatherman on 2006-10-26
same here with kubuntu edgy. Imho this is a showstopper.

---

### Post by nick122147 on 2006-10-26
Hi, try the alternate install disc. That works.
Steinar

---

### Post by dark_ixion on 2006-10-27
I've now used the alternative installation disc and it's installed fine.  Cheers guys.  They really will need to fix that problem as that's a show-stopper.

---

### Post by towsonu2003 on 2006-12-17
this issue seems to be known:
[https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/67130](https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/67130)
and documented
[http://wiki.ubuntu.com/EdgyReleaseNotes](http://wiki.ubuntu.com/EdgyReleaseNotes) (scroll down to "known problems")

---

