---
title: "Missing Windows 7"
date: 2011-10-21
forum: Installation &amp; Upgrades
---

### Post by chinner459 on 2011-10-21
Had trouble upgrading to 11.10 which started and then failed and no further attempts to restart were any good. Finally I found wubi.exe and started Ubuntu 11.10 from there.  This worked fine except that I can no longer see my Windows 7 from which I ran wubi.  This is a pain as I have been unable to get my Canon printer working in Ubuntu and was relying on being able to transfer any print file to my Windows OS and print from there.  On my machine I have three systems working,  Windows XP, Windows 7 and of course Ubuntu 11.10.
I have tried to mount the Windows  7 OS using the mount command but with no luck so far.  I would be grateful if someone could tell me how I can get my Windows 7 listed in the 11.10 file system

---

### Post by varunendra on 2011-10-25
First off, keep a Live Ubuntu CD handy in case it gets worse. Then boot into ubuntu, open a terminal and enter:
```
sudo update-grub
```
Reboot and see if Windows gets listed. If not, download, extract and run [boot info script]("http://bootinfoscript.sourceforge.net/") as described on the download page and post the contents of Result.txt file it generates.

---

### Post by Rubi1200 on 2011-10-25
+1 for the boot info script as it will really help us figure things out.

---

### Post by Mark Phelps on 2011-10-25
While we're waiting for you to run the script ... let me pass along a few comments ...

What you CAN do in Ubuntu, is see the files and directories in your Windows 7 OS partition.  If you installed using Wubi (can't really tell from your comments), the Win7 OS partition is ALREADY mounted (which is why you can't mount it -- again) under /host in your Linux filesystem.

What you can't do in Ubuntu is RUN Windows 7, including, using it to install any device drivers.  So, unfortunately, you won't be able to make use of an Windows Canon printer drivers in Ubuntu.

I would also advise against writing files to your Win7 OS partition from inside Ubuntu.  That runs the risk of corrupting the filesystem as it is really easy to leave it in an unusual state.

---

