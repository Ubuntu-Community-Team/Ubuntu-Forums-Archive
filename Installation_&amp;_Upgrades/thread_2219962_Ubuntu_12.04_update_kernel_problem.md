---
title: "Ubuntu 12.04 update kernel problem"
date: 2014-04-26
forum: Installation &amp; Upgrades
---

### Post by erotavlas on 2014-04-26
Hi,

I have Ubuntu 12.04 64 bit with several kernel versions installed. All except one (3.14.x) are installed from official repository with the command 
```

sudo apt-get install linux-headers-generic-lts-* linux-image-generic-lts-*

```
where * is the name of the version of Ubuntu.
I don't know if something is changed, but now I'm not able to update the kernel since I receive the following erros.

```

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-image-generic-lts-saucy linux-signed-generic-lts-raring linux-signed-image-generic-lts-raring
3 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
18 not fully installed or removed.
Need to get 0 B/6,596 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up initramfs-tools (0.99ubuntu13.5) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-3.11.0-17-generic (3.11.0-17.31~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.8.0-39-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.11.0-17-generic /boot/vmlinuz-3.11.0-17-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.11.0-17-generic /boot/vmlinuz-3.11.0-17-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.11.0-17-generic /boot/vmlinuz-3.11.0-17-generic
update-initramfs: Generating /boot/initrd.img-3.11.0-17-generic
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.11.0-17-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.11.0-17-generic.postinst line 1010.
dpkg: error processing linux-image-3.11.0-17-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.11.0-18-generic (3.11.0-18.32~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.11.0-17-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.11.0-18-generic /boot/vmlinuz-3.11.0-18-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.11.0-18-generic /boot/vmlinuz-3.11.0-18-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.11.0-18-generic /boot/vmlinuz-3.11.0-18-generic
update-initramfs: Generating /boot/initrd.img-3.11.0-18-generic
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.11.0-18-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.11.0-18-generic.postinst line 1010.
dpkg: error processing linux-image-3.11.0-18-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.11.0-19-generic (3.11.0-19.33~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.11.0-18-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.11.0-19-generic /boot/vmlinuz-3.11.0-19-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.11.0-19-generic /boot/vmlinuz-3.11.0-19-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.11.0-19-generic /boot/vmlinuz-3.11.0-19-generic
update-initramfs: Generating /boot/initrd.img-3.11.0-19-generic
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.11.0-19-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.11.0-19-generic.postinst line 1010.
dpkg: error processing linux-image-3.11.0-19-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.11.0-20-generic (3.11.0-20.34~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.11.0-19-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.11.0-20-generic /boot/vmlinuz-3.11.0-20-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.11.0-20-generic /boot/vmlinuz-3.11.0-20-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.11.0-20-generic /boot/vmlinuz-3.11.0-20-generic
update-initramfs: Generating /boot/initrd.img-3.11.0-20-generic
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.11.0-20-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.11.0-20-generic.postinst line 1010.
dpkg: error processing linux-image-3.11.0-20-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    Setting up linux-image-3.14.0-031400-generic (3.14.0-031400.201403310035) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.11.0-20-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.14.0-031400-generic /boot/vmlinuz-3.14.0-031400-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.14.0-031400-generic /boot/vmlinuz-3.14.0-031400-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.14.0-031400-generic /boot/vmlinuz-3.14.0-031400-generic
update-initramfs: Generating /boot/initrd.img-3.14.0-031400-generic
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.14.0-031400-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.14.0-031400-generic.postinst line 1025.
dpkg: error processing linux-image-3.14.0-031400-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    Setting up linux-image-3.14.0-031400-lowlatency (3.14.0-031400.201403310035) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.14.0-031400-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.14.0-031400-lowlatency /boot/vmlinuz-3.14.0-031400-lowlatency
run-parts: executing /etc/kernel/postinst.d/dkms 3.14.0-031400-lowlatency /boot/vmlinuz-3.14.0-031400-lowlatency
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.14.0-031400-lowlatency /boot/vmlinuz-3.14.0-031400-lowlatency
update-initramfs: Generating /boot/initrd.img-3.14.0-031400-lowlatency
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.14.0-031400-lowlatency with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.14.0-031400-lowlatency.postinst line 1025.
dpkg: error processing linux-image-3.14.0-031400-lowlatency (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    Setting up linux-image-3.8.0-36-generic (3.8.0-36.52~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.14.0-031400-lowlatency
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-36-generic /boot/vmlinuz-3.8.0-36-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.8.0-36-generic /boot/vmlinuz-3.8.0-36-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-36-generic /boot/vmlinuz-3.8.0-36-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-36-generic
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.8.0-36-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.8.0-36-generic.postinst line 1010.
dpkg: error processing linux-image-3.8.0-36-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    Setting up linux-image-3.8.0-37-generic (3.8.0-37.53~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.8.0-36-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-37-generic /boot/vmlinuz-3.8.0-37-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.8.0-37-generic /boot/vmlinuz-3.8.0-37-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-37-generic /boot/vmlinuz-3.8.0-37-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-37-generic
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.8.0-37-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.8.0-37-generic.postinst line 1010.
dpkg: error processing linux-image-3.8.0-37-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    Setting up linux-image-3.8.0-38-generic (3.8.0-38.56~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.8.0-37-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-38-generic /boot/vmlinuz-3.8.0-38-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.8.0-38-generic /boot/vmlinuz-3.8.0-38-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-38-generic /boot/vmlinuz-3.8.0-38-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-38-generic
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.8.0-38-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.8.0-38-generic.postinst line 1010.
dpkg: error processing linux-image-3.8.0-38-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    Setting up linux-image-3.8.0-39-generic (3.8.0-39.57~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.8.0-38-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-39-generic /boot/vmlinuz-3.8.0-39-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.8.0-39-generic /boot/vmlinuz-3.8.0-39-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-39-generic /boot/vmlinuz-3.8.0-39-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-39-generic
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.8.0-39-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.8.0-39-generic.postinst line 1010.
dpkg: error processing linux-image-3.8.0-39-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of linux-image-generic-lts-saucy:
 linux-image-generic-lts-saucy depends on linux-image-3.11.0-17-generic; however:
  Package linux-image-3.11.0-17-generic is not configured yet.
dpkg: error processing linux-image-generic-lts-saucy (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of linux-signed-image-3.8.0-39-generic:
 linux-signed-image-3.8.0-39-generic depends on linux-image-3.8.0-39-generic (= 3.8.0-39.57~precise1); however:
  Package linux-image-3.8.0-39-generic is not configured yet.
dpkg: error processing linux-signed-image-3.8.0-39-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-image-3.8.0-36-generic:
 linux-signed-image-3.8.0-36-generic depends on linux-image-3.8.0-36-generic (= 3.8.0-36.52~precise1); however:
  Package linux-image-3.8.0-36-generic is not configured yet.
dpkg: error processing linux-signed-image-3.8.0-36-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
                                                                                                                                        dpkg: dependency problems prevent configuration of linux-signed-image-3.8.0-37-generic:
 linux-signed-image-3.8.0-37-generic depends on linux-image-3.8.0-37-generic (= 3.8.0-37.53~precise1); however:
  Package linux-image-3.8.0-37-generic is not configured yet.
dpkg: error processing linux-signed-image-3.8.0-37-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of linux-signed-image-3.8.0-38-generic:
 linux-signed-image-3.8.0-38-generic depends on linux-image-3.8.0-38-generic (= 3.8.0-38.56~precise1); however:
  Package linux-image-3.8.0-38-generic is not configured yet.
dpkg: error processing linux-signed-image-3.8.0-38-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of linux-signed-image-generic-lts-raring:
 linux-signed-image-generic-lts-raring depends on linux-signed-image-3.8.0-36-generic; however:
  Package linux-signed-image-3.8.0-36-generic is not configured yet.
dpkg: error processing linux-signed-image-generic-lts-raring (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-generic-lts-raring:
 linux-signed-generic-lts-raring depends on linux-signed-image-generic-lts-raring; however:
  Package linux-signed-image-generic-lts-raring is not configured yet.
dpkg: error processing linux-signed-generic-lts-raring (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
                                                                                                                                        Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.13.0-031300-generic
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.13.0-031300-generic with 1.
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 linux-image-3.11.0-17-generic
 linux-image-3.11.0-18-generic
 linux-image-3.11.0-19-generic
 linux-image-3.11.0-20-generic
 linux-image-3.14.0-031400-generic
 linux-image-3.14.0-031400-lowlatency
 linux-image-3.8.0-36-generic
 linux-image-3.8.0-37-generic
 linux-image-3.8.0-38-generic
 linux-image-3.8.0-39-generic
 linux-image-generic-lts-saucy
 linux-signed-image-3.8.0-39-generic
 linux-signed-image-3.8.0-36-generic
 linux-signed-image-3.8.0-37-generic
 linux-signed-image-3.8.0-38-generic
 linux-signed-image-generic-lts-raring
 linux-signed-generic-lts-raring
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by ibjsb4 on 2014-04-30
The command for a kernel upgrade is

```
sudo apt-get dist-upgrade
```

Your command seems to want to install all available kernels which put you in a bad spot and I'm not so sure how to back out of this one :(

---

### Post by erotavlas on 2014-04-30
I tried also this
```

sudo update-initramfs -uv

```
with a very long output and final result
```

Available versions:  3.11.0-15-generic
Keeping /boot/initrd.img-3.11.0-15-generic.dpkg-bak
update-initramfs: Generating /boot/initrd.img-3.11.0-15-generic
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/hid/hid.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/hid/usbhid/usbhid.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/hid/hid-apple.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/hid/hid-cherry.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/input/ff-memless.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/hid/hid-logitech.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/hid/hid-logitech-dj.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/hid/hid-microsoft.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/hid/hid-a4tech.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/hid/hid-belkin.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/hid/hid-chicony.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/hid/hid-cypress.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/hid/hid-ezkey.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/hid/hid-generic.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/hid/hid-gyration.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/hid/hid-monterey.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/hid/hid-petalynx.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/hid/hid-pl.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/hid/hid-samsung.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/hid/hid-sony.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/hid/hid-sunplus.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/hid/hid-tmff.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/hid/hid-zpff.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/crypto/xor.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/lib/zlib_deflate/zlib_deflate.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/lib/raid6/raid6_pq.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/fs/btrfs/btrfs.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/fs/ext2/ext2.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/fs/isofs/isofs.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/fs/jfs/jfs.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/net/sunrpc/sunrpc.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/fs/lockd/lockd.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/fs/fscache/fscache.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/fs/nfs/nfs.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/fs/nfs_common/nfs_acl.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/fs/nfs/nfsv3.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/fs/nfs/nfsv4.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/fs/reiserfs/reiserfs.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/lib/crc-itu-t.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/fs/udf/udf.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/fs/xfs/xfs.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/fs/nls/nls_iso8859-1.ko
Copying module directory kernel/drivers/net
(excluding appletalk arcnet bonding can hamradio irda pcmcia tokenring usb wan wimax wireless)
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ppp/ppp_synctty.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/lib/crc-ccitt.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ppp/ppp_async.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ppp/pppox.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ppp/pppoe.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ppp/ppp_mppe.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ppp/ppp_deflate.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/net/ipv4/gre.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ppp/pptp.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ppp/bsd_comp.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/mdio.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/mii.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/micrel/ks8851.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/micrel/ks8842.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/micrel/ksz884x.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/micrel/ks8851_mll.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/realtek/r8169.ko
Adding binary /lib/firmware/3.11.0-15-generic/rtl_nic/rtl8168g-3.fw
Adding firmware rtl_nic/rtl8168g-3.fw
Adding binary /lib/firmware/3.11.0-15-generic/rtl_nic/rtl8168g-2.fw
Adding firmware rtl_nic/rtl8168g-2.fw
Adding binary /lib/firmware/3.11.0-15-generic/rtl_nic/rtl8106e-2.fw
Adding firmware rtl_nic/rtl8106e-2.fw
Adding binary /lib/firmware/3.11.0-15-generic/rtl_nic/rtl8106e-1.fw
Adding firmware rtl_nic/rtl8106e-1.fw
Adding binary /lib/firmware/3.11.0-15-generic/rtl_nic/rtl8411-2.fw
Adding firmware rtl_nic/rtl8411-2.fw
Adding binary /lib/firmware/3.11.0-15-generic/rtl_nic/rtl8411-1.fw
Adding firmware rtl_nic/rtl8411-1.fw
Adding binary /lib/firmware/rtl_nic/rtl8402-1.fw
Adding firmware rtl_nic/rtl8402-1.fw
Adding binary /lib/firmware/rtl_nic/rtl8168f-2.fw
Adding firmware rtl_nic/rtl8168f-2.fw
Adding binary /lib/firmware/3.11.0-15-generic/rtl_nic/rtl8168f-1.fw
Adding firmware rtl_nic/rtl8168f-1.fw
Adding binary /lib/firmware/rtl_nic/rtl8105e-1.fw
Adding firmware rtl_nic/rtl8105e-1.fw
Adding binary /lib/firmware/rtl_nic/rtl8168e-3.fw
Adding firmware rtl_nic/rtl8168e-3.fw
Adding binary /lib/firmware/rtl_nic/rtl8168e-2.fw
Adding firmware rtl_nic/rtl8168e-2.fw
Adding binary /lib/firmware/rtl_nic/rtl8168e-1.fw
Adding firmware rtl_nic/rtl8168e-1.fw
Adding binary /lib/firmware/rtl_nic/rtl8168d-2.fw
Adding firmware rtl_nic/rtl8168d-2.fw
Adding binary /lib/firmware/rtl_nic/rtl8168d-1.fw
Adding firmware rtl_nic/rtl8168d-1.fw
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/realtek/8139cp.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/realtek/8139too.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/realtek/atp.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/rdc/r6040.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/smsc/epic100.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/pcmcia/pcmcia_core.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/pcmcia/pcmcia.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/smsc/smc91c92_cs.ko
Adding binary /lib/firmware/ositech/Xilinx7OD.bin
Adding firmware ositech/Xilinx7OD.bin
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/smsc/smsc9420.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/smsc/smsc911x.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/fujitsu/fmvj18x_cs.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/amd/pcnet32.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/amd/amd8111e.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/amd/nmclan_cs.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/chelsio/cxgb4/cxgb4.ko
Adding binary /lib/firmware/cxgb4/t5fw.bin
Adding firmware cxgb4/t5fw.bin
Adding binary /lib/firmware/cxgb4/t4fw.bin
Adding firmware cxgb4/t4fw.bin
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/chelsio/cxgb4vf/cxgb4vf.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/chelsio/cxgb3/cxgb3.ko
Adding binary /lib/firmware/cxgb3/ael2020_twx_edc.bin
Adding firmware cxgb3/ael2020_twx_edc.bin
Adding binary /lib/firmware/cxgb3/ael2005_twx_edc.bin
Adding firmware cxgb3/ael2005_twx_edc.bin
Adding binary /lib/firmware/cxgb3/ael2005_opt_edc.bin
Adding firmware cxgb3/ael2005_opt_edc.bin
Adding binary /lib/firmware/cxgb3/t3c_psram-1.1.0.bin
Adding firmware cxgb3/t3c_psram-1.1.0.bin
Adding binary /lib/firmware/cxgb3/t3b_psram-1.1.0.bin
Adding firmware cxgb3/t3b_psram-1.1.0.bin
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/chelsio/cxgb/cxgb.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/neterion/s2io.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/neterion/vxge/vxge.ko
Adding binary /lib/firmware/vxge/X3fw.ncf
Adding firmware vxge/X3fw.ncf
Adding binary /lib/firmware/vxge/X3fw-pxe.ncf
Adding firmware vxge/X3fw-pxe.ncf
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/dlink/sundance.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/dlink/dl2k.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/silan/sc92031.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/dca/dca.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/myricom/myri10ge/myri10ge.ko
Adding binary /lib/firmware/myri10ge_rss_eth_z8e.dat
Adding firmware myri10ge_rss_eth_z8e.dat
Adding binary /lib/firmware/myri10ge_rss_ethp_z8e.dat
Adding firmware myri10ge_rss_ethp_z8e.dat
Adding binary /lib/firmware/myri10ge_eth_z8e.dat
Adding firmware myri10ge_eth_z8e.dat
Adding binary /lib/firmware/myri10ge_ethp_z8e.dat
Adding firmware myri10ge_ethp_z8e.dat
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ssb/ssb.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/broadcom/b44.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/pps/pps_core.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ptp/ptp.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/broadcom/tg3.ko
Adding binary /lib/firmware/3.11.0-15-generic/tigon/tg3_tso5.bin
Adding firmware tigon/tg3_tso5.bin
Adding binary /lib/firmware/3.11.0-15-generic/tigon/tg3_tso.bin
Adding firmware tigon/tg3_tso.bin
Adding binary /lib/firmware/3.11.0-15-generic/tigon/tg3.bin
Adding firmware tigon/tg3.bin
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/broadcom/bnx2x/bnx2x.ko
Adding binary /lib/firmware/3.11.0-15-generic/bnx2x/bnx2x-e2-7.8.17.0.fw
Adding firmware bnx2x/bnx2x-e2-7.8.17.0.fw
Adding binary /lib/firmware/3.11.0-15-generic/bnx2x/bnx2x-e1h-7.8.17.0.fw
Adding firmware bnx2x/bnx2x-e1h-7.8.17.0.fw
Adding binary /lib/firmware/3.11.0-15-generic/bnx2x/bnx2x-e1-7.8.17.0.fw
Adding firmware bnx2x/bnx2x-e1-7.8.17.0.fw
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/broadcom/bnx2.ko
Adding binary /lib/firmware/3.11.0-15-generic/bnx2/bnx2-rv2p-09ax-6.0.17.fw
Adding firmware bnx2/bnx2-rv2p-09ax-6.0.17.fw
Adding binary /lib/firmware/3.11.0-15-generic/bnx2/bnx2-rv2p-09-6.0.17.fw
Adding firmware bnx2/bnx2-rv2p-09-6.0.17.fw
Adding binary /lib/firmware/3.11.0-15-generic/bnx2/bnx2-mips-09-6.2.1b.fw
Adding firmware bnx2/bnx2-mips-09-6.2.1b.fw
Adding binary /lib/firmware/3.11.0-15-generic/bnx2/bnx2-rv2p-06-6.0.15.fw
Adding firmware bnx2/bnx2-rv2p-06-6.0.15.fw
Adding binary /lib/firmware/3.11.0-15-generic/bnx2/bnx2-mips-06-6.2.3.fw
Adding firmware bnx2/bnx2-mips-06-6.2.3.fw
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/uio/uio.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/broadcom/cnic.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/sun/cassini.ko
Adding binary /lib/firmware/sun/cassini.bin
Adding firmware sun/cassini.bin
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/sun/niu.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/sun/sunhme.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/sungem_phy.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/sun/sungem.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/sis/sis900.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/sis/sis190.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/mellanox/mlx5/core/mlx5_core.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/mellanox/mlx4/mlx4_core.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/mellanox/mlx4/mlx4_en.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/calxeda/xgmac.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/fealnx.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/xircom/xirc2ps_cs.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/i2c/algos/i2c-algo-bit.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/mtd/mtd.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/sfc/sfc.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/nvidia/forcedeth.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/jme.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/wiznet/w5300.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/wiznet/w5100.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/alteon/acenic.ko
Adding binary /lib/firmware/acenic/tg2.bin
Adding firmware acenic/tg2.bin
Adding binary /lib/firmware/acenic/tg1.bin
Adding firmware acenic/tg1.bin
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/cadence/macb.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/cadence/at91_ether.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/dec/tulip/de4x5.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/dec/tulip/de2104x.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/dec/tulip/uli526x.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/dec/tulip/xircom_cb.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/dec/tulip/dmfe.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/dec/tulip/winbond-840.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/dec/tulip/tulip.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/natsemi/ns83820.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/natsemi/natsemi.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/tehuti/tehuti.ko
Adding binary /lib/firmware/tehuti/bdx.bin
Adding firmware tehuti/bdx.bin
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/packetengines/hamachi.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/packetengines/yellowfin.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/microchip/enc28j60.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/8390/8390.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/8390/ne2k-pci.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/8390/pcnet_cs.ko
Adding binary /lib/firmware/cis/tamarack.cis
Adding firmware cis/tamarack.cis
Adding binary /lib/firmware/cis/PE-200.cis
Adding firmware cis/PE-200.cis
Adding binary /lib/firmware/cis/NE2K.cis
Adding firmware cis/NE2K.cis
Adding binary /lib/firmware/cis/PE520.cis
Adding firmware cis/PE520.cis
Adding binary /lib/firmware/cis/LA-PCM.cis
Adding firmware cis/LA-PCM.cis
Adding binary /lib/firmware/cis/DP83903.cis
Adding firmware cis/DP83903.cis
Adding binary /lib/firmware/cis/PCMLM28.cis
Adding firmware cis/PCMLM28.cis
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/8390/axnet_cs.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/dnet.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/intel/e1000/e1000.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/intel/ixgbe/ixgbe.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/intel/e100.ko
Adding binary /lib/firmware/3.11.0-15-generic/e100/d102e_ucode.bin
Adding firmware e100/d102e_ucode.bin
Adding binary /lib/firmware/3.11.0-15-generic/e100/d101s_ucode.bin
Adding firmware e100/d101s_ucode.bin
Adding binary /lib/firmware/3.11.0-15-generic/e100/d101m_ucode.bin
Adding firmware e100/d101m_ucode.bin
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/intel/ixgbevf/ixgbevf.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/intel/e1000e/e1000e.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/intel/igbvf/igbvf.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/intel/igb/igb.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/intel/ixgb/ixgb.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/renesas/sh_eth.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/stmicro/stmmac/stmmac.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/qlogic/qlge/qlge.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/qlogic/qla3xxx.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/qlogic/qlcnic/qlcnic.ko
Adding binary /lib/firmware/3.11.0-15-generic/phanfw.bin
Adding firmware phanfw.bin
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/qlogic/netxen/netxen_nic.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/icplus/ipg.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/ti/tlan.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/brocade/bna/bna.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/emulex/benet/be2net.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/ethoc.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/via/via-rhine.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/via/via-velocity.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/hp/hp100.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/marvell/mvmdio.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/marvell/skge.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/marvell/sky2.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/cisco/enic/enic.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/adaptec/starfire.ko
Adding binary /lib/firmware/3.11.0-15-generic/adaptec/starfire_tx.bin
Adding firmware adaptec/starfire_tx.bin
Adding binary /lib/firmware/3.11.0-15-generic/adaptec/starfire_rx.bin
Adding firmware adaptec/starfire_rx.bin
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/3com/3c59x.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/3com/3c589_cs.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/3com/3c574_cs.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/3com/typhoon.ko
Adding binary /lib/firmware/3.11.0-15-generic/3com/typhoon.bin
Adding firmware 3com/typhoon.bin
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ptp/ptp_pch.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/oki-semi/pch_gbe/pch_gbe.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/atheros/alx/alx.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/atheros/atl1e/atl1e.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/atheros/atlx/atl1.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/atheros/atlx/atl2.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/atheros/atl1c/atl1c.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/xen-netback/xen-netback.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/phy/spi_ks8995.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/caif/caif_serial.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/vhost/vringh.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/caif/caif_virtio.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/caif/cfspi_slave.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/caif/caif_hsi.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/macvlan.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/macvtap.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/dummy.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/eql.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ntb/ntb.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ntb_netdev.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/veth.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/hv/hv_vmbus.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/hyperv/hv_netvsc.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/net/ieee802154/ieee802154.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/net/mac802154/mac802154.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ieee802154/at86rf230.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ieee802154/fakelb.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ieee802154/mrf24j40.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/sb1000.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/nlmon.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/parport/parport.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/plip/plip.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/fddi/defxx.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/fddi/skfp/skfp.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/vmxnet3/vmxnet3.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/ifb.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/net/dsa/dsa_core.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/dsa/mv88e6xxx_drv.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/dsa/mv88e6060.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/rionet.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/net/ipv4/ip_tunnel.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/vxlan.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/fs/configfs/configfs.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/netconsole.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/net/slip/slip.ko
Copying module directory kernel/drivers/scsi
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/st.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/aacraid/aacraid.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/imm.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/raid_class.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/scsi_transport_sas.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/mpt3sas/mpt3sas.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/fdomain.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/scsi_tgt.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/scsi_transport_fc.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/lpfc/lpfc.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/hv_storvsc.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/qla1280.ko
Adding binary /lib/firmware/3.11.0-15-generic/qlogic/12160.bin
Adding firmware qlogic/12160.bin
Adding binary /lib/firmware/3.11.0-15-generic/qlogic/1280.bin
Adding firmware qlogic/1280.bin
Adding binary /lib/firmware/3.11.0-15-generic/qlogic/1040.bin
Adding firmware qlogic/1040.bin
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/csiostor/csiostor.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/arcmsr/arcmsr.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/libfc/libfc.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/fcoe/libfcoe.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/fnic/fnic.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/megaraid.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/eata.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/advansys.ko
Adding binary /lib/firmware/3.11.0-15-generic/advansys/38C1600.bin
Adding firmware advansys/38C1600.bin
Adding binary /lib/firmware/3.11.0-15-generic/advansys/38C0800.bin
Adding firmware advansys/38C0800.bin
Adding binary /lib/firmware/3.11.0-15-generic/advansys/3550.bin
Adding firmware advansys/3550.bin
Adding binary /lib/firmware/3.11.0-15-generic/advansys/mcode.bin
Adding firmware advansys/mcode.bin
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/osd/libosd.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/osd/osd.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/qla2xxx/qla2xxx.ko
Adding binary /lib/firmware/3.11.0-15-generic/ql2500_fw.bin
Adding firmware ql2500_fw.bin
Adding binary /lib/firmware/3.11.0-15-generic/ql2400_fw.bin
Adding firmware ql2400_fw.bin
Adding binary /lib/firmware/3.11.0-15-generic/ql2322_fw.bin
Adding firmware ql2322_fw.bin
Adding binary /lib/firmware/3.11.0-15-generic/ql2300_fw.bin
Adding firmware ql2300_fw.bin
Adding binary /lib/firmware/ql2200_fw.bin
Adding firmware ql2200_fw.bin
Adding binary /lib/firmware/ql2100_fw.bin
Adding firmware ql2100_fw.bin
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/target/target_core_mod.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/qla2xxx/tcm_qla2xxx.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/sym53c8xx_2/sym53c8xx.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/osst.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/stex.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/3w-xxxx.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/ips.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/scsi_transport_iscsi.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/virtio_scsi.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/qlogicfas408.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/hpsa.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/ipr.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/3w-9xxx.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/ufs/ufshcd.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/ufs/ufshcd-pltfrm.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/ufs/ufshcd-pci.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/megaraid/megaraid_mm.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/megaraid/megaraid_mbox.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/pmcraid.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/scsi_debug.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/gdth.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/dc395x.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/libiscsi.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/iscsi_boot_sysfs.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/qla4xxx/qla4xxx.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/mvumi.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/bnx2fc/bnx2fc.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/initio.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/3w-sas.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/mpt2sas/mpt2sas.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/libiscsi_tcp.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/cxgbi/libcxgbi.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/cxgbi/cxgb3i/cxgb3i.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/cxgbi/cxgb4i/cxgb4i.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/ch.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/dmx3191d.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/pcmcia/fdomain_cs.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/pcmcia/qlogic_cs.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/pcmcia/aha152x_cs.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/pcmcia/sym53c500_cs.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/libsas/libsas.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/isci/isci.ko
Adding binary /lib/firmware/isci/isci_firmware.bin
Adding firmware isci/isci_firmware.bin
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/be2iscsi/be2iscsi.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/hptiop.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/mvsas/mvsas.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/BusLogic.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/misc/enclosure.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/ses.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/a100u2w.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/device_handler/scsi_dh.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/device_handler/scsi_dh_emc.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/device_handler/scsi_dh_alua.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/device_handler/scsi_dh_hp_sw.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/device_handler/scsi_dh_rdac.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/tmscsim.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/atp870u.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/bfa/bfa.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/aic94xx/aic94xx.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/fcoe/fcoe.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/libsrp.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/bnx2i/bnx2i.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/dpt_i2o.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/vmw_pvscsi.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/scsi_transport_srp.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/pm8001/pm80xx.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/aic7xxx/aic79xx.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/aic7xxx/aic7xxx.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/iscsi_tcp.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/scsi/ppa.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/message/fusion/mptbase.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/message/fusion/mptscsih.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/message/fusion/mptfc.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/message/fusion/mptsas.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/message/fusion/mptspi.ko
Copying module directory kernel/drivers/block
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/nvme.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/cryptoloop.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/osdblk.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/paride/paride.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/paride/friq.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/paride/fit3.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/paride/epat.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/paride/pf.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/paride/bpck.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/paride/frpw.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/paride/kbic.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/paride/ktti.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/paride/on26.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/paride/comm.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/paride/epia.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/paride/pcd.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/paride/on20.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/paride/pg.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/paride/pt.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/paride/aten.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/paride/dstr.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/paride/pd.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/paride/fit2.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/xen-blkback/xen-blkback.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/mtip32xx/mtip32xx.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/rsxx/rsxx.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/cpqarray.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/floppy.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/nbd.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/lib/lru_cache.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/drbd/drbd.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/umem.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/pktcdvd.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/aoe/aoe.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/net/ceph/libceph.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/rbd.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/DAC960.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/sx8.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/block/cciss.ko
Copying module directory kernel/drivers/ata
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_triflex.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_platform.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_amd.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/sata_rcar.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_ninja32.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/sata_vsc.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_rz1000.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_pdc202xx_old.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_atiixp.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/sata_sx4.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/sata_svw.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_arasan_cf.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_cs5536.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_hpt366.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/sata_uli.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_efar.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/libahci.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/ahci.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/ahci_platform.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_netcell.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_marvell.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_cypress.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_acpi.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/sata_sil24.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_sil680.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_ns87410.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pdc_adma.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_hpt37x.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_legacy.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_optidma.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_jmicron.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_hpt3x2n.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_oldpiix.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/sata_sil.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_cmd640.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_cs5520.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/sata_inic162x.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_pdc2027x.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_piccolo.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_atp867x.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_sch.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_serverworks.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_it821x.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/sata_nv.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/sata_promise.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/ahci_imx.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/sata_mv.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_ns87415.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_ali.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/sata_via.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/acard-ahci.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_cs5530.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_sl82c105.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_rdc.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_via.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_radisys.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_mpiix.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_pcmcia.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_it8213.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_opti.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_artop.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/sata_sis.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/sata_qstor.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_sc1200.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_hpt3x3.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/ata/pata_cmd64x.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/message/i2o/i2o_core.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/message/i2o/i2o_block.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/firewire/firewire-core.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/firewire/firewire-ohci.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/firewire/firewire-sbp2.ko
Copying module directory kernel/drivers/mmc
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/mfd/rtsx_pci.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/mmc/host/rtsx_pci_sdmmc.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/mmc/host/sdhci.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/mmc/host/sdhci-pltfm.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/mmc/host/sdhci-pxav3.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/mmc/host/via-sdmmc.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/mmc/host/sdhci-pci.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/mmc/host/wbsd.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/misc/tifm_core.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/mmc/host/tifm_sd.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/mmc/host/sdhci-acpi.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/mmc/host/ushc.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/mmc/host/sdhci-pxav2.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/mmc/host/vub300.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/lib/crc7.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/mmc/host/mmc_spi.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/misc/cb710/cb710.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/mmc/host/cb710-mmc.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/mmc/host/sdricoh_cs.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/mmc/card/mmc_block.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/mmc/card/sdio_uart.ko
Copying module directory kernel/drivers/usb/storage
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/usb/storage/usb-storage.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/usb/storage/ums-alauda.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/usb/storage/ums-isd200.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/usb/storage/ums-usbat.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/usb/storage/ums-cypress.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/usb/storage/ums-datafab.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/usb/storage/ums-karma.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/usb/storage/ums-sddr55.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/usb/storage/ums-sddr09.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/usb/storage/ums-freecom.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/usb/storage/ums-eneub6250.ko
Adding binary /lib/firmware/ene-ub6250/ms_rdwr.bin
Adding firmware ene-ub6250/ms_rdwr.bin
Adding binary /lib/firmware/ene-ub6250/msp_rdwr.bin
Adding firmware ene-ub6250/msp_rdwr.bin
Adding binary /lib/firmware/ene-ub6250/ms_init.bin
Adding firmware ene-ub6250/ms_init.bin
Adding binary /lib/firmware/ene-ub6250/sd_rdwr.bin
Adding firmware ene-ub6250/sd_rdwr.bin
Adding binary /lib/firmware/ene-ub6250/sd_init2.bin
Adding firmware ene-ub6250/sd_init2.bin
Adding binary /lib/firmware/ene-ub6250/sd_init1.bin
Adding firmware ene-ub6250/sd_init1.bin
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/usb/storage/ums-onetouch.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/usb/storage/ums-realtek.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/usb/storage/ums-jumpshot.ko
Adding module /lib/modules/3.11.0-15-generic/kernel/drivers/hv/hv_utils.ko
Adding binary /etc/initramfs-tools/conf.d/resume
Adding binary /usr/lib/initramfs-tools/bin/wait-for-root
Adding library /lib/x86_64-linux-gnu/libudev.so.0
Adding library /lib/x86_64-linux-gnu/libc.so.6
Adding library /lib/x86_64-linux-gnu/librt.so.1
Adding library /lib64/ld-linux-x86-64.so.2
Adding library /lib/x86_64-linux-gnu/libpthread.so.0
Adding binary /sbin/modprobe
Adding binary /sbin/rmmod
Adding binary /sbin/blkid
Adding library /lib/x86_64-linux-gnu/libblkid.so.1
Adding library /lib/x86_64-linux-gnu/libuuid.so.1
Calling hook compcache
Calling hook fixrtc
Adding binary /bin/date
Adding binary /sbin/hwclock
Adding binary /sbin/dumpe2fs
Adding library /lib/x86_64-linux-gnu/libext2fs.so.2
Adding library /lib/x86_64-linux-gnu/libcom_err.so.2
Adding library /lib/x86_64-linux-gnu/libe2p.so.2
Calling hook fuse
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
Removing /boot/initrd.img-3.11.0-15-generic.dpkg-bak
update-initramfs: failed for /boot/initrd.img-3.11.0-15-generic with 1.

```

---

### Post by erotavlas on 2014-04-30
While with
```

sudo apt-get install -f

```
with a very long output and final result
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxmu-dev libxmu-headers freeglut3-dev freeglut3
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 2 not to upgrade.
19 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up initramfs-tools (0.99ubuntu13.5) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-3.11.0-17-generic (3.11.0-17.31~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.8.0-39-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.11.0-17-generic /boot/vmlinuz-3.11.0-17-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.11.0-17-generic /boot/vmlinuz-3.11.0-17-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.11.0-17-generic /boot/vmlinuz-3.11.0-17-generic
update-initramfs: Generating /boot/initrd.img-3.11.0-17-generic
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.11.0-17-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.11.0-17-generic.postinst line 1010.
dpkg: error processing linux-image-3.11.0-17-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.11.0-18-generic (3.11.0-18.32~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.11.0-17-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.11.0-18-generic /boot/vmlinuz-3.11.0-18-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.11.0-18-generic /boot/vmlinuz-3.11.0-18-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.11.0-18-generic /boot/vmlinuz-3.11.0-18-generic
update-initramfs: Generating /boot/initrd.img-3.11.0-18-generic
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.11.0-18-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.11.0-18-generic.postinst line 1010.
dpkg: error processing linux-image-3.11.0-18-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.11.0-19-generic (3.11.0-19.33~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.11.0-18-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.11.0-19-generic /boot/vmlinuz-3.11.0-19-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.11.0-19-generic /boot/vmlinuz-3.11.0-19-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.11.0-19-generic /boot/vmlinuz-3.11.0-19-generic
update-initramfs: Generating /boot/initrd.img-3.11.0-19-generic
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.11.0-19-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.11.0-19-generic.postinst line 1010.
dpkg: error processing linux-image-3.11.0-19-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.11.0-20-generic (3.11.0-20.34~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.11.0-19-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.11.0-20-generic /boot/vmlinuz-3.11.0-20-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.11.0-20-generic /boot/vmlinuz-3.11.0-20-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.11.0-20-generic /boot/vmlinuz-3.11.0-20-generic
update-initramfs: Generating /boot/initrd.img-3.11.0-20-generic
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.11.0-20-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.11.0-20-generic.postinst line 1010.
dpkg: error processing linux-image-3.11.0-20-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    Setting up linux-image-3.14.0-031400-generic (3.14.0-031400.201403310035) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.11.0-20-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.14.0-031400-generic /boot/vmlinuz-3.14.0-031400-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.14.0-031400-generic /boot/vmlinuz-3.14.0-031400-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.14.0-031400-generic /boot/vmlinuz-3.14.0-031400-generic
update-initramfs: Generating /boot/initrd.img-3.14.0-031400-generic
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.14.0-031400-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.14.0-031400-generic.postinst line 1025.
dpkg: error processing linux-image-3.14.0-031400-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    Setting up linux-image-3.14.0-031400-lowlatency (3.14.0-031400.201403310035) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.14.0-031400-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.14.0-031400-lowlatency /boot/vmlinuz-3.14.0-031400-lowlatency
run-parts: executing /etc/kernel/postinst.d/dkms 3.14.0-031400-lowlatency /boot/vmlinuz-3.14.0-031400-lowlatency
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.14.0-031400-lowlatency /boot/vmlinuz-3.14.0-031400-lowlatency
update-initramfs: Generating /boot/initrd.img-3.14.0-031400-lowlatency
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.14.0-031400-lowlatency with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.14.0-031400-lowlatency.postinst line 1025.
dpkg: error processing linux-image-3.14.0-031400-lowlatency (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    Setting up linux-image-3.14.2-031402-generic (3.14.2-031402.201404262053) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.14.0-031400-lowlatency
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.14.2-031402-generic /boot/vmlinuz-3.14.2-031402-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.14.2-031402-generic /boot/vmlinuz-3.14.2-031402-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.14.2-031402-generic /boot/vmlinuz-3.14.2-031402-generic
update-initramfs: Generating /boot/initrd.img-3.14.2-031402-generic
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.14.2-031402-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.14.2-031402-generic.postinst line 1025.
dpkg: error processing linux-image-3.14.2-031402-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    Setting up linux-image-3.14.2-031402-lowlatency (3.14.2-031402.201404262053) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.14.2-031402-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.14.2-031402-lowlatency /boot/vmlinuz-3.14.2-031402-lowlatency
run-parts: executing /etc/kernel/postinst.d/dkms 3.14.2-031402-lowlatency /boot/vmlinuz-3.14.2-031402-lowlatency
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.14.2-031402-lowlatency /boot/vmlinuz-3.14.2-031402-lowlatency
update-initramfs: Generating /boot/initrd.img-3.14.2-031402-lowlatency
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.14.2-031402-lowlatency with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.14.2-031402-lowlatency.postinst line 1025.
dpkg: error processing linux-image-3.14.2-031402-lowlatency (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    Setting up linux-image-3.8.0-36-generic (3.8.0-36.52~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.14.2-031402-lowlatency
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-36-generic /boot/vmlinuz-3.8.0-36-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.8.0-36-generic /boot/vmlinuz-3.8.0-36-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-36-generic /boot/vmlinuz-3.8.0-36-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-36-generic
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.8.0-36-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.8.0-36-generic.postinst line 1010.
dpkg: error processing linux-image-3.8.0-36-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    Setting up linux-image-3.8.0-37-generic (3.8.0-37.53~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.8.0-36-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-37-generic /boot/vmlinuz-3.8.0-37-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.8.0-37-generic /boot/vmlinuz-3.8.0-37-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-37-generic /boot/vmlinuz-3.8.0-37-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-37-generic
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.8.0-37-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.8.0-37-generic.postinst line 1010.
dpkg: error processing linux-image-3.8.0-37-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    Setting up linux-image-3.8.0-38-generic (3.8.0-38.56~precise1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.8.0-37-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-38-generic /boot/vmlinuz-3.8.0-38-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.8.0-38-generic /boot/vmlinuz-3.8.0-38-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-38-generic /boot/vmlinuz-3.8.0-38-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-38-generic
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.8.0-38-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.8.0-38-generic.postinst line 1010.
dpkg: error processing linux-image-3.8.0-38-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.8.0-39-generic (3.8.0-39.57~precise1) ...
No apport report written because MaxReports has already been reached
                                                                    Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.8.0-38-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-39-generic /boot/vmlinuz-3.8.0-39-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.8.0-39-generic /boot/vmlinuz-3.8.0-39-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-39-generic /boot/vmlinuz-3.8.0-39-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-39-generic
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.8.0-39-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.8.0-39-generic.postinst line 1010.
dpkg: error processing linux-image-3.8.0-39-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of linux-image-generic-lts-saucy:
 linux-image-generic-lts-saucy depends on linux-image-3.11.0-17-generic; however:
  Package linux-image-3.11.0-17-generic is not configured yet.
dpkg: error processing linux-image-generic-lts-saucy (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of linux-signed-image-3.8.0-36-generic:
 linux-signed-image-3.8.0-36-generic depends on linux-image-3.8.0-36-generic (= 3.8.0-36.52~precise1); however:
  Package linux-image-3.8.0-36-generic is not configured yet.
dpkg: error processing linux-signed-image-3.8.0-36-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-image-3.8.0-37-generic:
 linux-signed-image-3.8.0-37-generic depends on linux-image-3.8.0-37-generic (= 3.8.0-37.53~precise1); however:No apport report written because MaxReports has already been reached

  Package linux-image-3.8.0-37-generic is not configured yet.
dpkg: error processing linux-signed-image-3.8.0-37-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of linux-signed-image-3.8.0-38-generic:
 linux-signed-image-3.8.0-38-generic depends on linux-image-3.8.0-38-generic (= 3.8.0-38.56~precise1); however:
  Package linux-image-3.8.0-38-generic is not configured yet.
dpkg: error processing linux-signed-image-3.8.0-38-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of linux-signed-image-3.8.0-39-generic:
 linux-signed-image-3.8.0-39-generic depends on linux-image-3.8.0-39-generic (= 3.8.0-39.57~precise1); however:
  Package linux-image-3.8.0-39-generic is not configured yet.
dpkg: error processing linux-signed-image-3.8.0-39-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-image-generic-lts-raring:
 linux-signed-image-generic-lts-raring depends on linux-signed-image-3.8.0-36-generic; however:
  Package linux-signed-image-3.8.0-36-generic is not configured yet.
No apport report written because MaxReports has already been reached
                                                                    dpkg: error processing linux-signed-image-generic-lts-raring (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-15-generic
E: /usr/share/initramfs-tools/hooks/fuse failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.11.0-15-generic with 1.
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 linux-image-3.11.0-17-generic
 linux-image-3.11.0-18-generic
 linux-image-3.11.0-19-generic
 linux-image-3.11.0-20-generic
 linux-image-3.14.0-031400-generic
 linux-image-3.14.0-031400-lowlatency
 linux-image-3.14.2-031402-generic
 linux-image-3.14.2-031402-lowlatency
 linux-image-3.8.0-36-generic
 linux-image-3.8.0-37-generic
 linux-image-3.8.0-38-generic
 linux-image-3.8.0-39-generic
 linux-image-generic-lts-saucy
 linux-signed-image-3.8.0-36-generic
 linux-signed-image-3.8.0-37-generic
 linux-signed-image-3.8.0-38-generic
 linux-signed-image-3.8.0-39-generic
 linux-signed-image-generic-lts-raring
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Bashing-om on 2014-04-30
erotavlas; && ibjsb4;

Pardon me for wadding into this .
More than happy to see what can be done to restore this system.
The 1st thing that comes to my attention is this advisory from the package manager.
> 
The link /initrd.img is a dangling linkto /boot/initrd.img-3.8.0-39-generic

Let's see if we can follow that hint:
post back to us the output of terminal commands:
```

ls -la /initrd.img
ls -la /vmlinuz
dpkg -l | grep linux-

```

Maybe try and clean things up a bit  - which I expect will fail - but should give us reasons for failure that we can then address.

[INDENT][INDENT]what do yall think ?

[/INDENT][/INDENT]

---

### Post by ibjsb4 on 2014-04-30
> **Bashing-om said:**
> Pardon me for wadding into this .

No pardon necessary, your input I think is highly respected in this forum :)

---

### Post by erotavlas on 2014-05-01
Thank you for your replies. Today after many attempts I received kernel panic :( I'm not able to recover my system and so I decided to format it. Now I'm on Ubuntu 14.04 LTS and all works well :)

---

### Post by Bashing-om on 2014-05-01
erotavlas; Hey ;

Now that is a sure fired solution - (re-)install works every time.

Please mark this thread solved; aides others seeking the solution, helps keep the forum clean and precludes others miss-directing efforts to aid.

and just
[INDENT][INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT][/INDENT]

---

