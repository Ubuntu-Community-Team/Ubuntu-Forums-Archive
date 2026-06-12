---
title: "Lucid daily 4/7 kubuntu amd64 with nvidia drivers"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zanophol on 2010-04-08
I had downloaded the daily build for 4/7 not knowing if another beta was going to come out because I wanted to try some things with the 2.6.32 kernel. I did not get very far...

The box with the issue has an Nvidia GeForce series 9 card in it (don't remember the exact model offhand), but when Lucid installed, it used the nouveau driver. I want 3d effects for compositing etc, so I went to install the latest nvidia drivers (with the nouveau driver blacklisted even). I have tried from the repo's with nvidia-latest and the latest from nvidia's website. Both complain that they cannot find my kernel source code. It is loaded, as everything else I try builds fine (I have several other things that need it like vmware and a custom ethernet driver). However, with all the other links on this board about this problem, no where is it acknowledged that this is indeed broken (only alluded to).

Can someone verify? Is this indeed broken for the time being? I am currently stuck with the nouveau driver for now...

---

### Post by mionescu on 2010-04-08
Did you try "System->Administration->Hardware drivers"? You should have installed "nvidia-current"; see the release notes:
[http://www.ubuntu.com/testing/lucid/beta2](http://www.ubuntu.com/testing/lucid/beta2)

---

### Post by zanophol on 2010-04-08
I misspoke...My post should read "nvidia-current" not nvidia-latest. I have tried to install it from the repo, as well as nvidia website. Same issue with cannot find kernel source code, even though it is there and I can verify it.

---

### Post by mionescu on 2010-04-08
What about "Hardware drivers" option? That worked for me. In the release notes it is stated that the drivers from the nvidia website do not work in Lucid, but installing them using the "Hardware drivers" should work. Did you try to install, by mistake, nvidia-current-dev?

---

### Post by zanophol on 2010-04-08
I have tried both the 190 (current) and 173 drivers with the same issue. I have ensured that all packages are up to date.

---

### Post by zanophol on 2010-04-09
I can confirm that this happens with Kubuntu 10.04 beta 2 as well. I have wiped the 4.7 daily and installed beta 2. NO DICE with the installation of nvidia-current even when using the xorg-edgers repository. I have tried installing with apt-get install nvidia-current, as well as through jockey. The build process fails when it hits the update-initramfs step.

After the install fails, I try "sudo apt-get -f install", which yields:

Reading package lists... Done
Building dependency tree      
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up nvidia-current (195.36.15-0ubuntu1) ...
update-initramfs: deferring update (trigger activated)
Removing old nvidia-current-195.36.15 DKMS files...

------------------------------
Deleting module version: 195.36.15
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-current-195.36.15 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-19-generic
Building for architecture x86_64
Building initial module for 2.6.32-19-generic

Error! Bad return status for module build on kernel: 2.6.32-19-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-current/195.36.15/build/ for more information.
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 10
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-19-generic
Errors were encountered while processing:
 nvidia-current
E: Sub-process /usr/bin/dpkg returned an error code (1)
________________________

The make.log contains:

DKMS make.log for nvidia-current-195.36.15 for kernel 2.6.32-19-generic (x86_64)
Fri Apr  9 10:32:57 EDT 2010
If you are using a Linux 2.4 kernel, please make sure
you either have configured kernel sources matching your
kernel or the correct set of kernel headers installed
on your system.

If you are using a Linux 2.6 kernel, please make sure
you have configured kernel sources matching your kernel
installed on your system. If you specified a separate
output directory using either the "KBUILD_OUTPUT" or
the "O" KBUILD parameter, make sure to specify this
directory with the SYSOUT environment variable or with
the equivalent nvidia-installer command line option.

Depending on where and how the kernel sources (or the
kernel headers) were installed, you may need to specify
their location with the SYSSRC environment variable or
the equivalent nvidia-installer command line option.

*** Unable to determine the target kernel version. ***

make: *** [select_makefile] Error 1
__________________________

Ironically, this is the same error that the nvidia drivers from the nvidia website yields. Something is broken here!!!

---

### Post by zanophol on 2010-04-14
This was solved with the kernel 2.6.32-20 release.

---

