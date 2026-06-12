---
title: "trying to use kernal 2.6.32"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by Joker512 on 2010-01-08
Hello all and thank you for taking the time to read my post. I am trying to install the game "Eve-Online" on my computer but to do so I need the 2.6.32 kernel for it to work. I have been following the steps found on the games forum [http://www.eveonline.com/iNgameboard.asp?a=topic&threadID=1226117]("http://www.eveonline.com/iNgameboard.asp?a=topic&threadID=1226117"), but I am slightly confused. The directions on the forum tell me to download the rc6 kernel but another stated that:

 "If you take this route and your a Nvidia user you'll probably get some complaining when you recompile the Nvidia kernel module that the version of GCC on your system is not the version used to compile the kernel. Thus far i haven't had any problems tho. Its also possible rc6 was compiled with the version of gcc included in 9.10.

I'm using:

Ubuntu 9.10, install was fresh and is only a few weeks old
kernel 2.6.32_amd64 not the rc6 mentioned in this post, the final release, from the same mentioned ubuntu kernel PPA
Nvidia 195.22 drivers

with no issues.

2.6.32 changed some default settings for ext4, if you use ext4 you should check out this:

[http://www.phoronix.com/scan.php?page=article&item=linux_perf_regressions&num=2](http://www.phoronix.com/scan.php?page=article&item=linux_perf_regressions&num=2)

personally i have a UPS and mount with nobarrier (just add "nobarrier" to the options section of fstab) this removed any change in disk performance for me with 2 x 64GB OCZ Agility SSD's in mdadm RAID0." 


I have a dual AMD 64 processor as well as a nvidia 6800 graphics card. Should I still try to use the rc6 kernal? or should I be using this one [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/"). How would I go about downloading and installing the correct 2.6.32 kernel? Any help is much appreciated.

---

