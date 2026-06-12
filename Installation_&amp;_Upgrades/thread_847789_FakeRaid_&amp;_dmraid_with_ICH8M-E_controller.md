---
title: "FakeRaid &amp; dmraid with ICH8M-E controller"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by DJMatty on 2008-07-02
Hi

I have a Dell XPSM1730 laptop with raid 0 configured on with the two drives. This is working fine for the vista install that is on the machine, however when I boot to the hardy live cd, install dmraid and issue the command I get an error for each drive and it says there is no raid present.

```
ubuntu@ubuntu:~$ sudo dmraid -ay
ERROR: isw: Error finding disk table slot for /dev/sdb
ERROR: isw: Error finding disk table slot for /dev/sda
No RAID disks
```

I've done some digging and one article mentioned that dmraid relies on AHCI, after checking my bios, it's a bit cryptic about if that is enabled when raid is enabled...

Can anyone point me in the right direction to get the raid array visible to ubuntu?

Many thanks

Matt

---

### Post by oliwek on 2008-07-12
if you haven't solved this already, you can always install gutsy from the livecd on a fakeraid setup (follow [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)), then upgrade to gutsy, it's a known working method...

or follow this french post for hardy heron : [http://forum.ubuntu-fr.org/viewtopic.php?pid=1738308#p1738308](http://forum.ubuntu-fr.org/viewtopic.php?pid=1738308#p1738308)

[-o<

---

### Post by DJMatty on 2008-07-16
Hi

I just tried booting to the gutsy live cd and installing dmraid, then issuing sudo dmraid -ay command, and I get the same response as hardy, it seems dmraid doesn't correctly detect the raid array as it is configured on the ICH8M-E controller in my XPS M1730 machine.

Oh well...

Matt

---

