---
title: "Ubuntu 7.10 Installation destroyed my RAID 0"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by Crafty_Shadow on 2008-01-28
When installing Ubuntu, I managed to destroy my RAID 0 array.
I have 3 hdds, each 250gb. My RAID array is composed of the first 2 in stripple mode. It contains multiple partitions, including my windows installation. This is a software RAID, based on the on-board RAID capabilities of my Gigabyte GA-965P-DS4. I decided to install Ubuntu on my third hard drive (listed as /dev/sdc). I created a 20GB partition for the installation, and a 1GB swap partition. Rest of the space is occupied by two NTFS partitions.

Before proceeding to installation, I noticed that a partition manager would be installed on hard drive listed as hd(0). I paused for a second, but then I thought that this probably does not refer to sda or sdb(my member(0) and member(1) hdds for the RAID array). I was wrong. When the installation completed, and my computer restarted, the on-board raid manager alerted me to the fact my first disk of the array has gone bad. ( To be precise, it was listed as a non-member, normal, unbootable hard drive, and my array 0 was listed as failed )

I immediately grasped the fact that the boot manager was written to it, thus corrupting the raid metadata. As I have virtually zero experience in Linux, I was in panic. However, I decided to do what I can. The Ubuntu installation wouldn't start (the Grub loader returned error 26 or something), but I still had the Ubuntu CD at my disposal.

After some reading, I understood my mistake was in not using dmraid to set up the raid before starting the installation. However I couldn't really do nothing about it now, so I turn to you: Please, do help me restore that array, and finish up the Ubuntu installation. I do not have the option of reformatting the array, because there is some really important information there. 

As the two disks used in the array are completely identical, I think this might be of help:

```
ubuntu@ubuntu:~$ sudo dmraid -n
/dev/sdb (isw):
0x000 sig: "  Intel Raid ISM Cfg Sig. 1.0.00"
0x020 check_sum: 3848202338
0x024 mpb_size: 480
0x028 family_num: 2058774226
0x02c generation_num: 1902
0x030 reserved[0]: 4080
0x034 reserved[1]: 3221225472
0x038 num_disks: 2
0x039 num_raid_devs: 1
0x03a fill[0]: 2
0x03b fill[1]: 0
0x0d8 disk[0].serial: "      6QE0M3LE:0"
0x0e8 disk[0].totalBlocks: 488395055
0x0ec disk[0].scsiId: 0xffffffff
0x0f0 disk[0].status: 0x2
0x108 disk[1].serial: "        6QE0L0VK"
0x118 disk[1].totalBlocks: 488397168
0x11c disk[1].scsiId: 0x10000
0x120 disk[1].status: 0x13a
0x138 isw_dev[0].volume: "            HDD0"
0x14c isw_dev[0].SizeHigh: 0
0x148 isw_dev[0].SizeLow: 976779264
0x150 isw_dev[0].status: 0xc
0x154 isw_dev[0].reserved_blocks: 0
0x158 isw_dev[0].filler[0]: 65536
0x190 isw_dev[0].vol.migr_state: 0
0x191 isw_dev[0].vol.migr_type: 0
0x192 isw_dev[0].vol.dirty: 0
0x193 isw_dev[0].vol.fill[0]: 0
0x1a8 isw_dev[0].vol.map.pba_of_lba0: 0
0x1ac isw_dev[0].vol.map.blocks_per_member: 488389891
0x1b0 isw_dev[0].vol.map.num_data_stripes: 1907772
0x1b4 isw_dev[0].vol.map.blocks_per_strip: 256
0x1b6 isw_dev[0].vol.map.map_state: 3
0x1b7 isw_dev[0].vol.map.raid_level: 0
0x1b8 isw_dev[0].vol.map.num_members: 2
0x1b9 isw_dev[0].vol.map.reserved[0]: 1
0x1ba isw_dev[0].vol.map.reserved[1]: 255
0x1bb isw_dev[0].vol.map.reserved[2]: 1
0x1d8 isw_dev[0].vol.map.disk_ord_tbl[0]: 0x1000000
0x1dc isw_dev[0].vol.map.disk_ord_tbl[1]: 0x1

```

---

### Post by imtheguru on 2008-01-28
I did a bit of research on softraids before assembling my 500GB (458GiB) x4 raid5.

> This is a software RAID, based on the on-board RAID capabilities of my Gigabyte GA-965P-DS4.Right, that's called fakeraid. And there's lots of documentation on why fakeraid does not work well with Linux. Here's one document from Ubuntu help: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

> I noticed that a partition manager would be installed on hard drive listed as hd(0).Linux, without dmraid, sees the hardware the way it really is and thus saw your disks as sd devices--this is well-documented in linux-raid usage. [[http://www.google.com/search?hl=en&q=ubuntu+raid&btnG=Search]](http://www.google.com/search?hl=en&q=ubuntu+raid&btnG=Search])
Grub uses the BSD nomenclature of hd for all drives in accordance with their listing in the bios--this is well-documented in grub. [[http://www.gnu.org/software/grub/manual/grub.html#Naming-convention]](http://www.gnu.org/software/grub/manual/grub.html#Naming-convention])

Though my knowledge in Linux raids is fairly new, i'd venture to say there's no Linux-based tool to assemble it back into working order. Perhaps look into a windows-based tool to recover the same.

Moreover, this is one of the major risks of using raid0. It is assembled mostly for speed, the bonus of artificially increasing the column bandwidth of read/write operations and significantly speeding up swap access. But, raid0 is not a reliability configuration and offers zero failover. If a single device fails, the raid fails and pre-emptive backups become essential.

Further, if you have reason to use raid, you should invest in a tape backup device and test your backups weekly/fortnightly. Or use lots of DVDs/Blurays.

Cheers.

---

### Post by Crafty_Shadow on 2008-01-28
I do not have back-ups of the information, this is why restoring this array is so important to me. I also do not have an Windows installation CD with me right now.
What I would like to try is recover the raid metadata to the first distk. I have extracted the data from the second one (using "dmraid -r /dev/sdb -D" ), but am not exactly sure how to insert it to the first disk.(Resulting files are sdb_isw.dat, sdb_isw.offset and sdb_isw.size) Any help would be deeply appreciated.
(I suspect that provided that I recover the basic functionality of the RAID array, I shall be able to overwrite it's MBR with Windows XP's boot loader, though I may have to use the windows installation to do that.)

PS Gonna get a couple of hours sleep, cause it's 6 am here;

EDIT:
Using the following:
```
sudo dd if=/dev/sda of=sdb_isw.dat skip=$[ `cat sdb_isw.offset` / 512 - 1 ] count=1
```
I restored the metadata to the harddisk. Still, neither the onboard raid controller, nor dmraid recognize the /dev/sda as a raid member disk. Please, do help!

---

### Post by Crafty_Shadow on 2008-01-29
Shameless bump!

---

