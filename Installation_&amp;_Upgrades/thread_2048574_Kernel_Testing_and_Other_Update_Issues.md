---
title: "Kernel Testing and Other Update Issues"
date: 2012-08-26
forum: Installation &amp; Upgrades
---

### Post by Alcidious on 2012-08-26
Hey y'all,

I'm running 12.04 32-bit, and my Samsung laptop started having screen issues about a month ago.  I submitted a bug-report and have been following instructions.  I updated to a successful upstream kernel, which fixed the issue.  But I need to test another kernel to further help out, and ultimately fix my problem.  So I downloaded the kernel at the link provided:

"Can folks affected by this bug as a regression in 3.2.0-27.43 test the
latest test kernel?

The test kernels can be downloaded from:
[http://people.canonical.com/~jsalisbury/lp1028151/](http://people.canonical.com/~jsalisbury/lp1028151/)

This kernel has the following commit reverted:
9a2e71ce177a1602a0502fbcbb3f11e4bae584e4"

Now, when I first tried to install the headers and images using the mainline build that had successfully worked.  But I received a number of error messages, and I loaded my original kernel and am now using that kernel to try and install the test kernels.  Here is the command and error output:

alcidious42@IronMan:~/Downloads$ sudo dpkg i *.deb
[sudo] password for alcidious42: 
dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
alcidious42@IronMan:~/Downloads$ sudo dpkg -i *.deb
Selecting previously unselected package linux-headers-3.2.0-30-generic.
(Reading database ... 210528 files and directories currently installed.)
Unpacking linux-headers-3.2.0-30-generic (from linux-headers-3.2.0-30-generic_3.2.0-30.47~lp1028151v2_i386.deb) ...
Preparing to replace linux-image-3.2.0-30-generic 3.2.0-30.47~lp1028151v2 (using linux-image-3.2.0-30-generic_3.2.0-30.47~lp1028151v2_i386.deb) ...
Done.
Unpacking replacement linux-image-3.2.0-30-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-30-generic /boot/vmlinuz-3.2.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-30-generic /boot/vmlinuz-3.2.0-30-generic
dpkg: dependency problems prevent configuration of linux-headers-3.2.0-30-generic:
 linux-headers-3.2.0-30-generic depends on linux-headers-3.2.0-30; however:
  Package linux-headers-3.2.0-30 is not installed.
dpkg: error processing linux-headers-3.2.0-30-generic (--install):
 dependency problems - leaving unconfigured
Setting up linux-image-3.2.0-30-generic (3.2.0-30.47~lp1028151v2) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.2.0-30.47~lp1028151v2 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.2.0-30.47~lp1028151v2 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-30-generic /boot/vmlinuz-3.2.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-30-generic /boot/vmlinuz-3.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-30-generic /boot/vmlinuz-3.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-30-generic /boot/vmlinuz-3.2.0-30-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.6.0-030600rc1-generic
Found initrd image: /boot/initrd.img-3.6.0-030600rc1-generic
Found linux image: /boot/vmlinuz-3.2.0-30-generic
Found initrd image: /boot/initrd.img-3.2.0-30-generic
Found linux image: /boot/vmlinuz-3.2.0-27-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-27-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
Errors were encountered while processing:
 linux-headers-3.2.0-30-generic




What should I do? Was the test kernel remotely successful in being installed?  If my original kernel had the problems with the flickering, which kernel should I boot?  I appreciate any help!

---

### Post by Doug S on 2012-08-26
It looks as though you didn't copy over the "all" header file. You need both, and one is needed to be loaded before the other. I never remember the order, so if it doesn't work I try the other one first (I do things one at a time, instead of *.deb).
It looks as though your linux-image did install, but I would suggest to do everything again.

---

### Post by Alcidious on 2012-08-27
Thanks Doug! Got it done, appreciate it!

---

