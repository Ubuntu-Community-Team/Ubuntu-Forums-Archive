---
title: "Swap file disappeared"
date: 2012-08-27
forum: Installation &amp; Upgrades
---

### Post by Resistent on 2012-08-27
Hi all,

I am new on Ubuntu, have a 5 year old notebook with 1 GB RAM and dual boot system with Windows Vista. The default swap file after install was 256 MB, so I decided to make it bigger as described here: [http://ubuntuforums.org/showthread.php?t=1042946]("http://ubuntuforums.org/showthread.php?t=1042946").

After about 30 Minutes hard working, my notebook created a swapfile with size of 1.8 GB. And I did all other steps too. (hibernation did not worked yet, but it was not top priority).

After deinstalling "xubuntu" and "kubuntu", installing "lubuntu" (again) and restarting, Ubuntu crashed at startup, so I had to shut it down by the power button. Then I realized that my swap file disappeared.

**- Can I restore my 1.8 GB swap file? If not, the space on harddisk will be cleaned up? Or with autoclean?**

I am not sure, but I looked like that my Ubuntu was a little bit instable with the 1.8 GB swap file. (needed to login longer, some smaller problems). 

What I just need in Ubuntu is the Google Chrome for Youtube videos and web pages, and LibreOffice, so the RAM is on 30 - 40 % used max. At the moment swap is disabled. I set the swappiness to 0. **Maybe I dont need swap?**

sudo sysctl vm.swappiness=0


Thx,

---

### Post by oldfred on 2012-08-28
Welcome to the forums.

I would think with 1GB of RAM, you should have swap. Those with 4GB or more may not need it, but often system works a bit better if you have some swap.

post these.

# To clear cache and get new view:
sudo blkid -c /dev/null -o list

sudo cat /etc/fstab

mount

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

---

### Post by Resistent on 2012-08-28
Here are my settings:

**sudo blkid -c /dev/null -o list**

device       fs_type label    mount point      UUID
----------------------------------------------------------------------------------
/dev/loop0   ext3             /                56f0b0d5-304d-45dd-85dd-f3f02674c4e7
/dev/sda1    ntfs             (not mounted)    EA784139784105B3
/dev/sda2    ntfs    Vista    /host            D27E446E7E444E03

**sudo cat /etc/fstab**

# UNCONFIGURED FSTAB FOR BASE SYSTEM
/swapfile   none   swap   sw   0   0

**mount**

/dev/loop0 on / type ext3 (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda2 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda2 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/istvan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=istvan)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)

**sudo fdisk -l**
maybe helpfull too

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5b57e473

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    11266047     5632000   27  Hidden NTFS WinRE
/dev/sda2   *    11266048   156299263    72516608    7  HPFS/NTFS/exFAT


thx!

---

### Post by oldfred on 2012-08-28
You do not need swap partition as you are running wubi.

Wubi is a file inside the NTFS partition. It uses the Windows boot loader. 

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

I do not know a lot about wubi. It is a way to run a longer test of Ubuntu than just the liveCD. It allows full updates and mostly runs just like a normal partitioned install. But if Windows crashes you cannot separately boot into wubi.

From the creator of wubi.
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by Resistent on 2012-08-29
Thank you!

Now I know the difference between a real install and wubi install. Later, I will install Ubuntu normally on my main pc, without wubi.

---

### Post by chkneater on 2012-08-29
I noticed the same thing happening to mine after installing AV Linux.  I have Ubuntu Studio 10.10 and AV Linux, and after installing AV I had to use Gparted to create a swap file and then after logging in, use Gparted to turn the swap on manually.  There should be a script to start the swap file on startup??

---

