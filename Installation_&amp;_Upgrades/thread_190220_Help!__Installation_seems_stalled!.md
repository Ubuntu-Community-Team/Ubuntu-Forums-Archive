---
title: "Help!  Installation seems stalled!"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by Cable on 2006-06-06
Ubuntu is almost done installing!  The screen says it's installing the GRUB bootloader, but it's said that for about 10 minutes with the progress bar frozen at 0%.  I am doing a dual boot with Win XP Pro, and using the alternate (text-based) install CD.  I'm getting a bit worried...suggestions?

---

### Post by rcarring on 2006-06-06
Give it an hour, if it is still stuck then your install has failed on grub. Reboot into Windows if you can. If this works then you need to figure out why grub failed.

Boot with the Live CD and try to mount the ext3 drive and look for installation logs that might help you.

It may be that grub is trying very hard to write to the mbr (did you select that option) or that it tried and failed. I just hope it didn't munge your XP installation. If it did, boot with the XP CD and run recovery console -- choose option repair boot sector -- and remove the Linux partitions.

Consider using vmplayer and visit easyvmx.com to create a virtual machine.

---

Please note, the approach above is what I would do in the same situation, there may be a better way.

---

### Post by Cable on 2006-06-06
It actually didn't give me any options for where to install GRUB, it just started installing it without saying anything...

---

### Post by Cable on 2006-06-06
Anybody else have suggestions?  Just want to see if there are any other routes...

---

### Post by makrothumeo on 2006-06-06
I had the same problem man. It seems GRUB is picky on file system formats because I tried installing Ubuntu about 6 times through the live CD on XFS and failed at GRUB each time. I used the alternate CD which installed LILO and it worked the first time. So I decided to change my file system to JFS (just to test a theory really) and Ubuntu installed perfectly.

I should note that each time I did an install I repartitioned the drive.

So my advice is to change your file system and see if that works.

---

### Post by FoggyMtn on 2006-06-06
Might read this thread.....

[http://ubuntuforums.org/showthread.php?p=1102445#post1102445](http://ubuntuforums.org/showthread.php?p=1102445#post1102445)


Rob

---

