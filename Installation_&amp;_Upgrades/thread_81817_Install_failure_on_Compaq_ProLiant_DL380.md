---
title: "Install failure on Compaq ProLiant DL380"
date: 2005-10-25
forum: Installation &amp; Upgrades
---

### Post by kmcgregor-cow on 2005-10-25
I am attempting to install the 5.10 "Server" CD on a Compaq ProLiant DL380 server. The server hardware is dual 1 GHz Pentium III, 2 GB RAM, two 36 GB SCSI drives connected to the embedded RAID controller (which are set as a RAID 1 pair) and four 145 GB SCSI drives connected to a HP/Compaq SmartArray 431 RAID controller (set up as RAID 0+1).

I've installed Ubuntu 5.10 on the 36 GB volume. All goes well and it tells me to remove the CD and reboot. When I reboot, it gets to the point where it says "Loading, please wait...", which is shortly followed by
```
ALERT! /dev/ida/c0d0p1 does not exist. Dropping to a shell!

[Busy box message]
/bin/sh: can't access tty; job control turned off
```

And indeed, /dev/ida doesn't exist. Help! I'd love to get Ubuntu running on this server!

---

### Post by kmcgregor-cow on 2005-10-25
Okay, I'm guessing the cpqarray module is not a built-in module for the kernels included on the Ubuntu 5.10 Server CD. Can anyone confirm this?

---

### Post by eDave on 2005-11-16
I'd be interested in knowing how to do this also since I'm trying to get Ubuntu running on the same type of machine....

---

### Post by oucil on 2006-05-13
Sorry see below...

---

### Post by oucil on 2006-05-13
Dang forum error, see below again...

---

### Post by oucil on 2006-05-13
Has anyone found a solution to this problem yet, haven't found anything in any other threads.  I have almost an identical setup on a Compaq DL380 using the Smart Array with two 18gig drives.  I've tried all install combinations with every kind of raid setup available to me.

Please post the solution if you've found one!

Many thanks!

---

### Post by DavidRa on 2006-05-20
A genius calling himself or herself "vjshah" posted a working fix in [http://www.ubuntuforums.org/showthread.php?t=82466](http://www.ubuntuforums.org/showthread.php?t=82466).

I have quoted his fix here:

> **vjshah]
[LIST=1]
[*]Use your install CD to boot into rescue mode (insert CD and type "rescue" at the Boot: prompt).
[*]mkdir /target said:**
> If you created separate boot and usr partitions, mount the partitions on /target/boot and /target/usr (you are recreating the required tree under /target). You don't need any other partitions.
[*]chroot /target (now it looks like you are in your installation).
[*]add cpqarray to /etc/modules (nano /etc/modules and add "cpqarray" as the last line).
[*]/usr/sbin/mkinitramfs -o /boot/initrd.img /lib/modules/2.6.12-9-686/ (this will build the new initrd.img in /boot).
[*]Cd to /boot and verify that you are happy (I just ensured the new img was larger than the old one). Then backup the old img and rename the new img to the same name as the old img (initrd.img-2.6.12-9-686 for me).
[*]Reboot. Everything went smoothly after that.
[/LIST]
Now, I should note that I did NOT follow the procedure blindly:

[LIST]
[*]My root partition was automatically mounted to /target during rescue boot; I think (hazy memory) that /boot was already available in /target/boot.
[*]I didn't bother with chroot;
[*]I modified the paths to account for the fact that I wasn't chroot'd;
[*]I used the command "echo cpqarray >> /target/etc/mkinitramfs/modules" instead of a text editor (nano).
[/LIST]Hope this helps!

---

### Post by DavidRa on 2006-05-20
Edit: Double-posted due to mouse problem

---

