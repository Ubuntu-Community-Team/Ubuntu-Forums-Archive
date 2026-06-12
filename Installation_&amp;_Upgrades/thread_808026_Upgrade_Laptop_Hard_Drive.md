---
title: "Upgrade Laptop Hard Drive"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by linux-amt on 2008-05-26
I have Ubuntu 7.10 running great on my laptop with a 10GB drive. I now have a 30GB drive I want to install to replace the 10GB. I used Clonezilla and it copied all the files and the system worked great except it made the 30GB the same size as the 10GB and I can't access the remaining disk space. My question is number one, is there a way I can use Clonezilla and still access the extra disk space? Someone said something about using .tar files to upgrade but I can't find the instructions of how they said to do that. The only OS on the drive is Ubuntu.

Thanks in advance for any help....

---

### Post by joselin on 2008-05-26
Check with gparted if your partition have more than 10 Gb.

---

### Post by Barriehie on 2008-05-26
> **linux-amt said:**
> I have Ubuntu 7.10 running great on my laptop with a 10GB drive. I now have a 30GB drive I want to install to replace the 10GB. I used Clonezilla and it copied all the files and the system worked great except it made the 30GB the same size as the 10GB and I can't access the remaining disk space. My question is number one, is there a way I can use Clonezilla and still access the extra disk space? Someone said something about using .tar files to upgrade but I can't find the instructions of how they said to do that. The only OS on the drive is Ubuntu.

Thanks in advance for any help....

I just used gparted to shrink a partition and here's what happened.  After making a complete backup with this:

```
#!/bin/bash
tar cvpzf /home/barrie/disk/backup-files/bup$(date +%m%d%y).tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/home/barrie/disk --exclude=/var/spool/havp /
```I proceeded to boot from the gparted LiveCD and shrink the partition from 180 Gb to 100 Gb.  I figured this would take awhile and after 8 hours was beginning to freak out.  The keyboard was unresponsive and the HD light was randomly intermittent.  Having made a complete backup stored on another drive I went ahead and pulled the plug on the power.  My machine did reboot just fine and all is well so I can't tell you how long it might take or even if your results will be similar.  Major point being is **make a backup**

Barrie

---

