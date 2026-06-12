---
title: "GCC Installation Error"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by AlGorism on 2010-11-10
Hey guys. 

First of all, I'm new at forum and Ubuntu. I installed Ubuntu 8.04 last day. 
I have a homework, so I installed Java and Eclipse C/C++ IDE. Than, realized that I should install gcc. 
After a little search, I tried synaptic. I created a script for that, but it's too slow. I tried to delete, but I couldn't manage it.
Then, I tried these commands:
> 
sudo apt-get update
sudo apt-get install build-essential
It asked for confirmation then. I typed y. But, these showed up and I don't know what to do now.
> 
Do you want to continue [Y/n]? y
Failed to fetch cdrom:[Ubuntu 8.04.4 _Hardy Heron_ - Release i386 (20100121.1)]/pool/main/g/gcc-4.2/libstdc++6-4.2-dev_4.2.4-1ubuntu4_i386.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 8.04.4 _Hardy Heron_ - Release i386 (20100121.1)]/pool/main/g/gcc-4.2/g++-4.2_4.2.4-1ubuntu4_i386.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 8.04.4 _Hardy Heron_ - Release i386 (20100121.1)]/pool/main/t/timedate/libtimedate-perl_1.1600-9_all.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 8.04.4 _Hardy Heron_ - Release i386 (20100121.1)]/pool/main/p/patch/patch_2.5.9-4_i386.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 8.04.4 _Hardy Heron_ - Release i386 (20100121.1)]/pool/main/b/build-essential/build-essential_11.3ubuntu1_i386.deb  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

A minute ago, I tried to install g++ by the same way, same errors showed up. Then I deleted those scripts by sudo. Still same error.

SOLVED.
Here is the solution: [https://answers.launchpad.net/ubuntu/+question/131742](https://answers.launchpad.net/ubuntu/+question/131742)

---

### Post by sikander3786 on 2010-11-10
Please mark the thread Solved by using Thread Tools near the top of the page.

That would help others save some time who are trying to help you.

SImple solution was to disable CD-ROM from Software Sources.

---

