---
title: "Not Booting, Missing partitions"
date: 2014-04-25
forum: Installation &amp; Upgrades
---

### Post by pbhill on 2014-04-25
Having a similar problem. Had difficulty booting so I ran Boot Repair. Now it appears that my Linux drive (SDB) no longer exists! It just shows one . labeled as "unallocated". Before there were four partitions. I am worried for my Home partition. Cant boot either disk now.

---

### Post by oldfred on 2014-04-25
@pbhill
Please do not hijack another thread. Totally missing partitions are a different issue.
Start another thread with good title. Include link to Bootinfo or whatever you can.

---

### Post by pbhill on 2014-04-26
Sorry ... Not trying to "hijack"!  it's started from the same source, failure to boot. Just trying to get some help here!

---

### Post by pbhill on 2014-04-26
> **oldfred said:**
> @pbhill
Please do not hijack another thread. Totally missing partitions are a different issue.
Start another thread with good title. Include link to Bootinfo or whatever you can.

Sorry oldfred, but nobody's trying to hijack anything. This problem started at the same source, a failure to boot after an upgrade. I am just trying to get a little help here.

---

### Post by oldfred on 2014-04-26
Moved to your own thread as missing partitions is different and failure to boot is very generic. Most issues are unique.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

            Only if trusty 14.04, you need a work around to install, Boot-Repair for 14.04 trusty not yet released
 ----------- WORKAROUND 0 sandyd  compiled it
 [https://launchpad.net/~sandyd/+archive/boot-repair](https://launchpad.net/~sandyd/+archive/boot-repair)
 ----------- WORKAROUND 1
+ You can download the DEBs packages here: [https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages](https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages)
+ First install the 'glade2script' DEB, then 'boot-sav', then 'boot-repair'.
+ 
+ ----------- WORKAROUND 2
+ Use Boot-Repair-Disk [https://sourceforge.net/p/boot-repair-cd/home](https://sourceforge.net/p/boot-repair-cd/home)
+ ----------- WORKAROUND 3
[https://bugs.launchpad.net/boot-repair/+bug/1307218](https://bugs.launchpad.net/boot-repair/+bug/1307218)
Workaround. Change ppa from trusty to saucy.
[http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335](http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335)
gksudo gedit /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list
'[http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages)'
'[http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/saucy/main/binary-amd64/Packages)'

---

