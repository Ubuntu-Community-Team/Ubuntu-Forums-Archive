---
title: "initrd.img too big (REALLY BIG!)"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by nandelbosc on 2008-11-24
Hi!

I'm using ubuntu 8.10, it's my first steps in this distro. I'm using gentoo for more than 3 years and i'm going crazy with some differences between this distros.

After make some (two) changes in my kernel with "make menuconfig", I follow this steps to compile the new one:

```
make menuconfig
make-kpkg --initrd kernel_image kernel_headers
dpkg -i new_kernel.deb
dpkg -i new_kernel_HEADERS.deb
```

all works ok, and changes are applied, but the system seems more slowly, and the boot time is really more long.

looking /boot directiry we can see something strange...

now:

```
$ ls -lhS /boot/
total 56M
-rw-r--r-- 1 root root   41M 2008-11-23 01:28 initrd.img-2.6.27.2
-rw-r--r-- 1 root root  7,9M 2008-11-21 22:04 initrd.img-2.6.27-7-generic
-rw-r--r-- 1 root root  2,2M 2008-11-04 22:00 vmlinuz-2.6.27-7-generic
-rw-r--r-- 1 root root  2,2M 2008-11-23 00:37 vmlinuz-2.6.27.2
-rw-r--r-- 1 root root 1006K 2008-11-04 22:00 System.map-2.6.27-7-generic
-rw-r--r-- 1 root root  976K 2008-11-23 00:37 System.map-2.6.27.2
-rw-r--r-- 1 root root  496K 2008-11-04 22:00 abi-2.6.27-7-generic
-rw-r--r-- 1 root root  122K 2008-09-11 22:11 memtest86+.bin
-rw-r--r-- 1 root root   90K 2008-11-04 22:00 config-2.6.27-7-generic
-rw-r--r-- 1 root root   71K 2008-11-23 00:30 config-2.6.27.2
drwxr-xr-x 2 root root   12K 2008-11-21 19:37 lost+found
-rw-r--r-- 1 root root  1,1K 2008-11-04 22:02 vmcoreinfo-2.6.27-7-generic
drwxr-xr-x 4 root root  1,0K 2008-11-23 01:28 grub
```

before install new kernel:

```
$ ls -lhS /boot/
total 13M
-rw-r--r-- 1 root root  7,9M 2008-11-21 22:04 initrd.img-2.6.27-7-generic
-rw-r--r-- 1 root root  2,2M 2008-11-04 22:00 vmlinuz-2.6.27-7-generic
-rw-r--r-- 1 root root 1006K 2008-11-04 22:00 System.map-2.6.27-7-generic
-rw-r--r-- 1 root root  976K 2008-11-23 00:37 System.map-2.6.27.2
-rw-r--r-- 1 root root  496K 2008-11-04 22:00 abi-2.6.27-7-generic
-rw-r--r-- 1 root root  122K 2008-09-11 22:11 memtest86+.bin
-rw-r--r-- 1 root root   90K 2008-11-04 22:00 config-2.6.27-7-generic
-rw-r--r-- 1 root root   71K 2008-11-23 00:30 config-2.6.27.2
drwxr-xr-x 2 root root   12K 2008-11-21 19:37 lost+found
-rw-r--r-- 1 root root  1,1K 2008-11-04 22:02 vmcoreinfo-2.6.27-7-generic
drwxr-xr-x 4 root root  1,0K 2008-11-23 01:28 grub
```

here we see the size of new initrd.img it's more big than the original: before 7,9MB and now 41MB!

What's happens? It's possible this reduce the perfomance of the system and increases the boot time?

What I do wrong?

Thank's! And sorry for my english, but [i tried in spansih forum]("http://www.ubuntu-es.org/index.php?q=node/104795") with no luck!

PD: I read [this post]("http://ubuntuforums.org/showthread.php?t=417138") and I haven't the debug mode on...
```
marc@michael:~$ grep DEBUG /usr/src/linux/.config
# CONFIG_CGROUP_DEBUG is not set
CONFIG_SLUB_DEBUG=y
CONFIG_PM_DEBUG=y
# CONFIG_ACPI_DEBUG is not set
# CONFIG_CPU_FREQ_DEBUG is not set
# CONFIG_PCMCIA_DEBUG is not set
# CONFIG_IP_VS_DEBUG is not set
# CONFIG_NETFILTER_DEBUG is not set
# CONFIG_IP_DCCP_CCID2_DEBUG is not set
# CONFIG_IP_DCCP_CCID3_DEBUG is not set
# CONFIG_TIPC_DEBUG is not set
# CONFIG_AF_RXRPC_DEBUG is not set
# CONFIG_IEEE80211_DEBUG is not set
# CONFIG_MTD_DEBUG is not set
# CONFIG_MTD_PMC551_DEBUG is not set
# CONFIG_MTD_UBI_DEBUG is not set
# CONFIG_PNP_DEBUG is not set
# CONFIG_FUJITSU_LAPTOP_DEBUG is not set
# CONFIG_THINKPAD_ACPI_DEBUG is not set
# CONFIG_SCSI_SAS_LIBSAS_DEBUG is not set
CONFIG_AIC7XXX_DEBUG_ENABLE=y
CONFIG_AIC7XXX_DEBUG_MASK=0
CONFIG_AIC79XX_DEBUG_ENABLE=y
CONFIG_AIC79XX_DEBUG_MASK=0
# CONFIG_AIC94XX_DEBUG is not set
CONFIG_SCSI_DEBUG=m
# CONFIG_DM_DEBUG is not set
# CONFIG_I2C_DEBUG_CORE is not set
# CONFIG_I2C_DEBUG_ALGO is not set
# CONFIG_I2C_DEBUG_BUS is not set
# CONFIG_I2C_DEBUG_CHIP is not set
# CONFIG_POWER_SUPPLY_DEBUG is not set
# CONFIG_HWMON_DEBUG_CHIP is not set
# CONFIG_SSB_DEBUG is not set
# CONFIG_FB_NVIDIA_DEBUG is not set
# CONFIG_FB_RIVA_DEBUG is not set
# CONFIG_FB_INTEL_DEBUG is not set
# CONFIG_FB_RADEON_DEBUG is not set
# CONFIG_SND_DEBUG is not set
# CONFIG_HID_DEBUG is not set
# CONFIG_USB_DEBUG is not set
# CONFIG_USB_STORAGE_DEBUG is not set
CONFIG_USB_SERIAL_DEBUG=m
# CONFIG_USB_GADGET_DEBUG_FILES is not set
# CONFIG_USB_GADGET_DEBUG_FS is not set
# CONFIG_MMC_DEBUG is not set
CONFIG_INFINIBAND_MTHCA_DEBUG=y
CONFIG_INFINIBAND_AMSO1100_DEBUG=y
CONFIG_INFINIBAND_IPOIB_DEBUG=y
# CONFIG_INFINIBAND_IPOIB_DEBUG_DATA is not set
# CONFIG_EDAC_DEBUG is not set
# CONFIG_RTC_DEBUG is not set
# CONFIG_AUFS_DEBUG is not set
# CONFIG_BLK_DEV_COMPCACHE_DEBUG is not set
# CONFIG_TLSF_DEBUG is not set
# CONFIG_JBD_DEBUG is not set
# CONFIG_JBD2_DEBUG is not set
# CONFIG_JFS_DEBUG is not set
# CONFIG_XFS_DEBUG is not set
CONFIG_OCFS2_DEBUG_MASKLOG=y
# CONFIG_OCFS2_DEBUG_FS is not set
# CONFIG_NTFS_DEBUG is not set
# CONFIG_BEFS_DEBUG is not set
CONFIG_JFFS2_FS_DEBUG=0
# CONFIG_UBIFS_FS_DEBUG is not set
# CONFIG_UFS_DEBUG is not set
# CONFIG_CIFS_DEBUG2 is not set
# CONFIG_AFS_DEBUG is not set
# CONFIG_LDM_DEBUG is not set
# CONFIG_DLM_DEBUG is not set
CONFIG_DEBUG_FS=y
# CONFIG_DEBUG_KERNEL is not set
CONFIG_SCHED_DEBUG=y
# CONFIG_SLUB_DEBUG_ON is not set
CONFIG_DEBUG_BUGVERBOSE=y
CONFIG_DEBUG_MEMORY_INIT=y
# CONFIG_KEYS_DEBUG_PROC_KEYS is not set

```

Thank's!

---

### Post by cariboo on 2008-11-24
What is missing from the stock kernel that you have to compile your own custom kernel. The generic kernels work pretty well on everything I've installed it on. You don't have to do things the Gentoo way anymore, you're using Ubuntu. :)

Jim

---

### Post by nandelbosc on 2008-11-24
Hi cariboo907!

I don't miss nothing, but I would like to change one driver from module to built in the kernel.

But now that is not important, I like to know why the initial image weight around 8MB and my config (with minor changes) weight 40MB?!

---

### Post by maybeway36 on 2008-11-24
Is the initrd image gzipped? Try
```
file /boot/initrd.img-2.6.27.2
```

---

### Post by nandelbosc on 2008-11-24
Yes, is gzipped!

```
$ file /boot/initrd.img-2.6.27.2
/boot/initrd.img-2.6.27.2: gzip compressed data, from Unix, last modified: Sun Nov 23 04:28:49 2008
```

And yes, saturday I gonna sleep too late ( 04:28 ) ;)

---

### Post by manuelg on 2008-11-24
Did you copy the generic kernels .config file to the linux source directory and then made and saved your changes?

cd /usr/src/linux-source-2.6.27-7.15  *latest source from repositories*
cp /boot/config-$(uname -r) .config
make menuconfig    *or xconfig which is graphical*
make-kpkg --initrd --append-to-version=-<anything> kernel_image kernel_headers
dpkg -i linux-image-<name here>.deb
dpkg -i linux-headers-<name here>.deb
update-initramfs -k all -u -v  *if needed*
update-grub   *if neeeded*

Make sure when you make your .config changes that in section "kernel hacking", "kernel dubugging" is off.  It's a lot easier to find it when you use xconfig instead of menuconfig.

---

### Post by nandelbosc on 2008-11-24
Thank's manuelg,

> Did you copy the generic kernels .config file to the linux source directory and then made and saved your changes?

Yes, I do exactly what you write (except update-initramfs and update-grub)

> Make sure when you make your .config changes that in section "kernel hacking", "kernel dubugging" is off. It's a lot easier to find it when you use xconfig instead of menuconfig

As you can see on the first post...

```
# CONFIG_DEBUG_KERNEL is not set
```

... and I always use ```
make menuconfig
```

---

### Post by JoshGreen on 2008-12-16
I was having the same problem.  In my case it turned out to be because of the CONFIG_DEBUG_KERNEL option.  The initrd image file is just a gzipped cpio archive.  So you could extract it somewhere and examine the contents to try and figure out what is taking up so much space.  Example:

cd /tmp
mkdir blah
cd blah
gunzip -c /boot/initrd.img-2.6.27-9-generic | cpio -i

---

### Post by iponeverything on 2008-12-16
I ran into this too -- this should clear things up for you.

[http://ubuntuforums.org/showthread.php?t=417138](http://ubuntuforums.org/showthread.php?t=417138)

---

### Post by nandelbosc on 2008-12-17
thanks iponeverything, but I a read you link in the past and I haven't kernel debug in my kernel...


```
# CONFIG_DEBUG_KERNEL is not set
root@michael:/tmp/ddd# grep DEBUG /usr/src/linux-source-2.6.27/.config | grep KERN
# CONFIG_DEBUG_KERNEL is not set
root@michael:/tmp/ddd# grep DEBUG /usr/src/linux-source-2.6.27/.config | grep INF
CONFIG_INFINIBAND_MTHCA_DEBUG=y
CONFIG_INFINIBAND_AMSO1100_DEBUG=y
CONFIG_INFINIBAND_IPOIB_DEBUG=y
# CONFIG_INFINIBAND_IPOIB_DEBUG_DATA is not set
```


look this...

my own kernel...

```
root@michael:/tmp/ddd# ls -lh /lib/modules/2.6.27.2/kernel.old.notant/net/sunrpc/auth_gss/
total 1,4M
-rw-r--r-- 1 root root 486K 2008-11-23 00:37 auth_rpcgss.ko
-rw-r--r-- 1 root root 562K 2008-11-23 00:37 rpcsec_gss_krb5.ko
-rw-r--r-- 1 root root 365K 2008-11-23 00:37 rpcsec_gss_spkm3.ko
```

default (generic) kernel...

```
root@michael:/tmp/ddd# ls -lh /lib/modules/2.6.27-7-generic/kernel/net/sunrpc/auth_gss/                    total 100K
-rw-r--r-- 1 root root 51K 2008-11-04 22:01 auth_rpcgss.ko
-rw-r--r-- 1 root root 22K 2008-11-04 22:01 rpcsec_gss_krb5.ko
-rw-r--r-- 1 root root 19K 2008-11-04 22:01 rpcsec_gss_spkm3.ko
```

---

