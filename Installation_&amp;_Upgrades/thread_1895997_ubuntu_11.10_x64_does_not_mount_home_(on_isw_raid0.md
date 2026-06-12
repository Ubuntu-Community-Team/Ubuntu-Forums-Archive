---
title: "ubuntu 11.10 x64 does not mount /home (on isw raid0) at bootup"
date: 2011-12-16
forum: Installation &amp; Upgrades
---

### Post by rbsbscrp on 2011-12-16
Hi all (experts), can anyone help?

I've got a 64gig ssd from which I have win7 partition and /boot and / partitions for ubuntu 11.10 x64. There's also a raid0 isw (intel firmware type raid) which has partitions for data-w1(ntfs), /home(ext4), /data-l1(ext4), and swap. 

This is what I know so far... If I try to boot up normal, I just get a pink screen. When I boot up in recovery-mode I can choose Remount (fs -> read/write) and then I can hit Control-C which then allows things to progress. However I get a notice to the console that /home, /data-w1, and /datal1 are't ready or don't exist yet. I can press 'S' on the keyboard and allow things to progress til I get a commandline. Then I can enter:

```
 sudo kpartx -a -v /dev/mapper/isw_xxxVolume0
``` - which *usually* works. When it does I can ls /dev/mapper and see all of the partitions on the raid. Then I enter:

```
sudo mount -a
```

and have the partitions mounted (as I have them entered in the fstab. Then I can "sudo startx" and go.

So I entered these commands into /etc/rc.local (I even tried putting sleep5 around the commands) and sent the command stdout to /var/rc.local.log - where I see that either the kpartx failed or else something like "cannot stat() /dev/mapper/iswxxx_Volume0". BTW when I run /etc/rc.local manually from the commandline (as root) it also fails. 

I've read the UpStart docs but I still do not understand what is wrong here. Are there any experts out there who know what is going on here (or what _should_ be going on) ?

---

