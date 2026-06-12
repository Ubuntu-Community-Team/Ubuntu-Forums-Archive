---
title: "Can I dual-boot with XP on pre-existing RAID 0+1 (fakeraid) istallation?"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by moj on 2006-06-11
Hi, this is my first time installing ubuntu on a RAID machine and after searching the forums I'm still pretty lost. At the moment my PC just has XP intalled on a RAID 0+1 setup consisting of 4 drives, it is NVIDIA RAID (fakeraid) which comes with the motherboard. Is it possible to install ubuntu as dual-boot with XP, without losing any of the data on my XP partition/s whilst keeping everything RAID 0+1?

Judging by the posts I've read it's a risk I'm not willing to take, but I'd just like to confirm things.

---

### Post by Arnaud_B on 2006-06-11
Sure check this: [https://wiki.ubuntu.com/FakeRaidHowto?highlight=%28fakeraid%29](https://wiki.ubuntu.com/FakeRaidHowto?highlight=%28fakeraid%29)
However, I cannot tell you how well it work as I did not tested it myself but well seems that it works from what I heard... 
I have a setup very similar to yours with 4 hd but I choose to use a linux raid on 3 of them for ubuntu and let windows on the remaining one as I pretty much never use it... you might consider this option too if you feel like reinstalling windows later...
Good luck!
A.

---

### Post by moj on 2006-06-11
Thanks Arnaud, this looks like it may be exactly what I need! :) Just one question though; do you know which version of Dapper would be best to use? Right now I have the standard 6.06 DVD and CD versions, would it be better to use the alternate CD version, since I hear this has beter RAID support (or would this not matter as this is fakeraid anyway)?.

---

### Post by Arnaud_B on 2006-06-11
from what I understand (but as I said I did not test it so better check the wiki ;-) ) the way to go is to install with the live cd first because this allow you to install dmraid *before* starting the installation and the partitioning... the trick is that the regular installation cd (live or alternate do not contain dmraid which is what allow the partionner to see the intel raid array). However, I have no idea if dmraid is on the dvd so cannot help you on that...
Also, what you are mentioning that the alternate cd contain better raid support is true but for linux raid as the live cd does not allow AFAIK to setup mdadm but this has nothing to do with dmraid/fakeraid...
Hope that helps :-)
Good luck!
A.

---

### Post by moj on 2006-06-11
Cool, I'll get the live CD downloaded and try it out. Thanks again :)

---

