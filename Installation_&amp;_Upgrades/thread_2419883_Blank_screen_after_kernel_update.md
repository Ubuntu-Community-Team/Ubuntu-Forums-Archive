---
title: "Blank screen after kernel update"
date: 2019-05-26
forum: Installation &amp; Upgrades
---

### Post by Ed_B on 2019-05-26
Hi, I have ubuntu 16.04 with NVIDIA Geforce 210, the graphic driver I use is NVDIA driver 340.107.  Things work fine under the kernel 4.15.0-47-generic.  However, the kernel 4.15.0-48-generic as well as 
4.15.0-50-generic boot into a blank screen.  Recovery boot with failsafe graphic mode leads to the same result.  Any idea on how to fix this?

---

### Post by CatKiller on 2019-05-27
When you install the Nvidia driver it uses DKMS to generate the kernel module for the kernel version that you're using. This is also supposed to happen when you upgrade to a new version of the kernel.

It's possible that DKMS hasn't been re-run when you've upgraded the kernel. Purging the Nvidia driver and reinstalling it should generate new modules.

If that doesn't help, you'll need to say where you got the driver from and look through logs to see where the problem lies.

---

### Post by Ed_B on 2019-05-29
Thank you very much for answer.  I got the NVDIA driver from the official ubuntu depository.  I am sure DKMS has run, since for a long time, at each kernel update, there was a warning saying that NVIDIA driver wasn't installed for the new kernel, which made me stick to 4.13.x kernel for very long time, and there was no such warning for update to  4.15.0-48 and 4.15.0-50 kernel.  Besides, when DKMS didn't run, I still had working display (I don't remember whether I was using nouveau or vesa/fbdev driver) even with the new kernel.   

Besides, I have ```
/lib/modules/4.15.0-50-generic/kernel/drivers/video/fbdev/nvidia
/lib/modules/4.15.0-50-generic/kernel/drivers/video/fbdev/nvidia/nvidiafb.ko
/lib/modules/4.15.0-50-generic/updates/dkms/nvidia_340.ko
/lib/modules/4.15.0-50-generic/updates/dkms/nvidia_340_uvm.ko


``` and when I boot into 4.15.0-48 or 4.15.0-50 kernel under recovery mode/root shell, dmesg shows that nvidia module is loaded.

Which log should I look into?  Log for Xorg?

---

### Post by CatKiller on 2019-05-29
dmesg should show information about modesetting during boot. /var/log/Xorg.0.log should show messages about how X is functioning. Whichever display manager you're using may have a log about its own startup, too.

Being able to ssh in, or using one of the TTYs, may help identify what state the computer is in when you're experiencing the issue: whether it's hung, whether X couldn't start, whether it thinks everything's fine but it's using a resolution your monitor can't display, and so on. There are a lot of steps between booting and displaying a picture and "blank screen" doesn't really narrow it down much.

---

### Post by Ed_B on 2019-07-10
It took me a while to figure out a correct way to do it (I only have SSH server under chroot environment: and I had to access the filesystem from the chroot, among other things)

lightdm's log doesn't say anything useful.  Dmesg | grep nvidia gives
```
[   72.128580] nvidia: loading out-of-tree module taints kernel.
[   72.128595] nvidia: module license 'NVIDIA' taints kernel.
[   72.144907] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[   72.152389] nvidia 0000:02:00.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=none:owns=io+mem
[   72.152775] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:02:00.0 on minor 0
[   72.349518] nvidia_uvm: Loaded the UVM driver, major device number 242
[   72.798940] Modules linked in: nvidia_uvm(POE) nvidia(POE) coretemp kvm_intel reiserfs kvm r8188eu(C) gpio_ich snd_hda_codec_hdmi snd_hda_codec_realtek irqbypass snd_ens1371 snd_ac97_codec snd_hda_codec_generic snd_hda_intel snd_hda_codec snd_hda_core snd_seq_midi snd_seq_midi_event gameport ac97_bus input_leds drm snd_rawmidi snd_hwdep snd_pcm snd_seq snd_seq_device snd_timer shpchp serio_raw snd soundcore mac_hid lpc_ich rtl8192cu rtl_usb rtl8192c_common rtlwifi mac80211 cfg80211 parport_pc ppdev lp parport autofs4 hid_generic usbhid hid uas psmouse firewire_ohci usb_storage e1000e firewire_core pata_acpi crc_itu_t ptp pps_core
[   72.799045] CPU: 3 PID: 1049 Comm: nvidia-smi Tainted: P         C OE    4.15.0-54-generic #58~16.04.1-Ubuntu
[   72.799496] EIP: _nv000768rm+0x7b/0x600 [nvidia]
[   72.799704]  ? rm_init_adapter+0x4c/0xac [nvidia]
[   72.799857]  ? nvidia_open+0x233/0x840 [nvidia]
[   72.799987]  ? nvidia_frontend_open+0x3d/0x80 [nvidia]
```

Actually, there is a chunck of lines in dmesg that looks like
```

[   72.799045] CPU: 3 PID: 1049 Comm: nvidia-smi Tainted: P         C OE    4.15
.0-54-generic #58~16.04.1-Ubuntu
[   72.799060] Hardware name: HP-Pavilion GL323AA-ABF m8180.fr/Berkeley, BIOS 5.
13    10/24/2007
[   72.799078] EIP: vmalloc_fault+0x20f/0x230
[   72.799087] EFLAGS: 00010086 CPU: 3
[   72.799096] EAX: 02788000 EBX: 00000000 ECX: ffe00000 EDX: 00000000
[   72.799107] ESI: fd000000 EDI: dee2ce80 EBP: ecd4dc34 ESP: ecd4dc1c
[   72.799118]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[   72.799129] CR0: 80050033 CR2: fa000140 CR3: 2cd40000 CR4: 000006f0
[   72.799149] Call Trace:
[   72.799168]  __do_page_fault+0x3ad/0x540
[   72.799187]  ? ioremap_nocache+0x12/0x20
[   72.799205]  ? __do_page_fault+0x540/0x540
[   72.799223]  do_page_fault+0x29/0x100
[   72.799241]  ? __do_page_fault+0x540/0x540
[   72.799260]  common_exception+0x130/0x136
[   72.799496] EIP: _nv000768rm+0x7b/0x600 [nvidia]
[   72.799514] EFLAGS: 00010286 CPU: 3
[   72.799531] EAX: ec48c468 EBX: ec48c400 ECX: 00000001 EDX: ec48c468
[   72.799551] ESI: fa000000 EDI: ec48c400 EBP: ecd35fac ESP: ecd4dcd8
[   72.799571]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[   72.799704]  ? rm_init_adapter+0x4c/0xac [nvidia]
[   72.799727]  ? irq_startup+0x3b/0xf0
[   72.799857]  ? nvidia_open+0x233/0x840 [nvidia]
[   72.799987]  ? nvidia_frontend_open+0x3d/0x80 [nvidia]
[   72.800009]  ? chrdev_open+0xa7/0x180
[   72.800037]  ? do_dentry_open+0x1ca/0x2f0
[   72.800055]  ? cdev_put+0x20/0x20
[   72.800073]  ? vfs_open+0x41/0x70
[   72.800099]  ? path_openat+0x24c/0x1240
[   72.800119]  ? shmem_xattr_handler_set+0x30/0x30
[   72.800138]  ? do_filp_open+0x68/0xe0
[   72.800159]  ? __alloc_fd+0x36/0x150
[   72.800177]  ? do_sys_open+0x111/0x280
[   72.800194]  ? dput+0xc5/0x1e0
[   72.800212]  ? SyS_open+0x1d/0x20
[   72.800230]  ? do_fast_syscall_32+0x7f/0x1f0
[   72.800250]  ? entry_SYSENTER_32+0x6b/0xbe
[   72.800267] Code: 00 20 00 21 ce 89 f0 0f ac d8 0c 89 c2 8d 04 80 c1 ea 11 c1
 e2 04 8b 92 40 f2 eb de 83 e2 f8 8d 04 c2 39 45 ec 0f 84 c2 fe ff ff <0f> 0b 8d
 b4 26 00 00 00 00 83 c4 0c b8 ff ff ff ff 5b 5e 5f 5d
[   72.800356] EIP: vmalloc_fault+0x20f/0x230 SS:ESP: 0068:ecd4dc1c
[   72.800377] ---[ end trace 77ddebe330629d42 ]---


```

And Kern.log contains same lines with the date.  Now, Xorg.0.log contains fewer lines than what it contains usually, there are only

```

[   420.039] 
X.Org X Server 1.19.6
Release Date: 2017-12-20
[   420.039] X Protocol Version 11, Revision 0
[   420.039] Build Operating System: Linux 4.4.0-138-generic i686 Ubuntu
[   420.039] Current Operating System: Linux onyx 4.15.0-54-generic #58~16.04.1-
Ubuntu SMP Mon Jun 24 13:21:14 UTC 2019 i686
[   420.039] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-54-generic roo
t=UUID=63353a4b-c794-44bf-95bf-57ed8eced7d9 ro recovery nomodeset
[   420.040] Build Date: 25 October 2018  04:12:07PM
[   420.040] xorg-server 2:1.19.6-1ubuntu4.1~16.04.2 (For technical support plea
se see http://www.ubuntu.com/support) 
[   420.040] Current version of pixman: 0.33.6
[   420.040]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   420.040] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   420.041] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul  9 17:10:02 201
9
[   420.064] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   420.078] (==) No Layout section.  Using the first Screen section.
[   420.078] (==) No screen section available. Using defaults.
root@onyx:/mnt/ubuntuold/root# cat Xorg.0.log
[   420.039] 
X.Org X Server 1.19.6
Release Date: 2017-12-20
[   420.039] X Protocol Version 11, Revision 0
[   420.039] Build Operating System: Linux 4.4.0-138-generic i686 Ubuntu
[   420.039] Current Operating System: Linux onyx 4.15.0-54-generic #58~16.04.1-Ubuntu SMP Mon Jun 24 13:21:14 UTC 2019 i686
[   420.039] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-54-generic root=UUID=63353a4b-c794-44bf-95bf-57ed8eced7d9 ro recovery nomodeset
[   420.040] Build Date: 25 October 2018  04:12:07PM
[   420.040] xorg-server 2:1.19.6-1ubuntu4.1~16.04.2 (For technical support please see http://www.ubuntu.com/support) 
[   420.040] Current version of pixman: 0.33.6
[   420.040]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   420.040] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   420.041] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul  9 17:10:02 2019
[   420.064] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   420.078] (==) No Layout section.  Using the first Screen section.
[   420.078] (==) No screen section available. Using defaults.
[   420.078] (**) |-->Screen "Default Screen Section" (0)
[   420.078] (**) |   |-->Monitor "<default monitor>"
[   420.079] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   420.079] (==) Automatically adding devices
[   420.079] (==) Automatically enabling devices
[   420.079] (==) Automatically adding GPU devices
[   420.079] (==) Automatically binding GPU devices
[   420.079] (==) Max clients allowed: 256, resource mask: 0x1fffff
[   420.079] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   420.079]     Entry deleted from font path.
[   420.079] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   420.079]     Entry deleted from font path.
[   420.079] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   420.079]     Entry deleted from font path.
[   420.079] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   420.079]     Entry deleted from font path.
[   420.079] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   420.079]     Entry deleted from font path.
[   420.079] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   420.079] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   420.079] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   420.079] (II) Loader magic: 0x68e720
[   420.079] (II) Module ABI versions:
[   420.079]     X.Org ANSI C Emulation: 0.4
[   420.079]     X.Org Video Driver: 23.0
[   420.079]     X.Org XInput driver : 24.1
[   420.079]     X.Org Server Extension : 10.0
[   420.080] (++) using VT number 1

[   420.112] (EE) systemd-logind: failed to get session: PID 1691 does not belong to any known session
[   420.112] (II) xfree86: Adding drm device (/dev/dri/card0)
[   420.114] (--) PCI:*(0:2:0:0) 10de:0a65:1462:8094 rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x0000ec00/128, BIOS @ 0x????????/131072
[   420.114] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[   420.114] (II) "glx" will be loaded by default.
[   420.114] (II) LoadModule: "glx"
[   420.114] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[   420.155] (II) Module glx: vendor="NVIDIA Corporation"
[   420.155]     compiled for 4.0.2, module version = 1.0.0
[   420.155]     Module class: X.Org Server Extension
[   420.155] (II) NVIDIA GLX Module  340.107  Thu May 24 21:47:46 PDT 2018
[   420.156] (==) Matched nvidia as autoconfigured driver 0
[   420.156] (==) Matched nouveau as autoconfigured driver 1
[   420.156] (==) Matched nvidia as autoconfigured driver 2
[   420.156] (==) Matched nouveau as autoconfigured driver 3
[   420.156] (==) Matched modesetting as autoconfigured driver 4
[   420.156] (==) Matched fbdev as autoconfigured driver 5
[   420.156] (==) Matched vesa as autoconfigured driver 6
[   420.156] (==) Assigned the driver to the xf86ConfigLayout
[   420.156] (II) LoadModule: "nvidia"
[   420.156] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   420.156] (II) Module nvidia: vendor="NVIDIA Corporation"
[   420.156]     compiled for 4.0.2, module version = 1.0.0
[   420.156]     Module class: X.Org Video Driver
[   420.156] (II) LoadModule: "nouveau"
[   420.166] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   420.176] (II) Module nouveau: vendor="X.Org Foundation"
[   420.176]     compiled for 1.19.5, module version = 1.0.15
[   420.176]     Module class: X.Org Video Driver
[   420.176]     ABI class: X.Org Video Driver, version 23.0
[   420.176] (II) LoadModule: "modesetting"
[   420.176] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   420.177] (II) Module modesetting: vendor="X.Org Foundation"
[   420.177]     compiled for 1.19.6, module version = 1.19.6
[   420.177]     Module class: X.Org Video Driver
[   420.177]     ABI class: X.Org Video Driver, version 23.0
[   420.177] (II) LoadModule: "fbdev"
[   420.177] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   420.177] (II) Module fbdev: vendor="X.Org Foundation"
[   420.177]     compiled for 1.19.3, module version = 0.4.4
[   420.177]     Module class: X.Org Video Driver
[   420.177]     ABI class: X.Org Video Driver, version 23.0
[   420.177] (II) LoadModule: "vesa"
[   420.177] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   420.177] (II) Module vesa: vendor="X.Org Foundation"
[   420.177]     compiled for 1.19.3, module version = 2.3.4
[   420.177]     Module class: X.Org Video Driver
[   420.177]     ABI class: X.Org Video Driver, version 23.0
[   420.177] (II) NVIDIA dlloader X Driver  340.107  Thu May 24 21:24:47 PDT 2018
[   420.177] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   420.177] (II) NOUVEAU driver Date:   Fri Apr 21 14:41:17 2017 -0400
[   420.177] (II) NOUVEAU driver for NVIDIA chipset families :
[   420.177]     RIVA TNT        (NV04)
[   420.177]     RIVA TNT2       (NV05)
[   420.177]     GeForce 256     (NV10)
[   420.178]     GeForce 2       (NV11, NV15)
[   420.178]     GeForce 4MX     (NV17, NV18)
[   420.178]     GeForce 3       (NV20)
[   420.178]     GeForce 4Ti     (NV25, NV28)
[   420.178]     GeForce FX      (NV3x)
[   420.178]     GeForce 6       (NV4x)
[   420.178]     GeForce 7       (G7x)
[   420.178]     GeForce 8       (G8x)
[   420.178]     GeForce GTX 200 (NVA0)
[   420.178]     GeForce GTX 400 (NVC0)
[   420.178] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   420.178] (II) FBDEV: driver for framebuffer: fbdev
[   420.178] (II) VESA: driver for VESA chipsets: vesa
[   420.179] (II) Loading sub module "fb"
[   420.179] (II) LoadModule: "fb"
[   420.179] (II) Loading /usr/lib/xorg/modules/libfb.so
[   420.180] (II) Module fb: vendor="X.Org Foundation"
[   420.180]     compiled for 1.19.6, module version = 1.0.0
[   420.180]     ABI class: X.Org ANSI C Emulation, version 0.4
[   420.180] (WW) Unresolved symbol: fbGetGCPrivateKey
[   420.180] (II) Loading sub module "wfb"
[   420.180] (II) LoadModule: "wfb"
[   420.180] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   420.180] (II) Module wfb: vendor="X.Org Foundation"
[   420.180]     compiled for 1.19.6, module version = 1.0.0
[   420.180]     ABI class: X.Org ANSI C Emulation, version 0.4
[   420.180] (II) Loading sub module "ramdac"
[   420.180] (II) LoadModule: "ramdac"
[   420.180] (II) Module "ramdac" already built-in


```
When I boot normally, after this, it would continue with something like
```
[    74.858] (WW) Falling back to old probe method for modesetting
[    74.858] (WW) Falling back to old probe method for fbdev
[    74.858] (II) Loading sub module "fbdevhw"
[    74.858] (II) LoadModule: "fbdevhw"
[    74.858] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    74.858] (II) Module fbdevhw: vendor="X.Org Foundation"
[    74.858]     compiled for 1.19.6, module version = 0.0.2
[    74.858]     ABI class: X.Org Video Driver, version 23.0
[    74.858] (EE) open /dev/fb0: No such file or directory
[    74.858] (WW) Falling back to old probe method for vesa
[    74.858] (II) NVIDIA(0): Creating default Display subsection in Screen secti
on
    "Default Screen Section" for depth/fbbpp 24/32
[    74.858] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
...
...


```

So, where do things go wrong?

---

### Post by CatKiller on 2019-07-10
> **Ed_B said:**
> So, where do things go wrong?

As far as I can see from a quick look, here:

```
[   72.799078] EIP: vmalloc_fault+0x20f/0x23 
```

That's a memory allocation fault of some kind. Whether that's caused by the wrong kernel module, the wrong driver, iffy hardware, or what, I couldn't say, but it's definitely not happy at that point.

X also tries to load everything but the kitchen sink:

```

[   420.156] (==) Matched nvidia as autoconfigured driver 0
[   420.156] (==) Matched nouveau as autoconfigured driver 1
[   420.156] (==) Matched nvidia as autoconfigured driver 2
[   420.156] (==) Matched nouveau as autoconfigured driver 3
[   420.156] (==) Matched modesetting as autoconfigured driver 4
[   420.156] (==) Matched fbdev as autoconfigured driver 5
[   420.156] (==) Matched vesa as autoconfigured driver 6
```

Normally most of those would be blacklisted by the nvidia driver's installation scripts to avoid access conflicts.

I would generally recommend purging all the nvidia stuff and re-installing just the version of the proprietary driver that you want at this point, so you don't have a weird configuration and you get to re-run the install scripts. You said that you'd installed it using the .run file from the Nvidia website, though, and I don't know enough about that to say how best to get rid of everything that it installs.

---

### Post by pascua28 on 2019-07-22
Seems like the dkms module doesn't compile with the new linux kernel. Similar to broadcomm drivers where newer kernels sometimes break dkms until it is patched

---

### Post by Ed_B on 2019-08-06
I purged dkms, nvidia, nvidia-prime and reinstalled them (under  4.15.0-47 kernel), and now the driver is working for the newest 4.5.0-55 kernel!  Thank you very much.

---

### Post by rbmorse on 2019-08-06
Good that you got it working. 

In the future, if you need to purge the nvidia driver again for some reason, this will make sure you clean up all the little bits and pieces:

```
sudo apt purge nvidia-*
```

---

