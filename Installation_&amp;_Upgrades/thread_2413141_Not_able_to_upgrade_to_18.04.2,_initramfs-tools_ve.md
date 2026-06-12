---
title: "Not able to upgrade to 18.04.2, initramfs-tools version 0.122ubuntu8.14 bug?"
date: 2019-02-21
forum: Installation &amp; Upgrades
---

### Post by mike810 on 2019-02-21
I upgraded the system from 14.04.5 to 16.04.5

After upgrade, I tried to remove the old kernel 3.16.0-71 
```
# dpkg -l|grep linux-im
ii  linux-image-3.16.0-71-generic       3.16.0-71.92~14.04.1                       amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-141-generic       4.4.0-141.167                              amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-71-generic 3.16.0-71.92~14.04.1                       amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-141-generic 4.4.0-141.167                              amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                 4.4.0.141.147           
```

However, I am not able to remove one of the component (linux-image-extra-3.16.0-71-generic).  
```
||/ Name                                   Version                  Architecture             Description
+++-======================================-========================-========================-=================================================================================
rH  linux-image-extra-3.16.0-71-generic    3.16.0-71.92~14.04.1     amd64                    Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP

I tried to remove it again:
# apt-get remove --purge linux-image-extra-3.16.0-71-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-image-extra-3.16.0-71-generic*
0 upgraded, 0 newly installed, 1 to remove and 58 not upgraded.
After this operation, 157 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 71907 files and directories currently installed.)
Removing linux-image-extra-3.16.0-71-generic (3.16.0-71.92~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-71-generic /boot/vmlinuz-3.16.0-71-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-71-generic /boot/vmlinuz-3.16.0-71-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-71-generic
sync: invalid option -- 'f'
Try `sync --help' for more information.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.16.0-71-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

The pkg become half installed and every time I tried to run any apt install, remove, or update command will result the same error messages of trying to remove linux-image-extra-3.16.0-71-generic.

I have tried 
```
dpkg --configure -a
apt-get install -f
apt-get autoclean
apt-get autoremove
dpkg --remove --force-remove-reinstreq  linux-image-extra-3.16.0-71-generic
```

and still the same.

-- update 2/22
after debugging awhile, I finally realize it is the problem with initramfs-tools on version 0.122ubuntu8.14.  

I re-install 0.122ubuntu8 version and mark the version to hold so it won't upgrade to 0.122ubuntu8.14 version.  I was able to remove old kernels and run all necessary upgrade/update.  

I am about to upgrade to 18.04.2 so I need to unhold initramfs-tools so it can be upgrade to the latest version before system upgrade.  

Now I can't upgrade to 18.04.2 because of initramfs-tools(0.122ubuntu8.14)
```
Setting up initramfs-tools (0.122ubuntu8.14) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.122ubuntu8.14) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-142-generic
sync: invalid option -- 'f'
Try `sync --help' for more information.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools

Upgrade incomplete
```


Please help

thanks

---

