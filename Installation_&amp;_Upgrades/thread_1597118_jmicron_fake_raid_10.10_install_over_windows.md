---
title: "jmicron fake raid 10.10 install over windows"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by Losergamer04 on 2010-10-14
Hello everyone.  Long time follower, first time serious user here.  I'm a Unix sysad so I figured it was time to take the jump (especially with the easy of configuring the cool effects these days my wife will be easy to convert).  Anyways, off to the problem, shall we?

I was trying to install 10.10 Ubuntu on my main Windblows desktop.  However it's running off 2 OCZ vertex SSDs in raid 0.  I tried the dmraid -ay as well as the GUI commands but nothing is working.  I'm guessing it's because in the /dev/mapper jmicron_RAID0 doesn't exist as it should.... it's more like "jmicron_RAID         ".   Yup, lots of spaces at the end.  I found a forum with a person who had this problem but he had little support and he is running the same motherboard, a DS3 P965 Gigabyte.  

I can't blow the Windblows away because we need that for watching MKV files on our 360.  The wife would kill me.

Long story short, I think if I resolve the name of the file (and it seriously does have those blank, not underscores, spaces) I belive the /dev/mapper error would be resolved as the name would match what it's looking for.  How the hell can I do that?  No, sim linking it didn't work, just in case you ask.

Thanks for taking the time to read this,
Rob

---

### Post by ronparent on 2010-10-15
There is something about ssd's. I have one with win 7 installed, but no partitions show in gparted. I think it may have something to do about alignment. In any event my prior adventures with raid drives have shown me that nothing is simple with fakeraid. And if sudo dmraid -ay can't activate your raid partitons they won't show in /dev/mapper.

There are some articles on ssd alignments for linux systems which I haven't researched because on no need. If win 7 is on the raid it may be more complicated because partition alignment needs may not mesh with gparted. On its own, 10.10 has been much easier to install to raid drives. I think that the alignment issue may be why your raid partitions aren't recognized. And as I discovered with 10.04 if gparted can't create the partitions the installer won't install. I will watch this thread with interest because at least one other poster is running into the same problems. If its solvable with a workaround with your background is promising. Good luck.

---

### Post by Losergamer04 on 2010-10-15
Is there any way to ghost my current Windblows install on another hard drive (of the spinning platter variety), install 10.10 (with a software raid under Linux), then virtual box my Windblows and run it off another disk?

As another thought, I wonder when they change block sizes and release hard drives with more than 2TB if that will cause similar issues for people in the future?

Thanks,
Rob

---

### Post by Losergamer04 on 2010-10-16
ubuntu@ubuntu:/dev/mapper$ ls -al
total 0
drwxr-xr-x  2 root root     100 2010-10-16 07:00 .
drwxr-xr-x 19 root root    4340 2010-10-16 11:03 ..
crw-------  1 root root  10, 59 2010-10-16 07:00 control
brw-rw----  1 root disk 252,  0 2010-10-16 07:00 jmicron_RAID0           
brw-rw----  1 root disk 252,  1 2010-10-16 07:00 jmicron_RAID0           1


I think if I can just fix the space issue it will work.  Any help?

Oh, and I tried to install Ubuntu on a regular hard drive via Windblows and it rebooted and tried to install it on my RAID again.  Uhhg.

---

### Post by danwood76 on 2011-03-04
Hi,

I dont know if you fixed your issue, or you just gave up.

I had this issue in the previous couple of releases, its fixed upstream but not in debian/Ubuntu.

Here is my original bug in 10.04:
[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/576289](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/576289)

It is a regreassion on a few years ago, the fix for 10.04 was in my ppa here:
[https://launchpad.net/~danwood76/+archive/ppa-testing](https://launchpad.net/~danwood76/+archive/ppa-testing)

Its probably safe to load that dmraid package in 10.10 and befond as nothing serious has changed in the last year in dmraid apart from a naming convention I think.

---

### Post by Losergamer04 on 2011-04-23
I never got a chance to try it because I gave up on it.  Hopefully someone else will see this post and be able to try it out.  Thanks.

---

### Post by danwood76 on 2011-04-24
This bug is fixed in the latest Ubuntu release (11.04)
And the patches have been sent upstream so will hopefully be fixed in the next dmraid version also!

---

