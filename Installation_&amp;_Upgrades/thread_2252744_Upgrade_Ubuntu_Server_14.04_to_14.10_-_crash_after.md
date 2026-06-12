---
title: "Upgrade Ubuntu Server 14.04 to 14.10 - crash after plymouth-upstart-bridge and swap"
date: 2014-11-14
forum: Installation &amp; Upgrades
---

### Post by victorhooi on 2014-11-14
Hi,

I have a HP DL360 G5 running Ubuntu Server 14.04.

I just did a do-release-upgrade to 14.10.

The upgrade wizard itself seemed to proceed fine.

However, upon reboot, I get a message about plymouth-upstart-bridge, and then it appears to hang after a line about swap:
```

[     76.658794] init: plymouth-upstart-bridge main process (199) terminated with status 1
[     76.721567] init: plymouth-upstart-bridge main process ended, respawning
[     76.772407]init: plymouth-upstart-bridge main process (215) terminated with status 1
[     76.834786] init: plymouth-upstart-bridge main process ended, respawning
[     77.539657] Adding 2094076k swap on /dev/cciss/c0d0p5. Priority:-1 extents:1 across: 2094076k FS

```
After this, the machine is unresponsive.

I'm not able to SSH into the box either, I get:
```

ssh 192.168.2.120
^[[O^[[I^[[Ossh: connect to host 192.168.2.120 port 22: Operation timed out

```

There seem to be a few mentions on the internet of similar issues, but no explanation of what's actually going on, or what the definitive fix is:

[http://ubuntuforums.org/showthread.php?t=2224744](http://ubuntuforums.org/showthread.php?t=2224744)
[http://blog.jamesrhall.com/2014/04/ubuntu-server-1404-fun.html](http://blog.jamesrhall.com/2014/04/ubuntu-server-1404-fun.html)
[http://ubuntuforums.org/showthread.php?t=2218100](http://ubuntuforums.org/showthread.php?t=2218100)
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1309617](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/1309617)

Any thoughts on what I can try to recovery this?

Cheers,
Victor

---

### Post by MAFoElffen on 2014-11-14
Will this box boot on a LiveCD so you could paste pin the Sys Log to a pastebin and post it's boot log file? Does it get to a grub menu? What metal is this on? (hardware spec's?) Cause I see /dev/cciss and I'm trying to remember which one of my RAID controllers here comes up like that here on one of mine. Think one of my IBM XServers comes up device names like that (SmartRAID?) ...

---

### Post by victorhooi on 2014-11-16
Hi,

The machine is a HP DL360 G5, with a P400i SATA/SAS controller card. That would explain the /dev/cciss devices.

I can probably boot it up with a LiveCD and get the syslog.

However, before I do, I thought I should mention that I actually ended just inserting the "sleep 2" command as per [http://www.unrelatedshit.com/2014/07/30/kvm-too-fast-for-plymouth-upstart-bridge/](http://www.unrelatedshit.com/2014/07/30/kvm-too-fast-for-plymouth-upstart-bridge/)

After this, it seemed to boot up successfully.

However, I don't really understand the full significance of this (beyond it being some timing issue or possibly a race condition with Plymouth), or what is has to do with the swap device. It's really just a case of me blindly following a suggestion on a blog.

Is this a recognised bug in Ubuntu? Or is there some issue with my Ubuntu install that would cause this issue to manifest.

Regards,
Victor

---

