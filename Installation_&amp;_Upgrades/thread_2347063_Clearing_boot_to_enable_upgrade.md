---
title: "Clearing /boot to enable upgrade"
date: 2016-12-21
forum: Installation &amp; Upgrades
---

### Post by Alligator on 2016-12-21
Below is the procedure I took and the failed results.  This has worked before.

_____________________________

---

### Post by Impavidus on 2016-12-21
The names of the packages you want to remove are linux-image-4.2.0-34-generic, linux-image-extra-4.2.0-34-generic, linux-image-4.4.0-28-generic etc. You may have to make your terminal window a bit wider to read the full name of the packages.

Furthermore, those packages are already removed. rc stands for desired status is remove, currently only configuration files remaining. You can use purge instead of remove to remove the configuration files and get the packages removed completely, although that doesn't really matter here because these packages have no configuration files that wouldn't be removed.

Instead of attaching your terminal output in a text file, it may be easier if you simply put it in your post in code tags.

---

### Post by ajgreeny on 2016-12-21
Are you having problems due to a /boot partition being full?

If so you will not be able to get apt-get to do the removal job due to insufficient headroom, so will have to resort to using dpkg.

Come back with more details of the specific problem you have with the output please of command ```
df -h
```which will show us your partitions and %age use of them all.

---

### Post by Alligator on 2016-12-21
The error was to empty /boot when attempting an upgrade.

Sorry forgot how to use code tags.

ron@Cronluath:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           785M   18M  767M   3% /run
/dev/md0        720G  287G  398G  42% /
tmpfs           3.9G   27M  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sdb1       331M  247M   67M  79% /boot
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           785M  164K  785M   1% /run/user/1001
tmpfs           785M   80K  785M   1% /run/user/1000
ron@Cronluath:~$

---

### Post by Alligator on 2016-12-21
The error was to empty /boot when attempting an upgrade.

Sorry forgot how to use code tags.

ron@Cronluath:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           785M   18M  767M   3% /run
/dev/md0        720G  287G  398G  42% /
tmpfs           3.9G   27M  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sdb1       331M  247M   67M  79% /boot
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           785M  164K  785M   1% /run/user/1001
tmpfs           785M   80K  785M   1% /run/user/1000
ron@Cronluath:~$

---

### Post by Alligator on 2016-12-21
```

Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           785M   18M  767M   3% /run
/dev/md0        720G  288G  397G  43% /
tmpfs           3.9G   38M  3.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sdb1       331M  247M   67M  79% /boot
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           785M  164K  785M   1% /run/user/1001
tmpfs           785M   84K  785M   1% /run/user/1000

```

---

### Post by Alligator on 2016-12-22
I deleted files in /boot and upgrade was successful.  Why is the /boot now 95% used.

```

ron@Cronluath:~$ uname -r
4.4.0-57-generic
ron@Cronluath:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           785M  9.7M  775M   2% /run
/dev/md0        720G  288G  396G  43% /
tmpfs           3.9G  460K  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sdb1       331M  295M   18M  95% /boot
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           785M   44K  785M   1% /run/user/1001
tmpfs           785M   60K  785M   1% /run/user/1000


ron@Cronluath:~$ sudo dpkg --list 'linux-image*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                           Version              Architecture         Description
+++-==============================-====================-====================-==================================================================
un  linux-image                    <none>               <none>               (no description available)
un  linux-image-3.0                <none>               <none>               (no description available)
rc  linux-image-4.2.0-34-generic   4.2.0-34.39          amd64                Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-28-generic   4.4.0-28.47          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-31-generic   4.4.0-31.50          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-34-generic   4.4.0-34.53          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-36-generic   4.4.0-36.55          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-38-generic   4.4.0-38.57          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-42-generic   4.4.0-42.62          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-43-generic   4.4.0-43.63          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-45-generic   4.4.0-45.66          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-47-generic   4.4.0-47.68          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-51-generic   4.4.0-51.72          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-53-generic   4.4.0-53.74          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-57-generic   4.4.0-57.78          amd64                Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-34-gen 4.2.0-34.39          amd64                Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-28-gen 4.4.0-28.47          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-31-gen 4.4.0-31.50          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-34-gen 4.4.0-34.53          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-36-gen 4.4.0-36.55          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-38-gen 4.4.0-38.57          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-42-gen 4.4.0-42.62          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-43-gen 4.4.0-43.63          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-45-gen 4.4.0-45.66          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-47-gen 4.4.0-47.68          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-51-gen 4.4.0-51.72          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-53-gen 4.4.0-53.74          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-extra-4.4.0-57-gen 4.4.0-57.78          amd64                Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic            4.4.0.57.60          amd64                Generic Linux kernel image
ron@Cronluath:~$ 

```

---

### Post by ajgreeny on 2016-12-22
Oh dear! I hope you do not mean what I think you mean.

**You should never delete files in the /boot partition using a file manager or the rm command**

You must always remove any such files using the package manager such as apt, apt-get or dpkg to uninstall the packages that added those particular files.  If you just delete them you can cause the whole package management system to become very unstable and corrupted, perhaps adding further problems in future.

How did you delete the files in /boot, with your file manager or using command line?  You may find that they are still sitting in the trash folder of that /boot partition which will be why it is now 95% used.  See what command ```
sudo ls -laR /boot
``` has to say, and then we can move forward to the next step.

---

### Post by Impavidus on 2016-12-22
Yesterday your package manager was fine, but now you tried installing kernel 4.4.0-57. As the "iF" at the beginning of the line of dpkg output indicates, this installation failed and left you with a half-configured package. So read ajgreeny's post to get to know the exact situation you're in now and then we can guide you on how to cleanly uninstall the 4.4.0-51 kernel and then fix the 4.4.0-57 kernel.

---

### Post by Alligator on 2016-12-22
Procedure used to clean up /boot.

uname -r
Now run this command for a list of installed kernels:

sudo dpkg --list 'linux-image*'
and delete the kernels you don't want/need anymore by running this:

sudo apt-get remove linux-image-VERSION
Replace VERSION with the version of the kernel you want to remove.
```

uname -r
Now run this command for a list of installed kernels:

sudo dpkg --list 'linux-image*'
and delete the kernels you don't want/need anymore by running this:

sudo apt-get remove linux-image-VERSION
Replace VERSION with the version of the kernel you want to remove.

```
```

sudo ls -laR /boot
[sudo] password for ron: 
/boot:
total 294937
drwxr-xr-x  4 root root     6144 Dec 21 23:24 .
drwxr-xr-x 25 root root     4096 Dec 21 23:22 ..
-rw-r--r--  1 root root  1243479 Nov 24 15:12 abi-4.4.0-51-generic
-rw-r--r--  1 root root  1243479 Dec  2 13:11 abi-4.4.0-53-generic
-rw-r--r--  1 root root  1243800 Dec  9 22:04 abi-4.4.0-57-generic
-rw-r--r--  1 root root   189877 Nov 24 15:12 config-4.4.0-51-generic
-rw-r--r--  1 root root   189877 Dec  2 13:11 config-4.4.0-53-generic
-rw-r--r--  1 root root   189991 Dec  9 22:04 config-4.4.0-57-generic
drwxr-xr-x  5 root root     8192 Dec 21 23:23 grub
-rw-r--r--  1 root root  9962998 Dec 16 01:47 initrd.img-3.13.0-57-generic
-rw-r--r--  1 root root  9962572 Dec 16 01:47 initrd.img-3.13.0-58-generic
-rw-r--r--  1 root root  9962989 Dec 16 01:47 initrd.img-3.13.0-59-generic
-rw-r--r--  1 root root  9962263 Dec 16 01:47 initrd.img-3.13.0-61-generic
-rw-r--r--  1 root root  9962961 Dec 16 01:46 initrd.img-3.13.0-62-generic
-rw-r--r--  1 root root  9962981 Dec 16 01:46 initrd.img-3.13.0-63-generic
-rw-r--r--  1 root root  9962361 Dec 16 01:46 initrd.img-3.13.0-65-generic
-rw-r--r--  1 root root  9962905 Dec 16 01:46 initrd.img-3.13.0-66-generic
-rw-r--r--  1 root root  9963011 Dec 16 01:46 initrd.img-3.13.0-67-generic
-rw-r--r--  1 root root  9963010 Dec 16 01:46 initrd.img-3.13.0-68-generic
-rw-r--r--  1 root root  9963042 Dec 16 01:46 initrd.img-3.13.0-74-generic
-rw-r--r--  1 root root  9962245 Dec 16 01:46 initrd.img-3.13.0-76-generic
-rw-r--r--  1 root root  9962607 Dec 16 01:46 initrd.img-3.13.0-79-generic
-rw-r--r--  1 root root  9963067 Dec 16 01:46 initrd.img-3.13.0-83-generic
-rw-r--r--  1 root root  9963081 Dec 16 01:45 initrd.img-4.4.0-45-generic
-rw-r--r--  1 root root 37880623 Dec 16 01:45 initrd.img-4.4.0-51-generic
-rw-r--r--  1 root root 37880365 Dec 16 01:47 initrd.img-4.4.0-53-generic
-rw-r--r--  1 root root 37883541 Dec 21 23:23 initrd.img-4.4.0-57-generic
drwx------  2 root root    12288 May 31  2011 lost+found
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  3874377 Nov 24 15:12 System.map-4.4.0-51-generic
-rw-------  1 root root  3874377 Dec  2 13:11 System.map-4.4.0-53-generic
-rw-------  1 root root  3875329 Dec  9 22:04 System.map-4.4.0-57-generic
-rw-------  1 root root  7064208 Nov 24 15:12 vmlinuz-4.4.0-51-generic
-rw-------  1 root root  7065648 Dec  2 13:11 vmlinuz-4.4.0-53-generic
-rw-------  1 root root  7067152 Dec  9 22:04 vmlinuz-4.4.0-57-generic

/boot/grub:
total 2397
drwxr-xr-x 5 root root    8192 Dec 21 23:23 .
drwxr-xr-x 4 root root    6144 Dec 21 23:24 ..
drwxr-xr-x 2 root root    1024 Aug 12  2014 fonts
-rw-r--r-- 1 root root     915 Nov  5 07:28 gfxblacklist.txt
-r--r--r-- 1 root root   15182 Dec 21 23:23 grub.cfg
-rw-r--r-- 1 root root    1024 Dec 21 23:27 grubenv
drwxr-xr-x 2 root root    9216 Aug 12 09:26 i386-pc
drwxr-xr-x 2 root root    1024 Aug 12 09:26 locale
-rw-r--r-- 1 root root 2398585 Aug 12 09:26 unicode.pf2

/boot/grub/fonts:
total 2363
drwxr-xr-x 2 root root    1024 Aug 12  2014 .
drwxr-xr-x 5 root root    8192 Dec 21 23:23 ..
-rw-r--r-- 1 root root 2398585 Aug 12 09:26 unicode.pf2

/boot/grub/i386-pc:
total 2118
drwxr-xr-x 2 root root   9216 Aug 12 09:26 .
drwxr-xr-x 5 root root   8192 Dec 21 23:23 ..
-rw-r--r-- 1 root root   7956 Aug 12 09:26 915resolution.mod
-rw-r--r-- 1 root root  10020 Aug 12 09:26 acpi.mod
-rw-r--r-- 1 root root   1392 Aug 12 09:26 adler32.mod
-rw-r--r-- 1 root root   5720 Aug 12 09:26 affs.mod
-rw-r--r-- 1 root root   6800 Aug 12 09:26 afs.mod
-rw-r--r-- 1 root root  15552 Aug 12 09:26 ahci.mod
-rw-r--r-- 1 root root    704 Aug 12 09:26 all_video.mod
-rw-r--r-- 1 root root   1104 Aug 12 09:26 aout.mod
-rw-r--r-- 1 root root   3008 Aug 12 09:26 archelp.mod
-rw-r--r-- 1 root root   5704 Aug 12 09:26 ata.mod
-rw-r--r-- 1 root root   4360 Aug 12 09:26 at_keyboard.mod
-rw-r--r-- 1 root root   1712 Aug 12 09:26 backtrace.mod
-rw-r--r-- 1 root root   7316 Aug 12 09:26 bfs.mod
-rw-r--r-- 1 root root   4668 Aug 12 09:26 biosdisk.mod
-rw-r--r-- 1 root root   2320 Aug 12 09:26 bitmap.mod
-rw-r--r-- 1 root root   3672 Aug 12 09:26 bitmap_scale.mod
-rw-r--r-- 1 root root   2216 Aug 12 09:26 blocklist.mod
-rw-r--r-- 1 root root    512 Aug 12 09:26 boot.img
-rw-r--r-- 1 root root   2500 Aug 12 09:26 boot.mod
-rw-r--r-- 1 root root  29976 Aug 12 09:26 bsd.mod
-rw-r--r-- 1 root root  14520 Aug 12 09:26 btrfs.mod
-rw-r--r-- 1 root root   2180 Aug 12 09:26 bufio.mod
-rw-r--r-- 1 root root   2984 Aug 12 09:26 cat.mod
-rw-r--r-- 1 root root   3920 Aug 12 09:26 cbfs.mod
-rw-r--r-- 1 root root   3672 Aug 12 09:26 cbls.mod
-rw-r--r-- 1 root root   2492 Aug 12 09:26 cbmemc.mod
-rw-r--r-- 1 root root   1144 Aug 12 09:26 cbtable.mod
-rw-r--r-- 1 root root   2648 Aug 12 09:26 cbtime.mod
-rw-r--r-- 1 root root   3572 Aug 12 09:26 chain.mod
-rw-r--r-- 1 root root   3108 Aug 12 09:26 cmdline_cat_test.mod
-rw-r--r-- 1 root root   1288 Aug 12 09:26 cmosdump.mod
-rw-r--r-- 1 root root   1900 Aug 12 09:26 cmostest.mod
-rw-r--r-- 1 root root   2056 Aug 12 09:26 cmp.mod
-rw-r--r-- 1 root root   3803 Aug 12 09:26 command.lst
-rw-r--r-- 1 root root   2336 Aug 12 09:26 configfile.mod
-rw-r--r-- 1 root root  25159 Aug 12 09:26 core.img
-rw-r--r-- 1 root root   2876 Aug 12 09:26 cpio_be.mod
-rw-r--r-- 1 root root   2776 Aug 12 09:26 cpio.mod
-rw-r--r-- 1 root root   1796 Aug 12 09:26 cpuid.mod
-rw-r--r-- 1 root root   1728 Aug 12 09:26 crc64.mod
-rw-r--r-- 1 root root  10128 Aug 12 09:26 cryptodisk.mod
-rw-r--r-- 1 root root    936 Aug 12 09:26 crypto.lst
-rw-r--r-- 1 root root   4992 Aug 12 09:26 crypto.mod
-rw-r--r-- 1 root root   3952 Aug 12 09:26 cs5536.mod
-rw-r--r-- 1 root root   1860 Aug 12 09:26 datehook.mod
-rw-r--r-- 1 root root   2256 Aug 12 09:26 date.mod
-rw-r--r-- 1 root root   1316 Aug 12 09:26 datetime.mod
-rw-r--r-- 1 root root  10116 Aug 12 09:26 diskfilter.mod
-rw-r--r-- 1 root root   2480 Aug 12 09:26 disk.mod
-rw-r--r-- 1 root root   3908 Aug 12 09:26 div_test.mod
-rw-r--r-- 1 root root   1900 Aug 12 09:26 dm_nv.mod
-rw-r--r-- 1 root root   5448 Aug 12 09:26 drivemap.mod
-rw-r--r-- 1 root root   2028 Aug 12 09:26 echo.mod
-rw-r--r-- 1 root root   6356 Aug 12 09:26 efiemu32.o
-rw-r--r-- 1 root root   9784 Aug 12 09:26 efiemu64.o
-rw-r--r-- 1 root root  24008 Aug 12 09:26 efiemu.mod
-rw-r--r-- 1 root root  15852 Aug 12 09:26 ehci.mod
-rw-r--r-- 1 root root   5168 Aug 12 09:26 elf.mod
-rw-r--r-- 1 root root   1516 Aug 12 09:26 eval.mod
-rw-r--r-- 1 root root   5592 Aug 12 09:26 exfat.mod
-rw-r--r-- 1 root root   1536 Aug 12 09:26 exfctest.mod
-rw-r--r-- 1 root root   5672 Aug 12 09:26 ext2.mod
-rw-r--r-- 1 root root   4620 Aug 12 09:26 extcmd.mod
-rw-r--r-- 1 root root   5720 Aug 12 09:26 fat.mod
-rw-r--r-- 1 root root  16068 Aug 12 09:26 file.mod
-rw-r--r-- 1 root root  12604 Aug 12 09:26 font.mod
-rw-r--r-- 1 root root   2724 Aug 12 09:26 freedos.mod
-rw-r--r-- 1 root root   2624 Aug 12 09:26 fshelp.mod
-rw-r--r-- 1 root root    214 Aug 12 09:26 fs.lst
-rw-r--r-- 1 root root  96952 Aug 12 09:26 functional_test.mod
-rw-r--r-- 1 root root   1740 Aug 12 09:26 gcry_arcfour.mod
-rw-r--r-- 1 root root   8292 Aug 12 09:26 gcry_blowfish.mod
-rw-r--r-- 1 root root  34208 Aug 12 09:26 gcry_camellia.mod
-rw-r--r-- 1 root root  16548 Aug 12 09:26 gcry_cast5.mod
-rw-r--r-- 1 root root   3024 Aug 12 09:26 gcry_crc.mod
-rw-r--r-- 1 root root  19376 Aug 12 09:26 gcry_des.mod
-rw-r--r-- 1 root root   2356 Aug 12 09:26 gcry_dsa.mod
-rw-r--r-- 1 root root   3036 Aug 12 09:26 gcry_idea.mod
-rw-r--r-- 1 root root   3232 Aug 12 09:26 gcry_md4.mod
-rw-r--r-- 1 root root   3852 Aug 12 09:26 gcry_md5.mod
-rw-r--r-- 1 root root   2592 Aug 12 09:26 gcry_rfc2268.mod
-rw-r--r-- 1 root root  19296 Aug 12 09:26 gcry_rijndael.mod
-rw-r--r-- 1 root root   8304 Aug 12 09:26 gcry_rmd160.mod
-rw-r--r-- 1 root root   2176 Aug 12 09:26 gcry_rsa.mod
-rw-r--r-- 1 root root  15484 Aug 12 09:26 gcry_seed.mod
-rw-r--r-- 1 root root  17072 Aug 12 09:26 gcry_serpent.mod
-rw-r--r-- 1 root root   8012 Aug 12 09:26 gcry_sha1.mod
-rw-r--r-- 1 root root   4416 Aug 12 09:26 gcry_sha256.mod
-rw-r--r-- 1 root root   9292 Aug 12 09:26 gcry_sha512.mod
-rw-r--r-- 1 root root  12748 Aug 12 09:26 gcry_tiger.mod
-rw-r--r-- 1 root root  37348 Aug 12 09:26 gcry_twofish.mod
-rw-r--r-- 1 root root  24980 Aug 12 09:26 gcry_whirlpool.mod
-rw-r--r-- 1 root root  25308 Aug 12 09:26 gdb.mod
-rw-r--r-- 1 root root   5852 Aug 12 09:26 geli.mod
-rw-r--r-- 1 root root   4980 Aug 12 09:26 gettext.mod
-rw-r--r-- 1 root root  39296 Aug 12 09:26 gfxmenu.mod
-rw-r--r-- 1 root root   2960 Aug 12 09:26 gfxterm_background.mod
-rw-r--r-- 1 root root   5092 Aug 12 09:26 gfxterm_menu.mod
-rw-r--r-- 1 root root  10044 Aug 12 09:26 gfxterm.mod
-rw-r--r-- 1 root root   3884 Aug 12 09:26 gptsync.mod
-rw-r--r-- 1 root root   8456 Aug 12 09:26 gzio.mod
-rw-r--r-- 1 root root   4572 Aug 12 09:26 halt.mod
-rw-r--r-- 1 root root   5324 Aug 12 09:26 hashsum.mod
-rw-r--r-- 1 root root   7300 Aug 12 09:26 hdparm.mod
-rw-r--r-- 1 root root   1276 Aug 12 09:26 hello.mod
-rw-r--r-- 1 root root   2624 Aug 12 09:26 help.mod
-rw-r--r-- 1 root root   3236 Aug 12 09:26 hexdump.mod
-rw-r--r-- 1 root root   7324 Aug 12 09:26 hfs.mod
-rw-r--r-- 1 root root   3100 Aug 12 09:26 hfspluscomp.mod
-rw-r--r-- 1 root root   7648 Aug 12 09:26 hfsplus.mod
-rw-r--r-- 1 root root   5628 Aug 12 09:26 http.mod
-rw-r--r-- 1 root root  47292 Aug 12 09:26 hwmatch.mod
-rw-r--r-- 1 root root   2928 Aug 12 09:26 iorw.mod
-rw-r--r-- 1 root root   8656 Aug 12 09:26 iso9660.mod
-rw-r--r-- 1 root root   6168 Aug 12 09:26 jfs.mod
-rw-r--r-- 1 root root   6280 Aug 12 09:26 jpeg.mod
-rw-r--r-- 1 root root   5112 Aug 12 09:26 keylayouts.mod
-rw-r--r-- 1 root root   2044 Aug 12 09:26 keystatus.mod
-rw-r--r-- 1 root root   6608 Aug 12 09:26 ldm.mod
-rw-r--r-- 1 root root  29816 Aug 12 09:26 legacycfg.mod
-rw-r--r-- 1 root root  14536 Aug 12 09:26 legacy_password_test.mod
-rw-r--r-- 1 root root   8048 Aug 12 09:26 linux16.mod
-rw-r--r-- 1 root root  13184 Aug 12 09:26 linux.mod
-rw-r--r-- 1 root root   5924 Aug 12 09:26 loadenv.mod
-rw-r--r-- 1 root root   3056 Aug 12 09:26 loopback.mod
-rw-r--r-- 1 root root   4872 Aug 12 09:26 lsacpi.mod
-rw-r--r-- 1 root root   2352 Aug 12 09:26 lsapm.mod
-rw-r--r-- 1 root root   1884 Aug 12 09:26 lsmmap.mod
-rw-r--r-- 1 root root   4136 Aug 12 09:26 ls.mod
-rw-r--r-- 1 root root   4928 Aug 12 09:26 lspci.mod
-rw-r--r-- 1 root root   6724 Aug 12 09:26 luks.mod
-rw-r--r-- 1 root root   6776 Aug 12 09:26 lvm.mod
-rw-r--r-- 1 root root   8760 Aug 12 09:26 lzopio.mod
-rw-r--r-- 1 root root   3368 Aug 12 09:26 macbless.mod
-rw-r--r-- 1 root root   7624 Aug 12 09:26 macho.mod
-rw-r--r-- 1 root root   2124 Aug 12 09:26 mda_text.mod
-rw-r--r-- 1 root root   2084 Aug 12 09:26 mdraid09_be.mod
-rw-r--r-- 1 root root   2012 Aug 12 09:26 mdraid09.mod
-rw-r--r-- 1 root root   2036 Aug 12 09:26 mdraid1x.mod
-rw-r--r-- 1 root root   2092 Aug 12 09:26 memdisk.mod
-rw-r--r-- 1 root root   2920 Aug 12 09:26 memrw.mod
-rw-r--r-- 1 root root   3480 Aug 12 09:26 minicmd.mod
-rw-r--r-- 1 root root   3808 Aug 12 09:26 minix2_be.mod
-rw-r--r-- 1 root root   3644 Aug 12 09:26 minix2.mod
-rw-r--r-- 1 root root   3744 Aug 12 09:26 minix3_be.mod
-rw-r--r-- 1 root root   3612 Aug 12 09:26 minix3.mod
-rw-r--r-- 1 root root   3708 Aug 12 09:26 minix_be.mod
-rw-r--r-- 1 root root   3580 Aug 12 09:26 minix.mod
-rw-r--r-- 1 root root   8620 Aug 12 09:26 mmap.mod
-rw-r--r-- 1 root root   5191 Aug 12 09:26 moddep.lst
-rw-r--r-- 1 root root   2308 Aug 12 09:26 modinfo.sh
-rw-r--r-- 1 root root   2468 Aug 12 09:26 morse.mod
-rw-r--r-- 1 root root  27852 Aug 12 09:26 mpi.mod
-rw-r--r-- 1 root root   2528 Aug 12 09:26 msdospart.mod
-rw-r--r-- 1 root root  13504 Aug 12 09:26 multiboot2.mod
-rw-r--r-- 1 root root  13156 Aug 12 09:26 multiboot.mod
-rw-r--r-- 1 root root   4112 Aug 12 09:26 nativedisk.mod
-rw-r--r-- 1 root root  46120 Aug 12 09:26 net.mod
-rw-r--r-- 1 root root   3032 Aug 12 09:26 newc.mod
-rw-r--r-- 1 root root   6712 Aug 12 09:26 nilfs2.mod
-rw-r--r-- 1 root root 115092 Aug 12 09:26 normal.mod
-rw-r--r-- 1 root root   4456 Aug 12 09:26 ntfscomp.mod
-rw-r--r-- 1 root root   9908 Aug 12 09:26 ntfs.mod
-rw-r--r-- 1 root root   2616 Aug 12 09:26 ntldr.mod
-rw-r--r-- 1 root root   2840 Aug 12 09:26 odc.mod
-rw-r--r-- 1 root root   1592 Aug 12 09:26 offsetio.mod
-rw-r--r-- 1 root root  10504 Aug 12 09:26 ohci.mod
-rw-r--r-- 1 root root   1740 Aug 12 09:26 part_acorn.mod
-rw-r--r-- 1 root root   1968 Aug 12 09:26 part_amiga.mod
-rw-r--r-- 1 root root   2220 Aug 12 09:26 part_apple.mod
-rw-r--r-- 1 root root   2852 Aug 12 09:26 part_bsd.mod
-rw-r--r-- 1 root root   1848 Aug 12 09:26 part_dfly.mod
-rw-r--r-- 1 root root   1564 Aug 12 09:26 part_dvh.mod
-rw-r--r-- 1 root root   2460 Aug 12 09:26 part_gpt.mod
-rw-r--r-- 1 root root    111 Aug 12 09:26 partmap.lst
-rw-r--r-- 1 root root   2360 Aug 12 09:26 part_msdos.mod
-rw-r--r-- 1 root root   1876 Aug 12 09:26 part_plan.mod
-rw-r--r-- 1 root root   1600 Aug 12 09:26 part_sun.mod
-rw-r--r-- 1 root root   1692 Aug 12 09:26 part_sunpc.mod
-rw-r--r-- 1 root root     17 Aug 12 09:26 parttool.lst
-rw-r--r-- 1 root root   4664 Aug 12 09:26 parttool.mod
-rw-r--r-- 1 root root   1960 Aug 12 09:26 password.mod
-rw-r--r-- 1 root root   2880 Aug 12 09:26 password_pbkdf2.mod
-rw-r--r-- 1 root root   4824 Aug 12 09:26 pata.mod
-rw-r--r-- 1 root root   1540 Aug 12 09:26 pbkdf2.mod
-rw-r--r-- 1 root root   2248 Aug 12 09:26 pbkdf2_test.mod
-rw-r--r-- 1 root root   2548 Aug 12 09:26 pcidump.mod
-rw-r--r-- 1 root root   1464 Aug 12 09:26 pci.mod
-rw-r--r-- 1 root root   6380 Aug 12 09:26 plan9.mod
-rw-r--r-- 1 root root   2512 Aug 12 09:26 play.mod
-rw-r--r-- 1 root root   7496 Aug 12 09:26 png.mod
-rw-r--r-- 1 root root   1628 Aug 12 09:26 priority_queue.mod
-rw-r--r-- 1 root root   2728 Aug 12 09:26 probe.mod
-rw-r--r-- 1 root root   2224 Aug 12 09:26 procfs.mod
-rw-r--r-- 1 root root   2164 Aug 12 09:26 progress.mod
-rw-r--r-- 1 root root   2732 Aug 12 09:26 pxechain.mod
-rw-r--r-- 1 root root   3908 Aug 12 09:26 pxe.mod
-rw-r--r-- 1 root root   1488 Aug 12 09:26 raid5rec.mod
-rw-r--r-- 1 root root   2288 Aug 12 09:26 raid6rec.mod
-rw-r--r-- 1 root root   1516 Aug 12 09:26 read.mod
-rw-r--r-- 1 root root   1788 Aug 12 09:26 reboot.mod
-rw-r--r-- 1 root root  51152 Aug 12 09:26 regexp.mod
-rw-r--r-- 1 root root   8896 Aug 12 09:26 reiserfs.mod
-rw-r--r-- 1 root root  15044 Aug 12 09:26 relocator.mod
-rw-r--r-- 1 root root   4248 Aug 12 09:26 romfs.mod
-rw-r--r-- 1 root root   4804 Aug 12 09:26 scsi.mod
-rw-r--r-- 1 root root   3284 Aug 12 09:26 search_fs_file.mod
-rw-r--r-- 1 root root   3236 Aug 12 09:26 search_fs_uuid.mod
-rw-r--r-- 1 root root   3184 Aug 12 09:26 search_label.mod
-rw-r--r-- 1 root root   3692 Aug 12 09:26 search.mod
-rw-r--r-- 1 root root   7216 Aug 12 09:26 sendkey.mod
-rw-r--r-- 1 root root   7776 Aug 12 09:26 serial.mod
-rw-r--r-- 1 root root    708 Aug 12 09:26 setjmp.mod
-rw-r--r-- 1 root root   1772 Aug 12 09:26 setjmp_test.mod
-rw-r--r-- 1 root root   5424 Aug 12 09:26 setpci.mod
-rw-r--r-- 1 root root   5204 Aug 12 09:26 sfs.mod
-rw-r--r-- 1 root root   6544 Aug 12 09:26 signature_test.mod
-rw-r--r-- 1 root root   2344 Aug 12 09:26 sleep.mod
-rw-r--r-- 1 root root   2396 Aug 12 09:26 sleep_test.mod
-rw-r--r-- 1 root root   2156 Aug 12 09:26 spkmodem.mod
-rw-r--r-- 1 root root   6912 Aug 12 09:26 squash4.mod
-rw-r--r-- 1 root root  17144 Aug 12 09:26 syslinuxcfg.mod
-rw-r--r-- 1 root root   3384 Aug 12 09:26 tar.mod
-rw-r--r-- 1 root root    202 Aug 12 09:26 terminal.lst
-rw-r--r-- 1 root root   4416 Aug 12 09:26 terminal.mod
-rw-r--r-- 1 root root  11760 Aug 12 09:26 terminfo.mod
-rw-r--r-- 1 root root   1408 Aug 12 09:26 test_blockarg.mod
-rw-r--r-- 1 root root   2768 Aug 12 09:26 testload.mod
-rw-r--r-- 1 root root   5204 Aug 12 09:26 test.mod
-rw-r--r-- 1 root root   2396 Aug 12 09:26 testspeed.mod
-rw-r--r-- 1 root root   5376 Aug 12 09:26 tftp.mod
-rw-r--r-- 1 root root   4528 Aug 12 09:26 tga.mod
-rw-r--r-- 1 root root   1580 Aug 12 09:26 time.mod
-rw-r--r-- 1 root root   1764 Aug 12 09:26 trig.mod
-rw-r--r-- 1 root root   2468 Aug 12 09:26 tr.mod
-rw-r--r-- 1 root root   3612 Aug 12 09:26 truecrypt.mod
-rw-r--r-- 1 root root   1276 Aug 12 09:26 true.mod
-rw-r--r-- 1 root root   7880 Aug 12 09:26 udf.mod
-rw-r--r-- 1 root root   5900 Aug 12 09:26 ufs1_be.mod
-rw-r--r-- 1 root root   5516 Aug 12 09:26 ufs1.mod
-rw-r--r-- 1 root root   5612 Aug 12 09:26 ufs2.mod
-rw-r--r-- 1 root root   6760 Aug 12 09:26 uhci.mod
-rw-r--r-- 1 root root   3912 Aug 12 09:26 usb_keyboard.mod
-rw-r--r-- 1 root root  10632 Aug 12 09:26 usb.mod
-rw-r--r-- 1 root root   7164 Aug 12 09:26 usbms.mod
-rw-r--r-- 1 root root   2112 Aug 12 09:26 usbserial_common.mod
-rw-r--r-- 1 root root   2428 Aug 12 09:26 usbserial_ftdi.mod
-rw-r--r-- 1 root root   2760 Aug 12 09:26 usbserial_pl2303.mod
-rw-r--r-- 1 root root   1608 Aug 12 09:26 usbserial_usbdebug.mod
-rw-r--r-- 1 root root   3668 Aug 12 09:26 usbtest.mod
-rw-r--r-- 1 root root   9976 Aug 12 09:26 vbe.mod
-rw-r--r-- 1 root root  11692 Aug 12 09:26 verify.mod
-rw-r--r-- 1 root root   5144 Aug 12 09:26 vga.mod
-rw-r--r-- 1 root root   2252 Aug 12 09:26 vga_text.mod
-rw-r--r-- 1 root root   5768 Aug 12 09:26 video_bochs.mod
-rw-r--r-- 1 root root   6184 Aug 12 09:26 video_cirrus.mod
-rw-r--r-- 1 root root   5760 Aug 12 09:26 video_colors.mod
-rw-r--r-- 1 root root  21368 Aug 12 09:26 video_fb.mod
-rw-r--r-- 1 root root   4048 Aug 12 09:26 videoinfo.mod
-rw-r--r-- 1 root root     33 Aug 12 09:26 video.lst
-rw-r--r-- 1 root root   6212 Aug 12 09:26 video.mod
-rw-r--r-- 1 root root   2452 Aug 12 09:26 videotest_checksum.mod
-rw-r--r-- 1 root root   4336 Aug 12 09:26 videotest.mod
-rw-r--r-- 1 root root   7500 Aug 12 09:26 xfs.mod
-rw-r--r-- 1 root root  27072 Aug 12 09:26 xnu.mod
-rw-r--r-- 1 root root   2208 Aug 12 09:26 xnu_uuid.mod
-rw-r--r-- 1 root root   2084 Aug 12 09:26 xnu_uuid_test.mod
-rw-r--r-- 1 root root  15868 Aug 12 09:26 xzio.mod
-rw-r--r-- 1 root root   5564 Aug 12 09:26 zfscrypt.mod
-rw-r--r-- 1 root root   6664 Aug 12 09:26 zfsinfo.mod
-rw-r--r-- 1 root root  40384 Aug 12 09:26 zfs.mod

/boot/grub/locale:
total 16
drwxr-xr-x 2 root root 1024 Aug 12 09:26 .
drwxr-xr-x 5 root root 8192 Dec 21 23:23 ..
-rw-r--r-- 1 root root 1017 Aug 12 09:26 en_AU.mo
-rw-r--r-- 1 root root  553 Aug 12 09:26 en_CA.mo
-rw-r--r-- 1 root root 4874 Aug 12 09:26 en_GB.mo

/boot/lost+found:
total 18
drwx------ 2 root root 12288 May 31  2011 .
drwxr-xr-x 4 root root  6144 Dec 21 23:24 ..
ron@Cronluath:~$ 

```

---

### Post by ajgreeny on 2016-12-22
It looks as if you still have quite a lot of cruft from an installation of 14.04
```
-rw-r--r--  1 root root  9962998 Dec 16 01:47 initrd.img-3.13.0-57-generic
-rw-r--r--  1 root root  9962572 Dec 16 01:47 initrd.img-3.13.0-58-generic
-rw-r--r--  1 root root  9962989 Dec 16 01:47 initrd.img-3.13.0-59-generic
-rw-r--r--  1 root root  9962263 Dec 16 01:47 initrd.img-3.13.0-61-generic
-rw-r--r--  1 root root  9962961 Dec 16 01:46 initrd.img-3.13.0-62-generic
-rw-r--r--  1 root root  9962981 Dec 16 01:46 initrd.img-3.13.0-63-generic
-rw-r--r--  1 root root  9962361 Dec 16 01:46 initrd.img-3.13.0-65-generic
-rw-r--r--  1 root root  9962905 Dec 16 01:46 initrd.img-3.13.0-66-generic
-rw-r--r--  1 root root  9963011 Dec 16 01:46 initrd.img-3.13.0-67-generic
-rw-r--r--  1 root root  9963010 Dec 16 01:46 initrd.img-3.13.0-68-generic
-rw-r--r--  1 root root  9963042 Dec 16 01:46 initrd.img-3.13.0-74-generic
-rw-r--r--  1 root root  9962245 Dec 16 01:46 initrd.img-3.13.0-76-generic
-rw-r--r--  1 root root  9962607 Dec 16 01:46 initrd.img-3.13.0-79-generic
-rw-r--r--  1 root root  9963067 Dec 16 01:46 initrd.img-3.13.0-83-generic
```
and I have to admit defeat about the best way to remove all of that, which I don't think is going to be possible in the package manager as you installed all of those using another installation; your 16.04 will not know anything about them so they will not be removable using it, as far as I'm aware, and I don't think ```
sudo apt-get autoremove
``` will help either.

---

