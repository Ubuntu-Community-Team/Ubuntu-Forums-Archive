---
title: "fresh install 16.04, zfs not automounting. fstab?"
date: 2016-06-14
forum: Installation &amp; Upgrades
---

### Post by treykuhl on 2016-06-14
just started using ubuntu recently...dabbled in past but kept reverting to windows. now im here to stay.

From some other post some folks seem to indicate zfs should automount. ive done a fresh install of 16.04 server and created a new zfs raidz2 pool and after boot it will not mount. i have to zpool import poolname at any boot up.

i tried doing what this thread recommended, with no luck. [http://askubuntu.com/questions/768179/zfs-pools-not-mounted-16-04](http://askubuntu.com/questions/768179/zfs-pools-not-mounted-16-04) 

do we just add these mounts in fstab?

---

### Post by lukeiamyourfather on 2016-06-15
Don't use /etc/fstab, ZFS should be mounting the pools automatically. Where are you looking for them? By default they mount to /poolname on the root. In the past when pools haven't automatically mounted in my experience it's because the hostid isn't set (which it's supposed to do automatically) so ZFS thinks the pools are from another system and skips them.

---

### Post by treykuhl on 2016-06-15
I didnt think i should use fstab as it mounts at boot and the zfs service wont start with systemd till afterwards.

I did a fresh install of base server package only, then i install openssh server and the gui with no recommends, then did a update and reboot after settings my ip with nmcli and hostname, etc. 

The i did the install of zfsutils-linux and let it install the dependencies it required. I have a zpool i brought over and then i have some extra drives I tested with first. i created my new zpool and after playing a bit i imported the other from freenas. after reboot neither were available from /poolname. If i run a zpool list get nothing, zpool status nothing. if i run zpool import it list both and then i obviously need to rerun with the poolname/id. i can do that and it works fine but at reboot i suffer the same symptoms again. I even migrated all my data off my old zpool from freenas and destroyed it and recreated new and rebooted again to see if something lingered there to no avail.

i also tried to uninstall zfsutils-linux and zfs-doc and reinstall without luck.


this guide is good but it fails to mention anything about mounts, etc. [https://wiki.ubuntu.com/Kernel/Reference/ZFS](https://wiki.ubuntu.com/Kernel/Reference/ZFS)

but then i found with systemctl status some issue from reboot yesterday on zfs-import-cache.service

So right now i have 3 pools. I can reboot and then 

root@userver:/home/tp# zpool list
no pools available

root@userver:/home/tp# systemctl -l status zfs*
&#9679; zfs-import-cache.service - Import ZFS pools by cache file
   Loaded: loaded (/lib/systemd/system/zfs-import-cache.service; static; vendor preset: enabled)
   Active: failed (Result: exit-code) since Wed 2016-06-15 19:57:13 EDT; 2min 32s ago
  Process: 1275 ExecStart=/sbin/zpool import -c /etc/zfs/zpool.cache -aN (code=exited, status=1/FAILURE)
  Process: 1176 ExecStartPre=/sbin/modprobe zfs (code=exited, status=0/SUCCESS)
 Main PID: 1275 (code=exited, status=1/FAILURE)


Jun 15 19:57:13 userver.home.local systemd[1]: Starting Import ZFS pools by cache file...
Jun 15 19:57:13 userver.home.local zpool[1275]: cannot import 'seatank15': one or more devices is currently unava
Jun 15 19:57:13 userver.home.local zpool[1275]: cannot import 'seatank2': no such pool or dataset
Jun 15 19:57:13 userver.home.local zpool[1275]: cannot import 'seatank6': invalid vdev configuration
Jun 15 19:57:13 userver.home.local zpool[1275]:         Destroy and re-create the pool from
Jun 15 19:57:13 userver.home.local zpool[1275]:         a backup source.
Jun 15 19:57:13 userver.home.local systemd[1]: zfs-import-cache.service: Main process exited, code=exited, status
Jun 15 19:57:13 userver.home.local systemd[1]: Failed to start Import ZFS pools by cache file.
Jun 15 19:57:13 userver.home.local systemd[1]: zfs-import-cache.service: Unit entered failed state.
Jun 15 19:57:13 userver.home.local. systemd[1]: zfs-import-cache.service: Failed with result 'exit-code'.

Which makes no sense. I created all zpools directly on this machine now, so its "native" to whatever zfs structure/version ubuntu uses.

I can do a zpool import <poolnames> and all mount ok then. 

zpool list
NAME        SIZE  ALLOC   FREE  EXPANDSZ   FRAG    CAP  DEDUP  HEALTH  ALTROOT
seatank15  1.36T  1.20T   167G         -    68%    87%  1.00x  ONLINE  -
seatank2   9.06T  1.86T  7.20T         -    10%    20%  1.00x  ONLINE  -
seatank6     38T  10.6T  27.4T         -    15%    27%  1.00x  ONLINE  -





if i journalctl -xe | grep zfs i do see some odd errors...its as if the system if referring to the same disk under different names. to be clear, im using onboard sata ports plus a common 9211-8i 2008 LSI sas card 

systemd[1]: dev-disk-by\x2dpartlabel-zfs.device: Dev dev-disk-by\x2dpartlabel-zfs.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/host11/port-11:0/end_device-11:0/target11:0:0/11:0:0:0/block/sdi/sdi1 and /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/host11/port-11:6/end_device-11:6/target11:0:6/11:0:6:0/block/sdo/sdo1

systemd[1]: dev-disk-by\x2dpartlabel-zfs.device: Dev dev-disk-by\x2dpartlabel-zfs.device appeared twice with different sysfs paths /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/host11/port-11:0/end_device-11:0/target11:0:0/11:0:0:0/block/sdi/sdi1 and /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/host11/port-11:2/end_device-11:2/target11:0:2/11:0:2:0/block/sdk/sdk1

and this goes on for several disks

The only thing i can think at this point, is to try and create the zpools with disk UUIDs which should not change. maybe its something hinky with this motherboard sata ports and also the hba re-enumerating the dev paths?

---

### Post by lukeiamyourfather on 2016-06-16
> **treykuhl said:**
> The only thing i can think at this point, is to try and create the zpools with disk UUIDs which should not change. maybe its something hinky with this motherboard sata ports and also the hba re-enumerating the dev paths?

You can export the pool and then just import it again and specify how you'd like to define the paths. An example command is below (tank being the name of the pool).

```
sudo zpool import -d /dev/disk/by-id tank
```

---

### Post by justanotherjoe on 2016-07-31
did you get it to work? Im having a similar issue, I did a clean wipe to install 16.04 and am unable to import the volume.

```
sudo blkid/dev/sda1: UUID="158bb72a-02b2-4b3c-92c9-3ac6669d0d7c" TYPE="ext4" PARTUUID="86babc10-01"
/dev/sda5: UUID="5eadf4a8-9752-4e51-8976-a36fc93f47cf" TYPE="swap" PARTUUID="86babc10-05"
/dev/sdb2: LABEL="storage" UUID="18109451249176055876" UUID_SUB="12924680566677043356" TYPE="zfs_member" PARTUUID="b900d4da-7330-11e3-93a4-00270e29510e"
/dev/sdb1: PARTUUID="b8f1fb93-7330-11e3-93a4-00270e29510e"



```

it sees the drive but
```
sudo zfs listno datasets available



```

---

### Post by treykuhl on 2016-08-01
darth vader had the proper directions with > [COLOR=#000000][FONT=&quot]sudo zpool import -d /dev/disk/by-id tank[/FONT][/COLOR] but your issue seems a bit different. I could import fine, it just would not auto-remount at reboot. 

there were other threads i found regarding not being able to mount you probably want to look at. assuming you exported from the old OS (and for others to help the exact details of old OS 14? and what the zfs version may be helpful) you would need to first import the new set it may not just "show up" as your clean install doesnt have any knowledge of the zfs array. if you zpool import does it import?

looks like a single disk zfs?

---

