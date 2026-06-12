---
title: "dependency problems on installing/patching"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by cwacker on 2008-06-10
Every time i apt-get a program or uses the built in "security-patcher" i get this error, i haven't noticed anything not working but I'm afraid i will eventually...

Ive tried to reconfigure some packages and so on and reinstalling linux-restricted-modules-generic_2.6.24.18.20_i386.deb but i can't get it to work.. Do i need to mention I'm new to Linux..

I've been looking through the forums but I haven't found a solution that worked for me yet so please bear with me..

---

### Post by Partyboi2 on 2008-06-11
Have you run  out of disk space? You can check by opening a terminal (Applications>Accessories>Terminal) and type
```
df -h
```

---

### Post by cwacker on 2008-06-18
df -h results in this:

/dev/sda6              52G   17G   33G  33% /
varrun                501M  108K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M   64K  501M   1% /dev
devshm                501M  1.1M  500M   1% /dev/shm
lrm                   501M   38M  464M   8% /lib/modules/2.6.24-17-generic/volatile
/dev/sda3              46M   44M     0 100% /boot
gvfs-fuse-daemon       52G   17G   33G  33% /home/gundam/.gvfs


 however, when i run dpkg --configure -a i get this:

```
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-19-generic:
 linux-restricted-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not installed.
dpkg: error processing linux-restricted-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-19-generic:
 linux-ubuntu-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not installed.
dpkg: error processing linux-ubuntu-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not installed.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-19-generic; however:
  Package linux-ubuntu-modules-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-19-generic; however:
  Package linux-restricted-modules-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.19.21); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.19.21); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.24-18-generic (2.6.24-18.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-18-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-18-generic:
 linux-restricted-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-18-generic:
 linux-ubuntu-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: subprocess post-installation script returned error exit status 1
```

Here I  have found the following:

update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic
Failed to create initrd image.


Does this mean that the problem is the /boot partition (yes, it has its own) is 100% full? I didn't thought that the system would place files on /boot.:confused:


EDIT:
So I was thinking if this is the problem (which I think it is but I'm a noob so I'm not sure) I'm willing to sacrifice those 50 mb and move /boot to the main partition and just flag the then former /boot-partition as unallocated space. Would this solve my problems and how would I go trough with it?

---

### Post by Partyboi2 on 2008-06-18
A few options, you can  remove old kernel files through synaptic package manager to regain some space. Or you can increase the size of your /boot partition using gparted.

---

### Post by cwacker on 2008-06-18
If I increase /boot, will I eventually encounter the same problem, if it just gets filled with old kernel files as time and upgrades go by?

---

### Post by Partyboi2 on 2008-06-18
Yes, unless you remove the old kernel files.

---

### Post by cwacker on 2008-06-19
I can't run synaptic (tells med to run dkpg --configure -a wich i can't run because of the missing space), and gparted won't let me increase /boot...

Anyway to rm files in boot? i use 2.6.24-17 now, but i dont dare remove 2.6.24-16.

ls -Rsh /boot gives me this:


/boot:
total 39M
416K abi-2.6.24-16-generic	       7.2M initrd.img-2.6.24-17-generic.bak
416K abi-2.6.24-17-generic	        12K lost+found
416K abi-2.6.24-18-generic	       102K memtest86+.bin
 80K config-2.6.24-16-generic	       884K System.map-2.6.24-16-generic
 80K config-2.6.24-17-generic	       889K System.map-2.6.24-17-generic
 80K config-2.6.24-18-generic	       889K System.map-2.6.24-18-generic
1.0K grub			       1.9M vmlinuz-2.6.24-16-generic
7.6M initrd.img-2.6.24-16-generic      1.9M vmlinuz-2.6.24-17-generic
7.1M initrd.img-2.6.24-16-generic.bak  1.9M vmlinuz-2.6.24-18-generic
7.2M initrd.img-2.6.24-17-generic

/boot/grub:
total 181K
1.0K default		9.0K jfs_stage1_5     10K reiserfs_stage1_5
1.0K device.map		6.0K menu.lst	     1.0K stage1
8.0K e2fs_stage1_5	6.0K menu.lst~	     107K stage2
8.0K fat_stage1_5	5.0K menu.lst_bak     10K xfs_stage1_5
1.0K installed-version	8.0K minix_stage1_5

/boot/lost+found:
total 0

---

