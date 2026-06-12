---
title: "Can't get Ubuntu 11.10 or 12.04LTS to install"
date: 2012-02-19
forum: Installation &amp; Upgrades
---

### Post by jlh68 on 2012-02-19
I have tried to install 11.10 and 12.04 on my desktop without success.  I have downloaded 11.10 twice and burned a CD each time, neither burn has worked.  I downloaded 12.04 to a DVD (it is greater than 700MB) and it would not work.  Then I made a USB flash drive with 12.04 on it.  That would install either.  The USB flash drive would run as a "live CD" on my laptop.  I kept getting "kernel Panic" messages and more than a screen of text on my desktop system.  I was starting with a brand new hard drive.

I finally went and got my Ubuntu 10.10 CD and installed it on my desktop.  I am wondering if there is a problem with Unity and an AMD CPU?

---

### Post by darkod on 2012-02-19
It could rather be a video issue. 12.04 is still in Alpha so I'm not sure if we should expect great compatibility.

Did you try to run 11.10 in live mode with the nomodeset parameter? When the cd starts booting, at the first purple screen, hit Esc immediately. That should show the older type boot menu. Hit F6 for advanced options and select nomodeset. Then use the Try Ubuntu option and see if it loads the live mode correctly.

If it does, you can install but on first boot you will need to boot with the same parameter added and then make it permanent.

---

### Post by MAFoElffen on 2012-02-19
You said it was your desktop. I'm assuming that this one in your signature is it:
> ***White box computer***: ASUS M2N-SLI,Athlon64 2X CPU, nVidia 7300GT GPU,DVD-Writer, 500-GB HD, 320-GB HD,6-GB 2Channel RAM
I can confirm that one of my test boxes has similar hardware and installs/runs fine with 10.04 thru 12.04, which is what is loaded on it now.

Darko's instructions +1

---

### Post by kevdog on 2012-02-19
You verified the md5sums on the downloaded files?

---

### Post by jlh68 on 2012-02-21
**kevdog**:  I got the USB flash drive with 12.04 to load as a "live cd" on my Laptop (intel) just fine.  No I did not check the md5sums. 

How do I check the md5sums?  I did not see them on the Ubuntu site.

**MAFoElffen**  yes the white box computer is the desktop.  I am using Ubuntu 11.10 on my netbook, version 10.10 on my laptop, and I was trying to go to 11.10 on my desktop.  I guess I will go to 12.04LTS later on my laptop

**To all:**  A side issue that I posted in a separate post is that upon installing successfully 10.10, I was able to have good resolution and I was able to use screen rotation.  Because it was a new install of an old version, there were a lot of updates to be loaded, which I allowed to happen.  After the updates I had lousy resolution and I could not use screen rotation. I tried using the iNvidia driver and that improved the resolution but it did not support screen rotation.  Since my monitor will rotate 90 degrees from the horizontal to the vertical position, I would like to use screen rotation.  Having the icon in the panel was nice for the short time I had it.  How do I revert back to a working screen rotation function?

---

### Post by jlh68 on 2012-02-28
I still cannot get Ubuntu to upgrade.  I tried to use the Update Manager and update to 11.04 on line but that failed.  I have on my flash drive 12.04 that WILL work as a live CD on  my laptop but will not install on my desktop computer.  So every version with Unity will not install (11.04, 11.10 and 12.04).  That makes me think there is some kind of problem in the newer versions of the OS.

I will try to run 11.10 in live mode with the nomodeset parameter later to see if that works.

It all used to be so simple to upgrade/install and now this problem.

On my last try I got the following message:

BusyBox v1.18.4
(initramfs) stdin: error )
/init line 7: can't open /dev/sdb: no medium found
/init line 7: can't open /dev/sdc: no medium found
mount: mounting /dev/loop1 on /cow failed: invalad argument 
can not mount /dev/loop1 on /cow

That was with 12.04 on the flash drive.

---

### Post by dFlyer on 2012-02-28
I believe you need to go from 10.10 to 11.04 to 11.10 to 12.04 LTS when upgrading from a non-LTS version, while using the update manager.

---

### Post by jlh68 on 2012-02-28
I did try to update from 10.10 to 11.04 without it upgrading.  It did change the repositories to 11.04 Natty, but no upgrade.  That was my plan: to upgrade from 10.10 to 11.04 then to 11.10.  

I have frequent "kernel panic" episodes.

---

### Post by jlh68 on 2012-02-29
Checked the md5sum of my Ubuntu 11.10 download and it matches with the Ubuntu web site md5sum for that version.

---

### Post by mastablasta on 2012-03-01
> **jlh68 said:**
> Checked the md5sum of my Ubuntu 11.10 download and it matches with the Ubuntu web site md5sum for that version.
 
 
good. next you need to check the CD to verify it burned ok. i believe this is done on the first screen when you boot.
 
Though this doesn't apply to USB.

---

