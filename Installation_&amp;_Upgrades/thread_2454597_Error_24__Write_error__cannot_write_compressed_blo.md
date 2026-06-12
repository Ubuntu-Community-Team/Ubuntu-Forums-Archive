---
title: "Error 24 : Write error : cannot write compressed block"
date: 2020-12-02
forum: Installation &amp; Upgrades
---

### Post by wseyller on 2020-12-02
recently upgraded from an older version of Ubuntu.

Trying to run security updates  but I am receiving an output as shown below.  Think it is something to do with the kernal images but unsure how to deal with it exactly.

```
Setting up initramfs-tools (0.136ubuntu6.3) ...
update-initramfs: deferring update (triggered activated)
Processing triggers for initramfs-tools (0.136ubuntu6.3)
update-initramfs: Generating /boot/initrd.img-5.4.0.52-generic
Error 24 : Write error : cannot write compressed block
E: mkinitramfs failure cpio 141 lz4 -9 -I 24
update-initramfs: failed for /boot/initrd.img-5.4.0-52-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
installed initramfs-tools package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Ubuntu version:  20.04.1 LTS

: uname -r
```
4.4.0-193-generic
```

```
: dpkg --list | grep linux-image
ii  linux-image-4.15.0-122-generic         4.15.0-122.124                              amd64        Signed kernel image generic
rc  linux-image-4.2.0-27-generic           4.2.0-27.32~14.04.1                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-42-generic           4.2.0-42.49~14.04.1                         amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-101-generic          4.4.0-101.124                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-104-generic          4.4.0-104.127                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-109-generic          4.4.0-109.132                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-112-generic          4.4.0-112.135                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-116-generic          4.4.0-116.140                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-119-generic          4.4.0-119.143                               amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-193-generic          4.4.0-193.224                               amd64        Signed kernel image generic
rc  linux-image-4.4.0-79-generic           4.4.0-79.100                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-96-generic           4.4.0-96.119                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-5.4.0-52-generic           5.4.0-52.57                                 amd64        Signed kernel image generic
rc  linux-image-extra-4.2.0-27-generic     4.2.0-27.32~14.04.1                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-42-generic     4.2.0-42.49~14.04.1                         amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-101-generic    4.4.0-101.124                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-104-generic    4.4.0-104.127                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-109-generic    4.4.0-109.132                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-112-generic    4.4.0-112.135                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-116-generic    4.4.0-116.140                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-119-generic    4.4.0-119.143                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-135-generic    4.4.0-135.161                               amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-79-generic     4.4.0-79.100                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-96-generic     4.4.0-96.119                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                    5.4.0.52.55                                 amd64        Generic Linux kernel image
```

---

### Post by SeijiSensei on 2020-12-02
There are a couple of possible reasons:

1) You don't have permissions to write into /boot. Did you run the updater as root with sudo?  Is /boot and all the files it contains owned by root?

2)  If /boot resides on a separate partition from the root filesystem it can fill up with outdated kernels.  Try running "sudo apt autoremove" before installing.

3) Possibly the drive itself has problems that are leading to this error. Can you write files in other locations on the disk? Can you write a file into /boot using the nano editor ("sudo nano /boot/testfile")?

---

### Post by wseyller on 2020-12-02
I do use sudo to run the updater.  This process I normally do every month for patching.  After the upgrade to 20.04 it now throws the error.


I tried running "sudo apt autoremove".  I remember trying this before but it doesn't help.
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 65 not upgraded.


I was able to write to successfully write to a file with ""sudo nano /boot/testfile" and was able to save it.

---

### Post by SeijiSensei on 2020-12-02
Is /boot on a separate partition? Are you short of free space?

Ubuntu is supposed to leave just two sets of kernel files when updating, but that doesn't always seem to work completely, and "autoremove" doesn't find the residual files. Right now I have some extra initrd's and other files from older kernels taking up space.

I used to give /boot 256 MB when I assigned it to a separate partition. Now I use 512 MB to avoid running out of space.

---

### Post by wseyller on 2020-12-03
Looks like I got it corrected.  Thanks for your help.

**Checked the partitions**
NAME                         MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
fd0                            2:0    1    4K  0 disk
sda                            8:0    0  100G  0 disk
&#9500;&#9472;sda1                         8:1    0  243M  0 part /boot
&#9500;&#9472;sda2                         8:2    0    1K  0 part
&#9492;&#9472;sda5                         8:5    0 99.8G  0 part
  &#9500;&#9472;media--prod01--vg-root   252:0    0 91.8G  0 lvm  /
  &#9492;&#9472;media--prod01--vg-swap_1 252:1    0    8G  0 lvm  [SWAP]
sr0                           11:0    1  579M  0 rom

**Check the space available.  Looks like space is low on the boot partition.**
Filesystem                         1K-blocks     Used Available Use% Mounted on
udev                                 4067684        0   4067684   0% /dev
tmpfs                                 817504      824    816680   1% /run
/dev/mapper/media--prod01--vg-root  94558060 23675808  66055936  27% /
tmpfs                                4087508        0   4087508   0% /dev/shm
tmpfs                                   5120        0      5120   0% /run/lock
tmpfs                                4087508        0   4087508   0% /sys/fs/cgroup
/dev/sda1                             240972   193723     34808  85% /boot
tmpfs                                 817500        0    817500   0% /run/user/1005


**Checked the kernal in use**
4.4.0-193-generic


**Checked list of installed kernals**
ii  linux-image-4.15.0-122-generic          4.15.0-122.124      amd64        Signed kernel image generic
ii  linux-image-4.4.0-193-generic           4.4.0-193.224       amd64        Signed kernel image generic
ii  linux-image-5.4.0-52-generic            5.4.0-52.57         amd64        Signed kernel image generic
ii  linux-image-generic                     5.4.0.52.55         amd64        Generic Linux kernel image




**Removed linux-image-4.15.0-122-generic**
: sudo apt-get remove linux-image-4.15.0-122-generic


**Rechecked list of installed kernals**
ii  linux-image-4.4.0-193-generic           4.4.0-193.224       amd64        Signed kernel image generic
ii  linux-image-5.4.0-52-generic            5.4.0-52.57         amd64        Signed kernel image generic
ii  linux-image-generic                     5.4.0.52.55         amd64        Generic Linux kernel image




**Checked the space again. Boot partition now has more space available.**
Filesystem                         1K-blocks     Used Available Use% Mounted on
udev                                 4067684        0   4067684   0% /dev
tmpfs                                 817504      836    816668   1% /run
/dev/mapper/media--prod01--vg-root  94558060 23497408  66234336  27% /
tmpfs                                4087508        0   4087508   0% /dev/shm
tmpfs                                   5120        0      5120   0% /run/lock
tmpfs                                4087508        0   4087508   0% /sys/fs/cgroup
/dev/sda1                             240972   136046     92485  60% /boot
tmpfs                                 817500        0    817500   0% /run/user/1005

---

### Post by ActionParsnip on 2020-12-03
You can clear that up with:
```

sudo dpkg -P `dpkg --list | grep linux-image | grep ^rc | awk {'print $2'}`

```
It will clean up the list for you. Leaving only the fully installed kernels. You can then remove excess kernels (NOT the one you are running) to free up ~120Mb per kernel.

---

