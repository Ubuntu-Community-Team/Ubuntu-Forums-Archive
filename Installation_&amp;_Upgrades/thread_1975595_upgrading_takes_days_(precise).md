---
title: "upgrading takes days (precise)"
date: 2012-05-07
forum: Installation &amp; Upgrades
---

### Post by jim.hansson on 2012-05-07
I am trying to do upgrade from the update-manager and it is taking days to complete. after running for over 1 day, I still have 1 day and 10 hours before it will be done.  the harddrive-light is on most of the time, and the wireless is blinking almost constantly.

My computer is a sony vaio modlel: VPCF1151E
it has a Intel(R) Core(TM) i7 CPU   Q 720  @ 1.60GHz with 4 cores and 8 threads total
6 GB ram

I have one big partition for / and /home with encrypted /home, and my filesystem is btrfs.

When I look at the output from top I don't see any massive load on the processors
top - 21:43:50 up 1 day,  2:16,  1 user,  load average: 2.43, 2.47, 2.63
Tasks: 215 total,   2 running, 211 sleeping,   0 stopped,   2 zombie
Cpu(s):  1.0%us,  2.1%sy,  0.0%ni, 72.2%id, 24.7%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   6106820k total,  5512680k used,   594140k free,   429316k buffers
Swap:  9621500k total,    44536k used,  9576964k free,  3494928k cached

the only process that popup from time to time in top is "btrfs-endio-met" but as most 10% mostly 1-2%

I am thinking that this problem is somewhat IO or scheduling related but don't know where to look next? The machine basic spec is more than enough but why is the upgrade taking days instead of a few hours?
I hade the same problem with the same machine upgrading from 11.04 to 11.10 and I have the same problem now when upgrading from 11.10 to 12.04 but this is the only machine that I have this problem with.

I have attached a file with printouts from some different commands, is there anything more that I should attach?

---

### Post by vVvSHADOWvVv on 2012-05-07
> **jim.hansson said:**
> I am trying to do upgrade from the update-manager and it is taking days to complete. after running for over 1 day, I still have 1 day and 10 hours before it will be done.  the harddrive-light is on most of the time, and the wireless is blinking almost constantly.

My computer is a sony vaio modlel: VPCF1151E
it has a Intel(R) Core(TM) i7 CPU   Q 720  @ 1.60GHz with 4 cores and 8 threads total
6 GB ram

I have one big partition for / and /home with encrypted /home, and my filesystem is btrfs.

When I look at the output from top I don't see any massive load on the processors
top - 21:43:50 up 1 day,  2:16,  1 user,  load average: 2.43, 2.47, 2.63
Tasks: 215 total,   2 running, 211 sleeping,   0 stopped,   2 zombie
Cpu(s):  1.0%us,  2.1%sy,  0.0%ni, 72.2%id, 24.7%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   6106820k total,  5512680k used,   594140k free,   429316k buffers
Swap:  9621500k total,    44536k used,  9576964k free,  3494928k cached

the only process that popup from time to time in top is "btrfs-endio-met" but as most 10% mostly 1-2%

I am thinking that this problem is somewhat IO or scheduling related but don't know where to look next? The machine basic spec is more than enough but why is the upgrade taking days instead of a few hours?
I hade the same problem with the same machine upgrading from 11.04 to 11.10 and I have the same problem now when upgrading from 11.10 to 12.04 but this is the only machine that I have this problem with.

I have attached a file with printouts from some different commands, is there anything more that I should attach?

The update process is as dependent on bandwidth as system power. Please post your bandwidth speed test here.

This seems to be a bandwidth issue as your system is invariably sufficient. My system specs are:
Intel® Core™ i7-2820QM CPU @ 2.30GHz × 8 
Memory: 20.00 GiB
64-bit

Even with my superior system, it does take a while to upgrade. I recently upgraded to 12.04 from 11.10.

My guess is 2 reasons. 
1.) If you attempt to upgrade during the first 2 weeks of the release, you will notice that the Ubuntu upgrade systems are overloaded thereby making download of new packages slow.

2.) Your bandwidth may be slow.

&#7780;&#11367;&#480;&#7430;&#336;&#412;
shadowsgovernment.com

---

### Post by critin on 2012-05-07
I think if you used an ethernet wire during the process, it would speed up considerably.  wireless is too slow for me.

---

### Post by vVvSHADOWvVv on 2012-05-07
> **critin said:**
> I think if you used an ethernet wire during the process, it would speed up considerably.  wireless is too slow for me.

@critin

Completely incorrect. Wire or wireless does not make a difference as currently wireless N will support above 2.0MB/s. 

Yes I have a wireless N card and yes I have done this. Please do not post incorrect info without a firm understanding a wireless protocols and speeds.

&#7780;&#11367;&#480;&#7430;&#336;&#412;
shadowsgovernment.com

---

### Post by critin on 2012-05-07
> **vVvSHADOWvVv said:**
> @critin

Completely incorrect. Wire or wireless does not make a difference as currently wireless N will support above 2.0MB/s.

Yes I have a wireless N card and yes I have done this. Please do not post incorrect info without a firm understanding a wireless protocols and speeds.

&#7780;&#11367;&#480;&#7430;&#336;&#412;
shadowsgovernment.com

Completely incorrect?  I don't think so, but your tone is.

The key words here are:  "I think" and "for me"; the info is not incorrect.  No install should take days no matter what the excuses are, and when (wireless) downloads are this slow it could be due to a signal that is affected by too many things interfering with it. Or a bad antenna, or the wireless chipset.  Even the firewall, etc.  

We have to start somewhere and connecting a wire seems to be the simplest. (for me)

---

### Post by jim.hansson on 2012-05-08
thanks for all the answers, My bandwidth is 30/10 but the download of all needed packages is allready done, that step of the process only took an hour or two. it's the step after downloading of packages that is taking so long time. If I look at my traffic logs on my router it has been almost no traffic for last 24 hours. I have had problems before with other things interfering with my wireless network and have spent time fixing it (for some reason all my neighbors run all their wireless on the same channel) so that should not be a problem any more, have done a lot of testing of it.

At least now it has reached the part where it says "setting up <package X>....."  and only 10 hours left :-)

and while editing this post we got from 10 hours to 6 hours left, so now it goes really fast :-)

---

### Post by oldfred on 2012-05-08
Something is really wrong with your update/system. And or you have slow Internet. If slow Internet, I might install without updates, then change to a better location for downloading & then do updates. 

With my new SSD it is less than half an hour (15-20min with updates), but I install from a hard drive to the SSD. I have found that USB flash is faster than CD, and hard drive faster than flash.

I do find wired Ethernet faster but I have g not n. 

When installing from flash to hard drive without updates it was about 20 minutes & with a high speed Internet connection about another 20 minutes to do all the updates. 

Why btrfs? Each filesystem seemed to have some advantage in certain tests, but ext4 was best or close for most tests, so ext4 seems best overall.

Ubuntu 12.04 LTS - Benchmarking All The Linux File-Systems
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1)
Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)

---

### Post by jim.hansson on 2012-05-08
oldfred: why btrfs, because I can, wanted to try it out. No really good reason :-)

The upgrade was done 2 hours after my last message so I don't have the problem now, but an upgrade should not take 36-40 hours. 

I will mark this thread as solved, but will continue to investigate what the problem is. It looks like IO intesive applications slows down after running a while.

---

