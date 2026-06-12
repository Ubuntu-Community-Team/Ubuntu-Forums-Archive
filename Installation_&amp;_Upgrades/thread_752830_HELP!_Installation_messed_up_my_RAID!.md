---
title: "HELP! Installation messed up my RAID!"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by YellowBullet on 2008-04-12
Hi guys,

I am in desperate need of some help here.

I have a desktop box with a Gigabyte P35 DS3R board and two Maxtor 500GB drives in RAID 0 configuration (controlled by the on-board RAID controller), and an external USB drive. The RAID array is my main disk I was booting Vista from. It had three partitions

So I decided to install Hardy Heron on the external USB, and like an idiot forgot to go into the advanced options, so the installation overwrote my MBR on the RAID array.

But that's not the worst thing. Now during the BIOS startup, the RAID controller reports that both Maxtor 500GB drives are "offline" and that no RAID arrays are defined. I can't boot into anything except a Live CD.

If I go into the BIOS RAID setup, the only option I have is to mark the disks as non-RAID, delete them, then create a new RAID array, but that would of course destroy all my data (which I am desperately trying to avoid).

Is there ANY way to restore my system? I was thinking maybe booting into a Live CD then forcing a software RAID 0 from the two Maxtor drives (if such a thing is even possible), then restoring the MBR and crossing my fingers that the board will recognize the RAID...

Anyone have an idea what to do?

Thanks a lot.

---

### Post by YellowBullet on 2008-04-12
I'm pretty sure this is what happened: the Hardy installer didn't recognize the RAID array, but treated the disks as just two independent disks. So it wrote the MBR only on the first one, messing up the RAID configuration. The RAID controller now detects that something's wrong and puts both disks off-line.

Is there any way to restore the MBR if the two disks were in RAID?

---

### Post by YellowBullet on 2008-04-12
Here are the dmraid outputs:

root@ubuntu:~# dmraid -r
/dev/sdb: isw, "isw_cjjiaeije", GROUP, ok, 976773166 sectors, data@ 0
/dev/sda: isw, "isw_bdcigcjceg", GROUP, ok, 976773166 sectors, data@ 0
root@ubuntu:~# dmraid -l
asr     : Adaptec HostRAID ASR (0,1,10)
ddf1    : SNIA DDF1 (0,1,4,5,linear)
hpt37x  : Highpoint HPT37X (S,0,1,10,01)
hpt45x  : Highpoint HPT45X (S,0,1,10)
isw     : Intel Software RAID (0,1)
jmicron : JMicron ATARAID (S,0,1)
lsi     : LSI Logic MegaRAID (0,1,10)
nvidia  : NVidia RAID (S,0,1,10,5)
pdc     : Promise FastTrack (S,0,1,10)
sil     : Silicon Image(tm) Medley(tm) (0,1,10)
via     : VIA Software RAID (S,0,1,10)
dos     : DOS partitions on SW RAIDs
root@ubuntu:~# dmraid -n
/dev/sdb (isw):
0x000 sig: "  Intel Raid ISM Cfg Sig. 1.0.00"
0x020 check_sum: 308305384
0x024 mpb_size: 480
0x028 family_num: 299804894
0x02c generation_num: 1301
0x030 reserved[0]: 4080
0x034 reserved[1]: 2147483648
0x038 num_disks: 2
0x039 num_raid_devs: 1
0x03a fill[0]: 2
0x03b fill[1]: 0
0x040 filler[1]: 299804894
0x0d8 disk[0].serial: "        9QG07KT6"
0x0e8 disk[0].totalBlocks: 976771055
0x0ec disk[0].scsiId: 0x20000
0x0f0 disk[0].status: 0x53a
0x108 disk[1].serial: "        9QG07LA9"
0x118 disk[1].totalBlocks: 976773168
0x11c disk[1].scsiId: 0x30000
0x120 disk[1].status: 0x53a
0x138 isw_dev[0].volume: "       SATARAID1"
0x14c isw_dev[0].SizeHigh: 0
0x148 isw_dev[0].SizeLow: 1953531904
0x150 isw_dev[0].status: 0xc
0x154 isw_dev[0].reserved_blocks: 0
0x158 isw_dev[0].filler[0]: 65536
0x190 isw_dev[0].vol.migr_state: 0
0x191 isw_dev[0].vol.migr_type: 0
0x192 isw_dev[0].vol.dirty: 0
0x193 isw_dev[0].vol.fill[0]: 255
0x1a8 isw_dev[0].vol.map.pba_of_lba0: 0
0x1ac isw_dev[0].vol.map.blocks_per_member: 976766216
0x1b0 isw_dev[0].vol.map.num_data_stripes: 3815492
0x1b4 isw_dev[0].vol.map.blocks_per_strip: 256
0x1b6 isw_dev[0].vol.map.map_state: 0
0x1b7 isw_dev[0].vol.map.raid_level: 0
0x1b8 isw_dev[0].vol.map.num_members: 2
0x1b9 isw_dev[0].vol.map.reserved[0]: 1
0x1ba isw_dev[0].vol.map.reserved[1]: 255
0x1bb isw_dev[0].vol.map.reserved[2]: 1
0x1d8 isw_dev[0].vol.map.disk_ord_tbl[0]: 0x0
0x1dc isw_dev[0].vol.map.disk_ord_tbl[1]: 0x1

/dev/sda (isw):
0x000 sig: "  Intel Raid ISM Cfg Sig. 1.0.00"
0x020 check_sum: 3187998070
0x024 mpb_size: 480
0x028 family_num: 1328629246
0x02c generation_num: 45
0x030 reserved[0]: 4080
0x034 reserved[1]: 3221225472
0x038 num_disks: 2
0x039 num_raid_devs: 1
0x03a fill[0]: 2
0x03b fill[1]: 0
0x040 filler[1]: 1328629246
0x0d8 disk[0].serial: "        9QG07LA9"
0x0e8 disk[0].totalBlocks: 976773168
0x0ec disk[0].scsiId: 0x30000
0x0f0 disk[0].status: 0x13a
0x108 disk[1].serial: "        9QG07KT6"
0x118 disk[1].totalBlocks: 976773168
0x11c disk[1].scsiId: 0x20000
0x120 disk[1].status: 0x13a
0x138 isw_dev[0].volume: "         Volume0"
0x14c isw_dev[0].SizeHigh: 0
0x148 isw_dev[0].SizeLow: 1953536000
0x150 isw_dev[0].status: 0xc
0x154 isw_dev[0].reserved_blocks: 0
0x158 isw_dev[0].filler[0]: 65536
0x190 isw_dev[0].vol.migr_state: 0
0x191 isw_dev[0].vol.migr_type: 0
0x192 isw_dev[0].vol.dirty: 0
0x193 isw_dev[0].vol.fill[0]: 0
0x1a8 isw_dev[0].vol.map.pba_of_lba0: 0
0x1ac isw_dev[0].vol.map.blocks_per_member: 976768264
0x1b0 isw_dev[0].vol.map.num_data_stripes: 3815500
0x1b4 isw_dev[0].vol.map.blocks_per_strip: 256
0x1b6 isw_dev[0].vol.map.map_state: 0
0x1b7 isw_dev[0].vol.map.raid_level: 0
0x1b8 isw_dev[0].vol.map.num_members: 2
0x1b9 isw_dev[0].vol.map.reserved[0]: 1
0x1ba isw_dev[0].vol.map.reserved[1]: 255
0x1bb isw_dev[0].vol.map.reserved[2]: 1
0x1d8 isw_dev[0].vol.map.disk_ord_tbl[0]: 0x0
0x1dc isw_dev[0].vol.map.disk_ord_tbl[1]: 0x1

root@ubuntu:~# dmraid -ay
ERROR: isw device for volume "SATARAID1" broken on /dev/sdb in RAID set "isw_cjjiaeije_SATARAID1"
ERROR: isw: wrong # of devices in RAID set "isw_cjjiaeije_SATARAID1" [1/2] on /dev/sdb
ERROR: isw device for volume "Volume0" broken on /dev/sda in RAID set "isw_bdcigcjceg_Volume0"
ERROR: isw: wrong # of devices in RAID set "isw_bdcigcjceg_Volume0" [1/2] on /dev/sda

---

