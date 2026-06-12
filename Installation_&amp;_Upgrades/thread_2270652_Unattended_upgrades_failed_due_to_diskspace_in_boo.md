---
title: "Unattended upgrades failed due to diskspace in /boot. How to reinstall&amp;reconfig?"
date: 2015-03-24
forum: Installation &amp; Upgrades
---

### Post by soonthorn.ios on 2015-03-24
Hi,

System info
```

root@node-011:/# cat /etc/issue
Ubuntu 14.04.1 LTS \n \l


root@node-011:/# cat /proc/version_signature 
Ubuntu 3.13.0-34.60-generic 3.13.11.4



```

Our unattended upgrade failed due to no space left in /boot . 

```

[FONT=arial]unattended-upgrades-dpkg_2015-03-24_06:41:23.459705.log[/FONT]
[FONT=arial](Reading database ... 221703 files and directories currently installed.)[/FONT]
[FONT=arial]Preparing to unpack .../libgnutls-openssl27_2.12.23-12ubuntu2.2_amd64.deb ...[/FONT]
[FONT=arial]Unpacking libgnutls-openssl27:amd64 (2.12.23-12ubuntu2.2) over (2.12.23-12ubuntu2.1) ...[/FONT]
[FONT=arial]Preparing to unpack .../libgnutls26_2.12.23-12ubuntu2.2_amd64.deb ...[/FONT]
[FONT=arial]Unpacking libgnutls26:amd64 (2.12.23-12ubuntu2.2) over (2.12.23-12ubuntu2.1) ...[/FONT]
[FONT=arial]Selecting previously unselected package linux-image-3.13.0-48-generic.[/FONT]
[FONT=arial]Preparing to unpack .../linux-image-3.13.0-48-generic_3.13.0-48.80_amd64.deb ...[/FONT]
[FONT=arial]Done.[/FONT]
[FONT=arial]Unpacking linux-image-3.13.0-48-generic (3.13.0-48.80) ...[/FONT]
[FONT=arial]Selecting previously unselected package linux-image-extra-3.13.0-48-generic.[/FONT]
[FONT=arial]Preparing to unpack .../linux-image-extra-3.13.0-48-generic_3.13.0-48.80_amd64.deb ...[/FONT]
[FONT=arial]Unpacking linux-image-extra-3.13.0-48-generic (3.13.0-48.80) ...[/FONT]
[FONT=arial]Preparing to unpack .../linux-generic_3.13.0.48.55_amd64.deb ...[/FONT]
[FONT=arial]Unpacking linux-generic (3.13.0.48.55) over (3.13.0.46.53) ...[/FONT]
[FONT=arial]Preparing to unpack .../linux-image-generic_3.13.0.48.55_amd64.deb ...[/FONT]
[FONT=arial]Unpacking linux-image-generic (3.13.0.48.55) over (3.13.0.46.53) ...[/FONT]
[FONT=arial]Selecting previously unselected package linux-headers-3.13.0-48.[/FONT]
[FONT=arial]Preparing to unpack .../linux-headers-3.13.0-48_3.13.0-48.80_all.deb ...[/FONT]
[FONT=arial]Unpacking linux-headers-3.13.0-48 (3.13.0-48.80) ...[/FONT]
[FONT=arial]Selecting previously unselected package linux-headers-3.13.0-48-generic.[/FONT]
[FONT=arial]Preparing to unpack .../linux-headers-3.13.0-48-generic_3.13.0-48.80_amd64.deb ...[/FONT]
[FONT=arial]Unpacking linux-headers-3.13.0-48-generic (3.13.0-48.80) ...[/FONT]
[FONT=arial]Preparing to unpack .../linux-headers-generic_3.13.0.48.55_amd64.deb ...[/FONT]
[FONT=arial]Unpacking linux-headers-generic (3.13.0.48.55) over (3.13.0.46.53) ...[/FONT]
[FONT=arial]Setting up libgnutls26:amd64 (2.12.23-12ubuntu2.2) ...[/FONT]
[FONT=arial]Setting up libgnutls-openssl27:amd64 (2.12.23-12ubuntu2.2) ...[/FONT]
[FONT=arial]Setting up linux-image-3.13.0-48-generic (3.13.0-48.80) ...[/FONT]
[FONT=arial]Running depmod.[/FONT]
[FONT=arial]update-initramfs: deferring update (hook will be called later)[/FONT]
[FONT=arial]Examining /etc/kernel/postinst.d.[/FONT]
[FONT=arial]run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-48-generic /boot/vmlinuz-3.13.0-48-generic[/FONT]
[FONT=arial]run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-48-generic /boot/vmlinuz-3.13.0-48-generic[/FONT]
[FONT=arial]update-initramfs: Generating /boot/initrd.img-3.13.0-48-generic[/FONT]
[FONT=arial]run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-48-generic /boot/vmlinuz-3.13.0-48-generic[/FONT]
[FONT=arial]run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-48-generic /boot/vmlinuz-3.13.0-48-generic[/FONT]
[FONT=arial]Generating grub configuration file ...[/FONT]
[FONT=arial]Found linux image: /boot/vmlinuz-3.13.0-48-generic[/FONT]
[FONT=arial]Found initrd image: /boot/initrd.img-3.13.0-48-generic[/FONT]
[FONT=arial]Found linux image: /boot/vmlinuz-3.13.0-46-generic[/FONT]
[FONT=arial]Found initrd image: /boot/initrd.img-3.13.0-46-generic[/FONT]
[FONT=arial]Found linux image: /boot/vmlinuz-3.13.0-44-generic[/FONT]
[FONT=arial]Found initrd image: /boot/initrd.img-3.13.0-44-generic[/FONT]
[FONT=arial]Found linux image: /boot/vmlinuz-3.13.0-43-generic[/FONT]
[FONT=arial]Found initrd image: /boot/initrd.img-3.13.0-43-generic[/FONT]
[FONT=arial]Found linux image: /boot/vmlinuz-3.13.0-40-generic[/FONT]
[FONT=arial]Found initrd image: /boot/initrd.img-3.13.0-40-generic[/FONT]
[FONT=arial]Found linux image: /boot/vmlinuz-3.13.0-39-generic[/FONT]
[FONT=arial]Found initrd image: /boot/initrd.img-3.13.0-39-generic[/FONT]
[FONT=arial]Found linux image: /boot/vmlinuz-3.13.0-34-generic[/FONT]
[FONT=arial]Found initrd image: /boot/initrd.img-3.13.0-34-generic[/FONT]
[FONT=arial]Found memtest86+ image: /memtest86+.elf[/FONT]
[FONT=arial]Found memtest86+ image: /memtest86+.bin[/FONT]
[FONT=arial]done[/FONT]
[FONT=arial]Setting up linux-image-extra-3.13.0-48-generic (3.13.0-48.80) ...[/FONT]
[FONT=arial]run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-48-generic /boot/vmlinuz-3.13.0-48-generic[/FONT]
[FONT=arial]run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-48-generic /boot/vmlinuz-3.13.0-48-generic[/FONT]
[FONT=arial][COLOR=#b22222]update-initramfs: Generating /boot/initrd.img-3.13.0-48-generic[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222]
[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222]gzip: stdout: No space left on device[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222]E: mkinitramfs failure cpio 141 gzip 1[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222]update-initramfs: failed for /boot/initrd.img-3.13.0-48-generic with 1.[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222]run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222]dpkg: error processing package linux-image-extra-3.13.0-48-generic (--configure):[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222] subprocess installed post-installation script returned error exit status 1[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222]dpkg: dependency problems prevent configuration of linux-image-generic:[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222] linux-image-generic depends on linux-image-extra-3.13.0-48-generic; however:[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222]  Package linux-image-extra-3.13.0-48-generic is not configured yet.[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222]
[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222]dpkg: error processing package linux-image-generic (--configure):[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222] dependency problems - leaving unconfigured[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222]Setting up linux-headers-3.13.0-48 (3.13.0-48.80) ...[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222]No apport report written because the error message indicates its a followup error from a previous failure.[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222]Setting up linux-headers-3.13.0-48-generic (3.13.0-48.80) ...[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222]Setting up linux-headers-generic (3.13.0.48.55) ...[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222]dpkg: dependency problems prevent configuration of linux-generic:[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222] linux-generic depends on linux-image-generic (= 3.13.0.48.55); however:[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222]  Package linux-image-generic is not configured yet.[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222]
[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222]dpkg: error processing package linux-generic (--configure):[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222] dependency problems - leaving unconfigured[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222]No apport report written because the error message indicates its a followup error from a previous failure.[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222]Processing triggers for libc-bin (2.19-0ubuntu6.6) ...[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222]Errors were encountered while processing:[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222] linux-image-extra-3.13.0-48-generic[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222] linux-image-generic[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222] linux-generic[/COLOR][/FONT]
[FONT=arial][COLOR=#b22222]Error in function: [/COLOR][/FONT]



```

We have cleaned up /boot by running apt-get purge on some unused versions (we keep the current running one and the two latest ones).
```
[COLOR=#484848]apt-get purge  linux-headers-3.13.0-XX linux-headers-3.13.0-XX-generic  linux-image-3.13.0-XX-generic  linux-image-extra-3.13.0-XX-generic[/COLOR]  
```

Based on the log file, it said
[FONT=arial]Errors were encountered while processing:[/FONT]
[FONT=arial] linux-image-extra-3.13.0-48-generic[/FONT]
[FONT=arial] linux-image-generic[/FONT]
[FONT=arial] linux-generic

My questions are

1. 
What is the proper way to re-install/upgrade/config those packages?[/FONT]
Is the following command enough?

```
apt-get install --reinstall linux-image-extra-3.13.0-48-generic linux-image-generic linux-generic
```

I noticed that in unattened-upgrades log that there are errors during update-initramfs, run-parts, post installation script, configuration scripts.
Do I need to run other command after apt-get --reinstall those packages so that they are configured propertly?

2.
What exactly commands are run via unattended-upgrades? And how do I disable auto unattended-upgrades?

Thank you for your help.

---

### Post by ian-weisser on 2015-03-24
Are you, by chance, using LVM, encrypted disk, or another feature that requires a separate /boot partition?
There is a known bug that autoremoval of old kernels on separate /boot seems to be broken. Help locating and fixing the bug is welcome.

1) After you have freed some space by removing old kernel packages, simply re-run the upgrade.
If you specify a package to install, it will not be eligible for future auto-removal. In a few weeks, when the next kernel upgrade comes out, this will make your space problem worse.

2) Unattended-upgrades installs your security updates. With changed settings, it can be used for much more than that.
Best practice is to leave it enabled. If you are suffering from the separate /boot bug, then occasionally clean old kernels out of /boot manually.

---

### Post by Impavidus on 2015-03-24
You could try a lower level command to purge those old kernels:```
dpkg -P package1 package2
```(with root permissions of course, but I see you prefer a root terminal over sudo)
dpkg will uninstall a package without checking for broken stuff elsewhere. A great way to break your system, but also to fix it.

---

