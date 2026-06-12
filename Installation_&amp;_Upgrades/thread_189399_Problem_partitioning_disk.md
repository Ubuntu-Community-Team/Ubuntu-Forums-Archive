---
title: "Problem partitioning disk"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by grimbo on 2006-06-05
Hello

I downloaded the desktop Ubuntu 6.06 ISO last night, and have done the "test files on the CD" option on bootup, which it passes.

I'm trying to install it onto my laptop, which is a Dell D610 with a 60GB disk, 21 GB is used of a 59GB partition. I have run chkdsk in Windows XP which reports the disk is fine.

If I ask it to partition the disk, and select 30GB for Ubuntu and 30GB for Windows, it just sits there forever (I left it for 15 minutes in case it was having a think).

I have also tried the manual partition bit, which says "Not enough space" when I try the same manually.

Could anyone please point me to what I might be doing wrong?

Thanks in advance for any help.

---

### Post by TeeAhr1 on 2006-06-05
Are you using the partitioner in the installer itself?  That is known to be buggy; try using gparted first (it's in the live CD, system > admin > gnome partition editor).

Also, try resizing the Windows partition first and letting that operation run before telling it to create the ext3 partition.  May help, may not.

---

### Post by confused57 on 2006-06-05
May want to defrag your Windows before trying to resize the partition.

---

### Post by andre-gj on 2006-06-05
I've tried both gparted and the installation partitioner. Keep giving me an error saying something like can't resize hda1. I've tried several times to defrag in windows, even tried "power defrag". keep giving me the same error.

I've noticed in the windows defrag there seemes to be someting stored at the very end of the disk, but defrag doesn't move it, only parts of it....

Any ideas? Can I find what files are stored at the end of the disk and move them?

---

### Post by grimbo on 2006-06-07
Thank you all for the suggestions - the gparted tip did the trick, and I have managed to install it (And did the windows defrag)
Thanks for your help.
Sorry andre-gj am a clueless newbie, hopefully someone will help you.

---

