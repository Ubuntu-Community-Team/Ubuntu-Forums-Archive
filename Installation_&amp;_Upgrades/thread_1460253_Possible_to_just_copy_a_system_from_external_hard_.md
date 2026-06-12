---
title: "Possible to just copy a system from external hard drive?"
date: 2010-04-22
forum: Installation &amp; Upgrades
---

### Post by jonsayer on 2010-04-22
So my laptop has been crashing ever since I installed 9.04. I was recently told on these forums it might have something to do with using ext4 instead of an older, more stable file system on my hard drive like ext2 or 3. I have a plan to fix this problem, and I was hoping someone here might be able to point out the flaws in my plan.

1) copy the partition with my linux system onto an external USB hard drive. 

2) boot up the a Live CD and format the partition to ext3

3) still in the Live CD, copy the partition from the USB external hard drive back to the newly-formatted ext3 partition. 

4) reboot

What's going to break here? Am I going to need to reinstall grub or anything else?

---

### Post by uRock on 2010-04-22
You should be able to copy without any problems, but you may have to reinstall grub. 

You may want to do some more troubleshooting though. EXT4 has been rock solid for a while now. I have done quite a few installs with no problems from EXT4.

---

### Post by jonsayer on 2010-04-22
> You may want to do some more troubleshooting though. EXT4 has been rock solid for a while now. I have done quite a few installs with no problems from EXT4.

I posted here asking for help last week: [http://ubuntuforums.org/showthread.php?t=1458175](http://ubuntuforums.org/showthread.php?t=1458175) but got no responses. 

The troubles didn't start until I installed 9.04 with ext4. 8.04 with ext3 had no problems, which makes me think one of those two things are the problem. 

I don't really want to go back to 8.04, though, because 9.04 has such a nice auto wifi connection system and 9.10 won't boot up on my laptop.

---

