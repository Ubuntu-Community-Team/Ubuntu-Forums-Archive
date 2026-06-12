---
title: "[SOLVED] can't install ubuntu8.04.1 on new system"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by ticatfan on 2008-09-12
i have installed ubuntu on my old systems without problems in the past but my new system won't let me install.
mobo: asus p5q
hdd: 2 X 500GB seagate 7200
ram: 2 X 2GB kingston ddr2 800mhz 
vid: 256MB asus 8600gts pci-e

I have tried older versions of ubuntu and no luck. I can boot the live cd's but when i try to install it gets to the partitioner, scans 46% of my hard drives then stalls. the prepare partitions screen comes up but no partitions are listed so i can't get any further. i've tried system-> administration-> partition editor, it scans for a while then displays "no devices detected".
the BIOS sees the hard drives. I have even used win2k to set up a 30GB partition and installed win2k successfully, which is not what i wanted to do but at least i know it is possible to set up an O/S. any suggestions???

---

### Post by Pumalite on 2008-09-12
Did you do md5sum on the iso, burn at 4x or less, check for CD intregrity before install, not using CD-RW?

---

### Post by ticatfan on 2008-09-12
i did md5sum on ubuntu 7.1 which failed to install in the same manner. i tried to md5sum my 8.04.1 but can't get the md5sum from the web site, cdimage.ubuntu.com/releases/hardy/release, my md5sum for this disk was 5c8a8dd04a8284ad5ee60c642691c1fe for ubuntu-8.04.1-dvd-i386.iso. burned at 2.2x no cd-rw used for any ubuntu live disk. i have the gparted live disk and can see the hard drives with it. should i use the live disk to allocate the disks as /ext2??? any other ideas, i do know that i have got at least one good copy of ubuntu and have verified it and it will not install past the partitioner.

---

### Post by tinyviking on 2008-09-13
ensure your SATA configuration is set for AHCI rather than IDE or RAID.
I have the P5Q PRO board and had an issue where the second drive was not seen by Ubuntu at all!  messed with all BIOS settings and eventually got this working fine with 8.04.1 (64 bit).

---

### Post by ticatfan on 2008-09-13
thank you tinyviking...that was the solution...two days of head scratching. you have made me very happy...

---

### Post by jykke on 2008-09-16
I managed to install Vista64 and Ubuntu 8.04.1 with RAID option set on the P5Q Pro motherboard. 

I have two 500 gb harddrivers. And they make up for one Raid0 and one Raid1 disk as and Raid array. 

Here is a tutorial that I used: [http://hol.net.nz/blog/kubuntu-with-fakeraid](http://hol.net.nz/blog/kubuntu-with-fakeraid)

Before the part of sudo mount --bind /dev /target/dev you must mount the correct partition to target 

sudo mkdir /target
sudo mount -t ext3 /dev/mapper/via_hfciifae7 /target

Also before you can start the process you must have an usb stick or other means to install this LanDriver:

[http://ubuntuforums.org/showpost.php?p=5456722](http://ubuntuforums.org/showpost.php?p=5456722)

Also I had installed Vista first. And if you happend to break it's booting :) you can use the Vista installation DVD to correct this by using the repair options on the DVD.

---

