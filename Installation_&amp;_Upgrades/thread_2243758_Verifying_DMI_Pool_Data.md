---
title: "Verifying DMI Pool Data"
date: 2014-09-10
forum: Installation &amp; Upgrades
---

### Post by paopao on 2014-09-10
A few days ago, there was a power outage and when power was restored and I turned on my computer, I couldn't connect to it.  This computer is my server and has the server version of Ubuntu 12.04 installed.  It has been running and working fine without any major issues for at least five years (I have had to replace hard drives over time).  I hooked up a monitor and watched the boot process.  It hung at the state "Verifying DMI Pool Data".  I used Google to find out what would be the cause and people were split about the issue - either new hardware or hard drive causing problems, or some corruption with the booting part.  What I suspected is that the server had upgraded to a new linux version, but couldn't install the latest version properly because I ran out of room on /boot and thus when it restarted, it had problems.

Let's give a brief description of the computer.  It has two software RAIDs, two drives for the operating system mirrored, and six drives for all the data in RAID6 (this link provides a lot of information: [http://paste.ubuntu.com/8315125/](http://paste.ubuntu.com/8315125/) ).  I loaded up a recovery disk (technically USB using the LinuxSecureRemix: [https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix) ) and ran the "boot-repair" tool.  It told me to install mdadm because it detected RAID, and so I did.

Everything seemed fine and was going to fix /dev/md0 where boot should be but when I ran the program, it said something about GPT partition detected and I need to flag the partition with bios-boot or something using gparted.  I apologize for not writing down this message; the program closed before I could and takes half an hour to "load".

When I ran gparted, and checked the flags, /dev/sdh (or /dev/sdg) had  /boot with the flags "boot" and "linux-raid" while the other add no  flags.  I didn't see a flag called "bios-boot".

I'm relucant to proceed and just try things because I feel that I'll make a bigger problem.  I don't know what to do and the boot-repair tool didn't work because it couldn't handle GPT.


The program allowed me to gather a bunch of data to post on a forum: [http://paste.ubuntu.com/8315125/](http://paste.ubuntu.com/8315125/)

/dev/sda through /dev/sdf are the 2TB hard drives making up the RAID6 (/dev/md3)
/dev/sdg and /dev/sdh are the 750* GB drives making up the mirroring raid that has the OS installed, /dev/md0 is /boot and /dev/md1 is everything else.  /dev/md4 is just a bunch of swap space (I think /dev/md2 is also swap, but it's not showing up?).  When the computer was running, /dev/sda and /dev/sdb were the OS drives with /dev/sdc -> /dev/sdh as the data RAID6 drives.  I don't know why they moved around.

Thanks.


* of the two OS mirrored drives, one is 750 GB, the other is 1TB with 250GB just unused space.

---

