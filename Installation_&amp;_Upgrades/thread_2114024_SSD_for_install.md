---
title: "SSD for install"
date: 2013-02-08
forum: Installation &amp; Upgrades
---

### Post by mexjim on 2013-02-08
I'm considering buying an Acer M3-581T-6825.  It comes with a 20GB SSD and a 500GB HDD with W7 installed.  Has anyone installed Ubuntu on this config?  I'm thinking to install Ubuntu on the 20 GB SSD and my Home folder on the 500GB HDD.  I realize this would mean dumping W7 but that's okay.  I haven't used Windows for a few years anyway!

Another idea would be to partition the 500GB HDD and install ubuntu there.  Any thoughts?

---

### Post by papibe on 2013-02-08
Hi mexjim.

The increase performance and faster boot times would be so much better that I would say: go for it!

Something like this:
```
/     on SSD
/home on the 500GB HD
```
I imagine that Windows is installed on the SSD. If so, you could make a backup of it using Clonzilla or even gparted before wiping it out.

Just some thoughts.
Regards

---

### Post by darkod on 2013-02-09
If you want to dump windows it should be easy. In any case, you might consider making restore DVDs of win7 before deleting it so that in any time in the future you can restore to factory state if you wish to.

Also, note that the combination of hdd+ssd usually seems to come with Intel RST technology which is the disks in sort of a raid. You will probably need to go into bios and disable Intel RST, check the sata mode and change it from RAID to AHCI, then in ubuntu live mode first remove any meta data from the disks:
```
sudo dmraid -Er /dev/sda
sudo dmraid -Er /dev/sdb
```

After that you should be good to go and start the install. The disks should show as separate.

With Intel RST active and with meta data on them, this is not always the case.

---

### Post by oldfred on 2013-02-09
That is typical of Intel SRT systems.

Some users that have installed in SSD and others on Hard drive and turned Intel back on

       Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it. 
   > You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

