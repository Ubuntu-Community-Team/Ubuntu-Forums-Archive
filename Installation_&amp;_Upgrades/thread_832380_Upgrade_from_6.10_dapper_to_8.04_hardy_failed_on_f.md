---
title: "Upgrade from 6.10 dapper to 8.04 hardy failed on first reboot"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by timtipple on 2008-06-17
Summary:
Upgrade from 6.10 dapper (running kernel 2.6.15-51-server) to 8.04 hardy (2.6.24-18-server) failed on reboot: dropped to initramfs shell because could not find/mount root.

Details:
My server has two IDE hard disks (hda, hdb) each with a single Linux raid autodetect partition. These partitions are combined using mdadm to form a raid1 device /dev/md0. The raid1 device is used to create an LVM physical volume which is added to an LVM volume group. Seven logical volumes are created in the volume group. All logical volumes contain ext3 filesystems. My boot loader is lilo.

As this was a fairly non-standard configuration, I setup a dapper test server with a similar configuration to try out the upgrade to hardy. As this was a server installation I used the recommended upgrade procedure:
```
# apt-get install update-manager-core
# do-release-upgrade -d
```
Not unsurprisingly, the upgrade failed. On the first reboot, I was dropped into an initramfs shell. The last successfull boot message was
```
raid1: raid set md0 active with 2 out of 2 mirrors
Done.
```
followed by these error/info messages:
```
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=.....:......:......:......
Reading all physical volumes. This may take a while...
Found volume group "vg00" using metadata type lvm2
ALERT! /dev/root does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian.......(ash)
Enter 'help' for ...

(initramfs) _
```
The first error message was a big clue. I cannot remember exactly what /proc/cmdline contained but there was something about the "root" that made me think of my lilo configuration.

Luckily I could still boot using the previous kernel (2.6.15-51-server) and made some changes to /etc/lilo.conf. Before (excerpt):
```
boot=/dev/md0
root=/dev/mapper/vg00-root
raid-extra-boot=mbr-only
map=/boot/map
default=Linux

image=/vmlinuz
  label=Linux
  read-only
  initrd=/initrd.img

image=/vmlinuz.old
  label=LinuxOLD
  read-only
  initrd=/initrd.img.old
```
And after:
```
boot=/dev/md0
#root=/dev/mapper/vg00-root         # <=== commented out
raid-extra-boot=mbr-only
map=/boot/map
default=Linux

image=/vmlinuz
  label=Linux
  read-only
  initrd=/initrd.img
  append="root=/dev/mapper/vg00-root"        # <=== new line here

```
After these changes I ran
```
# update-initramfs -u -a
```
and rebooted. This time the test server started up just fine.

Thinking that I had things under control, I upgraded my main server. On the first reboot I ended up in the initramfs shell as before. I rebooted to the previous kernel, modified my lilo.conf, updated my initrd.img and rebooted again thinking all would be fine. But I ended up in the initramfs shell with this message:
```
md: md0 stopped.
md: md0 stopped.
Done.
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
Reading all physical volumes. This may take a while...
ALERT! /dev/mapper/vg00-root does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian.......(ash)
Enter 'help' for ...

(initramfs) _
```
So, similar result to my test server, but this time it seems that the problem occurs earlier: the raid1 array is not being found/assembled. Where to go from here?

Any advice will be much appreciated. Please be gentle, this is my first post to the Ubuntu forums :-)

---

### Post by simonstl on 2008-06-19
I wish I had good advice for your production box, but the techniques that worked for you on the test server worked on my own server. It had turned into a doorstop yesterday afternoon, taking down my public web presence and email.  With your advice, it took about an hour to fix; without it, I suspect I'd still be working on an acceptable solution.

Thanks, and I hope someone else will have more advice on the harder problem.

Simon St.Laurent
[http://simonstl.com/](http://simonstl.com/)

---

### Post by timtipple on 2008-06-19
Hi Simon,

I'm glad you were able to get your server up and running. At least my efforts have been worth it so far.

I continue to search for a solution for my 'production' server, but testing them out is not very popular with the users (family & friends). I just wish I could recreate this problem on my test server.

Anyone have any ideas here: i.e. how to break my test server :-)

---

### Post by simonstl on 2008-06-29
I still don't have a good way for you to break your server, but I'd like to report that the lilo.conf changes seem to have broken the upgrade process.

Aptitude explodes with:

> 
Errors were encountered while processing:
 linux-image-2.6.24-19-generic
 linux-ubuntu-modules-2.6.24-19-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.24-19-generic (2.6.24-19.34) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
update-initramfs: lilo run failed for /boot/initrd.img-2.6.24-19-generic:

Warning: LBA32 addressing assumed
Warning: '/proc/partitions' does not match '/dev' directory structure.
    Name change: '/dev/dm-0' -> '/dev/disk/by-id/dm-name-sda1'
Warning: Name change: '/dev/dm-1' -> '/dev/disk/by-id/dm-name-sdb1'
Warning: Name change: '/dev/dm-2' -> '/dev/evms/lvm2/main/homeFiles'
Warning: Name change: '/dev/dm-3' -> '/dev/evms/lvm2/main/swap'
Warning: Name change: '/dev/dm-4' -> '/dev/evms/lvm2/main/system'
Warning: Name change: '/dev/dm-5' -> '/dev/evms/lvm2/main/temp'
Warning: Name change: '/dev/dm-6' -> '/dev/evms/lvm2/main/variable'
Warning: Name change: '/dev/dm-7' -> '/dev/main/system'
Warning: Name change: '/dev/dm-8' -> '/dev/main/temp'
Warning: Name change: '/dev/dm-9' -> '/dev/main/variable'
Warning: Name change: '/dev/dm-10' -> '/dev/main/swap'
Warning: Name change: '/dev/dm-11' -> '/dev/main/homeFiles'
Fatal: is_primary:  Not a valid device  0xFE00
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-19-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-19-generic:
 linux-ubuntu-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-19-generic
 linux-ubuntu-modules-2.6.24-19-generic

I'm not quite sure what's going on (and I'm not particularly upset or surprised), but thought I should post it in case someone else runs into the same thing.

---

### Post by timtipple on 2008-07-02
I had to bite the bullet and do a fresh Hardy install using one of the disks taken from my test server. The installation went flawlessly of course, and thanks to my rsnapshot backup I have completely restored all home directories. I also used the rsnapshot backup to help me reconfigure all the services I run.

I do realise that I'm running the risk of having my server taken out by a disk failure one day so I plan to buy a similar disk and set up raid1 again; perhaps leaving the boot/root filesystems on a regular disk this time?

---

### Post by geeksmith on 2008-10-11
Too little, and way too late, but I left the root line at the top of the config and added the append line under the kernel entry, and that worked for me.  Removing the root line still dropped me into initramfs.

/proc/cmdline was pointing root to fd00 on some boots and fe00 on others.  I guess this was picked up from either /etc/blkid.tab or /etc/hosts.  cmdline now looks like this:
```
auto BOOT_IMAGE=Linux ro root=fe00 root=/dev/mapper/vg0-root
```

So something is still hosed, but at least my box will boot now.  BTW, it's RAID1/LVM.

@@ron

---

