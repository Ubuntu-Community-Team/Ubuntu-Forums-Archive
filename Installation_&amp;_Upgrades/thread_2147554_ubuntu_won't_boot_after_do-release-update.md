---
title: "ubuntu won't boot after do-release-update"
date: 2013-05-22
forum: Installation &amp; Upgrades
---

### Post by crott on 2013-05-22
Hi,

Yesterday I did do-release-update. I had (I'm not sure but it was old) probably 10.04 version. It was server edition + LXDE.
When I done update my server woudln't run, stopped during boot with prompt (initramfs) and something like this:
```
Gave up waiting for root device. Common problems:
[...]
```

I looked up for solutions and I did pruged and reinstalled grub2 with this:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Right now I don't have any more information "Gave up waiting for root device. Common problems:" just (initramfs) show's. That's all. 
I'm afraid to do anything more not to broke it completly. 

I have only Ubuntu at this computer (no windows, no other OSes).
At this computer I have RAID, other HDDs are not important (it's flash with live CD, one HDD for data (sdc1).

Additiona information got with live cd:
```
root@xubuntu:/# sudo dmraid -ay
sudo: unable to resolve host xubuntu
ERROR: ddf1: seeking device "/dev/dm-2" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-2" to 4608
ERROR: hpt45x: seeking device "/dev/dm-2" to 18446744073709547008
ERROR: isw: seeking device "/dev/dm-2" to 18446744073708469760
ERROR: sil: seeking device "/dev/dm-2" to 18446744073709289984
RAID set "pdc_dcdfffiee" already active
RAID set "pdc_dcdfffiee1" already active
RAID set "pdc_dcdfffiee5" already active
```

```
root@xubuntu:/# blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda: TYPE="promise_fasttrack_raid_member" 
/dev/sdb: TYPE="promise_fasttrack_raid_member" 
/dev/sdc1: LABEL="Nowy" UUID="16C8F5B5C8F592EB" TYPE="ntfs" 
/dev/mapper/pdc_dcdfffiee1: UUID="eafd999b-77bc-4b3f-9bb1-34e2a4cf9a4c" TYPE="ext4" 
/dev/mapper/pdc_dcdfffiee5: UUID="4db251b2-7035-4331-a6da-126c86c2db83" TYPE="swap" 
/dev/sdd1: LABEL="SPEEDY" UUID="72EF-D6BF" TYPE="vfat"
```

---

### Post by crott on 2013-05-22
When I'm in (initramfs) and do blkid I got:
```
/dev/sdb: TYPE="promise_fastttrack_raid_member"
/dev/sdc1: LABEL="Nowy" UUID="16C8F5B5C8F592EB" TYPE="ntfs"
/dev/sda: TYPE="promise_fasttrack_raid_member"
```

/dev/sdc1 is other disk, not important. Main is RAID.

---

### Post by crott on 2013-05-23
Bump.
Anyone?

---

