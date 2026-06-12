---
title: "Can't mount disks after upgrading to gutsy!"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by knooten on 2007-10-20
Hi,

I've just upgraded my server to ubuntu 7.10 from ubuntu 7.04...

Everything is ok, but i can't mount my disks! I've tried reboots and other stuff nothing seems to work!

All I get from mount -a is:
mount: /dev/sdd1 already mounted or /media/80 busy
mount: /dev/hdb1 already mounted or /media/120 busy
mount: /dev/hdc1 already mounted or /media/160 busy

and #lsof /dev/hdb
displays nothing anymore (displayed hddtemp, but I have shut it down).

Anyone know what to do?

---

### Post by knooten on 2007-10-20
SOLVED: apt-get remove --purge evms

---

### Post by siafulinux on 2007-10-20
I am having the same problem. Did the upgrade and previous mounts in fstab that worked before do not work now after the reboot. 

I tried "apt-get remove --purge evms" but it's not installed.

I keep getting the "wrong fs type, bad option, bad superblock" error, but I have changed nothing on the client or server side that I am trying to mount.

Ideas appreciated
Siafu

---

### Post by siafulinux on 2007-10-20
:SOLVED: Okay for some odd reason nfs-common was not there after the upgrade. A simple "sudo apt-get install nfs-common" solved the issue.

Siafu

---

### Post by yota on 2007-10-20
Thank you knooten!

```

aptitude purge evms

```

worked for me.

---

### Post by mary_poppins on 2007-10-21
> **siafulinux said:**
> :SOLVED: Okay for some odd reason nfs-common was not there after the upgrade. A simple "sudo apt-get install nfs-common" solved the issue.

Siafu

I have the same problem (cant mount my /dev/sdb1 after upgrading to gutsy),
and neither of the above two solutions does not help: evms was not installed, and 
installation of nfs-common does not help.

---

### Post by hack6500 on 2007-10-22
i too had this issue, i solved it differently...

first verify that dmraid has your drives mapped in /dev/mapper/
**ls -la /dev/mapper/**

next stop dmraid, which removes the drive mapping 
[B]sudo /etc/init.d/dmraid stop
sudo apt-get remove --purge dmraid[/B]

finally i restarted my array and mounted it
[B]sudo mdadm --assemble --scan --verbose
cat /proc/mdstat
mount /dev/md0
[/B]
bingo!

---

### Post by fakeollie on 2007-10-22
I had the same problem of having a few partitions not mounting after upgrading to Gutsy.

I've found that any partions that I had previously manually set on fstab as /dev/hdx (as opposed to using labels or uuids) would not mount. Apparently Gutsy got away with the hdx nomenclature and now only accepts sdx. 

Once I edited /etc/fstab and simply changed the values from /dev/hda5 to /dev/sda5 for instance, all partitions mounted correctly.

Hope this helps.

---

### Post by mary_poppins on 2007-10-22
> **fakeollie said:**
> I had the same problem of having a few partitions not mounting after upgrading to Gutsy.

I've found that any partions that I had previously manually set on fstab as /dev/hdx (as opposed to using labels or uuids) would not mount. Apparently Gutsy got away with the hdx nomenclature and now only accepts sdx. 

Once I edited /etc/fstab and simply changed the values from /dev/hda5 to /dev/sda5 for instance, all partitions mounted correctly.

Hope this helps.

This was not my case, because the partition that I can't mount was sdb1 from the beginning. **However, rather than trying various voodoo solutions, I want to understand how to figure out why the kernel thinks my /dev/sdb1 is in use.**  It happens during the boot sequence, because fsck fails with the same message.  **How the partition is being marked used? **Once I know that I can proceed to debugging it.

---

### Post by eugenwinter on 2007-10-22
Hi there 
 I had a similar problem with /var. I found a working solution under
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153144]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/153144")

It seems that this is a problem with the ramdisk. So as mentioned in one of the last posts
 on this page "update-initramfs -k all -c" did the job for me.
I hope this will help you.

best regards 
  Eugen

---

### Post by chosi on 2007-10-23
I had the same problem.
the last suggested solution (initramfs-thingie) helped - just FYI

---

### Post by evver on 2007-10-26
I too had the same problem.  nfs-common was already installed, removing evms did not help, and I could not manually mount the raid.  The only thing that worked for me was to go back to using kernel 2.6.20-16.  Using this kernel, I did not need to make any other changes.

I have set this as my default kernel for the present, but I would like to figure out how to get raid working with the latest kernel.

---

### Post by GoBieN on 2007-10-26
> **fakeollie said:**
> I had the same problem of having a few partitions not mounting after upgrading to Gutsy.

I've found that any partions that I had previously manually set on fstab as /dev/hdx (as opposed to using labels or uuids) would not mount. Apparently Gutsy got away with the hdx nomenclature and now only accepts sdx. 

Once I edited /etc/fstab and simply changed the values from /dev/hda5 to /dev/sda5 for instance, all partitions mounted correctly.

Hope this helps.

I had this problem too, but when i upgraded to fesity, did you skip feisty perhaps ?
Since fesity all my drives (ATA drivers) are now sdx

On gusty upgrade my system would not bot, had to purge evms.

---

### Post by rakku-toki telkio-kuuni on 2007-10-28
> **siafulinux said:**
> :SOLVED: Okay for some odd reason nfs-common was not there after the upgrade. A simple "sudo apt-get install nfs-common" solved the issue.

Siafu

Worked for me, thank you.

---

### Post by xpavement on 2007-11-07
Installed nfs-common and tried the initramfs command also, and now my extra disk is mounting correctly in the 2.6.22-14 kernel. Thanks!

---

