---
title: "Fiesty - Locked Out of Linux! Whole Computer Brought to a Crawl!"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by Rev. Nathan on 2007-04-21
After patientely waiting the two days to took to download and install up the upadtes, I was anxious to try Ubuntu 7. My whole custom panel in KDE was erased; no biggie. Hop into the firefox, and it crashes.

OK...

X gets killed and I have to Ctrl+Alt+Backspace... ugh! Within the first five minutes!

So I do it... doesn't fix the problem! Do it again... I have to restart!

Damn near thought my drive failed... look minutes to get to the GRUB screen... didn't bother waiting for Kubuntu to load... went to Windows to report this. Wondering what can be done.

---

### Post by jdong on 2007-04-21
The symptoms you report sound like a disk failure, first the kernel disabled access to your disk after detecting a read or write error to prevent further damage, then applications started crashing after that. GRUB will load very slowly on a drive that was uncleanly unmounted in this fashion.

Are you sure the disk is not physically bad?

---

### Post by Rev. Nathan on 2007-04-21
jdong,

I appreciate your promptness. The harddrive in question is hda (the partition in question is hda1). On hda2, I have Windows XP installed, which I am using now. As far as I am concerned, XP is running at its usual pace, albiet I never knew Internet Explorer was this slow at rendering pages. Given that grub is installed on hda1, my concern is in direct coorelation with hda1, not hda2. Thentherefore, hda is not the problem, and that is something to do with Ubuntu itself. And also given this problem has never occoured with Ubuntu 6, saying it has something to do with the recent update to 7 with be most apt.

I'd appreciate input, and since I do have access to video editing on Windows, I can provide a video of the boot process, if you wish.

---

### Post by jdong on 2007-04-21
Well, the thing is, an upgrade is a disk-intensive operation. It in effect replaces all half or million or so files comprising your Ubuntu installation. It's possible that this could've tripped over a "bad spot" on your disk or pushed it over the edge figuratively.

One thing you can try to see if it's a disk error, boot onto a LiveCD, then run **sudo dd if=/dev/hda1 of=/dev/null** from a terminal. This will silently read all the contents of the first partition, block by block.

At the same time, in a different terminal, periodically check the output of **dmesg** (towrads the end), look for any strange errors about unreadable sectors, or aborted commands.

If the dd command fully completes without any dmesg errors, then your disk is probably ok, and we should look into the software aspects.

---

### Post by Rev. Nathan on 2007-04-21
> **jdong said:**
> Well, the thing is, an upgrade is a disk-intensive operation. It in effect replaces all half or million or so files comprising your Ubuntu installation. It's possible that this could've tripped over a "bad spot" on your disk or pushed it over the edge figuratively.

One thing you can try to see if it's a disk error, boot onto a LiveCD, then run **sudo dd if=/dev/hda1 of=/dev/null** from a terminal. This will silently read all the contents of the first partition, block by block.

At the same time, in a different terminal, periodically check the output of **dmesg** (towrads the end), look for any strange errors about unreadable sectors, or aborted commands.

If the dd command fully completes without any dmesg errors, then your disk is probably ok, and we should look into the software aspects.
Certainly.

How long will it take? Ubuntu is formatted 100GB on a 7200RPM HDD.

---

### Post by jdong on 2007-04-21
Unfortunately that will take as long as it takes to read back 100GB of data from your hard drive.... maybe a few hours. And there is no progress indication, unless of course you hit a read error, which causes it to abort.


If you are using the ext3 filesystem, alternatively you can issue **sudo e2fsck -f -c -v /dev/hda1** to perform a full disk check, including a bad blocks scan. This does display a progress and will even attempt to mark bad blocks.

---

### Post by Rev. Nathan on 2007-04-21
I'm using ReiserFS; a file system I adopted from my speed binge days. Any pointers on that?

---

### Post by jdong on 2007-04-21
That explains the slow grub (grub is especially slow when reiserfs is improperly shut down).....

With reiser you have to be very careful about fscking the disk blindly, because in my experience and in others' too, sometimes when reiserfsck is confused it will go on a data destroying rampage.

First, very importantly, make sure you have a copy of all your important data on the disk.

I'd suggest running "sudo reiserfsck --check /dev/hda1" and, if it doesn't look too bad, a --fix-fixable also. Do not run --rebuild-sb or --rebuild-tree unless you have a full backup of all your valuable data.

---

### Post by Rev. Nathan on 2007-04-21
K, on a live CD

Should I use the command from post 4 or the command from post 8 first?

---

### Post by jdong on 2007-04-21
I would first try the --check command from #8 first, and if that seems to find things "wrong" with the disk (it's just a check, does not do any repairing), then I'd do #4 to check that it's not a physical disk problem.

---

### Post by Rev. Nathan on 2007-04-21
OK. I'm copying files from /home/nathan to my external drive... ~1 hour to go. Might to go to bed. Either way, I'll report my findings when performed.

---

### Post by Rev. Nathan on 2007-04-21
I can't do much. I'm on a Ubuntu 5.10 Live CD, and the resierfsck commands seem to activate, but not work. The command offered in post 4 is taking a long while, and I'm getting a little testy.

Can I not just reinstall ubuntu?

And if I can, where can I find a copy of kubuntu 5.10 for download (for some reason, the version 6 CD dropped support for my mouse input... I'm guessing this will be the same with 7).

---

### Post by Rev. Nathan on 2007-04-21
Gad zooks! I rebooted, and outta nowhere, my partition is running at full pace!

Methinks that "mystery function" jdong posted in post 8 did the trick.

Thanks!

---

