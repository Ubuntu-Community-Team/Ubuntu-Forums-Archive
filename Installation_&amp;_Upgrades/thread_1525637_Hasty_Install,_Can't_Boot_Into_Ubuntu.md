---
title: "Hasty Install, Can't Boot Into Ubuntu"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by erickomans on 2010-07-07
So I was having trouble in a different distro getting anything networking to cooperate with me. In desperation to get to something operable, I installed and ran Vista for all of fifteen minutes to burn an install CD for Ubuntu.

When I installed Ubuntu I completely cleared the drive I was installing it to, but then when I rebooted my computer was still trying to boot into Windows.

Everything I Googled about it kept telling me I needed to remove from within Windows. This has left me with a fresh install of Vista (again) which is really just compounding the problem for me.

I don't want anything to do with Windows. I only needed it to download/burn a CD and now I want rid of it so I can be solely Ubuntu. I'm not even sure what to search because everything keeps leading me to dualbooting with XP and I'm not even sure what is applicable from that.

This is my first day with Ubuntu, and it's installed, but I haven't been able to actually access that installation yet. I'm posting this using the Live CD, and I'm really interested in giving this distro a legit few-months at the very least.

---

### Post by Yarui on 2010-07-07
So you installed vista to burn the CD, then you formatted the drive, then installed Ubuntu, then reformatted with Vista again, then reformatted with Ubuntu again, then booted onto the live CD to post this?  Is that right?

Regardless of what you have done up to this point, you should be able to start up the installation process and when it gets to the point where you prepare the disk, say that you want to install Ubuntu using the entire disk.  If you do that it should totally wipe out windows regardless of whether or not you have already removed it yourself and install Ubuntu.  This should work without a hitch if you are installing as a single OS.  Could you describe what you did to install and exactly what happened when you were done?

---

### Post by vangop on 2010-07-07
You probably installed ubuntu from windows..
Now that you have a liveCD just **boot from it** and click on install ubuntu.

Then when it asks about disk space/partitions, choose to install on the whole disk/use entire disk (if you don't have user data somewhere on windows drive d:,e: etc. If you only had one c: drive under windows, this is your option, as all the data on entire hard drive will be lost).

---

### Post by erickomans on 2010-07-07
> **vangop said:**
> You probably installed ubuntu from windows..
Now that you have a liveCD just **boot from it** and click on install ubuntu.


I never booted into windows when I tried installing Ubuntu at any time.  Each time I've installed Ubuntu or needed the live CD, I changed boot  order to go with the CD drive first.

> Then when it asks about disk space/partitions, choose to install on the whole disk/use entire disk (if you don't have user data somewhere on windows drive d:,e: etc. If you only had one c: drive under windows, this is your option, as all the data on entire hard drive will be lost).

I've just now done this. When I reboot, I'm still getting Windows Boot asking me which installation of Vista I want to use.

---

### Post by Yarui on 2010-07-07
Do you, by chance, have multiple hard drives?

---

### Post by erickomans on 2010-07-07
Yes I do. I've got two 300gb.

---

### Post by Yarui on 2010-07-07
You could try unplugging the second one, then installing Ubuntu on the remaining drive.  If you have two drives it's possible you have installed Ubuntu on the wrong one, which would explain why you aren't getting the grub, because the MBR is probably still intact on the first drive.

---

### Post by erickomans on 2010-07-07
The installation process indicated that it installed to the proper drive.

If it hadn't, Windows wouldn't have been overwritten and I'd be able to boot into it, I'd imagine.

It also would mean that I overwrote my entire second harddrive (given that I selected that option the first installation attempt and this most recent one) and that would... whew. Don't wanna think about that one, haha...

EDIT: I can mount and access all the files on my second drive, so I know it isn't overwritten.

---

### Post by Yarui on 2010-07-07
Even if you think there is no chance, simplifying the system can't hurt.  I would give it a shot.

---

### Post by erickomans on 2010-07-07
No difference.

---

### Post by Yarui on 2010-07-07
Have you tried manually setting up the partition table?  Maybe the automated system just isn't doing it right.

---

### Post by erickomans on 2010-07-09
This seems to have resolved it!

Posting from my second boot into Ubuntu. This has made my day :D

EDIT: I re-created the partition table in GParted off the LiveCD, remade the partitions, and installed from there.

---

### Post by Yarui on 2010-07-10
That's great. I'm sure it's quite a relief after 2-3 days with no luck.  Be sure to mark the thread as solved.

---

