---
title: "software raid-1 + XFS issues"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by aromanov on 2007-03-08
Hi all,

I have installed recently an Ubuntu 6.10 server on Dell 1600SC on software raid-1 PATA disks formatted with XFS filesystem.

All looks and runs good (kudos to Ubuntu team), but occasionally, after system crashes (due to defective DVD-RW drive, which will be changed soon), I have some troubles with missing directories in /var/run directory. Which prevent some services to start (in particular firebird2 sql server and ngircd IRC server). I have been able to resolve these problems, by using dpkg-reconfigure command and looking for error messages, but as these problems are verified two times, I'm a little bit worried. In a dmesg log I see:
[42949383.210000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[42949383.210000] SGI XFS Quota Management subsystem
[42949383.240000] XFS mounting filesystem md0
[42949383.400000] Starting XFS recovery on filesystem: md0 (logdev: internal)
[42949384.450000] Ending XFS recovery on filesystem: md0 (logdev: internal)

Seems everything is ok, but after recovery some /var/run directories are missing.

Should I make a full backup of server and install it on ext3 filesystem? Or it is software raid-1 problem?

Thanks in advance,
Andrey.

---

### Post by Justintoxicated on 2007-03-08
Sorry I can't help but what do you use to install Raid-1?  I'm stuck here the partition manager does not appear to support it?  Is there a link to a how to that works for version 6.10?  I'm going to give it another few hours then Suse is going on

---

### Post by aromanov on 2007-03-12
Well, I have used Debian setup CD to partition and format HDD. Then Ubuntu install went on  software raid-1 without problems. One note: you should install LILO boot manager instead of GRUB, otherwise it will not boot.

---

### Post by gpremuda on 2007-04-02
See [http://www.ubuntuforums.org/showthread.php?t=200837&highlight=%2Fvar%2Frun%2Ffirebird2](http://www.ubuntuforums.org/showthread.php?t=200837&highlight=%2Fvar%2Frun%2Ffirebird2)

---

