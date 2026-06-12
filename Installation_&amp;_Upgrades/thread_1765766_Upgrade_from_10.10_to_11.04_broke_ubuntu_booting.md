---
title: "Upgrade from 10.10 to 11.04 broke ubuntu booting"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by cpburns on 2011-05-23
I upgraded from 10.10 to 11.04 (kernel 2.6.38-9) and now Ubuntu won't fully boot. I get this message:

```

Gave up waiting for root device.  Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT!  /dev/mapper/isw_jhdfjbgej_Volume01 does not exist.  Dropping to a shell
```Which resulted in falling back to a BusyBox shell.

If I `ls -l /dev/mapper` i get:

```

isw_jhdfjbgej_Volume0 -> ../dm-0
isw_jhdfjbgej_Volume0p1 -> ../dm-1
isw_jhdfjbgej_Volume0p5 -> ../dm-2
```I tried booting with an older kernel (2.6.35-28) and that worked (except for x because the nvidia drivers weren't build) and did `ls -l /dev/mapper` and I got:

```

isw_jhdfjbgej_Volume0 -> ../dm-0
isw_jhdfjbgej_Volume01 -> ../dm-1  # my ext4 partition
isw_jhdfjbgej_Volume05 -> ../dm-2  # my swap partition
```So I `sudo apt-get purge linux-image-2.6.38-9-common` and then reinstalled `nvidia-common` for 2.6.35-28 (dkms rebuild the module). Then when I rebooted into 2.6.35-28 I got the same `/dev/mapper/isw_jhdfjbgej_Volume01` error that I got with 2.6.38-9.

---

### Post by Hedgehog1 on 2011-05-23
Do you have RAID setup?

We need to get a look at your system to get an idea what is going on.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

[IMG]http://img854.imageshack.us/img854/4563/codetags.png[/IMG]


***The Hedge***

:KS

---

