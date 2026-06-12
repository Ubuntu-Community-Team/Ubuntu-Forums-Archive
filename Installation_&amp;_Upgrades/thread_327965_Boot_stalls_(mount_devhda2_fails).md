---
title: "Boot stalls (mount /dev/hda2 fails)"
date: 2006-12-30
forum: Installation &amp; Upgrades
---

### Post by DougS on 2006-12-30
First, hope it's OK to post Kubuntu issue here? (or where?)

Dual boot system working fine for weeks (newcomer trying to learn about Linux)

After installing Streamripper & Audacity and adjusting memory settings in Open Office to speed it up (can't see any reason why these should affect but they may?)...

Grub works and boot options displayed, select Kubuntu,
Kubuntu splash screen,
Stalls at "mounting root file system"
Initiating error message: Mounting/dev/hda2 (this is the linux partition...) on root failed no such device

Then BusyBox command line prompt appears.

I have no idea why the changes made should prevent a boot?
Is this a completely separate problem to the application changes?
Is there an undo or restore last good setup function (you can tell which OS I'm coming from here - sorry ;-)  )?

Any advice welcomed.

Doug S
Jarrow, Tyne & Wear, UK

---

### Post by taurus on 2006-12-30
Boot from the LiveCD.  Then paste the output of this command here?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by DougS on 2006-12-31
Thanks for responding during this live CD session, found:
[http://www.ubuntuforums.org/showthread.php?t=246895&highlight=%2Fdev%2Fhda](http://www.ubuntuforums.org/showthread.php?t=246895&highlight=%2Fdev%2Fhda)

which was identical problem?

Have tried following commands and will try re-boot to see if anything has worked.

My overriding concern is WHY this has happened as it puts doubt in my mind concerning reliability.

BTW I'm quite prepared to re-install from scratch although I would also like to learn how to REPAIR a system and what all of the coding means.


Anyway, here's the output of terminal:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14796   118848838+   7  HPFS/NTFS
/dev/hda2           16709       19664    23744070   83  Linux
/dev/hda3           19665       19929     2128612+   5  Extended
/dev/hda4           14797       16708    15358140    c  W95 FAT32 (LBA)
/dev/hda5           19665       19794     1044162   82  Linux swap / Solaris
/dev/hda6           19795       19929     1084356   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$

The above says my boot Kubuntu partition should be  /hda2 when Grub boots Kubuntu?


   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14796   118848838+   7  HPFS/NTFS
/dev/hda2           16709       19664    23744070   83  Linux
/dev/hda3           19665       19929     2128612+   5  Extended
/dev/hda4           14797       16708    15358140    c  W95 FAT32 (LBA)
/dev/hda5           19665       19794     1044162   82  Linux swap / Solaris
/dev/hda6           19795       19929     1084356   82  Linux swap / Solaris

Partition table entries are not in disk order


Then tried advice in thread above:
ubuntu@ubuntu:~$ sudo mount -t ext3 -o rw /dev/hda2 /mnt
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# sudo apt-get update; apt-get upgrade; apt-get install udev
sudo: unable to lookup ubuntu via gethostbyname()
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree... Done
udev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/#


IS my udev (whatever it is!) the latest version, or not?




Then tried alternative:
root@ubuntu:/# chroot /mnt
chroot: cannot run command `/bin/bash': No such file or directory
root@ubuntu:/# dir
bin   cdrom  etc   initrd      lib         media  opt   root  srv  tmp  var
boot  dev    home  initrd.img  lost+found  mnt    proc  sbin  sys  usr  vmlinuz
root@ubuntu:/# cd /mnt
root@ubuntu:/mnt# wget [http://archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_079-0ubuntu34_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_079-0ubuntu34_i386.deb)
--09:43:12--  [http://archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_079-0ubuntu34_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_079-0ubuntu34_i386.deb)
           => `udev_079-0ubuntu34_i386.deb'
Resolving archive.ubuntu.com... 195.248.90.35, 195.248.90.38
Connecting to archive.ubuntu.com|195.248.90.35|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 238,892 (233K) [application/x-debian-package]

100%[==========================================================>] 238,892      252.24K/s

09:43:13 (251.93 KB/s) - `udev_079-0ubuntu34_i386.deb' saved [238892/238892]

root@ubuntu:/mnt# dpkg -i udev_079-0ubuntu34_i386.deb
(Reading database ... 69054 files and directories currently installed.)
Preparing to replace udev 079-0ubuntu34 (using udev_079-0ubuntu34_i386.deb) ...
Unpacking replacement udev ...
Setting up udev (079-0ubuntu34) ...


I hope I haven't been silly doing the second step. I'll see if it boot and post back what happens.
Regards
Doug

root@ubuntu:/mnt#

---

### Post by DougS on 2006-12-31
One or other of the methods above has worked and the system now boots OK!

My remaining questions which would help greatly are:

Any ideas WHY this happened in the first place?

What is the basic meaning of the solution (or where do I go to find out more?)

Thanks again for the prompt support (a strength of the community) and regards
Doug

---

