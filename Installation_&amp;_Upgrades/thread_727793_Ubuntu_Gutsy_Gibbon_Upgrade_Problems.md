---
title: "Ubuntu Gutsy Gibbon Upgrade Problems"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by billgates456 on 2008-03-18
I upgraded my Ubuntu 6.06 Dapper Dark to Ubuntu 7.10 Gutsy Gibbon and I faced following problems after upgradation.

1. My pen drive is not working properly. 
    System said Wrong fs

2. My VMWARE workstations are not working properly because he said the compiler version is greater then compiler version by which Kernel is compiled. That's why it modules are not working correctly.

3. Internet sometimes said (connection : resource not available)

If you have solution of this problem then please inform to me.

thanks
Billgates456

---

### Post by PmDematagoda on 2008-03-18
For the first question, post the output of:-
```
sudo fdisk -l
```
when the pen drive is plugged in.

For the second one, that is because Ubuntu 7.10 uses a different kernel and components as opposed to Ubuntu 6.06. Reinstall VMWare Workstation and then try running it.

---

### Post by billgates456 on 2008-03-18
With sudo fdisk -l I got this Error Message.


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd42ad42a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19083   153284166   83  Linux
/dev/sda2           19084       19457     3004155    5  Extended
/dev/sda5           19084       19457     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 1031 MB, 1031798272 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         126     1007584    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(124, 254, 63) logical=(125, 112, 50)


Please give some reply to me.

Thanks
billgates456

---

### Post by PmDematagoda on 2008-03-18
Can you post the output of:-
```
cat /etc/mtab
```

---

### Post by billgates456 on 2008-03-18
The following is the output of the mtab

/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-386/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

thanks
billgates456

---

### Post by billgates456 on 2008-03-18
this is the problem when I am installing the VMWARE SERVER on the System.
 I removed the gcc and when I again install then I got the same gcc version.


Your kernel was built with "gcc" version "4.1.2", while you are trying to use 
"/usr/bin/gcc" version "4.1.3". This configuration is not recommended and 
VMware Server may crash if you'll continue. Please try to use exactly same 
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.1.3" anyway? [no] 

If you any other method of installing the VMWARE server then please tell me

thanks
billgates456

---

### Post by PmDematagoda on 2008-03-18
About the pen drive, perfom an fsck check on it with:-
```
sudo fsck /dev/sdb1 -r
```

About the VMWare problem, I suggest that you create a different thread concerning this issue in the [Virtualisation section]("http://ubuntuforums.org/forumdisplay.php?f=308").

---

### Post by billgates456 on 2008-03-19
This is the output of the above file

fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sdb1: 1 files, 1/251400 clusters


I also did one thing that is evms I first uninstall evms and then again reinstall evms.

May be this is the problem

the dmesg | tail shows the following results

[ 2953.888942] sdb: Mode Sense: 0b 00 00 08
[ 2953.888945] sdb: assuming drive cache: write through
[ 2953.900918] SCSI device sdb: 512000 512-byte hdwr sectors (262 MB)
[ 2953.903912] sdb: Write Protect is off
[ 2953.903916] sdb: Mode Sense: 0b 00 00 08
[ 2953.903918] sdb: assuming drive cache: write through
[ 2953.903921]  sdb: sdb1
[ 2953.910963] sd 8:0:0:0: Attached scsi removable disk sdb
[ 2953.911008] sd 8:0:0:0: Attached scsi generic sg2 type 0
[ 2954.465011] FAT: Unrecognized mount option "usefree" or missing value


Thanks
billgates456

---

### Post by Sef on 2008-03-19
> I upgraded my Ubuntu 6.06 Dapper Dark to Ubuntu 7.10 Gutsy Gibbon

Did you upgrade directly from Dapper to Gutsy?  If you did that is what caused the problems.  Upgrades have to be done to the next release; hence, Dapper > Edgy > Fiesty > Gutsy.  The only exception to that is it may be possible to upgrade directly from one Long Term Support (LTS) to another.   I have heard it is possible, but I have not seen any documentation to that effect.

---

### Post by billgates456 on 2008-03-27
I upgrade one by one

First I upgrade from 6.06 to 6.10 then 7.0 something then in the last 7.10

Please give me some solution of it.

Thanks
billgates456

---

### Post by billgates456 on 2008-03-27
I think nobody knows the solution here

billgates456

---

