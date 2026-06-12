---
title: "apt-get update fails"
date: 2015-05-09
forum: Installation &amp; Upgrades
---

### Post by jorritTyb on 2015-05-09
When I do apt-get update I get these errors:

> 
W: Failed to fetch [http://be.archive.ubuntu.com/ubuntu/dists/saucy-updates/universe/binary-i386/Packages](http://be.archive.ubuntu.com/ubuntu/dists/saucy-updates/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://be.archive.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/binary-i386/Packages](http://be.archive.ubuntu.com/ubuntu/dists/saucy-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://be.archive.ubuntu.com/ubuntu/dists/saucy-backports/main/source/Sources](http://be.archive.ubuntu.com/ubuntu/dists/saucy-backports/main/source/Sources)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://be.archive.ubuntu.com/ubuntu/dists/saucy-backports/restricted/source/Sources](http://be.archive.ubuntu.com/ubuntu/dists/saucy-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://be.archive.ubuntu.com/ubuntu/dists/saucy-backports/universe/source/Sources](http://be.archive.ubuntu.com/ubuntu/dists/saucy-backports/universe/source/Sources)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://be.archive.ubuntu.com/ubuntu/dists/saucy-backports/multiverse/source/Sources](http://be.archive.ubuntu.com/ubuntu/dists/saucy-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://be.archive.ubuntu.com/ubuntu/dists/saucy-backports/main/binary-amd64/Packages](http://be.archive.ubuntu.com/ubuntu/dists/saucy-backports/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]


W: Failed to fetch [http://be.archive.ubuntu.com/ubuntu/dists/saucy-backports/restricted/binary-amd64/Packages](http://be.archive.ubuntu.com/ubuntu/dists/saucy-backports/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.15 80]




And a lot more like these. This worked before.

I'm using ubuntu 13.10

Any idea how to fix this?

---

### Post by Bucky Ball on 2015-05-09
Yes, upgrade to a supported release. 13.10 is EOL, dead, and the repositories are closed. That's why you are getting, and will continue to get, these error messages. You are trying to update from repos that no longer exist. 

If you need help with the upgrade/fresh install, just ask. ;)

It worked previously because 13.10 was probably still supported last time you tried (or not long out of it).

PS: I'd suggest going for 14.04 LTS. It is supported until 2019. LTS releases have five years support. Interim releases have nine months.

---

### Post by jorritTyb on 2015-05-09
> **Bucky Ball said:**
> Yes, upgrade to a supported release. 13.10 is EOL, dead, and the repositories are closed. That's why you are getting, and will continue to get, these error messages. You are trying to update from repos that no longer exist. 

If you need help with the upgrade/fresh install, just ask. ;)

It worked previously because 13.10 was probably still supported last time you tried (or not long out of it).

PS: I'd suggest going for 14.04 LTS. It is supported until 2019. LTS releases have five years support. Interim releases have nine months.

Hmm. I tried to upgrade to 14.04 in the past and it also failed for reasons that nobody here managed to find there.

Probably best to try a fresh install but I hate doing that so I'll probably postpone it until I'm absolutely forced to do that :-)

Thanks for the reply

---

### Post by Bucky Ball on 2015-05-09
Now is probably that time. You will get no updates, and that includes security updates. If this machine is not online, carry on. If it is it becomes more security vulnerable with each passing week. 

Also, you will get no software updates and therefore will end up using out of date apps (which you already would be).

If this is all fine by you, by all means, postpone. If not, backup your valuable data and fresh install (or plug in an ethernet cable, disable all third-party manually installed PPAs and upgrade through the Software Updater).

If you are going to stick with 13.10, please mark this thread as solved as that is the reason you are getting the errors you have reported. Thanks and good luck. ;)

---

