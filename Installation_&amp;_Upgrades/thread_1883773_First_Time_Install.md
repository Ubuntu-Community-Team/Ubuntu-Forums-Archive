---
title: "First Time Install"
date: 2011-11-19
forum: Installation &amp; Upgrades
---

### Post by Hipster Doofus on 2011-11-19
Complete noob here. I have been having one hell of a time getting to the stage I am now at.

I have finally got grub to work. Took two days of trial & error using 'boot repair' disc.

At the boot screen I get the attached picture.

If I go with the top selection I get to the wallpaper screen & nothing else. (first attempt saw a screen with scrolling text - 2nd picture)

If I go with the second selection into 'recovery mode' then at the next screen go 'normal boot', I can get into the system.

Even though I am going into recovery mode, 'normal boot' is it getting me to where I want to be?

---

### Post by Hipster Doofus on 2011-11-20
I give up. Now when booting up it looks like the graphics driver has snuffed it. Ah well back to windows.

---

### Post by coldraven on 2011-11-20
I suspect that the install disc had errors on it. Unlike an audio or video disc every single bit on an install disc has to be correct.
Try burning another one at a slow speed.
Sorry it did not work for you, I have never had any problems installing Ubuntu over the last few years.

---

### Post by Hipster Doofus on 2011-12-22
Thanks coldraven. I'm back for more.
 I've dug a hole so deep..............:popcorn:

I just tried to install from a fresh perspective. Windows 7 first then Ubuntu. Still having problems.

I partitioned a spare drive to this-

/dev /sbd

/dev /sbd1

Made a primary, ext 3 in it.

Booted to ubuntu hoping to get it to automatically install to the created partition. It refused so I had to do it manually.

Please see if I am doing this right.

From the start I wasn't sure what to do about the swap volume so I just left it as is. I am setting it up on a total of 20 - 25gb.

To the above I have-

mount point = /

boot loader went to /dev /sbd1

Rebooted after the install & it went straight into windows. AHHHHHHHHH!

I'm now in the process of setting up raid0, partitioning the drive for window & install windows 7. That will leave me with plenty of room for a Ubuntu load on the remainder of the drive.

I'm also going to redownload the ubuntu iso.

Any advice at this stage will be much appreciated. :KS

---

### Post by QIII on 2011-12-22
You have two physical drives, correct?  Do you have a compelling reason for RAID?

---

### Post by Hipster Doofus on 2011-12-23
That's right. Two physical drives although now they are in raid0. 

I tried setting them up as individual drives & had some very weird stuff going on when installing Ubuntu. Gave up. Now windows 7 is installed & I have 57gb left. Thought I would go with around 20-25gb for Ubuntu.

Just got windows up & running, all drivers installed.

---

### Post by QIII on 2011-12-23
Alas!  Now that you have made it a RAID, you have moved outside of my area of expertise.

But just for future reference, using two separate physical disks really makes this dead easy.

Unplug one disk and install Windows on the one still connected.

Unplug the Windows disk, plug in the other and install Ubuntu on it.

Plug both disks in.

When you next boot, go to the BIOS settings and make sure the Ubuntu disk is the first in the boot order (behind your optical drive.)

Continue booting to Ubuntu.

Update GRUB

```
sudo update-grub2
```

You should see it pick up the Windows installation in GRUB.

Restart and check that Windows is a choice in the GRUB menu and that you can boot to it.

Shut down and do the same to make sure you can boot to Ubuntu.

The beauty of doing it that way is that if one or the other of the drives craps out on you, you can boot the drive that is left without problems while you run over to Frys to get a new disk for the other OS.

I have 5 disks on one of my machines.  Each of them has a partition for an OS and the rest is NTFS for common storage.  My OSs are all on separate physical disks.

I have 5 OSs -- one on each drive -- that I can boot to.  I can unplug four and still get into the one that is left.

---

### Post by Hipster Doofus on 2011-12-23
Thanks [QIII]("http://ubuntuforums.org/member.php?u=628170").

Bookmarked for the future. 

I think I did something similar. When I used Boot Repair for the grub it did not work. It would not even see my windows install.

Stuck the windows disc in, booted up to 'repair' & then even that would not see the windows OS. Very confusing. Tried a few things but could not get the windows mbr back.

Just wondering if it is something to do with the SSDs?

Anyway I started another thread dealing with raid.

Thanks again. :)

---

