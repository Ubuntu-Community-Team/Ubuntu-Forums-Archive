---
title: "[SOLVED] Failed kernel upgrade"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by SkonesMickLoud on 2008-06-18
I built and installed the 2.6.25.5 kernel, and all seemed to go well until reboot.  When everything's loaded I notice that I'm still running my old 2.6.24-19.  So I reboot again, go into GRUB and there is no option for 2.6.25.5.  Now, whenever I try to do anything with apt-get, aptitude, or Synaptic I get some form of the following error:

```

skones@skones-laptop:~$ sudo apt-get install --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-19-generic
0 upgraded, 0 newly installed, 1 to remove and 26 not upgraded.
2 not fully installed or removed.
After this operation, 15.6MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 152899 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-19-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-19-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-19-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-19-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It's telling me that I have no space left on the disk, yet I have 3.5Gb clear on / and another ~135Gb on /home.

Any ideas?

[EDIT]

Now Synaptic is giving me this when I try to apply updates:

```

Not enough free disk space

The upgrade aborts now. The upgrade needs a total of 31.5M free space on disk '/boot'. Please free at least an additional 31.5M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

```

Like I said before, "sudo apt-get clean" gives the same error.

---

### Post by iaculallad on 2008-06-18
Post the output of:

```
df -h
```

---

### Post by SkonesMickLoud on 2008-06-18
> **iaculallad said:**
> Post the output of:

```
df -h
```

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.9G  5.9G  3.5G  63% /
varrun                760M  108K  760M   1% /var/run
varlock               760M     0  760M   0% /var/lock
udev                  760M   48K  760M   1% /dev
devshm                760M   12K  760M   1% /dev/shm
lrm                   760M   38M  723M   5% /lib/modules/2.6.24-16-generic/volatile
/dev/sda4              99M   44M   51M  47% /boot
/dev/sda3             134G  2.3G  125G   2% /home
gvfs-fuse-daemon      9.9G  5.9G  3.5G  63% /home/skones/.gvfs

```

---

### Post by iaculallad on 2008-06-18
> **SkonesMickLoud said:**
> ```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.9G  5.9G  3.5G  63% /
varrun                760M  108K  760M   1% /var/run
varlock               760M     0  760M   0% /var/lock
udev                  760M   48K  760M   1% /dev
devshm                760M   12K  760M   1% /dev/shm
lrm                   760M   38M  723M   5% /lib/modules/2.6.24-16-generic/volatile
/dev/sda4              99M   44M   51M  47% /boot
/dev/sda3             134G  2.3G  125G   2% /home
gvfs-fuse-daemon      9.9G  5.9G  3.5G  63% /home/skones/.gvfs

```

Try to delete *.bak files on your /boot to free more space (boot directory only has 51MB remaining) then retry your **sudo apt-get install --fix-missing** terminal command.

```
cd /boot
sudo rm *.bak
sudo apt-get install --fix-missing
```

---

### Post by SkonesMickLoud on 2008-06-18
Now I get:

```

skones@skones-laptop:/boot$ sudo apt-get install --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.25 (386) ...
Internal Error: Could not find image (/boot/vmlinuz-2.6.25)
dpkg: error processing linux-image-2.6.25 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.25
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Synaptic and apt-get now look for, and can't find 2.6.25.

---

### Post by iaculallad on 2008-06-18
Try to follow this [guide]("http://ubuntuforums.org/showthread.php?t=311158&highlight=kernel") for the Failed Kernel.

---

### Post by SkonesMickLoud on 2008-06-18
I'll give it a shot tomorrow, but following the first instruction is a no-go as I can't apt-get.

I'm thinking I'll wipe / and start anew.  \\:D/ for separate / and /home!!!

Thanks for the try.

---

