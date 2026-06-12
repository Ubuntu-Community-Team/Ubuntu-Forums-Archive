---
title: "Ubuntu 10.04 one major and some minor problems"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by Costas100 on 2010-06-11
My last thread in the new installation of Ubuntu 10.04 was 3 weeks ago . After thread [http://ubuntuforums.org/showthread.php?t=1484615](http://ubuntuforums.org/showthread.php?t=1484615) my problems continued in some new areas.
My computer has 2 ubuntu (10.04 and 9.10) and XP home installed in separate partitions and I have. 10.04 and XP are installed in the master HD and 9.10 in the slave. Both HDs have partitions for files (linux and windows)

**1.**  A major problem is that from time to time (about 1 in 3 startups) a crash occurs at startup which leaves me no option but to do a hard computer restart (despite the fact that this is a no no issue). The last screen which remains for ever in my monitor has the following statement:    [    16.148101] [drm:rs400_gart_adjust_size]   *ERROR*  Forcing to 32M GART size  (because of ASIC  bug  ?) -  This is critical because of the hard reboot which may eventually destroy all my systems.

**2.**  I do have a couple of minor issues which I think with time I will find a solution:

[LIST]
[*]I have problems with recording sound. I can play sound from all sources but no luck in recording. I read thread [http://ubuntuforums.org/showthread.php?p=9343309](http://ubuntuforums.org/showthread.php?p=9343309) which basically suggests to kill pulse and use  alsamixer. I did not try it yet from fear of making the situation worst. Any suggestions will be appreciated.

[*]I have another minor problem, that in most startups of 10.04 when I open Places/Computer I cannot see the media  (NTFS and Fat32) partitions which include my files. I found a workaround by installing and using Dolphin (which reads all my partitions)  and as soon an the partition is opened in Dophin it becomes visible also in Computer. I can live with that unless there is a simple fix.
[/LIST]
All in all (and despite my age) my experience  with UBUNTU is excellent and this includes the latest 10.04 and in the last few years I helped many of my friends and relatives, including my 6 year old grand daughter to become UBUNTU followers. **Thank you all for the excellent and unselfish work.**

---

### Post by nerdzero on 2010-06-11
Hi Costas100,

I checked on launchpad for your error message regarding your major issue and there seems to be a bug about it.  There is a workaround posted in the comments (comment #16), maybe it will work for you.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/562843](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/562843)

---

### Post by Costas100 on 2010-06-11
Thank you nerdzero, I checked the link and I see I am not alone. I do not think at this stage I will attempt any of the changes suggested. I will wait for a bit and I will not use 10.04 (I do have 9.10 in the same computer and 9.04 in another and both work fine). Maybe a new live CD will be available soon. 

I may try a grub CD or usb stick for startup and see how things go. My Linux knowledge and my age tells me to be very careful.

Thank you very much

Costas

---

