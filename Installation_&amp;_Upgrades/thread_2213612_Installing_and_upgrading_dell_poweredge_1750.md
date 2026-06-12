---
title: "Installing and upgrading dell poweredge 1750"
date: 2014-03-27
forum: Installation &amp; Upgrades
---

### Post by tuxfr34k on 2014-03-27
I have taken on a new project.  The project is to move my existing xubuntu btsync server to a dell poweredge 1750.  The problem is the hard drive space on the poweredge is very small amount 20GB for the operating system drive and 50GB for the applications and storage drive.  I would like to upgrade to a couple terabytes for the storage amount.  I started looking for upgrades on the drives online and boy are they pricey. I mainly wanted to move it over to the server because right now it sits on an optiplex 320 dell 2GBS memory 80GB internal drive and a 1.5TB external drive.  also don't really want to have to setup everybody all over again on the btsync is there a way I can move the install over saving all settings and config?  I guess I can just retain the external drive I am using and hook it to the server to keep the backups going to that for now.  Thanks in advance for anybody that can help.

---

### Post by tgalati4 on 2014-03-27
Find a 1/2 height SATA card that will fit inside the 1750 case and use cheaper SATA drives.  You could simply *cp* the existing drive to the new drive and use gparted to partition the existing space.  I get a lot of grief for this but it works:

```
sudo cp /dev/sda /dev/sdg
```

Then use *gparted* to fix the partition boundary and repartition the extra space.  You will have to make changes to your /etc/fstab to correct the UUID using *blkid* and change GRUB so it boots the correct drive, but it generally works.  This will save all of your configuration and basically act as a mirror of your existing installation--magic!

---

