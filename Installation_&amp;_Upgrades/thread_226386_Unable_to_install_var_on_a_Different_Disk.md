---
title: "Unable to install /var on a Different Disk"
date: 2006-07-31
forum: Installation &amp; Upgrades
---

### Post by igb on 2006-07-31
I have been trying to install Dapper on my server, which previously had Breezy. This is a clean install from scratch. The setup, which worked fine on both Hoary and Breezy is:

hda 160 GByte /
hdc and hdd configured as software RAID 1 as /dev/md0 and mounted as /var

Initially I installed the whole system on hda then did:

```

init 1
mv /var /var.old
mount -t ext3 /dev/md0 /mirror
cp -a /var.old/* /mirror/
mkdir /var
```

Edit fstab to mount /dev/md0 on /var and reboot.

In Dapper during boot I get errors like:

mkdir cannot create /var/run/network
mount special device /var/run does not exist

The system boots eventually, but mysql won't start as it can't create a socket in /var/run/mysql.

I have repeated the whole procedure using Breezy, to check my procedure for errors, and I can mount /var on /dev/md0 with no problems.

My guess is that the kernel shipped with Dapper wants to access /var before the RAID device is mounted.

Anyone got any ideas?

Ian.

---

### Post by gr83 on 2006-08-03
[https://launchpad.net/distros/ubuntu/+source/initscripts/+bug/51452](https://launchpad.net/distros/ubuntu/+source/initscripts/+bug/51452)

---

### Post by igb on 2006-08-04
Thanks. So, it looks as though creating /var/run and /var/lock manually should fix the problem. I'll report back when I have tried it out.

Ian.

---

