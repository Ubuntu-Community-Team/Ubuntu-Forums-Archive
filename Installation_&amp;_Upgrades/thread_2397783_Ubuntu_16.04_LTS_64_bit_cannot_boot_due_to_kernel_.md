---
title: "Ubuntu 16.04 LTS 64 bit: cannot boot due to kernel module loading problem"
date: 2018-08-03
forum: Installation &amp; Upgrades
---

### Post by erotavlas on 2018-08-03
Hi,
I have a problem with boot on my ubuntu 16.04 LTS 64 bit and kernel 4.13 after that I tried to install anbox by following the official documentation.
I have different modules that are not properly loaded ```
ashmem_linux, binder_linux, vboxdrv.
```

```
journalctl | grep module
ago 03 11:04:25 user-laptop kernel: ACPI: Executed 1 blocks of module-level executable AML code
ago 03 11:04:25 user-laptop kernel: loop: module loaded
ago 03 11:04:25 user-laptop systemd-modules-load[272]: Failed to find module 'ashmem_linux'
ago 03 11:04:25 user-laptop systemd-modules-load[272]: Failed to find module 'binder_linux'
ago 03 11:04:25 user-laptop systemd-modules-load[272]: Inserted module 'lp'
ago 03 11:04:25 user-laptop systemd-modules-load[272]: Inserted module 'ppdev'
ago 03 11:04:25 user-laptop systemd-modules-load[272]: Inserted module 'parport_pc'
ago 03 11:04:25 user-laptop systemd-udevd[314]: NAME="%k" is ignored, because it breaks kernel supplied names, please remove it from /lib/udev/rules.d/60-anbox-modules-dkms.rules:1
ago 03 11:04:25 user-laptop systemd-udevd[314]: NAME="%k" is ignored, because it breaks kernel supplied names, please remove it from /lib/udev/rules.d/60-anbox-modules-dkms.rules:2
ago 03 11:04:32 user-laptop systemd-modules-load[888]: Failed to find module 'ashmem_linux'
ago 03 11:04:32 user-laptop systemd-modules-load[888]: Failed to find module 'binder_linux'
ago 03 11:04:32 user-laptop systemd[1]: systemd-modules-load.service: Main process exited, code=exited, status=1/FAILURE
ago 03 11:04:32 user-laptop systemd[1]: systemd-modules-load.service: Unit entered failed state.
ago 03 11:04:32 user-laptop systemd[1]: systemd-modules-load.service: Failed with result 'exit-code'.
ago 03 11:04:43 user-laptop gpu-manager[1142]: Error: can't open /lib/modules/4.13.0-45-generic/updates/dkms
ago 03 11:04:43 user-laptop gpu-manager[1142]: Error: can't open /lib/modules/4.13.0-45-generic/updates/dkms
ago 03 11:04:44 user-laptop lightdm[1430]: PAM adding faulty module: pam_kwallet.so
ago 03 11:04:44 user-laptop lightdm[1430]: PAM adding faulty module: pam_kwallet5.so
ago 03 11:04:45 user-laptop lightdm[1507]: PAM adding faulty module: pam_kwallet.so
ago 03 11:04:45 user-laptop lightdm[1507]: PAM adding faulty module: pam_kwallet5.so
ago 03 11:04:49 user-laptop systemd[1]: Starting LSB: VirtualBox Linux kernel module...
ago 03 11:04:49 user-laptop virtualbox[1552]:  * Loading VirtualBox kernel modules...
ago 03 11:04:49 user-laptop virtualbox[1552]:  * No suitable module for running kernel found
ago 03 11:04:49 user-laptop systemd[1]: Failed to start LSB: VirtualBox Linux kernel module.
ago 03 11:04:50 user-laptop tlp[1665]: Loading kernel modules...done.
ago 03 11:07:03 user-laptop systemd[1]: Stopped LSB: VirtualBox Linux kernel module.
ago 03 11:07:03 user-laptop systemd[1]: Starting LSB: VirtualBox Linux kernel module...
ago 03 11:07:03 user-laptop virtualbox[5615]:  * Loading VirtualBox kernel modules...
ago 03 11:07:03 user-laptop virtualbox[5615]:  * No suitable module for running kernel found
ago 03 11:07:03 user-laptop systemd[1]: Failed to start LSB: VirtualBox Linux kernel module.
ago 03 11:07:46 user-laptop systemd[1]: Stopped LSB: VirtualBox Linux kernel module.
ago 03 11:07:46 user-laptop systemd[1]: Starting LSB: VirtualBox Linux kernel module...
ago 03 11:07:46 user-laptop virtualbox[6071]:  * Loading VirtualBox kernel modules...
ago 03 11:07:46 user-laptop virtualbox[6071]:  * No suitable module for running kernel found
ago 03 11:07:46 user-laptop systemd[1]: Failed to start LSB: VirtualBox Linux kernel module.
ago 03 11:10:33 user-laptop systemd-udevd[314]: NAME="%k" is ignored, because it breaks kernel supplied names, please remove it from /lib/udev/rules.d/60-anbox-modules-dkms.rules:1
ago 03 11:10:33 user-laptop systemd-udevd[314]: NAME="%k" is ignored, because it break

```

I searched a lot on the Web, I also installed different kernel versions without success. What can I do?
Thank you

---

### Post by erotavlas on 2018-08-06
Hi,
I intalled the lastest kernel from 18.04 via
```
apt-get install linux-image-generic-hwe-16.04 linux-headers-generic-hwe-16.04
```


```
journalctl | grep module
ago 04 19:47:33 user-laptop kernel: ACPI: Executed 1 blocks of module-level executable AML code
ago 04 19:47:33 user-laptop kernel: loop: module loaded
ago 04 19:47:33 user-laptop systemd-modules-load[279]: Inserted module 'lp'
ago 04 19:47:33 user-laptop systemd-modules-load[279]: Inserted module 'ppdev'
ago 04 19:47:33 user-laptop systemd-modules-load[279]: Inserted module 'parport_pc'
ago 04 19:47:33 user-laptop systemd-udevd[335]: NAME="%k" is ignored, because it breaks kernel supplied names, please remove it from /lib/udev/rules.d/60-anbox-modules-dkms.rules:1
ago 04 19:47:33 user-laptop systemd-udevd[335]: NAME="%k" is ignored, because it breaks kernel supplied names, please remove it from /lib/udev/rules.d/60-anbox-modules-dkms.rules:2
ago 04 19:48:14 user-laptop systemd[1]: Starting VirtualBox Linux kernel module...
ago 04 19:48:14 user-laptop vboxdrv.sh[1345]: vboxdrv.sh: Building VirtualBox kernel modules.
ago 04 19:48:14 user-laptop vboxdrv.sh[1513]: Building VirtualBox kernel modules.
ago 04 19:48:15 user-laptop lightdm[1680]: PAM adding faulty module: pam_kwallet.so
ago 04 19:48:15 user-laptop lightdm[1680]: PAM adding faulty module: pam_kwallet5.so
ago 04 19:48:16 user-laptop lightdm[2103]: PAM adding faulty module: pam_kwallet.so
ago 04 19:48:16 user-laptop lightdm[2103]: PAM adding faulty module: pam_kwallet5.so
ago 04 19:48:20 user-laptop systemd[1]: Starting LSB: VirtualBox Linux kernel module...
ago 04 19:48:20 user-laptop systemd[1]: Started LSB: VirtualBox Linux kernel module.
ago 04 19:49:09 user-laptop vboxdrv.sh[12757]: VirtualBox kernel modules built.
ago 04 19:49:09 user-laptop kernel: vboxdrv: loading out-of-tree module taints kernel.
ago 04 19:49:09 user-laptop kernel: vboxdrv: module verification failed: signature and/or required key missing - tainting kernel
ago 04 19:49:09 user-laptop systemd-udevd[335]: NAME="%k" is ignored, because it breaks kernel supplied names, please remove it from /lib/udev/rules.d/60-anbox-modules-dkms.rules:1
ago 04 19:49:09 user-laptop systemd-udevd[335]: NAME="%k" is ignored, because it breaks kernel supplied names, please remove it from /lib/udev/rules.d/60-anbox-modules-dkms.rules:2
ago 04 19:49:09 user-laptop systemd[1]: Started VirtualBox Linux kernel module.
ago 04 19:49:10 user-laptop tlp[12804]: Loading kernel modules...done.
ago 04 19:50:45 user-laptop org.gnome.gedit[2856]: (gedit:13745): libpeas-WARNING **: Error loading plugin '/usr/lib/x86_64-linux-gnu/gedit/plugins/dashboard.plugin': module name 'dashboard' has already been used
```

I still have a problem on boot. My graphic driver does not work properly.
Do you have any idea?

---

### Post by erotavlas on 2018-08-06
I solved by following [this]("https://askubuntu.com/a/646431").

---

