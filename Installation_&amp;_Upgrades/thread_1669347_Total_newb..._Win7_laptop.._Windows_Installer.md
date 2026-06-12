---
title: "Total newb... Win7 laptop.. Windows Installer?"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by tombihn on 2011-01-17
I've been browsing the forums and searching for terms such as A52F, Installer, Windows Installer... so far, I'm not exactly sure I'm following the right path. I'm sure this question must've been asked already, but can't seem to locate it.

So, after all that, here's the question.

I purchased an ASUS A52F laptop with Windows 7 64 bit on it. I adjusted the partitioning to give me a 100GB partition to play with Ubuntu. I went to download and saw there was a windows installer for it, so I am currently downloading this into the new D (Ubuntu) partition I created and quick formatted using Windows 7. Should I be downloading to the C drive or was it the right thing to download to the D drive? By the instructions, it looks like I'll get a boot menu when the system restarts.

I guess I need reassurance I'm going the right direction and hopefully to save a few hours of downloading again with another method or two lol.

---

### Post by CodeToad on 2011-01-17
Google WUBI (Windows UBuntu Installer).

---

### Post by tombihn on 2011-01-17
Thanks I'll do that.

It looks like the installer wasn't what I was looking for exactly. It seems it installed the installation files on the D partition, but I didn't see the D partition when it booted into Ubuntu, only the C partition. 

The installer went very smoothly and was very fast. It was apparently for 10.04 LTR. I think I'll download an ISO and see if I can shove it into my D partition.

I was hoping to keep the two OS's segregated to prevent issues. I'm surprised you can have two OS's installed in the same partition.

---

### Post by wilee-nilee on 2011-01-17
> **tombihn said:**
> Thanks I'll do that.

It looks like the installer wasn't what I was looking for exactly. It seems it installed the installation files on the D partition, but I didn't see the D partition when it booted into Ubuntu, only the C partition. 

The installer went very smoothly and was very fast. It was apparently for 10.04 LTR. I think I'll download an ISO and see if I can shove it into my D partition.

I was hoping to keep the two OS's segregated to prevent issues. I'm surprised you can have two OS's installed in the same partition.

Do us a favor once you have downloaded the Ubuntu cd boot it to a try ubuntu session.

Go to system-->admin-->gparted open it take a screen shot and post it using the paperclip icon in the reply panel to upload it and put in a reply.

I suggest this as there is a limit to the amount of 4 primary partitions that can be put on a single HD, lets make sure your doing the right thing here.

The wubi install is a file inside of windows, not stable at times and a bit of trouble in general.

---

### Post by tombihn on 2011-01-17
> **wilee-nilee said:**
> Do us a favor once you have downloaded the Ubuntu cd boot it to a try ubuntu session.

Go to system-->admin-->gparted open it take a screen shot and post it using the paperclip icon in the reply panel to upload it and put in a reply.

I suggest this as there is a limit to the amount of 4 primary partitions that can be put on a single HD, lets make sure your doing the right thing here.

The wubi install is a file inside of windows, not stable at times and a bit of trouble in general.

I have the hidden recovery partition /dev/sda, the Win7 partition, /dev/sda1, and the unallocated partition.

---

### Post by wilee-nilee on 2011-01-17
So as the second person suggested you have a wubi install, is it working?

To install to the 100gig unallocated you need to boot the Ubuntu cd to a live session, and put partitions in the 100 gig space then custom install in a formatted ext4 partition for Ubuntu.

So the wubi is for trying it out, and is just a Ubuntu file inside of Windows. A dual boot as described above with the booted cd is the usual way and safer way of running Ubuntu.

If you decide you want to partition the unallocated and install that way just post your intentions and help should be around.

---

### Post by Rubi1200 on 2011-01-18
I also suggest that you don't mix and match here with Wubi and a regular install. We have seen that it can sometimes cause problems.

---

