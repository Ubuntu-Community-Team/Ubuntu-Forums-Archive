---
title: "Failed upgrade from kernel 3.0.0-13 to 3.0.0-14"
date: 2011-12-03
forum: Installation &amp; Upgrades
---

### Post by phyzik on 2011-12-03
Hey guys (and girls)! I need some help from the community :)

I'm running 32-bit 11.10 and I usually update from "proposed" repository. But a recent update that contained the new kernel 3.0.0-14 didn't install correctly.

I still have a working system (because it boots the old kernel), but now I cannot do any updates! Every time I try, it downloads the 3.0.0-13 kernel but fails to "finish" the update.
This is the output I get from **apt-get upgrade**:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 36.5 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ oneiric-security/main linux-image-3.0.0-13-generic i386 3.0.0-13.22 [36.5 MB]
Fetched 36.5 MB in 43s (835 kB/s)                                              
(Reading database ... 251013 files and directories currently installed.)
Preparing to replace linux-image-3.0.0-13-generic 3.0.0-13.22 (using .../linux-image-3.0.0-13-generic_3.0.0-13.22_i386.deb) ...
Done.
Unpacking replacement linux-image-3.0.0-13-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.0.0-14-generic...
P: Writing config for /boot/vmlinuz-3.0.0-13-generic.dpkg-tmp...
P: Writing config for /boot/vmlinuz-3.0.0-13-generic...
P: Updating /boot/extlinux/linux.cfg...
P: Writing config for Windows Recovery Environment (loader) on /dev/sda1...
P: Writing config for Windows 7 (loader) on /dev/sda2...
E: /usr/share/syslinux/debian/extlinux: No such file or directory
run-parts: /etc/kernel/postrm.d/zz-extlinux exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.0.0-13-generic.postrm line 328.
dpkg: warning: subprocess old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.0.0-14-generic...
P: Writing config for /boot/vmlinuz-3.0.0-13-generic.dpkg-tmp...
P: Writing config for /boot/vmlinuz-3.0.0-13-generic...
P: Writing config for Windows Recovery Environment (loader) on /dev/sda1...
P: Writing config for Windows 7 (loader) on /dev/sda2...
E: /usr/share/syslinux/debian/extlinux: No such file or directory
run-parts: /etc/kernel/postrm.d/zz-extlinux exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/tmp.ci/postrm line 328.
dpkg: error processing /var/cache/apt/archives/linux-image-3.0.0-13-generic_3.0.0-13.22_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.0.0-14-generic...
P: Writing config for /boot/vmlinuz-3.0.0-13-generic...
P: Updating /boot/extlinux/linux.cfg...
P: Writing config for Windows Recovery Environment (loader) on /dev/sda1...
P: Writing config for Windows 7 (loader) on /dev/sda2...
E: /usr/share/syslinux/debian/extlinux: No such file or directory
run-parts: /etc/kernel/postrm.d/zz-extlinux exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/tmp.ci/postrm line 328.
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.0.0-13-generic_3.0.0-13.22_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I tried running ** dpkg --configure -a**:

```
Setting up linux-image-3.0.0-14-generic (3.0.0-14.23) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.0.0-14-generic...
P: Writing config for /boot/vmlinuz-3.0.0-13-generic...
P: Writing config for Windows Recovery Environment (loader) on /dev/sda1...
P: Writing config for Windows 7 (loader) on /dev/sda2...
E: /usr/share/syslinux/debian/extlinux: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-extlinux exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-14-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-14-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.0.0-14-generic; however:
  Package linux-image-3.0.0-14-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.0.0.14.16); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.0.0-14-generic
 linux-image-generic
 linux-generic
```

Now I can't even install/uninstall other packages...Please help!

---

### Post by oldtimer7777 on 2011-12-03
Don't ever enable proposed unless you are an expert developer in Ubuntu OS. 

Not something that should be done. Backports are usually acceptable to enable after about a year, but I wouldn't enable backports and certainly never enable proposed. 

I don't know how you can reverse the process to fix your system after enabling proposed either.  I think you may have hosed your system, but I am not sure. 

Maybe someone else will read this and tell you a way to purge the proposed repo from your system and reverse the installation of all those buggy packages on your OS presently, or it could already be beyond repair.  Hard to say. You may think it is just a kernel issue, but I believe it to be much much more related to the buggy updates you have installed along with the buggy new kernel. That would be my best professional guess.

> **damien37 said:**
> Hey guys (and girls)! I need some help from the community :)

I'm running 32-bit 11.10 and I usually update from "proposed" repository. But a recent update that contained the new kernel 3.0.0-14 didn't install correctly.

I still have a working system (because it boots the old kernel), but now I cannot do any updates! Every time I try, it downloads the 3.0.0-13 kernel but fails to "finish" the update.
This is the output I get from **apt-get upgrade**:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 36.5 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ oneiric-security/main linux-image-3.0.0-13-generic i386 3.0.0-13.22 [36.5 MB]
Fetched 36.5 MB in 43s (835 kB/s)                                              
(Reading database ... 251013 files and directories currently installed.)
Preparing to replace linux-image-3.0.0-13-generic 3.0.0-13.22 (using .../linux-image-3.0.0-13-generic_3.0.0-13.22_i386.deb) ...
Done.
Unpacking replacement linux-image-3.0.0-13-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.0.0-14-generic...
P: Writing config for /boot/vmlinuz-3.0.0-13-generic.dpkg-tmp...
P: Writing config for /boot/vmlinuz-3.0.0-13-generic...
P: Updating /boot/extlinux/linux.cfg...
P: Writing config for Windows Recovery Environment (loader) on /dev/sda1...
P: Writing config for Windows 7 (loader) on /dev/sda2...
E: /usr/share/syslinux/debian/extlinux: No such file or directory
run-parts: /etc/kernel/postrm.d/zz-extlinux exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.0.0-13-generic.postrm line 328.
dpkg: warning: subprocess old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.0.0-14-generic...
P: Writing config for /boot/vmlinuz-3.0.0-13-generic.dpkg-tmp...
P: Writing config for /boot/vmlinuz-3.0.0-13-generic...
P: Writing config for Windows Recovery Environment (loader) on /dev/sda1...
P: Writing config for Windows 7 (loader) on /dev/sda2...
E: /usr/share/syslinux/debian/extlinux: No such file or directory
run-parts: /etc/kernel/postrm.d/zz-extlinux exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/tmp.ci/postrm line 328.
dpkg: error processing /var/cache/apt/archives/linux-image-3.0.0-13-generic_3.0.0-13.22_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.0.0-14-generic...
P: Writing config for /boot/vmlinuz-3.0.0-13-generic...
P: Updating /boot/extlinux/linux.cfg...
P: Writing config for Windows Recovery Environment (loader) on /dev/sda1...
P: Writing config for Windows 7 (loader) on /dev/sda2...
E: /usr/share/syslinux/debian/extlinux: No such file or directory
run-parts: /etc/kernel/postrm.d/zz-extlinux exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/tmp.ci/postrm line 328.
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.0.0-13-generic_3.0.0-13.22_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```I tried running ** dpkg --configure -a**:

```
Setting up linux-image-3.0.0-14-generic (3.0.0-14.23) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.0.0-14-generic...
P: Writing config for /boot/vmlinuz-3.0.0-13-generic...
P: Writing config for Windows Recovery Environment (loader) on /dev/sda1...
P: Writing config for Windows 7 (loader) on /dev/sda2...
E: /usr/share/syslinux/debian/extlinux: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-extlinux exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-14-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-14-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.0.0-14-generic; however:
  Package linux-image-3.0.0-14-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.0.0.14.16); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.0.0-14-generic
 linux-image-generic
 linux-generic
```Now I can't even install/uninstall other packages...Please help!

---

### Post by sordna on 2011-12-06
try moving /etc/kernel/postinst.d/zz-extlinux
out of the way temporarily, since that's what seems to be giving you the errors.
That should allow you clean up, and then you can remove the proposed repository and install the regular kernel from the main repository.

---

