---
title: "Ubuntu 20.04 clean install fails with grub error"
date: 2020-04-23
forum: Installation &amp; Upgrades
---

### Post by djerkg on 2020-04-23
I'm trying to install Ubuntu 20.04 on a system with 2x SSD and one HDD. I'd like to **raid0** the OS, swap and cache for the HDD. Thus efi is native on gpt 1st partition, root and home etc are all on LVM. I guess it is likely the raid that's causing grub issues. But I can't figure out how to resolve the issue. I'm not using encryption and this setup worked fine in a Ubuntu 18.04 VM easlier this week.

Error halting installation:
```
Executing 'glub-install /dev/sda' failed. This is a fatal error.
```

**/var/log/syslog** (filtered)
ubuntu ubiquity: grub-probe: error: disk `lvmid/16fyZ7-hrJe-UuEX-F0qj-dO3V-lGXO-T5cA3z/xahMGS-mUuh-nLwp-d0cN-Rdyd-fjlW-AySH7n' not found.
ubuntu ubiquity: grub-probe: error: disk `lvmid/16fyZ7-hrJe-UuEX-F0qj-dO3V-lGXO-T5cA3z/xahMGS-mUuh-nLwp-d0cN-Rdyd-fjlW-AySH7n' not found.
ubuntu ubiquity: /usr/sbin/grub-probe: error: disk `lvmid/16fyZ7-hrJe-UuEX-F0qj-dO3V-lGXO-T5cA3z/xahMGS-mUuh-nLwp-d0cN-Rdyd-fjlW-AySH7n' not found.
ubuntu ubiquity: message repeated 2 times: [ /usr/sbin/grub-probe: error: disk `lvmid/16fyZ7-hrJe-UuEX-F0qj-dO3V-lGXO-T5cA3z/xahMGS-mUuh-nLwp-d0cN-Rdyd-fjlW-AySH7n' not found.]
ubuntu grub-installer: grub-install: error: disk `lvmid/16fyZ7-hrJe-UuEX-F0qj-dO3V-lGXO-T5cA3z/xahMGS-mUuh-nLwp-d0cN-Rdyd-fjlW-AySH7n' not found.
ubuntu grub-installer: error: Running 'grub-install  --force "/dev/sdb"' failed.

**Manual disk layout**
/dev/sda1 efi (autodetected as efi during install)
/dev/sda2 lvm pv
/dev/sdb1 efi (autodetected as efi during install)
/dev/sdb2 lvm pv
/dev/sdc lvm pv

/vg_ml1/lv_root - raid0 on sda2 sdb2 (set as ext4 / during install)
/vg_ml1/lv_swap - raid0 on sda2 sdb2 (autodetected as swap during install)
/vg_ml1/lv_cache - raid0 on sda2 sdb2 (cache for lv_home)
/vg_ml1/lv_home_ssd  - raid1 on sda2 sdb2 (unassigned during install)
/vg_ml1/lv_home - 100% of sdc (set as /home during install)

**blkid** (removed live cd items)
```
root@ubuntu:/# blkid | grep -v loop
/dev/sda1: LABEL_FATBOOT="EFI_0" LABEL="EFI_0" UUID="B2A0-A1AA" TYPE="vfat" PARTLABEL="EFI" PARTUUID="b1aa1788-b3b6-431c-ae89-b3ce50d736ee"
/dev/sdb1: LABEL_FATBOOT="EFI_1" LABEL="EFI_1" UUID="8C4A-CFD3" TYPE="vfat" PARTLABEL="EFI" PARTUUID="9d63359b-1165-4323-b7b4-804a69367d30"
/dev/sda2: UUID="eEfA9v-wQ1a-sBQ3-5t4x-oS33-h0zQ-kECQ0n" TYPE="LVM2_member" PARTUUID="a3f54acd-e8ac-4d06-8dc1-c311fcae2969"
/dev/sdb2: UUID="jvoDwD-grcT-BqIL-YFLY-GBJJ-eRdC-Cr9805" TYPE="LVM2_member" PARTUUID="4973df34-e312-4429-b743-e9aaf4a028c4"
/dev/sdc: UUID="vBNV2M-yA22-dpY4-6hFT-a7rF-CibM-OY66q2" TYPE="LVM2_member"
/dev/mapper/vg_ml1-lv_home: UUID="fb6c2b91-b6d2-4ee1-b59e-5f40428b5a13" TYPE="ext4"
/dev/mapper/vg_ml1-lv_root: UUID="355b3cc1-82e9-4986-88ed-71c450aff185" TYPE="ext4"
/dev/mapper/vg_ml1-lv_root_rimage_0: UUID="355b3cc1-82e9-4986-88ed-71c450aff185" TYPE="ext4"

```

**LVM**
```
root@ubuntu:/# pvs
  PV         VG     Fmt  Attr PSize    PFree 
  /dev/sda2  vg_ml1 lvm2 a--  <465.26g  7.16g
  /dev/sdb2  vg_ml1 lvm2 a--  <476.44g 18.40g
  /dev/sdc   vg_ml1 lvm2 a--   931.51g     0 
root@ubuntu:/# vgs
  VG     #PV #LV #SN Attr   VSize  VFree 
  vg_ml1   3   4   0 wz--n- <1.83t 25.56g
root@ubuntu:/# lvs
  LV          VG     Attr       LSize   Pool             Origin          Data%  Meta%  Move Log Cpy%Sync Convert
  lv_home     vg_ml1 Cwi-aoC--- 931.51g [lv_cache_cpool] [lv_home_corig] 29.06  9.68            0.00            
  lv_home_ssd vg_ml1 Rwi-a-r--- 360.00g                                                         100.00          
  lv_root     vg_ml1 rwi-aor--- 100.00g                                                                         
  lv_swap     vg_ml1 rwi---r---  32.00g

```

Root VG/LV details
```
root@ubuntu:/# vgdisplay 
  --- Volume group ---
  VG Name               vg_ml1
  System ID             
  Format                lvm2
  Metadata Areas        3
  Metadata Sequence No  11
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                4
  Open LV               2
  Max PV                0
  Cur PV                3
  Act PV                3
  VG Size               <1.83 TiB
  PE Size               4.00 MiB
  Total PE              479541
  Alloc PE / Size       472997 / 1.80 TiB
  Free  PE / Size       6544 / 25.56 GiB
  VG UUID               16fyZ7-hrJe-UuEX-F0qj-dO3V-lGXO-T5cA3z
   
root@ubuntu:/# lvdisplay 
  --- Logical volume ---
  LV Path                /dev/vg_ml1/lv_swap
  LV Name                lv_swap
  VG Name                vg_ml1
  LV UUID                TkmuqW-aXrR-vFHv-PybY-WO0z-E8JF-jlgBJF
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2020-04-23 21:28:41 +0100
  LV Status              NOT available
  LV Size                32.00 GiB
  Current LE             8192
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
   
  --- Logical volume ---
  LV Path                /dev/vg_ml1/lv_root
  LV Name                lv_root
  VG Name                vg_ml1
  LV UUID                xahMGS-mUuh-nLwp-d0cN-Rdyd-fjlW-AySH7n
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2020-04-23 21:32:37 +0100
  LV Status              available
  # open                 1
  LV Size                100.00 GiB
  Current LE             25600
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:7

```

**update-grub** from /target chroot
```
root@ubuntu:/# update-grub2 
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
grub-probe: error: disk `lvmid/16fyZ7-hrJe-UuEX-F0qj-dO3V-lGXO-T5cA3z/xahMGS-mUuh-nLwp-d0cN-Rdyd-fjlW-AySH7n' not found.
grub-probe: error: disk `lvmid/16fyZ7-hrJe-UuEX-F0qj-dO3V-lGXO-T5cA3z/xahMGS-mUuh-nLwp-d0cN-Rdyd-fjlW-AySH7n' not found.
Found linux image: /boot/vmlinuz-5.4.0-26-generic
Found initrd image: /boot/initrd.img-5.4.0-26-generic
/usr/sbin/grub-probe: error: disk `lvmid/16fyZ7-hrJe-UuEX-F0qj-dO3V-lGXO-T5cA3z/xahMGS-mUuh-nLwp-d0cN-Rdyd-fjlW-AySH7n' not found.
/usr/sbin/grub-probe: error: disk `lvmid/16fyZ7-hrJe-UuEX-F0qj-dO3V-lGXO-T5cA3z/xahMGS-mUuh-nLwp-d0cN-Rdyd-fjlW-AySH7n' not found.
/usr/sbin/grub-probe: error: disk `lvmid/16fyZ7-hrJe-UuEX-F0qj-dO3V-lGXO-T5cA3z/xahMGS-mUuh-nLwp-d0cN-Rdyd-fjlW-AySH7n' not found.
Adding boot menu entry for UEFI Firmware Settings
done

```

grub-probe doesn't seem to be raid aware:
```
root@ubuntu:/# grub-probe --device /dev/sda1
fat
root@ubuntu:/# grub-probe --device /dev/sda
grub-probe: error: unknown filesystem.
root@ubuntu:/# grub-probe --device /dev/mapper/vg_ml1-lv_home
grub-probe: error: disk `lvmid/16fyZ7-hrJe-UuEX-F0qj-dO3V-lGXO-T5cA3z/wQ7o4e-cGat-F4xQ-6tyv-jX5H-uyBO-q2XSNX' not found.
root@ubuntu:/# grub-probe --device /dev/mapper/vg_ml1-lv_root
grub-probe: error: disk `lvmid/16fyZ7-hrJe-UuEX-F0qj-dO3V-lGXO-T5cA3z/xahMGS-mUuh-nLwp-d0cN-Rdyd-fjlW-AySH7n' not found.
root@ubuntu:/# grub-probe --device /dev/mapper/vg_ml1-lv_root_rimage_0
ext2

```

rimage_0 refers to an element of the raid.

---

### Post by djerkg on 2020-04-24
I removed lv_root and recreated it as a standard LV, same size using space from both sda2 and sdb2. Installation succeeds without issue. Is grub just incompatible with raid0 on LVM?

---

### Post by dino99 on 2020-04-24
Related threads
[https://askubuntu.com/questions/43036/how-do-i-install-grub-on-a-raid-system-installation](https://askubuntu.com/questions/43036/how-do-i-install-grub-on-a-raid-system-installation)
[https://gist.github.com/umpirsky/6ee1f870e759815333c8](https://gist.github.com/umpirsky/6ee1f870e759815333c8) (old)

---

### Post by djerkg on 2020-04-24
The advice to use a bios boot area. I thought this wasn't needed when using GPT. Should this bios boot area reside outside of LVM and how is this different to installing grub to /dev/sda or why not put grub on the efi partition?

The old link is about mdadm. I'm using dm_raid which is part of (or used by) lvm.

---

### Post by CelticWarrior on 2020-04-24
> **djerkg said:**
> The advice to use a bios boot area. I thought this wasn't needed when using GPT. Should this bios boot area reside outside of LVM and how is this different to installing grub to /dev/sda or why not put grub on the efi partition?

The old link is about mdadm. I'm using dm_raid which is part of (or used by) lvm.

The "bios_grub" partition is for GPT drives when installing in BIOS/Legacy/CSM mode, something you DON'T want if installing in a modern machine, in UEFI mode, as it should be. All you need is the ESP (EFI System Partition).

There's a lot of bad advice still floating around and sadly promoted by people who should know better.

---

### Post by djerkg on 2020-04-24
That's what I figured. The key seems to be that grub-probe can't find find a raid0 lvm logical volume. The path exists but grub just can't see it. It throws an "grub-probe: error: disk 'lvmid/<vg-uuid>/<lv-uuid>' not found."

If I can fix this, then all should start working. I wonder if I need to load a dm_raid module during installation. However booting from a live disk, chroot and editing /etc/initramfs-tools/modules to add those modules doesn't fix anything. Editing /etc/default/grub to add GRUB_PRELOAD_MODULES with raid0, raid1 and dm_raid doesn't make any difference either.

---

### Post by djerkg on 2020-04-24
As a side note. raid0 for swap appears to be overkill as the OS stripes between two partitions by default.

---

### Post by djerkg on 2020-04-24
I've simplified things to the point of just sda1 and sdb1 being efi partitions and a single lv for /. If this lv is raid0 then things break. Even if I add an lv for /boot as raid1.

So the next thing to try is to create lv_root as raid1 instead of raid0. I noticed that at one point between live USB boots when I landed in grub> that ls showed only the raid1 volumes and none of the raid0 ones. A different error this time about apt, a warning about potential broken packages, but the system boots just fine.

---

