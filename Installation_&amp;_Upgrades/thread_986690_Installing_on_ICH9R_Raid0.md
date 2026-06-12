---
title: "Installing on ICH9R Raid0"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by diagza on 2008-11-18
Hello all,

Trying to install 8.10 on a fake-RAID array, but running to trouble.

My setup is:
ICH9R controlling 3 HDDs
fake-RAIDed into 2 equal 1TB RAID 0 arrays
1st RAID array is partitioned with an openSUSE install
2nd RAID array is partitioned with Windows

I'm trying to wipe the 1st RAID array and install Ubuntu 8.10. I tried the original liveCD first, and got to the partition section. The 3 actual HDDs show up, but none of the arrays. So, I switched over to the altCD. I got to the partition section again, but this time nothing at all shows up - just 2 blanks spaces in between the normal default selections at that screen (Help, Format, and something else).

Any and all advice/ideas are welcome. Thanks in advance.

---

### Post by diagza on 2008-11-19
Some more info, if pertinent:

I have tried using ImgBurn as well as booting from the CD to verify the install CD (or more accurately I burned to CD image onto a DVD) and it passed, so I'm assuming the DVD itself is not the problem.

Also, when starting up with the altCD I get 2 USB error messages in the beginning; "Failed to enumerate USB to port 2" and something else, but I'm pretty sure those are just errors for my (USB) keyboard/mouse/speaker setup not having their drivers installed.

Oh and bump.

---

### Post by psusi on 2008-11-20
You need to install the dmraid package.  See [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto).

---

### Post by diagza on 2008-11-20
I thought the altCD already included the dmraid package though. I guess I'll try going back to the liveCD, try those steps, and see where it takes me. Thanks for your reply.

> Method 1

{*} According to the latest FakeRAID spec, Intrepid users can now install directly to SATA RAID with no additional setup or configuration required. This is is not yet supported in the Ubiquity graphical installer so you must use the Alternate Install CD. The installer will prompt you to activate the RAID partitions, which will make them available to the partitioner and allow you to continue with the installation as normal. 

---

### Post by psusi on 2008-11-20
Yes, the alternate CD is supposed to work out of the box, but since you have two volumes defined within the raid set, there is a bug in the version of dmraid that shipped with Intrepid handling this on Intel raids.  See [https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/292302](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/292302).  Try the updated package on the livecd and see if you can manage to install that way.

---

