---
title: "Update fails for some reason."
date: 2012-07-04
forum: Installation &amp; Upgrades
---

### Post by ConfusedHP on 2012-07-04
Whenever I try to update my packages, things seem to go ok. Then towards the end, I get this output and I am unsure as to how to remedy the problem:

Setting up linux-image-3.2.0-26-generic (3.2.0-26.41) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-26-generic...
P: Writing config for /boot/vmlinuz-3.2.0-25-generic...
P: Writing config for /boot/vmlinuz-3.2.0-23-generic...
P: Writing config for Windows 7 (loader) on /dev/sda3...
E: /usr/share/syslinux/themes/debian/extlinux: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-extlinux exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-26-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-26-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-26-generic; however:
  Package linux-image-3.2.0-26-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.26.28); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-3.2.0-26-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


How do I fix this problem? 

EDIT: Here is another example of output I got when trying to install GIMP editor from the Ubuntu Software Center Repo:

installArchives() failed: Selecting previously unselected package libgegl-0.0-0. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 242821 files and directories currently installed.) 
Unpacking libgegl-0.0-0 (from .../libgegl-0.0-0_0.0.22-2ubuntu3_amd64.deb) ... 
Selecting previously unselected package gimp. 
Unpacking gimp (from .../gimp_2.6.12-1ubuntu1_amd64.deb) ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for man-db ... 
Processing triggers for menu ... 
Setting up linux-image-3.2.0-26-generic (3.2.0-26.41) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic 
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic 
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic 
P: Checking for EXTLINUX directory... found. 
P: Writing config for /boot/vmlinuz-3.2.0-26-generic... 
P: Writing config for /boot/vmlinuz-3.2.0-25-generic... 
P: Writing config for /boot/vmlinuz-3.2.0-23-generic... 
P: Writing config for Windows 7 (loader) on /dev/sda3... 
E: /usr/share/syslinux/themes/debian/extlinux: No such file or directory 
run-parts: /etc/kernel/postinst.d/zz-extlinux exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-26-generic.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-26-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of linux-image-generic: 
 linux-image-generic depends on linux-image-3.2.0-26-generic; however: 
  Package linux-image-3.2.0-26-generic is not configured yet. 
dpkg: error processing linux-image-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic: 
 linux-generic depends on linux-image-generic (= 3.2.0.26.28); however: 
  Package linux-image-generic is not configured yet. 
dpkg: error processing linux-generic (--configure): 
 dependency problems - leaving unconfigured 
Setting up libgegl-0.0-0 (0.0.22-2ubuntu3) ... 
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
Setting up gimp (2.6.12-1ubuntu1) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Processing triggers for menu ... 
Errors were encountered while processing: 
 linux-image-3.2.0-26-generic 
 linux-image-generic 
 linux-generic 
Setting up linux-image-3.2.0-26-generic (3.2.0-26.41) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic 
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic 
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic 
P: Checking for EXTLINUX directory... found. 
P: Writing config for /boot/vmlinuz-3.2.0-26-generic... 
P: Writing config for /boot/vmlinuz-3.2.0-25-generic... 
P: Writing config for /boot/vmlinuz-3.2.0-23-generic... 
P: Writing config for Windows 7 (loader) on /dev/sda3... 
E: /usr/share/syslinux/themes/debian/extlinux: No such file or directory 
run-parts: /etc/kernel/postinst.d/zz-extlinux exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-26-generic.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-26-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of linux-image-generic: 
 linux-image-generic depends on linux-image-3.2.0-26-generic; however: 
  Package linux-image-3.2.0-26-generic is not configured yet. 
dpkg: error processing linux-image-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic: 
 linux-generic depends on linux-image-generic (= 3.2.0.26.28); however: 
  Package linux-image-generic is not configured yet. 
dpkg: error processing linux-generic (--configure): 
 dependency problems - leaving unconfigured 


The package seemed to install fine, but I still keep getting this output. Please help!

---

### Post by dino99 on 2012-07-04
i suppose you not only use the packages from archives, but some extra repo outside ubuntu, right ?

---

### Post by ConfusedHP on 2012-07-04
I recently uninstalled the Kubuntu and Ubuntu desktops from the Lubuntu one. As far as repos go, I think I only utilize what is given.  

Everything else seems to work fantastic, though. Even when I go to install programs from the Software center, the error above pops up but it still manages to install anyway. What should I do with my repos to solve this problem? Is the info I provided not enough?

---

### Post by ConfusedHP on 2012-07-04
Is there anything else that I should include for troubleshooting purposes? This thing really is concerning me, and I cannot seem to find a solution on here as I did with my last thread.

---

### Post by frijj2k on 2012-07-05
Same problem here...  

Running latest Kubuntu and problem occurs when trying to update system to kernel 3.2.0-26-generic.

update-initramfs fails with:

Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-26-generic.postinst line 1010.

Any ideas?

---

### Post by ConfusedHP on 2012-07-05
I really am at a loss as to why this is happening. Do you get the same exact output that I get? Or is it slightly attenuated?

Thank goodness I have a Windows 7 partition just in case this turns out to be something serious.

---

### Post by dino99 on 2012-07-05
Well guys, you are mixing kde (kubuntu) with gnome2 (lubuntu) and gnome3 (ubuntu)

so remember what your mom says: clean & sort your room :P

try:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

if you are lucky then (maybe) your system will work; otherwise let's go for a new fresh install ;)

---

### Post by frijj2k on 2012-07-05
@dino99

Thank dino... your suggestions didn't fix the problem but running final command (sudo apt-get autoremove) alerted me to the fact that my /boot partition was full.

I deleted old unused kernels and now everything is OK.

Thanks again!

---

### Post by ConfusedHP on 2012-07-05
Those commands did not help to rectify the problem on my PC either. I appreciate you taking the time out to troubleshoot with us, but I honestly thought this process would be incredibly simple.

Do I really need to reinstall the entire thing again just to remedy this problem? I mean I have a significant amount of data, and it would take an enormous amount of time.

---

### Post by ConfusedHP on 2012-07-06
Lol. looks like it's back to windows then. I appreciate the suggestions, but maybe i'll try this thing out a couple months from now when it is more stable.

Thanks!):P

---

