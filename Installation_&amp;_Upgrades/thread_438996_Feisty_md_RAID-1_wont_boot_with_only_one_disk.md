---
title: "Feisty md RAID-1 wont boot with only one disk"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by smellems on 2007-05-10
Hi,
  I Installed Ubuntu Feisty on my new computer.  I have 2 Identical 250Gb SATA hard drives, partition like this.

sda1   50Gb
sda2   10Gb
sda3    2Gb
sda4   extended containing sda5
sda5   the rest

and

sda1   50Gb
sda2   10Gb
sda3    2Gb
sda4   extended containing sda5
sda5   the rest

all set as raid, I fallowed this tutorial to set up the partitions:
[http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)

then

md0  sda1/sdb1   /home
md1  sda2/sdb2   /
md2  sda5/sdb5   /media/Stufff  (mounted after install)
md3  sda3/sdb3   swap


everything works great.  boots normally and the arrays seem to work


~$ cat /proc/mdstat
Personalities : [raid1]
md2 : active raid1 sda5[0] sdb5[1]
      177791232 blocks [2/2] [UU]
     
md3 : active raid1 sda3[0] sdb3[1]
      1951808 blocks [2/2] [UU]
     
md1 : active raid1 sda2[0] sdb2[1]
      9767424 blocks [2/2] [UU]
     
md0 : active raid1 sda1[0] sdb1[1]
      54685120 blocks [2/2] [UU]
     
unused devices: <none>


I can simulate the failure like this

~$ sudo mdadm --manage -f /dev/md0 /dev/sda1
mdadm: set /dev/sda1 faulty in /dev/md0

~$ cat /proc/mdstat
Personalities : [raid1]
md2 : active raid1 sda5[0] sdb5[1]
      177791232 blocks [2/2] [UU]
     
md3 : active raid1 sda3[0] sdb3[1]
      1951808 blocks [2/2] [UU]
     
md1 : active raid1 sda2[0] sdb2[1]
      9767424 blocks [2/2] [UU]
     
md0 : active raid1 sda1[2](F) sdb1[1]
      54685120 blocks [2/1] [_U]
     
unused devices: <none>

~$ sudo mdadm /dev/md0 -r /dev/sda1
mdadm: hot removed /dev/sda1

~$ cat /proc/mdstat
Personalities : [raid1]
md2 : active raid1 sda5[0] sdb5[1]
      177791232 blocks [2/2] [UU]
     
md3 : active raid1 sda3[0] sdb3[1]
      1951808 blocks [2/2] [UU]
     
md1 : active raid1 sda2[0] sdb2[1]
      9767424 blocks [2/2] [UU]
     
md0 : active raid1 sdb1[1]
      54685120 blocks [2/1] [_U]
     
unused devices: <none>

~$ sudo mdadm /dev/md0 -a /dev/sda1
mdadm: re-added /dev/sda1

~$ cat /proc/mdstat
Personalities : [raid1]
md2 : active raid1 sda5[0] sdb5[1]
      177791232 blocks [2/2] [UU]
     
md3 : active raid1 sda3[0] sdb3[1]
      1951808 blocks [2/2] [UU]
     
md1 : active raid1 sda2[0] sdb2[1]
      9767424 blocks [2/2] [UU]
     
md0 : active raid1 sda1[2] sdb1[1]
      54685120 blocks [2/1] [_U]
      [>....................]  recovery =  0.5% (307648/54685120) finish=11.7min speed=76912K/sec
     
unused devices: <none>

~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Mon May  7 06:39:28 2007
     Raid Level : raid1
     Array Size : 54685120 (52.15 GiB 56.00 GB)
    Device Size : 54685120 (52.15 GiB 56.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu May 10 09:07:46 2007
          State : clean, degraded, recovering
 Active Devices : 1
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 1

 Rebuild Status : 1% complete

           UUID : 05b74c58:987d4618:4c6b9d8f:61efa6fa
         Events : 0.128

    Number   Major   Minor   RaidDevice State
       2       8        1        0      spare rebuilding   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1


So it rebuilds itself after drive failure...  seems all good.

then I wanted to do a real test: so I unpluged drive sda, it got to grub but hanged at startup.  The I pluged the sda back in and unpluged sdb, it did not even get to grub.  after lots of searching, I configured grub to boot from either disk

sudo grub
grub> device (hd0) /dev/sda
grub> root (hd0,1)
grub> setup (hd0)
grub> device (hd1) /dev/sdb
grub> root (hd1,1)
grub> setup (hd1)
grub> quit

now it get to grub and tries to load but hangs on startup just like sda.  both the errors seem to be a bit different.  But I end up in a busybox shell.

I will write the output just before it hangs a bit latter.  Does anyone else have this problem? or heard of this?  could this be a Feisty problem?

thank you for reading my long post..

---

### Post by Child of Wonder on 2007-05-10
Grub has problems booting into RAID.

I recall having the same problems on my box and ended up going with lilo and that worked without any issues.

---

### Post by irvin on 2007-05-16
Hallo

I have the same problem with testing a failed HD. Until now I don't have a solution but i think I'll try the lilo.

Here's the thread:

[http://ubuntuforums.org/showthread.php?t=289609](http://ubuntuforums.org/showthread.php?t=289609)

Bye
Irvin

Edit:

I just read that I can't use Grub and lilo on ubuntu at the same time, so I will stay with Grub and look forward to a solution.

---

### Post by irvin on 2007-05-17
Hi

I Think i finally found a solution (nearly no sleep). As I tried a lot more things, there was one magic word:

mdrun

I took one HD away and made the recovery boot. the i waited until the initramfs came and i had the command line

then: wrote mdrun and enter

the md0 stopped and started again. I don't know exactly was mdrun does but i think it checked if the two drieves ara available. it says something like running 1 from 2.

then i made a reboot (normal graphics) and the system started - perfect !

The I put the second hd2 on and started made the mdadm --add stuff and the hd's synced.

the I tried the same if the first hd fails, the grub bootloader was isntalled so also, mdrun... worked.

the i deleted the aother hd, started made exactly same partitions and the --add stuff.
they resynced, everything works now, hopefully there's no problem again if the really fail sometime and the kernel is changed again and again... we will see.
Many thanx for the support and the "good words" to try it with the software raid.

I was so in the windows thing where everything went great in the last years with the VIA Raid drivers and software, but I really was not in the probs with the kernel changes.
So you can never be sure if your system will boot again in raid after updates.
Bye
Irvin

---

### Post by brunux on 2007-11-06
Hi Irvin, 
I've tried to follow your instructions on my Edubuntu 7.10, where I have 2 SATA disks in RAID1  perfectly synced as md0 (/boot) md1 (swap) md2 (/). The system boots, but if I unplug one of the disks I arrive to the initramfs prompt, after a read-error on swap-device, according to what the recovery mode says. 
I've tried then to write mdrun on the initramfs prompt and it doesn't look like an existing command!

So I'm stuck again. 

Please help, I'm struggling with this obnoxious RAID1 for 3 weeks now! It's a shame that such a common task has to be so incredibly difficult to figure out. 

brunux

---

