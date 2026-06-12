---
title: "software raid 10 : my experience"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by jaygo on 2007-10-25
After four days, I gave up on software raid 10. A couple of critical problems I ran into:
[LIST=1]
[*]Contrary to popular opinion, GRUB doesn't really do raid 1. I'm not really familiar with how the MBR works on a drive, but I'm pretty sure that it can't be duplicated with softRAID. Therefore, GRUB needs to be installed separately on every physical drive that you want to boot the system. Otherwise, you end up with a bootable MBR on one disk and an unbootable, but pretty, RAID 1 array of your /boot partition on your other drives. I finally found out how to install GRUB onto other drives, but apparently could not get it installed into the MBR on those drives from the GRUB prompt (in a liveCD console). So without some fancy GRUB footwork -- and even then, if your boot drive dies, you'll need to physically reorder your drives -- you cannot get true redundancy through software raid. Since I want RAID to make my system faster and more robust, this isn't good enough for me.
[*]Initrd doesn't love you. This seems to be the biggest obstacle to migrating linux installations to other drives, RAID arrays, etc. Apparently, it needs to be rebuilt any time you make significant changes to grub or to your boot & root partitions. As far as I can tell, you can't rebuild initrd from a live CD.
[*]At this point, I don't see how software raid 10 is even possible with mdadm. GRUB can boot off of one of your disks. If you setup your RAID array(s) from your distro's installer, then initrd should load the md module early enough in the boot process to let GRUB (or whatever is running the show at this point) assemble your md arrays and find the / partition. However, it seems to do a single pass, where it assembles all of the md arrays that it can, then moves on. Well with raid 10, you first need your two raid 1 arrays assembled, *then* you need the raid 0 array assembled on top of them.
[*]After GRUB launches, I would get an error stating that it couldn't find the arrays listed in the config file. At first, I assumed it was referring to my mdadm.conf file, which is supposed to be optional, and would be inaccessible anyway because it was locked up in a raid10 array. The way it seems to be designed is to actually scan special sections (called superblocks) of all attached hard drives for info on md arrays. Then it builds those arrays accordingly. I did some googling but never found an answer for that one.
[/LIST]
Back to reality ... I've wasted a ridiculous amount of time on this and should have just bit the bullet as soon as I found out that ubiquity (the GUI installer for ubuntu, kubuntu, mint, etc) doesn't recognize md arrays. My $370 3ware raid card should be here this morning so I can get back to work by this afternoon. :)

I'm posting this as an easy to find thread that will hopefully save others time. If I'm factually incorrect about some of my conclusions, feel free to post corrections. On the shoulders of giants ...

PS. I've heard of people running raid 10 in mdadm but at this point (7.10) it's an uphill battle to get it working ... or find out that it doesn't.

---

### Post by etarip on 2007-10-30
I've set up RAID 1 + RAID 10 on an Ubuntu 6.06.1 AMD64 server with four identical SATA disks. I think it works on Ubuntu 7.10 to. Here are the main steps(please follow the links for details):

1. [Following this]("http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/"), set up RAID1 on the first small(say 5 G) partition of sda/sdb/sdc/sdd. Install the base system on it. You'll get /dev/md0 constituted of /dev/sda1, /dev/sdb1, /dev/sdc1 and /dev/sdd1. If your main memory is enough, just use /dev/md0 as / without swap. And you could make all drives bootable too.

2. Login to the system, make four identical partition tables on /dev/sda, /dev/sdb, /dev/sdc and /dev/sdd using fdisk. Be careful, sda/b/c/d1 are already used as /dev/md0. Notice: you should set the new partitions' Id to fd (Linux raid auto) using commond t in fdisk.

3. [Creating 4-disk RAID10 using mdadm]("http://www.tgharold.com/techblog/2006/08/creating-4-disk-raid10-using-mdadm.shtml") on the new partitions added in step 2. Because ubuntu already has /dev/md0 to /dev/md24, you needn't run mknod. After that, you'll get something like /dev/md1 as RAID10 constituted of /dev/sda/b/c/d2, /dev/md2 as RAID10 constituted of /dev/sda/b/c/d3 and so on. 

4. Run apt-get clean to remove the apt cache (I'll explain this later). Make swap on a new /dev/mdX, and make your favorite file system on the other new /dev/mdX. Then you could copy (using cp -a or cp -dpRx) /usr /var /home /opt etc from /dev/md0 to /dev/mdX following [this]("http://www.debian-administration.org/articles/238"), modify /etc/fstab accordingly, reboot. Then, no news is good news.

5. (Optional) Remove the original /usr /var /home etc on /dev/md0. Start system using single mode, umount /usr /var /home (they are the new ones on /dev/mdX), then the old ones will appear. Remove them using rm -fr /usr /home (You probably can't remove /var, let it be, so running apt-get clean in step 4 can reduce the /var space). **DO remount  /dev/mdX on /usr /var /home before rebooting**.

6. Login and run dmesg | less, you'll see something like:

md: md0 stopped.
md: bind<sdd1>
raid1: raid set md0 active with 1 out of 4 mirrors

run cat /proc/mdstat, there will be:

md0 : active raid1 sdd1[3]
      4883648 blocks [1/4] [___U]

[Following this]("http://piirakka.com/misc_help/Linux/raid_starts_degraded.txt"),  hot-add /dev/sda/b/c1 to /dev/md0 by running mdadm --add /dev/md0 /dev/sda/b/c1, then run update-initramfs -k `uname -r` -t -u, then reboot, md0 will be four active drives.

If you see something like "md: md3: raid array is not clean -- starting background reconstruction" in dmesg, just wait for the reconstruction finishing before reboot. You can see the progress in cat /proc/mdstat.


All is done!:)


Acknowledgments to my boss Alex Xuehu Zhang.

---

