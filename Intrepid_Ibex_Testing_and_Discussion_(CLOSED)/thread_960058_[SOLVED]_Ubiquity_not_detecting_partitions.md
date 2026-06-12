---
title: "[SOLVED] Ubiquity not detecting partitions"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by kagashe on 2008-10-27
Hi,

I downloaded Intrepid RC Desktop iso and tried to install. I don't burn the iso to CD but use the method installation from Linux described on Ubuntu Community Documentation.

I started to install from the desktop but the existing partitions were not listed and I could not proceed. If I run the Partition Editor from System/Administration all the partitions are detected. If I boot with only-ubiquity option still my partitions are not detected.

I went to the launchpad and found [this bug]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/288675"). But I am not happy about the "undecided" status of the bug.

Then I found a new entry in System/Administration to make a Live USB stick. I made the USB stick and could boot from it. Running the installer produced same results i.e. partitions were not listed.

On running only-ubiquity from USB stick the partitions on USB stick are listed which is not of any use since I would like to install on the hard disc.

kagashe

---

### Post by panda726 on 2008-10-27
I had this with one of my disks when installing Intrepid RC.  What I found is that it seems that if ANY partition of a disk is mounted on the live CD, then the install will fail to detect the disk entirely.

Would I be right in thinking that you are trying to install from your existing partition to a different partition on the same disk?  If so, try burning the ISO and installing from the live disk, or download and use the alternate disk (my preference for an install, but the result is the same).

Tor

---

### Post by kagashe on 2008-10-27
> **panda726 said:**
> I had this with one of my disks when installing Intrepid RC.  What I found is that it seems that if ANY partition of a disk is mounted on the live CD, then the install will fail to detect the disk entirely.

Would I be right in thinking that you are trying to install from your existing partition to a different partition on the same disk?  If so, try burning the ISO and installing from the live disk, or download and use the alternate disk (my preference for an install, but the result is the same).

TorThe Document [URL="https://help.ubuntu.com/community/Installation/FromLinux"]Installation/FromLinux 
[/URL] is meant for this i.e.install from your existing partition to a different partition on the same disk. Ok. Let us assume that it will not work for Intrepid.

But why is it not working when I am booting from USB stick?

kagashe

---

### Post by panda726 on 2008-10-27
That I don't know, and looking again, I see that you did say you could boot from it (misread it before).  Not having a USB stick myself to test with I can't run any tests myself, and I don't know enough to have an idea on why the USB would detect itself, but not the hard disk.

The only idea I have right now (that somehow you weren't booting from USB correctly) seems rather unlikely, given how different live boots are from installed boots.  I don't see how you would have booted the image on your hard disk instead without knowing it, so I think I'll have to let someone else take over, and watch and learn.

Tor

---

### Post by kagashe on 2008-10-27
> **kagashe said:**
> But why is it not working when I am booting from USB stick?

kagasheI asked the question and the answer flashed in my mind. I was booting from USB but it was detecting the Intrepid files on the hard disc partition and mounting the hard disc partition at /cdrom.

I reformatted the hard disc partition and reboot from USB stick mounted /dev/sdb1 on /cdrom and now the installer is showing the hard disc partitions.

kagashe

---

