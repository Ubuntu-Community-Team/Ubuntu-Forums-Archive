---
title: "How to install Ubuntu 9.10 side by side with Kubuntu 9.04?"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by killabee44 on 2010-03-31
Hi all,

I did a search but for this topic and I thought it would be discussed quite a bit, did not get any results. Maybe I did not use the correct words?



Anyhow, I am running Kubuntu 9.04 and wish to switch to Ubuntu Karmic 9.10. I do still want to keep Kubuntu 9.04 as a boot up option temporarily in case I have major issues with Ubuntu.

Ill also need to know how to get rid of Kubuntu after Im sure all is well with Ubuntu. Finally, there are a ton of boot options (different kernels Ive upgraded to) in Grub when Kubuntu boots up. How do I get rid of those?

I also have a Windows XP partition that I boot into occasionally. 

Does anyone have a link to a tutorial for how to do this? Thanks.

---

### Post by oldfred on 2010-03-31
I did something similar when I converted to Karmic, but I had a new hard drive so I had lots of room. I had been updating my ubuntu for 3 years (every 6 months) and only had root (with lots of old cruft), swap and a small shared FAT partition for dual boot of XP. I wanted to convert the shared to NTFS, move /home and move all data to /data. I created space for several root installs, so I have previous, current and beta (just to test before full install). I will alternate my previous and current root partitions and link all data & /home into each. I also created enought extra space for additional root partitions incase I want to test other installs. Each only needs to be 10-20GB since all data is elsewhere.

I used this to move /home:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

I used this for /data
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

I aggressively move hidden folders with lots of data like firefox and thunderbird out of home into either shared or /data, so my home now is only 1GB. My root is about 5GB and all my data is in /data or shared.

---

### Post by killabee44 on 2010-04-04
Thanks for your reply...

This sounds like a good idea. It will give me the option of trying out new versions of Ubuntu and still keeping my stable install (like you are doing). 

Im still kind of green with Linux, but am willing to try. I will post back when I finally get it done or with any issues I run into.

Question: I read about moving GRUB to a partition of its own... did you do that also?

---

### Post by oldfred on 2010-04-04
I am booting Karmic directly with grub2 but have a grub partition for chainbooting the older versions that had grub legacy where I installed grub legacy in the PBR.

Grub2 does not like to be installed in a partition to allow chainbooting. I did that with my Karmic beta install and it complained on every update.

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition)
grub-setup -v /dev/sda6
Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force 

Herman on separate grub partition:
[http://ubuntuforums.org/showthread.php?t=1320270](http://ubuntuforums.org/showthread.php?t=1320270)
Grub partition slakkie
[http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/](http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/)

With grub2 I modified my menu a lot just becasue of all the systems:

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

Another way:
Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

---

### Post by killabee44 on 2010-04-06
Thanks oldfred...

A lot of info to digest. I will look into this further.

---

