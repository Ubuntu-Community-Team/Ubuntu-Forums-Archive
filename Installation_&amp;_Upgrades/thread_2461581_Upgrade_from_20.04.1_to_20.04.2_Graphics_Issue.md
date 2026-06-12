---
title: "Upgrade from 20.04.1 to 20.04.2 Graphics Issue"
date: 2021-05-03
forum: Installation &amp; Upgrades
---

### Post by sampsonats on 2021-05-03
After upgrading from 20.04.1 to .2, the desktop is very sluggish.  The inxi command shows differences before and after.  Is this expected?  Is this my problem?

When I move a window around, top shows Xorg and gnome-shell taking a lot of CPU time.
[INDENT]BEFORE UPGRADE (20.04.1)[/INDENT]
[INDENT]dfr@m9kmission:~$ inxi -Gxi --display[/INDENT]
[INDENT]Graphics:  Device-1: Intel HD Graphics P630 driver:[COLOR=#ff0000] i915[/COLOR] [COLOR=#ff0000]v: kernel[/COLOR] bus ID: 00:02.0 [/INDENT]
[INDENT]           Display: server: X.Org 1.20.[COLOR=#ff0000]8[/COLOR] driver: [COLOR=#ff0000]i915 resolution: 1920x1200~60Hz[/COLOR] [/INDENT]
[INDENT]           OpenGL: renderer: [COLOR=#ff0000]Mesa Intel HD Graphics P630 (KBL GT2) v: 4.6[/COLOR] Mesa 20.2.6 direct render: Yes [/INDENT]

[INDENT]AFTER UPGRADE (20.04.2)
[/INDENT]
[INDENT]Graphics:  Device-1: Intel HD Graphics P630 driver:[COLOR=#ff0000] N/A[/COLOR] bus ID: 00:02.0 [/INDENT]
[INDENT]           Display: server: X.Org 1.20.[COLOR=#ff0000]9[/COLOR] driver: [COLOR=#ff0000]fbdev unloaded: modesetting,vesa resolution: 1920x1200~77Hz[/COLOR] [/INDENT]
[INDENT]           OpenGL: renderer:[COLOR=#ff0000] llvmpipe (LLVM 11.0.0 256 bits) v: 4.5[/COLOR] Mesa 20.2.6 direct render: Yes
[/INDENT]

I did the upgrade in the normal way: sudo apt update,  sudo apt upgrade

Thanks!

---

### Post by guiverc on 2021-05-03
You haven't been specific on whether or not you're using Ubuntu Server, Ubuntu Desktop or a *flavor* install of Ubuntu (*graphics implies desktop, but it's better if we're told and not making assumptions*).

 The significance to me of this is Server & *flavor* installs of 20.04 & 20.04.1 default to the GA kernel (meaning 20.04.1 & 20.04.2 both use the 5.4 kernel thus identical *kernel modules (drivers)*) 

*OR*

you're using Ubuntu Desktop (which defaulted to using the HWE kernel stack thus the 20.04.2 bump will mean you switch from 5.4 kernel to using 5.8 with the corresponding kernel modules being changed which didn't occur if using the GA stack).

If it was me, I'd likely test a 20.04.2 system (*live *can be used so you don't need to install/change your system) using the *other* software stack.  If it acts better there, I'd consider switching which stack I'm using (or at least install the other stack & use it until I've another solution; you can have both stacks installed with the only side effect being slightly more disk space used & more packages to upgrade)

ps:  I'd also `sudo apt full-upgrade` to ensure you're fully up-to-date, as some upgraded packages can be left behind with only `sudo apt upgrade`.

For more details on stack choices
- [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
- [URL="https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack"]https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack

[/URL]

---

### Post by Impavidus on 2021-05-04
You switched from using the proper graphics driver to software rendering, which explains the poor performance. This may be the result of a kernel upgrade, but shouldn't happen. Centainly not with Intel graphics. Does it work better if you boot an older kernel from the grub menu? That may be a temporary workaround.

Maybe some kernel packages weren't properly installed. Have a look:```
dpkg --list 'linux-*' | grep -v '^rc\|^ii\|^un'
```
For most people the upgrade from 20.04.1 to 20.04.2, including the kernel upgrade from 5.4 to 5.8, happened in January. The upgrade from .1 to .2 isn't very relevant, except that it more or less coincides with a major kernel upgrade.

---

### Post by sampsonats on 2021-05-04
Thanks for your gracious replies.

I am using Ubuntu 20.04.2 Desktop.

[COLOR=#000000]sudo apt full-upgrade didn't help.[/COLOR]

If I run kernel 5.4.0-42-generic from grub menu instead of 5.8.0-50-generic,** it works.**

I notice dmesg shows some issues related to i915.  Seems like some kind of a library mismatch??
dfr@m9kmission:~$ dmesg | grep i915
[    4.635852] i915: Unknown symbol drm_dp_cec_irq (err -2)
[    4.635873] i915: Unknown symbol drm_atomic_helper_check_modeset (err -2)
[    4.635918] i915: Unknown symbol drm_dp_clock_recovery_ok (err -2)
[    4.636008] i915: Unknown symbol drm_kms_helper_poll_fini (err -2)
[    4.636049] i915: Unknown symbol drm_lspcon_set_mode (err -2)
[    4.636343] i915: Unknown symbol drm_fb_helper_init (err -2)
[    4.636543] i915: Unknown symbol drm_fb_helper_debug_enter (err -2)
[    4.636581] i915: Unknown symbol drm_scdc_set_scrambling (err -2)
(and lots more similar)

I notice this also: (SPL is grub secondary program loader)
[    5.385826] spl: loading out-of-tree module taints kernel.
[    5.391424] znvpair: module license 'CDDL' taints kernel.
[    5.391425] Disabling lock debugging due to kernel taint

```
dpkg --list 'linux-*' | grep -v '^rc\|^ii\|^un'   Doesn't show any issues but I took out the \ and it displays:
dfr@m9kmission:~$ dpkg --list 'linux-*' | grep -v '^rc|^ii|^un' 
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                  Version              Architecture Description
+++-=====================================-====================-============-==============================================================
ii  linux-base                            4.5ubuntu3.1         all          Linux image base package
un  linux-doc                             <none>               <none>       (no description available)
ii  linux-firmware                        1.187.11             all          Firmware for Linux kernel drivers
un  linux-firmware-raspi2                 <none>               <none>       (no description available)
un  linux-firmware-snapdragon             <none>               <none>       (no description available)
ii  linux-generic-hwe-20.04               5.8.0.50.56~20.04.34 amd64        Complete Generic Linux kernel and headers
un  linux-headers                         <none>               <none>       (no description available)
un  linux-headers-3.0                     <none>               <none>       (no description available)
ii  linux-headers-5.4.0-42                5.4.0-42.46          all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-42-generic        5.4.0-42.46          amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.8.0-50-generic        5.8.0-50.56~20.04.1  amd64        Linux kernel headers for version 5.8.0 on 64 bit x86 SMP
ii  linux-headers-generic-hwe-20.04       5.8.0.50.56~20.04.34 amd64        Generic Linux kernel headers
ii  linux-hwe-5.8-headers-5.8.0-50        5.8.0-50.56~20.04.1  all          Header files related to Linux kernel version 5.8.0
un  linux-hwe-5.8-source-5.8.0            <none>               <none>       (no description available)
un  linux-hwe-5.8-tools                   <none>               <none>       (no description available)
un  linux-image                           <none>               <none>       (no description available)
ii  linux-image-5.4.0-42-generic          5.4.0-42.46          amd64        Signed kernel image generic
ii  linux-image-5.8.0-50-generic          5.8.0-50.56~20.04.1  amd64        Signed kernel image generic
ii  linux-image-generic-hwe-20.04         5.8.0.50.56~20.04.34 amd64        Generic Linux kernel image
un  linux-image-unsigned-5.4.0-42-generic <none>               <none>       (no description available)
un  linux-image-unsigned-5.8.0-50-generic <none>               <none>       (no description available)
un  linux-initramfs-tool                  <none>               <none>       (no description available)
un  linux-kernel-log-daemon               <none>               <none>       (no description available)
ii  linux-modules-5.4.0-42-generic        5.4.0-42.46          amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.8.0-50-generic        5.8.0-50.56~20.04.1  amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-42-generic  5.4.0-42.46          amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.8.0-50-generic  5.8.0-50.56~20.04.1  amd64        Linux kernel extra modules for version 5.8.0 on 64 bit x86 SMP
un  linux-restricted-common               <none>               <none>       (no description available)
ii  linux-sound-base                      1.0.25+dfsg-0ubuntu5 all          base package for ALSA and OSS sound systems
un  linux-source-5.4.0                    <none>               <none>       (no description available)
un  linux-tools                           <none>               <none>       (no description available)
```




Any further ideas what might be wrong or how to go about debugging?

---

### Post by sampsonats on 2021-05-07
I edited grub to boot the 5.4 kernel and everything works.  The problem is, this is not just one computer.  This is part of a process to setup computers in production.  It is difficult for production to edit grub as opposed to just hitting a button.

Is it likely that the 5.8 kernel will start working after some updates?

Is it possible for me to 'fix' the 5.8 kernel now?  The setup is automated with Ansible so I can easily do pretty much anything if I knew what to do.

Every time I've seen 'unknown symbol' error, it's been some kind of a library mis-match.

It would be huge if someone could help me.

Thanks!

---

### Post by grahammechanical on 2021-05-07
This link will explain what llvmpipe is:

[https://docs.mesa3d.org/drivers/llvmpipe.html](https://docs.mesa3d.org/drivers/llvmpipe.html)

You could try going to Software & Updates? Additional Drivers tab and activating a proprietary video driver if one is available. We need to be connected to the internet to do this.

We can do this from the command line. This command will show the graphic hardware.

```
ubuntu-drivers devices
```

This command will show available drivers

```
ubuntu-drivers list
```

This command will automatically install the latest available driver.

```
ubuntu-drivers autoinstall
```

Regards

---

### Post by Impavidus on 2021-05-08
The 5.8 kernel was properly installed, so that's not the issue. Maybe a later upgrade to the 5.8 kernel fixes it. But when upgrading to the kernels used by 21.04, 21.10 and 22.04 3 months after those get released, similar problems might happen again. The other option is to just stick to the 5.4 kernels by using the standard kernels instead of the HWE kernels. Install the linux-generic package, remove linux-generic-hwe-20.04 (both are metapackages) and autoremove all 5.8 kernel packages.

---

### Post by ajgreeny on 2021-05-08
I would be tempted to remove any packages with hwe in their names, probably easiest found using synaptic and searching for "name" only, then replacing, for example,  ***linux-generic-hwe-20.04*** with ***linux-generic***.

When you then run the update/upgrade commands your currently installed 5.4.0-42 will be added to and you will get 5.4.0-72 as well, the latest in the 5.4 series.

I am aware that there have been several users having problems with the 5.8 kernel series, particularly earlier in its life with versions 5.8.0-32, I believe, but have not paid a great deal of attention to that as I have never needed nor used any of the hwe series of kernels or xorg packages that can be useful for users with very recent hardware.
As the 5.4.0- kernel series is fully supported throughout the life of 20.04 and my hardware is now a minimum of 6 years old and works very well with that series, I see no reason to move to the hwe series of 5.8.0-.

"If it ain't broke, don't fix it!"  and the 5.4.0- series ain't broke!

---

