---
title: "Clean Install - Slow Boot"
date: 2016-12-01
forum: Installation &amp; Upgrades
---

### Post by josiahlund on 2016-12-01
Hey guys,

I'm new to Ubuntu/Linux. I've got a computer with a 250 GB drive (sda) running Windows 10, and a 120 GB drive (sdb) that I have installed 16.04.1 on. I set up with a 104 GB Ext4 partition for my root directory and a 16 GB swap. Boot loaders are installed on the 120 GB drive. I'm pretty happy with the everything except the 90+ second boot time. I have seen multiple posts on this and have chased down every lead I could understand, but I still can't figure it out.

dmesg:

[   3.555992 ] random: nonblocking pool is initialized
[ 91.385626 ] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)

Any help would be greatly appreciated!

Thanks

---

### Post by oldfred on 2016-12-01
What brand/model system? Some need boot parameters.
What model video card/chip? Not having correct driver can make a difference.

Even with new install have you tried fsck on your ext4 partition sdb1?
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by alexjpowell on 2016-12-02
This might be working as expected
How fast does windows boot?

---

### Post by josiahlund on 2016-12-02
Boot time for windows is about 5 seconds.

The  system is a computer that I build myself. I am currently running off  the motherboard graphics slot as I am still waiting for my GPU to be  returned to me (died and had to RMA). I listed the GPU that I will have,  but it is not currently installed. I also listed a 2 TB HDD that I have  installed that seems to be functioning as I would expect.

Intel Desktop Motherboard LGA1155 DDR3 1600 ATX * BOXDZ77GA*70K
[FONT=arial]Intel 520 Series Solid*State Drive 120 GB SSDSC2CW120A310[/FONT]
[FONT=arial]Samsung 850 EVO 250GB 2.5-Inch SATA III Internal SSD (MZ-75E250B/AM)
[/FONT]
(EVGA  GeForce GTX 970 Superclocked ACX 2.0 4GB GDDR5 256bit, DVI*I, DVI*D,  HDMI, DP SLI Ready Graphics Card Graphics Cards 04G*P4*2974*KR)
WD Green 2 TB Desktop Hard Drive: 3.5 Inch, SATA III, 64 MB Cache * WD20EZRX


When  booting to my USB, I get the following message sitting on my screen for  a long time before things load "[ 4.553786 ] EDID block is all zeroes". I did see this message in red when I  did my dmesg command earlier, but it did not seem to be hanging anything up, so I  assumed it was not causing an issue. I did another dmesg command when booted to the USB and I'm seeing a 111  sec boot with the sdb1 drive being mounted at 95 seconds.

fsck output:

[B]ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sdb1
                                                                               
      222457 inodes used (3.50%, out of 6356992)
          55 non-contiguous files (0.0%)
         233 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 175058/20
     1577867 blocks used (6.21%, out of 25398784)
           0 bad blocks
           1 large file

      135309 regular files
       22637 directories
          55 character device files
          25 block device files
           0 fifos
           4 links
       64421 symbolic links (47290 fast symbolic links)
           1 socket
------------
      222452 files


[/B]Nothing here jumped out to me as an error, so I did not run the second command.

Thanks

---

### Post by josiahlund on 2016-12-02
I went into my BIOS to take pictures to upload just for reference sake, and I found a "Secondary LAN" setting that was checked that I was not able to find earlier. In one of the posts I read when trying to debug this on my own, that was the issue, so I unchecked that box, and now my boot time is 4 seconds!

Thanks for the help to both of you

---

### Post by alexjpowell on 2016-12-02
Thanks josiahlund
Anyone know how you can detect this via logs instead of having to guess?

4 seconds is pretty unreal, my own laptop with a decent SSD hits the desktop in 15

---

