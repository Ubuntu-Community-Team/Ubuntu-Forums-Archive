---
title: "Installation Problem on Raid0"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by WillockBoy on 2008-05-26
I've been reading the "Ubuntu fakeRaid 0 How To - 7.10 Gutsy Gibbon" forum article and have been trying to install Ubuntu 8.04 on my Dell 9200 Raid0 machine running Vista Home Premium.

I get as far as......

ubuntu@ubuntu:~$ sudo dmraid -r 
/dev/sdb: isw, "isw_hijeaaced", GROUP, ok, 312499998 sectors, data@ 0 
/dev/sda: isw, "isw_hijeaaced", GROUP, ok, 312499998 sectors, data@ 0 
ubuntu@ubuntu:~$ sudo fdisk /dev/mapper/isw_hijeaaced 
 
Unable to open /dev/mapper/isw_hijeaaced 
ubuntu@ubuntu:~$  
 ... and then get the above error.

Any help would be welcome. I have to say that attempting to get Ubuntu installed on a Raid system is becoming a real pain. Is it better to uninstall the Raid system?

---

