---
title: "Live USB Leaving Boot Images On HDs"
date: 2014-06-16
forum: Installation &amp; Upgrades
---

### Post by ufarmer on 2014-06-16
On two computers where I have used a live USB to boot into Linux -- Ubuntu and Mint -- subsequent reboots have booted into Linux even without the USB being plugged in.  The first occurence was a Live USB of Ubuntu 12.04.  I realized I was booting with the USB plugged in and pulled it out, but apparently too late.  After that, the computer would boot only into a broken 12.04.  I figured it must have been a fluke but I had no choice except to reformat the drive.  Now, on another computer where I never attempted to abort a boot while using the Live USB, and after many reboots since trying out Mint, I just booted into Mint a couple of times in a row before finally booting back into Windoze (which should be the only boot image).  I have never seen anything like this.  To my understanding, the Live USBs should not be leaving any kind of boot image on the disks.  Also, I cannot think of any reason why such an image -- the Mint one -- would be triggered apparently at random.  Any advice is appreciated.  In particular, I would like to exorcise this image from the disk!

Ah, I'm an idiot.  My computer mysteriously chose to boot from the CDROM this time -- which has had a copy of Mint sitting in it for weeks.  So that's one mystery solved and another one raised.  As a matter of intellectual curiosity though, I have always wondered what might have gone wrong with I tried to abort the Live USB boot into Ubuntu 12.04.  But, other than in interesting discussion, this turned out to be a non-issue.  I could not find any way to delete this post.

---

### Post by oldfred on 2014-06-17
Your system will boot slightly faster if you set your hard drive as first in boot order in BIOS.
Then it does not have to search for CD or flash drives then default to hard drive.

If you want to boot CD or flash drive you should have a one time boot key, its f12 on my system and many others, but does vary by vendor.

---

