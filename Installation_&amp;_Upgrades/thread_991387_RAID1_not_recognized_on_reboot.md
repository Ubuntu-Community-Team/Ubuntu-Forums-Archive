---
title: "RAID1 not recognized on reboot"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by thadrolling on 2008-11-23
[FONT="Arial"][SIZE="2"]Hello - 

I am having a problem with my Raid-1 array and I am hoping I could find some help here.  I have two 205 GB disks and I am NOT using the array for boot.  I have gone through all the steps that (I believe) are needed, however, the array doesn't work when I reboot.  After reboot, if I type the two following commands, everything works like a charm.  So, my question is...what am I missing?

Here are the two commands that, once typed after reboot, everything is splendid:

```
sudo mdadm --assemble /dev/md0
sudo mount -t ext3 /dev/md0 /media/raid1/
```

The two disks that make up the array are SATA, 250 GB and /dev/sdb and /dev/sdc.

The contents of the critical files are as shown below.

/etc/mdadm/mdadm.conf:
```
DEVICE /dev/sdb1 /dev/sdc1

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes
# automatically tag new arrays as belonging to the local system
HOMEHOST <system>
# instruct the monitoring daemon where to send mail alerts
MAILADDR thad
# definitions of existing MD arrays   
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=8ac89895:88b5997c:a95107c4:8449513d

```

/etc/fstab
```
UUID=2e0d5642-5138-4fdc-838d-e67b7a287751 /               ext3    relatime,errors=remount-ro 0       1

# home
UUID=e5131f75-2114-4b30-8abb-f95bc739aeb0 /home           ext3    relatime        0       2

# swap
UUID=19b34c00-0112-4659-9873-96683d83bb96 none            swap    sw              0       0

# cdrom
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# 160 GB parallel IDE
UUID=0b88076e-bb76-402f-b4fa-e99b1f1c1bba    /media/160GB    ext3    defaults0    0

# RAID-1 (twin 250 GB HDDs)
/dev/md0    /media/raid1    ext3    defaults    0    0
```

Also, I am running Ubuntu 8.04, 32-bit version.

Any help is greatly appreciated!

Thanks, Thad[/FONT][/SIZE][/FONT]

---

### Post by pdwerryhouse on 2008-11-23
Have you set the partition types to "raid autodetect"? I think the type number is 'fd'

---

### Post by thadrolling on 2008-11-23
I believe so...that is done via fdisk, correct?  

The funny thing is, the RAID level 1 works great once mdadm is run and the mount command is issued.  Just not sure why it doesn't work upon reboot.

---

### Post by thadrolling on 2008-11-24
Ok....I did check the disks and they are type 'fd'.  Any additional ideas out there?  I am really stumped by this one and I could really use some ideas!

Thanks in advance.

---

### Post by pmdw on 2009-01-02
Hi

I am also having a problem with mdadm :(
Try this 
sudo mdadm --detail /dev/md0

And see what you get it may help isolate the problem.

Peter

---

