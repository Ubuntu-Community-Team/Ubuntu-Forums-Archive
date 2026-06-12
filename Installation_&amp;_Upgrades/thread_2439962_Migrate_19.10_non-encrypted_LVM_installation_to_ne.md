---
title: "Migrate 19.10 non-encrypted LVM installation to new disk"
date: 2020-04-03
forum: Installation &amp; Upgrades
---

### Post by 2lid8xh2o8 on 2020-04-03
I have a Ubuntu 19.10 installation that was upgraded from 19.04, which was installed to a PCI 3.0 NVMe SSD. The system was recently upgraded to a PCI 4.0 motherboard, so I would like to also upgrade to a PCI 4.0 NVMe SSD as well. I was wondering if anyone knew of a way to do this that wouldn't involve doing a complete re-install. 

This [SettingUpLVM-WithoutACleanInstall]("https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall") wiki page refers to Ubuntu 7.04, 8.04 (my first Ubuntu experience!!!), and 9.04. I can't tell if it's been updated in the past decade. I highly doubt it's still the same process today, but I suppose what I'm trying to do could be adapted to the "A new blank hard drive you've added to your system" use-case/requirement. It's just that I'm actually already on LVM, but the new drive doesn't care about that (does it?).

Here's my lvdisplay and pvdisplay output:

```

me@b450:~$ sudo lvdisplay
  /dev/sda: open failed: No medium found
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/root
  LV Name                root
  VG Name                ubuntu-vg
  LV UUID                uhW5C1-QFwM-m60n-Y08h-PUm3-Xg3o-LYQ8d2
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2019-07-24 07:59:47 -0400
  LV Status              available
  # open                 1
  LV Size                150.00 GiB
  Current LE             38400
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0
   
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/swap_1
  LV Name                swap_1
  VG Name                ubuntu-vg
  LV UUID                ExN1Lm-tZxw-wMSb-eHce-QVbJ-QJyu-dfUGMP
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2019-07-24 07:59:47 -0400
  LV Status              available
  # open                 2
  LV Size                10.00 GiB
  Current LE             2560
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:1
   
me@b450:~$ sudo pvdisplay
  /dev/sda: open failed: No medium found
  --- Physical volume ---
  PV Name               /dev/nvme0n1p2
  VG Name               ubuntu-vg
  PV Size               <953.37 GiB / not usable 0   
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              244062
  Free PE               203102
  Allocated PE          40960
  PV UUID               e2nA27-ofN3-BvTP-GvrL-nQfa-2j3W-n0CWta

```

---

### Post by TheFu on 2020-04-03
A fresh install is 15 minutes. The storage layout is unimportant.  i wouldn't waste much time on it.

Backup and restore the data to a fresh install [https://ubuntuforums.org/showthread.php?t=2436006&p=13928432#post13928432](https://ubuntuforums.org/showthread.php?t=2436006&p=13928432#post13928432)
Since you have LVM,  [https://ubuntuforums.org/showthread.php?t=2422831&p=13935233#post13935233](https://ubuntuforums.org/showthread.php?t=2422831&p=13935233#post13935233)

if you don't have a backup, seems that chances of wiping the data is much higher.  By using the restore process as part of your migration, you get to validate that your current backups actually capture what is needed to restore when it isn't an emergency or too stressful.

BTW, there are newer summary commands for LVM.
```
sudo pvs
sudo vgs
sudo lvs
lsblk -e 7 -o name,size,type,fstype,mountpoint
df -hT -x squashfs -x tmpfs -x devtmpfs
```

i would fix the current LV layout to be more organized.
[https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277) has an example.

---

### Post by 2lid8xh2o8 on 2020-04-04
> **TheFu said:**
> A fresh install is 15 minutes. The storage layout is unimportant.  i wouldn't waste much time on it.

Backup and restore the data to a fresh install [https://ubuntuforums.org/showthread.php?t=2436006&p=13928432#post13928432](https://ubuntuforums.org/showthread.php?t=2436006&p=13928432#post13928432)
Since you have LVM,  [https://ubuntuforums.org/showthread.php?t=2422831&p=13935233#post13935233](https://ubuntuforums.org/showthread.php?t=2422831&p=13935233#post13935233)

if you don't have a backup, seems that chances of wiping the data is much higher.  By using the restore process as part of your migration, you get to validate that your current backups actually capture what is needed to restore when it isn't an emergency or too stressful.

BTW, there are newer summary commands for LVM.
```
sudo pvs
sudo vgs
sudo lvs
lsblk -e 7 -o name,size,type,fstype,mountpoint
df -hT -x squashfs -x tmpfs -x devtmpfs
```

i would fix the current LV layout to be more organized.
[https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277) has an example.

Thank you for the thorough response!

Along with packgages installed with apt, there's Nix packages, Guix packages, Flatpack packages, Snap packages, and a lot of Steam games. The backup-restore methodology would be more complex with all of these. This is why I'd prefer to just copy the logical volume to the new drive. Could I do a fresh LVM install on the new drive, and then just overwrite the root logical volume with my old one? I wonder if there is a way to do that - it looks like your 2nd link is pretty close.

You've given me a fair bit to mull over, and made a great point about backup testing before an emergency.

---

### Post by TheFu on 2020-04-04
You'll need to export the LVM metadata and import the LVM metadata.
Or you could use pvmove.  
Or you could setup an LVM mirror between the disks, give it time to sync, then break the LVM mirror leaving the data on the new disk.

I would not "> just overwrite the root logical volume with my old one?"  Seems like asking for problems.

Snap packages have a "list" method.  I don't use any of the either methods.  I do have some manually built stuff that is placed in /usr/local/ - but I back that up just like normal data, so when it gets restored, it is there with the correct owner, group, permissions, ACLs and files, in the correct location of new storage.

You're the admin. You should backup the stuff however you feel is best BEFORE attempting this stuff.  I've used pvmove, but not with an OS.  I've not used the LVM mirror technique.

IF you choose to use any LVM technique, be certain to review the manpage for each command carefully.  LVM stuff can't be "winged" to see how it goes, unless you seek disappointment.

IF it were me, I'd use the LV mirror method, assuming a backup/restore was too scary.  You'll still have to handle grub and boot stuff manually.

---

