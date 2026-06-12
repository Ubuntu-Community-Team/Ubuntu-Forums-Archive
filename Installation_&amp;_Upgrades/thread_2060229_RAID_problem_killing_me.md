---
title: "RAID problem killing me"
date: 2012-09-19
forum: Installation &amp; Upgrades
---

### Post by MorneDJ on 2012-09-19
I recently bought 2x HP 40L microservers to assist as NAS for my house and at the office. After some reading I selected Ubuntu server (older version) as the way forward. I fitted each out with the same ram (2x 4GB EEC each) as well as the same HDDs (4x Seagate 2TB drives). The servers will boot from a 8 GB Kingston flashdrive.

I installed from a CD rom, but after the installation the idea was to remove the CDrom as the PC's will not require one. I followed the how-to as found on: [http://www.studiob.co.za/setupnas.html]("http://www.studiob.co.za/setupnas.html")

The first server worked like a charm, and is currently doing service as a backup NAS at my office. I use 3 of the drives in RAID5 with the 4th drive as a hot spare. It has been working silently and brilliantly for a week.

I have however been unable to setup the RAID on the other machine. At first it did not show the Linux RAID under Hardware, so after trying a few hints from other websites, I reinstalled. Same problem. Needless to say, I followed the procedure I used with the first PC exactly. Again no Linux RAID under Hardware (in Webmin).

With the third install I just left the harddrives connected to the PC and manually pointed to the flashdrive. After the install and after setting up webmin, I was granted with Linux RAID under hardware.

However, no matter what I do I cannot mount it. I have read about every page in this regard I could find, tried it. Nothing. I created directory /NAS, but when I try to mount it I get the following error:
```
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
whatever that may mean.
```
> dmesg | tail
[40224.585852]  disk 2, o:1, dev:sdc1
[40224.585856]  disk 3, o:1, dev:sdd1
[40224.585912] md0: detected capacity change from 0 to 6001193189376
[40224.588835]  md0:
[40224.588845] md: resync of RAID array md0
[40224.588854] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[40224.588912] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
[40224.588925] md: using 128k window, over a total of 1953513408 blocks.
[40224.598473]  unknown partition table
[40256.836868] EXT2-fs (md0): error: can't find an ext2 filesystem on dev md0.
```
I followed the instructions exactly, and I am sure that I am selecting the ext3 file system. 
hhhmmm ... perhaps I have solved this myself. Lemme try mkfs ext3 /dev/md0 ...

---

### Post by darkod on 2012-09-19
Webmin?

How about creating the raid array with the installer during the install?

---

