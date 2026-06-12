---
title: "Some problems, biggies"
date: 2006-09-14
forum: Installation &amp; Upgrades
---

### Post by kauf on 2006-09-14
Back to school... my university gives out copies of Ubuntu - Great!  Until you try to install and mess up your existing OS even though it's on another HDD from where you wanted to install Ubuntu.

This hurts bad, first week of school and I go mess up my pc.  At least there aren't term papers due, lol.

What are my symptoms?  While booting the live cd I get those buffer I/O errors, a screen and a half's worth.  It seems a lot of people get those errors, however, it continues to boot and the live CD loads and appears to work fine.  I am unsure if other's get past the errors.  Currently the only OS that works for me now is the live cd, which takes approx. 15 minutes to load so I can't just hop on the PC (partly because the I/O error stuff takes forever to get past).

Installation of Ubuntu took a few tries to get working, I had to switch which DVD drive I used (benq dvd burner bad, pioneer dvd drive good), on the benq installation froze at random points, sometimes 15% another time 27% I think.  Regardless with the pioneer I've "successfully" installed Ubuntu twice on my 40GB HDD which I set the partition manager to reformat to ensure a proper install, in theory.

I say "successfully" because it tells me it works and I should reboot and remove the live cd so the OS boots. Upon boot to my 40GB, I am told "Operating system not found", I installed it again, and still got the error.  My windows drive now loads as such: 
```
GRUB loading stage 1.5
GRUB loading, please wait...
Error 15: File not found
```
or something like that.  I'll take a look at it again later, right now I just want Ubuntu to work, I'll deal with either fixing windows or simply accessing those files later.

It just seems weird, if the live cd runs fine how come it won't install properly?

Gotta go to class hope someone has some advice.

---

### Post by sethmahoney on 2006-09-14
You might try downloading and burning the alternate installer CD here: [http://www.ubuntu.com/download](http://www.ubuntu.com/download)

A lot of people have fewer problems with it.  And, if you want to set up a dual boot between Windows and linux, that's the way to go.

---

### Post by moore.bryan on 2006-09-14
*if you can, post the errors, too...*

---

### Post by kauf on 2006-09-14
The first of the errors goes as such:
4294763.22900 Buffer I/O error on device dm-0: logical block 6341985

the first series of numbers move up at a random pace, the logical block number increases from 6341985 to 6342013 then bumps back down to 6342008 and repeats a few times (*2008 to *2013), the first series keeps increasing even when the logical block goes back down.  

I forget what is stated before the errors... on my next boot I'll write it down.  There are only three or so steps left in the booting process after the errors.

Would those errors ruin the installation?  The installation completes, and there is no indication that the cd or the installation is corrupted, however something is because it just doesn't work.  In another thread I read that taking one of the two ddr sticks of RAM might allow it to install and work, not for me.  So unless I can do something through the terminal (I don't even know how to access it, so I'm wary of that) it seems all I can do is try to get the alternate CD and install from that.

---

### Post by kauf on 2006-09-14
I'm looking for the alternate installer, those listed at [http://www.ubuntu.com/download]("http://www.ubuntu.com/download")... are they the alternate DL or the live CD?  I see no mention of either on the page.  Thanks for the help guys.

---

### Post by sethmahoney on 2006-09-14
> **kauf said:**
> I'm looking for the alternate installer, those listed at [http://www.ubuntu.com/download]("http://www.ubuntu.com/download")... are they the alternate DL or the live CD?  I see no mention of either on the page.  Thanks for the help guys.

After you pick your location, the alternate install CD will be available for download at the bottom of the page (right above the file list).

---

### Post by kauf on 2006-09-14
Sweet, thanks... and I just noticed that there is a cd/dvd creator accompanying the live CD (so I don't need to hassle someone to burn it for me!).  I really hope that the alternate DL will fix things.  I'm still baffled that the live CD runs fine, so I know that Ubuntu CAN work on my system... and it appears to install without a hitch (now that I've found that it doesn't like my benq DVD drive)... yet it doesn't work.  I really want to run a linux machine, but it is clear why this OS is far from general public adoption.

edit: DAMN IT ALL TO HELL!  I/O error: no room left on device.  Only got 10% of the alternate DL... I should have known it was gonna happen, I was surprised that I could even start the DL (had a decent speed on it too).  The more I use the live CD the more I want to get linux working properly, it hurts.

Good thing I'm going to my brother's tomorrow... hope he has a blank CD.

---

### Post by confused57 on 2006-09-15
You might want to go ahead and repair your Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

and consider setting up your system this way:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

Grub isn't installed to the Windows mbr...and if you can get Ubuntu up and running on your 2nd hard drive, it's usually pretty easy to add the entry to your /boot/grub/menu.lst to boot your Windows drive.  It's another option for you to consider, at least you can "play" around with getting Ubuntu installed and not affect your Windows drive.

---

### Post by tmcahow on 2006-09-15
Why is it the only answer provided in this forum is the same one?  Download the alternate-cd...and when the advice is followed the inital poster returns with the same problem?

---

### Post by kauf on 2006-09-20
An update!  Some good news and some bads news, I'll mix 'em up to keep the suspense (so: chronological order).

I got my brother to burn me the alternate CD, that was... saturday.  Good news right?  WRONG - it was corrupted somehow, doesn't really matter how.  So I got another friend who lives closer to DL it and burn it, got that today (tuesday).  I tried to install it before work, but it was taking too long and I had to complete the installation after work (mind you I only had 15 minutes to spare).  I don't know if that may have messed up the install - oh yeah, it didn't work, but it looks promising - but if it didn't I don't know what did.

So the errors I now get are:
mount: Mounting /dev/root on /root failed: no such device
mount: Mounting /root/dev on /dev/.static/dev failed: no such file or directory
mount: Mounting /sys on /root/sys failed: no such file or directory
mount: Mounting /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have /sbin/init

There are some other steps inbetween but they all pass or seem inconsequential...

Also, I chose to use LILO not GRUB this time... and I haven't fixed my MBR yet, so windows is stil MIA.  I want to get linux up and running before I try to fix windows, don't want to fix it them mess it up again.

So, I'm now at a loss... the HDD starts to boot linux finally but it gets those errors - which is much better than with the live cd install.  The fact that it starts to boot linux off the HDD shows to me that changing that HDD to master not slave probably won't help, that was going to be the aspect I changed if it didn't work at all this time.

Any help?

Thanks for the continued support.

edit:  I'm going to try to reinstall from the alternate CD, doubt it will do anything but it's worth the try.  You guys probably know better... but in my eyes maybe 7 hours of it waiting for my input messed up the /root installation.  Please be the case.

---

### Post by kauf on 2006-09-20
I did the whole install again, no dice.

I didn't mention that after those failed mounts I get:

BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for ------------ (unimportant):
/bin/sh: Can't access tty; job control turned off

I can then enter commands, but I know my limits and just entered "help" to see what is at my disposal.  lol, why can't this just work?  I need sleep.

---

### Post by kauf on 2006-09-20
I hate to do this... bump?

This community has been very helpfull so far, I hope you can continue to assist me in getting ubuntu running on my machine.  The last post on the previous page details my current problems.

---

