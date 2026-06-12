---
title: "Latest kernel update 3.2.0-33  for 12.04 failed, Package system broken"
date: 2012-11-17
forum: Installation &amp; Upgrades
---

### Post by PhaseMod on 2012-11-17
My latest software update on my Ubuntu 12.04 system has failed leaving two header packages uninstalled:

linux-headers-3.2.0-33
linux-headers-3.2.0-33-generic-pae

Now dependencies appear to be severely compromised and the package system is broken according to the update manager.

Update software detail showed this:

```

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
(Reading database ... 431255 files and directories currently installed.)
Preparing to replace libgtk-3-bin 3.4.2-0ubuntu0.4 (using .../libgtk-3-bin_3.4.2-0ubuntu0.5_i386.deb) ...
Leaving 'diversion of /usr/sbin/update-icon-caches to /usr/sbin/update-icon-caches.gtk2 by libgtk-3-bin'
Leaving 'diversion of /usr/share/man/man8/update-icon-caches.8.gz to /usr/share/man/man8/update-icon-caches.gtk2.8.gz by libgtk-3-bin'
Unpacking replacement libgtk-3-bin ...
Preparing to replace libgail-3-0 3.4.2-0ubuntu0.4 (using .../libgail-3-0_3.4.2-0ubuntu0.5_i386.deb) ...
Unpacking replacement libgail-3-0 ...
Preparing to replace libgtk-3-0 3.4.2-0ubuntu0.4 (using .../libgtk-3-0_3.4.2-0ubuntu0.5_i386.deb) ...
Unpacking replacement libgtk-3-0 ...
Preparing to replace libgtk-3-common 3.4.2-0ubuntu0.4 (using .../libgtk-3-common_3.4.2-0ubuntu0.5_all.deb) ...
Unpacking replacement libgtk-3-common ...
Preparing to replace libtiff4 3.9.5-2ubuntu1.2 (using .../libtiff4_3.9.5-2ubuntu1.3_i386.deb) ...
Unpacking replacement libtiff4 ...
Selecting previously unselected package linux-image-3.2.0-33-generic.
Unpacking linux-image-3.2.0-33-generic (from .../linux-image-3.2.0-33-generic_3.2.0-33.52_i386.deb) ...
Done.
Preparing to replace gir1.2-gtk-3.0 3.4.2-0ubuntu0.4 (using .../gir1.2-gtk-3.0_3.4.2-0ubuntu0.5_i386.deb) ...
Unpacking replacement gir1.2-gtk-3.0 ...
Preparing to replace linux-generic 3.2.0.32.35 (using .../linux-generic_3.2.0.33.36_i386.deb) ...
Unpacking replacement linux-generic ...
Preparing to replace linux-image-generic 3.2.0.32.35 (using .../linux-image-generic_3.2.0.33.36_i386.deb) ...
Unpacking replacement linux-image-generic ...
Selecting previously unselected package linux-headers-3.2.0-33.
Unpacking linux-headers-3.2.0-33 (from .../linux-headers-3.2.0-33_3.2.0-33.52_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-33_3.2.0-33.52_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-33/arch/arm/plat-mxc/include/mach/mx3_camera.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-33/arch/arm/plat-mxc/include/mach/mx3_camera.h'): No space left on device
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Selecting previously unselected package linux-headers-3.2.0-33-generic.
Unpacking linux-headers-3.2.0-33-generic (from .../linux-headers-3.2.0-33-generic_3.2.0-33.52_i386.deb) ...
Selecting previously unselected package linux-headers-3.2.0-33-generic-pae.
Unpacking linux-headers-3.2.0-33-generic-pae (from .../linux-headers-3.2.0-33-generic-pae_3.2.0-33.52_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-33-generic-pae_3.2.0-33.52_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-33-generic-pae/include/config/sc1200/wdt.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-33-generic-pae/include/config/sc1200/wdt.h'): No space left on device
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to replace linux-headers-generic 3.2.0.32.35 (using .../linux-headers-generic_3.2.0.33.36_i386.deb) ...
Unpacking replacement linux-headers-generic ...
Preparing to replace linux-headers-generic-pae 3.2.0.32.35 (using .../linux-headers-generic-pae_3.2.0.33.36_i386.deb) ...
Unpacking replacement linux-headers-generic-pae ...
Preparing to replace linux-libc-dev 3.2.0-32.51 (using .../linux-libc-dev_3.2.0-33.52_i386.deb) ...
Unpacking replacement linux-libc-dev ...
Processing triggers for man-db ...
Processing triggers for libglib2.0-0 ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-33_3.2.0-33.52_all.deb
 /var/cache/apt/archives/linux-headers-3.2.0-33-generic-pae_3.2.0-33.52_i386.deb
Error in function: 
Setting up libgtk-3-common (3.4.2-0ubuntu0.5) ...
Setting up linux-image-3.2.0-33-generic (3.2.0-33.52) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-33-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-33-generic /boot/vmlinuz-3.2.0-33-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-33-generic
Found initrd image: /boot/initrd.img-3.2.0-33-generic
Found linux image: /boot/vmlinuz-3.2.0-32-generic
Found initrd image: /boot/initrd.img-3.2.0-32-generic
Found linux image: /boot/vmlinuz-3.2.0-31-generic
Found initrd image: /boot/initrd.img-3.2.0-31-generic
Found linux image: /boot/vmlinuz-3.2.0-30-generic
Found initrd image: /boot/initrd.img-3.2.0-30-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-27-generic
Found initrd image: /boot/initrd.img-3.2.0-27-generic
Found linux image: /boot/vmlinuz-3.2.0-26-generic
Found initrd image: /boot/initrd.img-3.2.0-26-generic
Found linux image: /boot/vmlinuz-3.2.0-25-generic
Found initrd image: /boot/initrd.img-3.2.0-25-generic
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.0.0-17-generic
Found initrd image: /boot/initrd.img-3.0.0-17-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
Found Windows NT/2000/XP on /dev/sda2
done
Setting up linux-libc-dev (3.2.0-33.52) ...
dpkg: dependency problems prevent configuration of linux-headers-3.2.0-33-generic:
 linux-headers-3.2.0-33-generic depends on linux-headers-3.2.0-33; however:
  Package linux-headers-3.2.0-33 is not installed.
dpkg: error processing linux-headers-3.2.0-33-generic (--configure):
 dependency problems - leaving unconfigured
Setting up libgtk-3-0 (3.4.2-0ubuntu0.5) ...
Setting up libtiff4 (3.9.5-2ubuntu1.3) ...
Setting up linux-image-generic (3.2.0.33.36) ...
dpkg: dependency problems prevent configuration of linux-headers-generic-pae:
 linux-headers-generic-pae depends on linux-headers-3.2.0-33-generic-pae; however:
  Package linux-headers-3.2.0-33-generic-pae is not installed.
dpkg: error processing linux-headers-generic-pae (--configure):
 dependency problems - leaving unconfigured
Setting up libgtk-3-bin (3.4.2-0ubuntu0.5) ...
Setting up linux-generic (3.2.0.33.36) ...
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.2.0-33-generic; however:
  Package linux-headers-3.2.0-33-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Setting up gir1.2-gtk-3.0 (3.4.2-0ubuntu0.5) ...
Setting up libgail-3-0 (3.4.2-0ubuntu0.5) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```Trying to update these again gives a daemon has stopped responding message and thereafter the update says the package system is broken. 

I opened the Ubuntu Software Center which notices the damage and trying to repair results in an error with this detail:

```

installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 444046 files and directories currently installed.) 
Unpacking linux-headers-3.2.0-33 (from .../linux-headers-3.2.0-33_3.2.0-33.52_all.deb) ... 
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-33_3.2.0-33.52_all.deb (--unpack): 
 unable to create `/usr/src/linux-headers-3.2.0-33/include/net/slhc_vj.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-33/include/net/slhc_vj.h'): No space left on device 
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Unpacking linux-headers-3.2.0-33-generic-pae (from .../linux-headers-3.2.0-33-generic-pae_3.2.0-33.52_i386.deb) ... 
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-33-generic-pae_3.2.0-33.52_i386.deb (--unpack): 
 error creating directory `./usr/src/linux-headers-3.2.0-33-generic-pae/include/config/pps': No space left on device 
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Errors were encountered while processing: 
 /var/cache/apt/archives/linux-headers-3.2.0-33_3.2.0-33.52_all.deb 
 /var/cache/apt/archives/linux-headers-3.2.0-33-generic-pae_3.2.0-33.52_i386.deb 
Error in function:  
dpkg: dependency problems prevent configuration of linux-headers-3.2.0-33-generic: 
 linux-headers-3.2.0-33-generic depends on linux-headers-3.2.0-33; however: 
  Package linux-headers-3.2.0-33 is not installed. 
dpkg: error processing linux-headers-3.2.0-33-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-headers-generic-pae: 
 linux-headers-generic-pae depends on linux-headers-3.2.0-33-generic-pae; however: 
  Package linux-headers-3.2.0-33-generic-pae is not installed. 
dpkg: error processing linux-headers-generic-pae (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-headers-generic: 
 linux-headers-generic depends on linux-headers-3.2.0-33-generic; however: 
  Package linux-headers-3.2.0-33-generic is not configured yet. 
dpkg: error processing linux-headers-generic (--configure): 
 dependency problems - leaving unconfigured 

```Not sure what to do from here :( Pretty certain my system will be unbootable now as I saw something similar happen last year which left me needing to reinstall with no relevant help found online.

Perhaps someone has an better idea of how to proceed?

---

### Post by PhaseMod on 2012-11-17
Finally digging in at this discovered there wasn't enough free space to install these (with >1GB free?!). Why are so many old header sources saved anyway?

Solution:

```

sudo apt-get autoclean
sudo rm -rf /usr/src/linux-kernel-headers-3.2.0-2*
sudo apt-get -f install

```

---

### Post by efflandt on 2012-11-18
It is up to you to clean house if you have a small separate /boot partition or / is full because Ubuntu is not going to know which older kernel(s) you need if a new one does not work for some reason.  Can you still boot one of the earlier kernels?

That used to be easier when Synaptic was the default package manager because you could enter **linux** as a search term to find and remove old kernel images and headers.  But if you did not install Synaptic from Software Center, the Software Center itself is useless for finding and removing old kernels.

You can find which kernels you have installed to remove with sudo apt-get with```
dpkg-query -l linux*
```Some people have written scripts to remove all but several most recent kernels, but I do not have such a script.

After removing any kernels, you should run```
sudo update-grub
```

---

### Post by PhaseMod on 2012-11-20
Thanks very much for the useful information.

I was able to remove  the linux-header packages with Software Manager that I had effectively  deleted from the command line once the apt-get was able to finish with  the two packages and fix the package system.

I was mostly  surprised that what was clearly showing as a free space problem in  apt-get was being shown to be something entirely different in Software  Manager and the Update Manager. And perhaps secondarily surprised that  1.2GB wasn't enough to install those two header packages. Maybe I should  be reviewing my quota system. ;)

Thanks again for the additional insight.

---

