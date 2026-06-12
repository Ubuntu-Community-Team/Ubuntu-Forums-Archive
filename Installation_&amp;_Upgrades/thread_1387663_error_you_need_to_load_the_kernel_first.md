---
title: "error: you need to load the kernel first"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by sneilan on 2010-01-22
Hey All,

I'm having weird problems after I installed ubuntu over arch linux.

I have 2 harddrives. The primary one that I run grub off has both ubuntu & windows xp. The other has just ubuntu. I boot onto grub on the primary hard drive & then select ubuntu off the second.

My grub.conf is here:
[http://pastebin.com/m7fad8e2f](http://pastebin.com/m7fad8e2f)

My output from df is here:
/dev/sda2              2569552   2340020     99004  96% /
udev                   2059308       360   2058948   1% /dev
none                   2059308       912   2058396   1% /dev/shm
none                   2059308        88   2059220   1% /var/run
none                   2059308         0   2059308   0% /var/lock
none                   2059308         0   2059308   0% /lib/init/rw
/dev/sdb1                37635     16338     19289  46% /media/d36f0b70-f525-4b0a-a3cb-2e915c483780
/dev/sdb3             30723344   3070800  27652544  10% /media/f0471efb-0122-47f2-8785-a0dccb5e49c5
/dev/sdb4            453404716 106064156 347340560  24% /media/f22c7f59-721d-4ace-ab5f-282ee85fda6a
/dev/sda1            290438104  96762432 193675672  34% /media/C6ECE9B6ECE9A0C3

Also, I should mention that on the second drive / is mounted to one partition, /boot is on another & /home is on another. /boot in df is mounted as /media/d36f0b70-f525-4b0a-a3cb-2e915c483780. I'm pretty sure that's /dev/sdb1.

I'm also running ubuntu 9.10 in both places with grub 2. This grub.conf & df stuff is from booting off ubuntu on the primary drive.

For some reason, when I select ubuntu from the second drive, I get "error: You need to load the kernel first".

Any ideas? Thank you for your time.

-Sean

---

