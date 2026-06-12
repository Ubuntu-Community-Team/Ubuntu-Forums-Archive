---
title: "In the middle of an update, got error, need to fix before reboot."
date: 2015-05-22
forum: Installation &amp; Upgrades
---

### Post by MistyFoggyRain on 2015-05-22
Just did an update via terminal:

```
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-49 linux-headers-3.13.0-49-generic
  linux-image-3.13.0-49-generic linux-image-extra-3.13.0-49-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  fglrx-core linux-headers-3.13.0-53 linux-headers-3.13.0-53-generic
  linux-image-3.13.0-53-generic linux-image-extra-3.13.0-53-generic
The following packages will be upgraded:
  accountsservice apport apport-gtk fglrx fglrx-amdcccle fuse
  libaccountsservice0 libfuse2 liboxideqt-qmlplugin liboxideqtcore0
  liboxideqtquick0 libspice-server1 linux-firmware linux-headers-generic
  linux-image-generic linux-libc-dev oxideqt-codecs-extra python3-apport
  python3-problem-report
19 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 227 MB of archives.
After this operation, 490 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
```

It downloaded and unpacked files, everything was automated until it asked for my input before replacing the following files:
I backed them up then chose to replace them:

```
DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Setting up fglrx (2:15.200-0ubuntu0.3) ...

Configuration file '/etc/ati/amdpcsdb.default'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** amdpcsdb.default (Y/I/N/O/D/Z) [default=N] ? Y
Installing new version of config file /etc/ati/amdpcsdb.default ...

Configuration file '/etc/ati/atiapfxx'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** atiapfxx (Y/I/N/O/D/Z) [default=N] ? Y
Installing new version of config file /etc/ati/atiapfxx ...

Configuration file '/etc/ati/control'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** control (Y/I/N/O/D/Z) [default=N] ? ^[Y 

Configuration file '/etc/ati/control'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** control (Y/I/N/O/D/Z) [default=N] ? Y
Installing new version of config file /etc/ati/control ...

Configuration file '/etc/ati/signature'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** signature (Y/I/N/O/D/Z) [default=N] ? Y
Installing new version of config file /etc/ati/signature ...

Configuration file '/etc/ati/atiapfxx.log'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** atiapfxx.log (Y/I/N/O/D/Z) [default=N] ? Y
Installing new version of config file /etc/ati/atiapfxx.log ...

Configuration file '/etc/ati/atiapfxx.blb'
 ==> File on system created by you or by a script.
 ==> File also in package provided by package maintainer.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** atiapfxx.blb (Y/I/N/O/D/Z) [default=N] ? Y   
Installing new version of config file /etc/ati/atiapfxx.blb ...
Creating backups for the fglrx-core transition
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken
Restoring backups for the fglrx-core transition
Setting up fglrx-amdcccle (2:15.200-0ubuntu0.3) ...
Setting up linux-firmware (1.127.12) ...
Setting up linux-headers-3.13.0-53 (3.13.0-53.89) ...
Setting up linux-headers-3.13.0-53-generic (3.13.0-53.89) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-53-generic /boot/vmlinuz-3.13.0-53-generic

Good news! Module version  for fglrx.ko
exactly matches what is already found in kernel 3.13.0-53-generic.
DKMS will not replace this module.
You may override by specifying --force.
Setting up linux-headers-generic (3.13.0.53.60) ...
Setting up linux-image-extra-3.13.0-53-generic (3.13.0-53.89) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-53-generic /boot/vmlinuz-3.13.0-53-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-53-generic /boot/vmlinuz-3.13.0-53-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-53-generic /boot/vmlinuz-3.13.0-53-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-53-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-53-generic /boot/vmlinuz-3.13.0-53-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-53-generic /boot/vmlinuz-3.13.0-53-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-53-generic /boot/vmlinuz-3.13.0-53-generic
Generating grub configuration file ...
Found theme: /boot/grub/themes/Zorin/theme.txt
Found linux image: /boot/vmlinuz-3.13.0-53-generic
Found initrd image: /boot/initrd.img-3.13.0-53-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-51-generic
Found initrd image: /boot/initrd.img-3.13.0-51-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
  No volume groups found
Found Windows XP Professional x64 Edition on /dev/sda1
done
Setting up linux-image-generic (3.13.0.53.60) ...
Setting up oxideqt-codecs-extra:amd64 (1.7.8-0ubuntu0.14.04.1) ...
Setting up liboxideqtcore0:amd64 (1.7.8-0ubuntu0.14.04.1) ...
Setting up liboxideqtquick0:amd64 (1.7.8-0ubuntu0.14.04.1) ...
Setting up liboxideqt-qmlplugin:amd64 (1.7.8-0ubuntu0.14.04.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-53-generic
W: Operation was interrupted before it could finish
```

Finally the error in red immediately above pops up.
I searched the net and found a site with an article dated back in 2010  that said to fix the error before rebooting or I'd probably not be able  to boot to Linux.
Which I'm doing right now, I've not yet rebooted.

How should I recover from such an error before I reboot.

The site had several solutions depending upon other variables, one of which was to delete and/or re-run something. But none of the solutions seemed to fit my case.

I'm running the Zorin OS 9 Theme on top of Ubuntu 14.04 LTS, an AMD PhenomII 64bit 4 core processor on an ASUS MB. The video card is also an AMD/ATI, hence the need for the fglrx drivers listed above.

I'm not sure if the overwriting of the ATI/AMD driver config files shown above are responsible for the error or not.  I did nothing that I was aware of that might have caused it, except close another instance of terminal that was runnning, and a libre office writer window.

Any ideas on how to solve this before I reboot would be greatly appreciated.

TIA

MistyFoggyRain

---

### Post by MistyFoggyRain on 2015-05-22
Thanks to EDDY1 in LinuxQuestions.org I simply opened a terminal window and executed the following command:

> sudo update-initramfs -u

It updated flawlessly. Then rebooted and had to change my display options, then everything was good.

Thanks to all that read my question, I really appreciate your time.

---

