---
title: "Insufficient disk space issue on CUDA Toolkit installation"
date: 2018-04-29
forum: Installation &amp; Upgrades
---

### Post by ubuntini2 on 2018-04-29
[COLOR=#111111][FONT=Ubuntu]Tried repeatedly to install latest Nvidia CUDA 9.1 Toolkit but always get a 'not enough disk space' error at the end, even if I target external drive with over 400GB available! What gives?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]If I run df -h in the command line I see
[/FONT][/COLOR]```

Filesystem      Size  Used Avail Use% Mounted on
udev             32G     0   32G   0% /dev
tmpfs           6.3G  147M  6.2G   3% /run
/dev/sdb2        40G   35G  2.4G  94% /
tmpfs            32G   55M   32G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs            32G     0   32G   0% /sys/fs/cgroup
/dev/sdb3       630G   54G  545G   9% /home
/dev/sdb1       549M  5.8M  544M   2% /boot/efi
tmpfs           6.3G   52K  6.3G   1% /run/user/1000
/dev/sda1       1.9T  1.5T  427G  78% /media/jim/Seagate_1
```

---

### Post by ubfan1 on 2018-04-29
How are you trying to install the toolkit, .run file or .deb?  The deb may be extracted to  a location 
```
dpkg-deb -x package.deb output_dir
```
and the run file may use the non-interactive method:

```
./runfile.run --silent \
--toolkit --toolkitpath=/my/new/toolkit \
--samples --samplespath=/my/new/samples
```


See [https://docs.google.com/viewer?url=https%3A%2F%2Fdeveloper.download.nvidia.com%2Fcompute%2Fcuda%2F9.1%2FProd%2Fdocs%2Fsidebar%2FCUDA_Installation_Guide_Linux.pdf&pdf=true](https://docs.google.com/viewer?url=https%3A%2F%2Fdeveloper.download.nvidia.com%2Fcompute%2Fcuda%2F9.1%2FProd%2Fdocs%2Fsidebar%2FCUDA_Installation_Guide_Linux.pdf&pdf=true)
for more details if necessary.

---

