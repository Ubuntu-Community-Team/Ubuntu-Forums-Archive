---
title: "Ubuntu won't start (Maybe Gnome-Baker / Hibernation problem)"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by spofer on 2010-09-23
Hi all,

First of all I'm pretty new to Ubuntu so please be easy on me.

I've recently installed Ubuntu 10.04 from a USB install. It worked very well for a few days, in which i hibernated at least once. Today, I hibernated Ubuntu again - But after powering up the ubuntu opened up fresh. In the same session I've installed GnomeBaker, and tried to use it  - But it failed burning.

A couple of restarts later Ubuntu stopped starting up - It doesn't even show the graphical ubuntu load screen, just quickly writes a lot of text, and the last screen contains a trace (i think), mounting errors, and the error "Target filesystem doesn't have /sbin/init.". I have a BusyBox console (v1.13.3) with the cursor "(initramfs)".

I found this post
[http://wwww.ubuntuforums.org/showthread.php?t=1167710&page=2](http://wwww.ubuntuforums.org/showthread.php?t=1167710&page=2)
In which transmutable describes the same problem I have, but I wasn't able to start into a live USB (or Live CD), and got error like the one described in the following post
[http://ubuntuforums.org/showthread.php?t=1345125](http://ubuntuforums.org/showthread.php?t=1345125)

I'm pretty clueless here, as I'm not sure how can i solve this issue.

My computer is Lenovo T410, and I'm dual booting Windows 7 32bit (Yes, there is a recovery partition - But Ubuntu worked before, so I reckon this is not the case)

Thanks for your time!
Spofer

---

### Post by spofer on 2010-09-25
Hi again,

Since the problem seems to be /dev/sda related - I checked my partitions - It seems i have 5 partitions - All primary. I vaguely remember from the old days there was a 4 primary partitions limit. Obviously it doesn't exist anymore for Windows 7.

Could this have caused this kind of issue?

My partitions are:
1. SYSTEM_DRV - Windows 7
2. Main Windows 7 disk
3. Linux Swap
4. Linux Main
5. Lenovo Recovery

I'm not sure which of these could be made non-primary. Since GRUB loads windows 7, can't partition #2 be extended / logical?

And last of all - Do you have recommendations for a good disk partitioning software (windows / liveCD)?
I'm downloading GParted Live now.

EDIT: I've attached a GParted screenshot

Thanks!
Spofer

---

### Post by spofer on 2010-09-25
Okay, problem solved. It probably was a file system issue.
What i did was this:

Started GParted - Did nothing with it - only checked partition info.

Then when i restarted the CD was ejected. Now, for some reason - Ubuntu detected file system errors and fixed it - And the problem was gone.
LiveCD works too - I tried fsck and nothing was reported.

So it was either GParted or just leaving the CD bay open while restarting that fixed the problem. Either way - I'm good for now

Thanks!
Spofer

---

