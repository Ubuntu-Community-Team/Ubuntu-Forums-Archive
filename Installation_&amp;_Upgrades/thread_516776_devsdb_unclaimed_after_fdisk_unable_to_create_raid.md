---
title: "/dev/sdb unclaimed after fdisk unable to create raid array"
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by fpirz on 2007-08-03
I've upgraded one of my systems from 6.10 to 7.04
when the system was 6.10 I had the system installed on /dev/hda and a pair of sata disks
set up as /dev/sda and /dev/sdb in a raid0 mdadm array /dev/md0.
the md0 array was only used for data.
when I upgraded i did a clean install from the cdrom onto /dev/hda [wiping the old system].
I did not re-install the raid array, opting to do some iozone benchmarking on the disks first.
[ie, using /dev/sda fdisk'ed as /dev/sda1 and formatted as an XFS drive]
now that the benchmarking is complete, I'm trying to re-create the raid array.
however, when I fdisk /dev/sdb and create /dev/sdb1 i get the following:

fpirz@castor:/etc/mdadm$ ls -l /dev/sd*
brw-rw---- 1 root disk 8,  0 2007-08-03 13:51 /dev/sda
brw-rw---- 1 root disk 8,  1 2007-08-03 14:07 /dev/sda1
brw-rw---- 1 root disk 8, 16 2007-08-03 15:35 /dev/sdb*
cr-------- 1 root root 8, 17 2007-08-03 16:29 /dev/sdb1

and the output of
fpirz@castor:/etc/mdadm$ sudo lshw -C disk
[part deleted]
-disk:0
       description: SCSI Disk
       product: WDC WD5000KS-00M
       vendor: ATA
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 07.0
       serial: WD-WCANU1564594
       size: 465GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@0:0.0.0,1
          logical name: /dev/sda1
          capacity: 465GB
          capabilities: primary
  *-disk:1
       description: SCSI Disk
       product: WDC WD5000KS-00M
       vendor: ATA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: 07.0
       serial: WD-WCANU1607829
       size: 465GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume UNCLAIMED
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@1:0.0.0,1
          capacity: 465GB
          capabilities: primary
[ie, the volume is showing as unclaimed and there is no logical name!!!]

the mdadm command to create md0 fails.
any suggestions?

i've tried deleting /dev/sdb1 and using mknod to create a coorect /dev/sdb1 entry
but that does not change the lshw results and the mdadm command still fails.

I'm baffled...

Frank Pirz

---

### Post by fpirz on 2007-08-05
First, I no longer have any confidence that the UNCLAIMED status shown by 
 lshw -C disk
has any validity..
I noticed that on my currently running system
fpirz@castor:/media$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: MAXTOR 6L060L3
       vendor: Maxtor
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: A93.0500
       serial: 663128913568
       size: 55GB
       capacity: 55GB
       capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
       configuration: mode=udma6 smart=on
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: ide@0.0,1
          logical name: /dev/hda1
          capacity: 18GB
          capabilities: primary
     *-volume:1
          description: Linux swap / Solaris partition
          physical id: 2
          bus info: ide@0.0,2
          logical name: /dev/hda2
          capacity: 4769MB
          capabilities: primary nofs
     *-volume:2 UNCLAIMED
          description: Linux filesystem partition
          physical id: 3
          bus info: ide@0.0,3
          capacity: 32GB
          capabilities: primaryfpirz@castor:/media$ ls -l /dev/hd*
brw-rw---- 1 root disk   3, 0 2007-08-05 21:52 /dev/hda
brw-rw---- 1 root disk   3, 1 2007-08-05 21:53 /dev/hda1
brw-rw---- 1 root disk   3, 2 2007-08-05 21:52 /dev/hda2
brw-rw---- 1 root disk   3, 3 2007-08-05 21:52 /dev/hda3

andfpirz@castor:/media$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             19228276   2750892  15500636  16% /
varrun                 1038068       228   1037840   1% /var/run
varlock                1038068         0   1038068   0% /var/lock
procbususb             1038068       124   1037944   1% /proc/bus/usb
udev                   1038068       124   1037944   1% /dev
devshm                 1038068         0   1038068   0% /dev/shm
lrm                    1038068     33788   1004280   4% /lib/modules/2.6.20-16-generic/volatile
/dev/hda3             34193664    168948  34024716   1% /var/lib
/dev/md0             976635904      1056 976634848   1% /media/testmd

both show /dev/hda3, volume 2, existing, and in use....

secondly, I noticed that if I swapped the disks that I was trying to use for the raid pair
/dev/sda and /dev/sdb that the fdisk problem followed the disk..
Now these are brand new disks and they worked before the upgrade...
I downloaded WD's bootable disk diagnostic and ran it.
[see support.wdc.com, data lifeguard for dos..bootable cd iso]
the diagnostics showed no problems
I ran a quick zero write on both drives.
Viola!
I can now fdisk BOTH drives, create a raid0 array using mdadm and mount it!!!

Frank Pirz



note that volume two shows up as UNCLAIMED...
BUT..

---

