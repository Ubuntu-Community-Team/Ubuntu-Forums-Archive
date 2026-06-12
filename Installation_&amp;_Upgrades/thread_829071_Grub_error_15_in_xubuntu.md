---
title: "Grub error 15 in xubuntu"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by Hooya on 2008-06-14
So I can't boot into a fresh install of Xubuntu.  I get the Grub Error 15 (File not found).  All the tutorials that I find tell you how to fix it assuming that the /boot/grub directory exists.  It doesn't on my system.  The system images are there, but there's no Grub directory.  So how the heck am I supposed to fix it if the files don't exist at all?  Re-installing does not help, the directory still isn't there.  Grub is on the MBR, that's not the problem, the problem is that it can't find the files because they aren't there!

Any idea on how to get them there?  Super Grub Disk was useless because all it wants to do is find the grub directory, it won't make it.

---

### Post by heatpumpcontrol on 2008-06-14
list some of the things that you've tried so that you're not asked to repeat them..

---

### Post by Hooya on 2008-06-14
Well, nothing that involves an attempt at restoring Grub settings works, since the /grub directory isn't there.  So anything that assumes that a /grub directory exists will not solve this problem.

I've tried re-installing the system from scratch using the Xubuntu Live CD, letting it format the / partition and I got the same problem every time (whether booting into the OS through the Live CD first or going directly to install).  I always tried to keep my partitioning structure because I had a /home partition set up, although I would let it format /

I just gave in and let it totally wipe my system (which I didn't want to do because I had a separate /home partition set up).  And found that all the times I've tried to install before it never asked me to restart my computer but this time it did strangely enough.  Now it boots.  So it must have been an issue in the installer when keeping the directory structure, but not giving /boot it's own partition or something... yeah...

---

### Post by heatpumpcontrol on 2008-06-14
Glad to see you got it working though not in the manner you had hoped for. 

Mark this thread as "Solved" just in case others have a similar issue.

---

### Post by Habbit on 2008-06-14
Damn it I arrived late :(. Most probably you could have fixed it by booting off the live CD, chrooting into your Xubuntu installation and manually installing GRUB with apt-get.

---

### Post by Hooya on 2008-06-29
I'm unsolving this thread and posting more on it because I decided to try a similar thing and had the same problem.  This time I went more into it, following instructions here:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
which involve doing a chroot into the install from a live CD to re-install grub.  I had problems doing this though.

I mounted the file system of the installation just fine, but as soon as I tried to do "sudo grub" it gave me an error of not being able to "resolve host ubuntu".  So I was never able to fix grub that way.

I tried booting into the system, still having error 15, and did manage by copying the files from the /usr/lib/grub/i386-pc/ on the live CD to the /boot/grub directory to get a grub prompt at boot instead of a simple Error 15.  I even made my own menu.lst from scratch.  Everything I tried eventually resulted in an Error 15 when finally booting.

So I'm back to the chroot into my installation option, trying to figure out why I'm getting "unable to resolve host ubuntu" error after doing the chroot command.

Any ideas?  I could just wipe the system again, but I don't want to do that this time.  I want to keep my /home partition.
Trying to install the system with a separate /boot partition doesn't make any difference.

I should mention one more thing.  By default I do not have a file "initrd.img-2.6.24-xx-generic" file, only that file with the .bak extension.  Is this a big deal?  Seems to me that it is!

Edit:
After careful editing and adding of files manually into /boot and /boot/grub I finally managed to boot my system.  I can't log in though.  It lists the name of the computer different than I selected at install (it's calling itself "terranova" and the time zone is wrong) and I'm stuck at the login screen with no correct username or password.  Also, it takes a long time to boot up compared to how it used to be before I tried messing with all this stuff.  Any clue as to what to do now?

One final edit:  I started with the live CD, backed up my home directory on a usb drive (what I could of it anyway) and had the installer format the /home partition as well as the root partition.  This time it worked.  So the difference between it working and not working was formatting the entire drive or not formatting the entire drive, or at least formatting the /home partition.  Still, not really a fixed issue, but I've also posted in a few bugs in launchpad I found related to the problem.

---

