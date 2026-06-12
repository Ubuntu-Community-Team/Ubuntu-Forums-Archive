---
title: "Can't boot after upgrade - freezes after udev warnings"
date: 2010-01-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by doctordruidphd on 2010-01-22
I am trying to upgrade a karmic system to lucid. I had it working in the past, but on or about Jan 8th, an upgrade to lucid killed the system. It would no longer boot, freezing after the udev warnings in the boot process. I have re-done the upgrade several times since then, and it always fails at the same point. There are a few errors during the upgrade, requiring --force-overwrites, but in the end, everything seems to go through properly. No logs are being written to the system, suggesting that the file system is not being mounted. I tried the upgrade again last night, and ran update-initramfs after the upgrade just to make sure it worked, and it ran without errors. 
I am not sure exactly what is failing, maybe mountall, but since there is no log file being written, it's pretty hard to trace. Any ideas on this?

Note: I can access the file system from karmic, so that much is intact.

Edit: I should mention that this is actually kubuntu, on a 64-bit quad core system.

---

### Post by philinux on 2010-01-22
> **doctordruidphd said:**
> I am trying to upgrade a karmic system to lucid. I had it working in the past, but on or about Jan 8th, an upgrade to lucid killed the system. It would no longer boot, freezing after the udev warnings in the boot process. I have re-done the upgrade several times since then, and it always fails at the same point. There are a few errors during the upgrade, requiring --force-overwrites, but in the end, everything seems to go through properly. No logs are being written to the system, suggesting that the file system is not being mounted. I tried the upgrade again last night, and ran update-initramfs after the upgrade just to make sure it worked, and it ran without errors. 
I am not sure exactly what is failing, maybe mountall, but since there is no log file being written, it's pretty hard to trace. Any ideas on this?

Note: I can access the file system from karmic, so that much is intact.

Edit: I should mention that this is actually kubuntu, on a 64-bit quad core system.

If you're dual booting with a stable karmic install and attemting to test lucid I would suggest you download the alpha2 livecd and install from that.

---

### Post by doctordruidphd on 2010-01-22
> If you're dual booting with a stable karmic install and attemting to test lucid I would suggest you download the alpha2 livecd and install from that.

Not possible. For one thing, none of the live cd's since 8.10 will work on this system. Thanks for the suggestion, but I really don't want to get sidetracked on that issue. I need to figure out why the system won't boot, and what to do about it. It did work fine, up until Jan 8th, so there is a problem that needs attention.

---

### Post by philinux on 2010-01-22
> **doctordruidphd said:**
> Not possible. For one thing, none of the live cd's since 8.10 will work on this system. Thanks for the suggestion, but I really don't want to get sidetracked on that issue. I need to figure out why the system won't boot, and what to do about it. It did work fine, up until Jan 8th, so there is a problem that needs attention.

Ok.

I seem to vaguely remember the udev thing a while back. If you search this forum for udev you might track the fix down.

---

### Post by ranch hand on 2010-01-22
Keep the bugger updated.

---

### Post by ronacc on 2010-01-22
> **doctordruidphd said:**
> Not possible. For one thing, none of the live cd's since 8.10 will work on this system. 

mabye what you need to do first is track down why livecd's since 8.10 won't work on your sys . I am running an AMD dual core sys and except for the normal occasional glitches with alphas and daily's haven't had a problem with them .

---

### Post by doctordruidphd on 2010-01-22
> **ranch hand said:**
> Keep the bugger updated.

I'd really like to, but if it won't boot...

I should add that I cannot boot into a text console at all. Not on either normal boot or recovery mode. The problem persists even if I boot an older kernel; I suspect the kernel itself is alive, as CTRL-ALT-DEL and ALT-SYSRQ-REISUB work as expected. 

> I seem to vaguely remember the udev thing a while back. If you search this forum for udev you might track the fix down. 

Thanks again for the suggestion. I'll keep searching, but so far I haven't found a thread where the system would not boot.  What I suspect is that the file system won't mount (it fsck's OK from another system), but then again, why no busybox error to that effect?

---

### Post by ranch hand on 2010-01-22
You have another OS right nest door.  Chroot into the bugger and update it.

My test platform has 7 versions of 10.04 including Lubuntu.  I am on my daytime production OS on that drive right now.  As I have boinc running I do not like to leave here when I don't have to.

I have a script (thanks philinux) to get into all of them.  That is how I do all the updates and upgrading.

It is a lot easier if your partitions are labeled.  Use gparted from your LiveCD to do that.  Then just modify this to fit your drive;
```

#!/bin/sh

sudo mkdir /mnt/Mini-root
sudo mount /dev/sda15 /mnt/Mini-root/
sudo mount -o bind /proc /mnt/Mini-root/proc
sudo mount -o bind /dev /mnt/Mini-root/dev
sudo mount -o bind /dev/pts /mnt/Mini-root/dev/pts
sudo mount -o bind /sys /mnt/Mini-root/sys
sudo cp /etc/resolv.conf /mnt/Mini-root/etc/resolve.conf
sudo chroot /mnt/Mini-root /bin/bash

fi

```
Save that in a gedit file and mark the permissions to make it executable.  After the first use you will need to comment out the first line (add # and a space in front of it).

---

### Post by doctordruidphd on 2010-01-22
```
#!/bin/sh

sudo mkdir /mnt/Mini-root
sudo mount /dev/sda15 /mnt/Mini-root/
sudo mount -o bind /proc /mnt/Mini-root/proc
sudo mount -o bind /dev /mnt/Mini-root/dev
sudo mount -o bind /dev/pts /mnt/Mini-root/dev/pts
sudo mount -o bind /sys /mnt/Mini-root/sys
sudo cp /etc/resolv.conf /mnt/Mini-root/etc/resolve.conf
sudo chroot /mnt/Mini-root /bin/bash


```

Thanks for that script! 
I modified it appropriately, and from my karmic working system into my testing system with the kde-4.4 beta upgrade, it works beautifully.  However, for the broken lucid system, when I try an apt-get update, I get a swarm of errors about not being able to connect to anything. So I take it the system is major broken. 
Everything is backed up, I can wipe the lucid system and do the upgrade again, but so far three attempts have led to the same result. Still banging away at it...

---

### Post by ranch hand on 2010-01-22
Ah, if it was not connecting to the repos take a look at your (9.10) /etc/resolv.conf (that is spelled right).  It should look something like;
> 
# Generated by NetworkManager
nameserver 10.0.0.2

Then look at the one in 10.04.  I bet it doesn't look like that.  Assuming that your 9.01 does, just copy/paste the bugger.

---

### Post by ronacc on 2010-01-22
if you are wireless and can get a cat5 cable to that box try chrooting and  updating again wired . also check the /etc/apt/sources.list it it's so broken you can't even get to a recovery console no telling what is borked .

---

### Post by doctordruidphd on 2010-01-22
Interesting. In my (dead) lucid system, there is no /etc/resolv.conf. In fact, the whole structure of /etc/resolvconf.d is different. Which means that either lucid is doing things differently, or the upgrade didn't work properly, in which case more than resolv.conf is likely messed up.

OK, I just copied over the resolv.conf, and now the repos are connecting. But I'll bet what is wrong is the upgrade didn't go through right, thereby clobbering the whole thing. Will hack at this further. But this is progress, at least in understanding what went wrong.

---

### Post by ranch hand on 2010-01-22
My resolv.conf are pretty identical.  Could be you are badly corrupted.

Have you run;
```

dpkg --configure -a

```
That doesn't have the sudo as I assume a chroot environment.  It may help and should at least give you some useful messages.

---

### Post by doctordruidphd on 2010-01-22
> dpkg --configure -a

Yes. During the upgrade, which I did from within the system, there were several abort points which needed 'dpkg -i --force-overwrite packagename', and there were several 'apt-get install -f', 'dpkg --configure -a' and 'apt-get dist-upgrade' commands needed, all sudo. At the end of about 2 hours of this, install -f and --configure both came out clean. I suspect, though, that it didn't really go all that well. I just checked and noticed, for example, that in /etc/init, there were no mountall.conf files, so I did a 'dpkg-reconfigure mountall', and lo! they suddenly appeared there.

---

### Post by ranch hand on 2010-01-22
Might be a good idea to do that to all the "x" stuff too.

---

### Post by doctordruidphd on 2010-01-22
Yeah. I think the problem is before x, though. I guess it's gonna be step-by-step through the files. 
Oh well, I wasn't planning anything for the next week or so...

---

### Post by Petr.cz on 2010-04-29
There's a bug in Lucid - everything in /etc/fstab must by mountable  during boot.

I had the same problem after new installation of Lucid Lynx 64 RC. 
Everything was OK until I added my own mounting point to /etc/fstab. After this
boot up freezed before mounting partitions (mountall), that's why threre's no log written to the system.  Check your /etc/fstab. If any of the mount points failed to mount during boot, booting freeze !

---

### Post by doctordruidphd on 2010-04-29
> There's a bug in Lucid - everything in /etc/fstab must by mountable during boot.

Yes, that's the problem. I forgot to mark this thread "solved", which I will do now. I had entries in fstab for several usb drives, so they would mount properly when inserted. That doesn't work in Lucid; I changed them to "noauto", and it boots fine.

---

