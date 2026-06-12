---
title: "Update ERROR!"
date: 2011-08-09
forum: Installation &amp; Upgrades
---

### Post by -Mr.S- on 2011-08-09
can somebody take a look please:
(after i update packages, it says error, and here's whats in the details tab)
Preconfiguring packages ...
(Reading database ... 197969 files and directories currently installed.)
Preparing to replace flashplugin-installer 10.3.181.34ubuntu0.11.04.1 (using .../flashplugin-installer_10.3.181.34ubuntu0.11.04.1_i386.deb) ...
Unpacking replacement flashplugin-installer ...
Preparing to replace flashplugin-nonfree 10.3.181.34ubuntu0.11.04.1 (using .../flashplugin-nonfree_10.3.181.34ubuntu0.11.04.1_i386.deb) ...
Unpacking replacement flashplugin-nonfree ...
Preparing to replace ubuntu-restricted-extras 43 (using .../ubuntu-restricted-extras_43_i386.deb) ...
Unpacking replacement ubuntu-restricted-extras ...
Preparing to replace libquvi0 0.2.11-1 (using .../libquvi0_0.2.11-1_i386.deb) ...
Unpacking replacement libquvi0 ...
Setting up linux-image-2.6.38-10-generic (2.6.38-10.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
 * dkms: running auto installation service for kernel 2.6.38-10-generic         
 *       vboxhost (4.0.4)...                                             [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
/etc/default/grub: 35: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-10-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.38-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.38-10-generic; however:
  Package linux-image-2.6.38-10-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.38.10.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up flashplugin-installer (10.3.181.34ubuntu0.11.04.1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Downloading...
--2011-08-09 20:41:23--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.3.181.34.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.3.181.34.orig.tar.gz)
Resolving archive.canonical.com... 91.189.88.33
Connecting to archive.canonical.com|91.189.88.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5429585 (5.2M) [application/x-gzip]
Saving to: `./adobe-flashplugin_10.3.181.34.orig.tar.gz'

     0K .......... .......... .......... .......... ..........  0%  182K 29s
    50K .......... .......... .......... .......... ..........  1%  179K 29s
   100K .......... .......... .......... .......... ..........  2%  184K 28s
   150K .......... .......... .......... .......... ..........  3%  180K 28s
   200K .......... .......... .......... .......... ..........  4%  183K 28s
   250K .......... .......... .......... .......... ..........  5%  181K 28s
   300K .......... .......... .......... .......... ..........  6% 43.2K 40s
   350K .......... .......... .......... .......... ..........  7% 3.24M 35s
   400K .......... .......... .......... .......... ..........  8% 1.29M 31s
   450K .......... .......... .......... .......... ..........  9%  156M 28s
   500K .......... .......... .......... .......... .......... 10%  166K 27s
   550K .......... .......... .......... .......... .......... 11%  184K 27s
   600K .......... .......... .......... .......... .......... 12%  177K 27s
   650K .......... .......... .......... .......... .......... 13%  181K 26s
   700K .......... .......... .......... .......... .......... 14%  177K 26s
   750K .......... .......... .......... .......... .......... 15%  149K 26s
   800K .......... .......... .......... .......... .......... 16%  216K 25s
   850K .......... .......... .......... .......... .......... 16%  184K 25s
   900K .......... .......... .......... .......... .......... 17%  172K 25s
   950K .......... .......... .......... .......... .......... 18%  172K 25s
  1000K .......... .......... .......... .......... .......... 19%  172K 24s
  1050K .......... .......... .......... .......... .......... 20%  164K 24s
  1100K .......... .......... .......... .......... .......... 21%  192K 24s
  1150K .......... .......... .......... .......... .......... 22%  177K 23s
  1200K .......... .......... .......... .......... .......... 23%  149K 23s
  1250K .......... .......... .......... .......... .......... 24%  198K 23s
  1300K .......... .......... .......... .......... .......... 25%  182K 23s
  1350K .......... .......... .......... .......... .......... 26%  159K 22s
  1400K .......... .......... .......... .......... .......... 27%  157K 22s
  1450K .......... .......... .......... .......... .......... 28%  182K 22s
  1500K .......... .......... .......... .......... .......... 29%  145K 22s
  1550K .......... .......... .......... .......... .......... 30%  198K 21s
  1600K .......... .......... .......... .......... .......... 31%  195K 21s
  1650K .......... .......... .......... .......... .......... 32%  182K 21s
  1700K .......... .......... .......... .......... .......... 33%  177K 20s
  1750K .......... .......... .......... .......... .......... 33%  140K 20s
  1800K .......... .......... .......... .......... .......... 34%  198K 20s
  1850K .......... .......... .......... .......... .......... 35%  201K 19s
  1900K .......... .......... .......... .......... .......... 36%  177K 19s
  1950K .......... .......... .......... .......... .......... 37%  177K 19s
  2000K .......... .......... .......... .......... .......... 38%  184K 19s
  2050K .......... .......... .......... .......... .......... 39%  172K 18s
  2100K .......... .......... .......... .......... .......... 40%  182K 18s
  2150K .......... .......... .......... .......... .......... 41%  177K 18s
  2200K .......... .......... .......... .......... .......... 42%  181K 17s
  2250K .......... .......... .......... .......... .......... 43%  172K 17s
  2300K .......... .......... .......... .......... .......... 44%  179K 17s
  2350K .......... .......... .......... .......... .......... 45%  168K 17s
  2400K .......... .......... .......... .......... .......... 46%  168K 16s
  2450K .......... .......... .......... .......... .......... 47%  192K 16s
  2500K .......... .......... .......... .......... .......... 48%  172K 16s
  2550K .......... .......... .......... .......... .......... 49%  165K 15s
  2600K .......... .......... .......... .......... .......... 49%  189K 15s
  2650K .......... .......... .......... .......... .......... 50%  170K 15s
  2700K .......... .......... .......... .......... .......... 51%  179K 15s
  2750K .......... .......... .......... .......... .......... 52%  132K 14s
  2800K .......... .......... .......... .......... .......... 53%  176K 14s
  2850K .......... .......... .......... .......... .......... 54%  173K 14s
  2900K .......... .......... .......... .......... .......... 55%  179K 14s
  2950K .......... .......... .......... .......... .......... 56%  172K 13s
  3000K .......... .......... .......... .......... .......... 57%  183K 13s
  3050K .......... .......... .......... .......... .......... 58%  177K 13s
  3100K .......... .......... .......... .......... .......... 59%  183K 12s
  3150K .......... .......... .......... .......... .......... 60%  179K 12s
  3200K .......... .......... .......... .......... .......... 61%  139K 12s
  3250K .......... .......... .......... .......... .......... 62%  246K 11s
  3300K .......... .......... .......... .......... .......... 63%  173K 11s
  3350K .......... .......... .......... .......... .......... 64%  174K 11s
  3400K .......... .......... .......... .......... .......... 65%  180K 11s
  3450K .......... .......... .......... .......... .......... 66%  184K 10s
  3500K .......... .......... .......... .......... .......... 66%  173K 10s
  3550K .......... .......... .......... .......... .......... 67%  181K 10s
  3600K .......... .......... .......... .......... .......... 68%  167K 9s
  3650K .......... .......... .......... .......... .......... 69%  183K 9s
  3700K .......... .......... .......... .......... .......... 70%  181K 9s
  3750K .......... .......... .......... .......... .......... 71%  179K 9s
  3800K .......... .......... .......... .......... .......... 72%  139K 8s
  3850K .......... .......... .......... .......... .......... 73%  228K 8s
  3900K .......... .......... .......... .......... .......... 74%  178K 8s
  3950K .......... .......... .......... .......... .......... 75%  148K 7s
  4000K .......... .......... .......... .......... .......... 76%  186K 7s
  4050K .......... .......... .......... .......... .......... 77%  179K 7s
  4100K .......... .......... .......... .......... .......... 78%  171K 7s
  4150K .......... .......... .......... .......... .......... 79%  151K 6s
  4200K .......... .......... .......... .......... .......... 80%  115K 6s
  4250K .......... .......... .......... .......... .......... 81%  151K 6s
  4300K .......... .......... .......... .......... .......... 82%  214K 5s
  4350K .......... .......... .......... .......... .......... 82%  150K 5s
  4400K .......... .......... .......... .......... .......... 83%  153K 5s
  4450K .......... .......... .......... .......... .......... 84%  148K 5s
  4500K .......... .......... .......... .......... .......... 85% 94.6K 4s
  4550K .......... .......... .......... .......... .......... 86%  177K 4s
  4600K .......... .......... .......... .......... .......... 87%  182K 4s
  4650K .......... .......... .......... .......... .......... 88%  173K 4s
  4700K .......... .......... .......... .......... .......... 89%  178K 3s
  4750K .......... .......... .......... .......... .......... 90%  178K 3s
  4800K .......... .......... .......... .......... .......... 91%  178K 3s
  4850K .......... .......... .......... .......... .......... 92%  156K 2s
  4900K .......... .......... .......... .......... .......... 93%  193K 2s
  4950K .......... .......... .......... .......... .......... 94%  164K 2s
  5000K .......... .......... .......... .......... .......... 95%  177K 1s
  5050K .......... .......... .......... .......... .......... 96%  182K 1s
  5100K .......... .......... .......... .......... .......... 97%  173K 1s
  5150K .......... .......... .......... .......... .......... 98%  178K 1s
  5200K .......... .......... .......... .......... .......... 99% 35.2K 0s
  5250K .......... .......... .......... .......... .......... 99%  160K 0s
  5300K ..                                                    100%  106K=32s

2011-08-09 20:41:56 (165 KB/s) - `./adobe-flashplugin_10.3.181.34.orig.tar.gz' saved [5429585/5429585]

Download done.
Flash Plugin installed.
Setting up flashplugin-nonfree (10.3.181.34ubuntu0.11.04.1) ...
Setting up ubuntu-restricted-extras (43) ...
Setting up libquvi0 (0.2.11-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 linux-image-2.6.38-10-generic
 linux-image-generic
 linux-generic
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.38-10-generic (2.6.38-10.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
 * dkms: running auto installation service for kernel 2.6.38-10-generic         
 *       vboxhost (4.0.4)...                                             [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
/etc/default/grub: 35: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-10-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.38-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.38-10-generic; however:
  Package linux-image-2.6.38-10-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.38.10.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.38-10-generic
 linux-image-generic
 linux-generic

How to fix This?
i haven't messed with Ubuntu much...Why am i getting an error about a kernel update?

---

### Post by gpost3 on 2011-08-09
Have you tried doing this with one step previous version of linux kernel available from grub?

---

### Post by -Mr.S- on 2011-08-09
I was gonna try later, when i get a chance...
I'll report back after it. :-)

---

### Post by -Mr.S- on 2011-08-09
i have restarted now and i opened update manager, this is what i got:

W:Failed to fetch [http://kw.archive.ubuntu.com/ubuntu/dists/lucid-backports/main/binary-i386/Packages](http://kw.archive.ubuntu.com/ubuntu/dists/lucid-backports/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://kw.archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/binary-i386/Packages](http://kw.archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://kw.archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/binary-i386/Packages](http://kw.archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://kw.archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/binary-i386/Packages](http://kw.archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Obviously these have to do with lucid and for some reason they are still here on 11.04, or it could be the "kw" for kuwait(i dont know how that got there)

After the refresh some security updates came up so i updated them, and heres what i got:

installArchives() failed: (Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 197969 files and directories currently installed.)
Preparing to replace libecryptfs0 87-0ubuntu1 (using .../libecryptfs0_87-0ubuntu1.1_i386.deb) ...
Unpacking replacement libecryptfs0 ...
Preparing to replace ecryptfs-utils 87-0ubuntu1 (using .../ecryptfs-utils_87-0ubuntu1.1_i386.deb) ...
Unpacking replacement ecryptfs-utils ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up linux-image-2.6.38-10-generic (2.6.38-10.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
 * dkms: running auto installation service for kernel 2.6.38-10-generic        
 *       vboxhost (4.0.4)...        
[ OK ]
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
/etc/default/grub: 35: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-10-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.38-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.38-10-generic; however:
  Package linux-image-2.6.38-10-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.38.10.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up libecryptfs0 (87-0ubuntu1.1) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Setting up ecryptfs-utils (87-0ubuntu1.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 linux-image-2.6.38-10-generic
 linux-image-generic
 linux-generic
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

Setting up linux-image-2.6.38-10-generic (2.6.38-10.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
 * dkms: running auto installation service for kernel 2.6.38-10-generic        
 *       vboxhost (4.0.4)...        
[ OK ]
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
/etc/default/grub: 35: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-10-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.38-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.38-10-generic; however:
  Package linux-image-2.6.38-10-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.38.10.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured

i will try to reinstall linux-generic, linux-image-generic, linux-image-2.6.38-10-generic

---

### Post by -Mr.S- on 2011-08-11
i tried reinstalling the above but no luck...
flash is now working after the recent update!
but i still got that error.
I am installing the linux-headers-2.6.38-10-generic-pae package because thats what synaptics suggested.

---

