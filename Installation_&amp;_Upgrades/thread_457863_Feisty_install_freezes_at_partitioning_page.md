---
title: "Feisty install freezes at partitioning page"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by Buster95 on 2007-05-29
Using the "official" Canonical 7.04 disk, install freezes every time at page 5 partitioning. I'd like to set it up as a dual boot and have already got XP on board. It works well of course.

During the freeze, the screen image stays up but no keyboard or mouse.

My desktop was running Edgy OK. The disk checks out OK.
I'm not sure what next steps to take. Appreciate any help.
Cheers

---

### Post by aysiu on 2007-05-29
Well, if all of what you're saying is true, I don't know what's wrong. 

Freeze-ups usually happen for one or more of the following reasons:

1. Not enough RAM
2. Hardware failure
3. Bum CD

You say > The disk checks out OK. Are you saying that because it's an official CD, or because you actually checked it out? And if the latter, then by what method did you check it out?

---

### Post by Buster95 on 2007-05-29
I first ran the disk check option that comes up first on install.
Then I started the installation.
On the partitioning screen (page 5), I took the first option "guided partition".
I tried that 3 times and it froze each time.

Since posting the message, I tried again, only this time using the 3rd option, "manual partition".
This progressed the install to completion. However, I haven't had an opportunity to extensively test it to see whether everything works.

I'll report later on that, however, I'm now very wary about this OS. Edgy has always worked well for me on this desktop and I'm prepared to revert at the first sign of misbehaviour.

I was also going to try Feisty on my laptop, knowing that Edgy has never worked well on that machine for me. Now, I have this feeling I'm in for a few long nights trying to get things to work on it. For the laptop, I might try "Plan B", another OS.

Cheers

---

### Post by Buster95 on 2007-06-01
Follow-up note:
Manual install didn't work either. On start the boot option doesn't come up. It just starts up XP, which works OK. I can run Feisty off the disk (painfully slowly). I'm assuming that the install somehow isn't going to completion. But there doesn't seem to be anything I can do except follow the install prompts. I'm not sure what to do next.

Following the manual partition option, step 4 (Prepare partitions) shows:
/dev/hda1 ntfs  2146MB Presumably that's where XP is located
/dev/hda2 ext3 4507MB
/dev/hda5 swap 666MB
/dev/hda6 unknown 3002MB
free space 69701 MB

I am then asked to specify a partition for the root file system. I selected /dev/hda6. I am then prompted to edit that partition, by defining "use as" and "mount point".
It is unclear to me what to enter into these fields. The help documents seem to assume that it all just rolls on.

Any guidance would be appreciated.

---

### Post by Buster95 on 2007-06-02
2nd update
Tried another manual install. This time, when I rebooted, it returned a boot screen with Ubuntu, Ubuntu safe, memtest, Windows XP. So far so good.
Everything seems to work OK so I'll provisionally declare this thread resolved.

Unfortunately, the boot screen also shows what looks suspiciously like another copy of Ubuntu. Seems like one of the previous install attempts managed to load up, but failed to show the boot screen.
Now I have to work out which install I'm using and how to get rid of it. I'll address that on another thread.

---

