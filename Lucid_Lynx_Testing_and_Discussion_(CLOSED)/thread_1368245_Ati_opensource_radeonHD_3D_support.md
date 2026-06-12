---
title: "Ati opensource radeonHD 3D support"
date: 2009-12-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by n3had on 2009-12-30
Anyone with r6xx/r7xx cards been successful enabling compiz?

I am still experiencing this [bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/419126"). Removed compiz --replace from the startup applications menu. I can log in successfully and any attempt to turn compiz on makes the whole screen unresponsive using RadeonHD drivers from xorg-edger's PPA

---

### Post by zika on 2009-12-30
> **n3had said:**
> Anyone with r6xx/r7xx cards been successful enabling compiz?

I am still experiencing this [bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/419126"). Removed compiz --replace from the startup applications menu. I can log in successfully and any attempt to turn compiz on makes the whole screen unresponsive using RadeonHD drivers from xorg-edger's PPAYes. ATI HD3650 512M, Lucid, xorg-edgers... I've not used Ubuntu without xorg-edgers for quite some time. I do not use Compiz but I try it, from time to time, just to check ...

---

### Post by n3had on 2009-12-30
thanks for the quick reply and are you using ati, radeon or radeonhd drivers? and can you post your xorg? btw Onboard ATI HD4200 + 128M SB here

---

### Post by zika on 2009-12-30
> **n3had said:**
> thanks for the quick reply and are you using ati, radeon or radeonhd drivers? and can you post your xorg? btw Onboard ATI HD4200 + 128M SB hereRadeon. No xorg.conf. As far as I know there are only two: radeon and radeonhd. Radeonhd is, as far as I know, a dying animal.

---

### Post by zika on 2009-12-30
> **n3had said:**
> thanks for the quick reply and are you using ati, radeon or radeonhd drivers? and can you post your xorg? btw Onboard ATI HD4200 + 128M SB hereRadeon. No xorg.conf. As far as I know there are only two (open source, of course, I do not get close to fglrx): radeon and radeonhd. Radeonhd is, as far as I know, a dying animal.

---

### Post by n3had on 2009-12-30
so should i go for radeon driver instead of radeonhd? and if i keep xorg.conf blank the X window run fine you guess?

---

### Post by ranch hand on 2009-12-30
> **n3had said:**
> so should i go for radeon driver instead of radeonhd? and if i keep xorg.conf blank the X window run fine you guess?
How come do you have a xorg.conf file?

---

### Post by Gourgi on 2009-12-30
> **zika said:**
> Radeon. No xorg.conf. As far as I know there are only two (open source, of course, I do not get close to fglrx): radeon and radeonhd. Radeonhd is, as far as I know, a dying animal.

do you have 3d with radeon driver ? are you sure ?
maybe you use radeonhd instead ?

---

### Post by zika on 2009-12-30
> **Gourgi said:**
> do you have 3d with radeon driver ? are you sure ?
maybe you use radeonhd instead ?Yes.
Yes.```
~$ glxinfo|grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI R600 (RV635 9598) 20090101  TCL DRI2
```
No. I do not even have radeonhd installed.```
~$ dmesg|grep radeon
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.33-999-generic root=UUID=2c53f5b7-8d17-47c7-a450-5544c483596e ro radeon.modeset=1
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.33-999-generic root=UUID=2c53f5b7-8d17-47c7-a450-5544c483596e ro radeon.modeset=1
[   15.633965] [drm] radeon kernel modesetting enabled.
[   15.635004] radeon 0000:01:00.0: setting latency timer to 64
[   15.639525] [drm] radeon: Initializing kernel modesetting.
[   15.650818] [drm] radeon: 256M of VRAM memory ready
[   15.650820] [drm] radeon: 512M of GTT memory ready.
[   15.650881] radeon 0000:01:00.0: irq 28 for MSI/MSI-X
[   15.650887] [drm] radeon: using MSI.
[   15.650910] [drm] radeon: irq initialized.
[   15.651714] platform radeon_cp.0: firmware: requesting radeon/RV635_pfp.bin
[   15.708835] platform radeon_cp.0: firmware: requesting radeon/RV635_me.bin
[   15.812926] platform radeon_cp.0: firmware: requesting radeon/R600_rlc.bin
[   15.914022] [drm] radeon: ib pool ready.
[   16.118086] fb0: radeondrmfb frame buffer device
[   16.118094] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
```

---

### Post by zika on 2009-12-30
> **ranch hand said:**
> How come do you have a xorg.conf file?You can, (almost) always, make xorg.conf, either automatically, either manually... Do You need it, that is another question. In most cases You do not.

---

### Post by zika on 2009-12-30
> **n3had said:**
> so should i go for radeon driver instead of radeonhd? and if i keep xorg.conf blank the X window run fine you guess?I can not guess without knowledge of how Your machine responds to various settings. I do not like to guess, I guess.

---

### Post by Gourgi on 2009-12-30
> **zika said:**
> Yes.
Yes.```
~$ glxinfo|grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI R600 (RV635 9598) 20090101  TCL DRI2
```
No. I do not even have radeonhd installed.```
~$ dmesg|grep radeon
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.33-999-generic root=UUID=2c53f5b7-8d17-47c7-a450-5544c483596e ro radeon.modeset=1
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.33-999-generic root=UUID=2c53f5b7-8d17-47c7-a450-5544c483596e ro radeon.modeset=1
[   15.633965] [drm] radeon kernel modesetting enabled.
[   15.635004] radeon 0000:01:00.0: setting latency timer to 64
[   15.639525] [drm] radeon: Initializing kernel modesetting.
[   15.650818] [drm] radeon: 256M of VRAM memory ready
[   15.650820] [drm] radeon: 512M of GTT memory ready.
[   15.650881] radeon 0000:01:00.0: irq 28 for MSI/MSI-X
[   15.650887] [drm] radeon: using MSI.
[   15.650910] [drm] radeon: irq initialized.
[   15.651714] platform radeon_cp.0: firmware: requesting radeon/RV635_pfp.bin
[   15.708835] platform radeon_cp.0: firmware: requesting radeon/RV635_me.bin
[   15.812926] platform radeon_cp.0: firmware: requesting radeon/R600_rlc.bin
[   15.914022] [drm] radeon: ib pool ready.
[   16.118086] fb0: radeondrmfb frame buffer device
[   16.118094] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0 on minor 0
```

interesting! i thought the radeon drivers couldn't enable 3d on r600 cards. 
thank you for clearing this

---

### Post by zika on 2009-12-30
> **Gourgi said:**
> interesting! i thought the radeon drivers couldn't enable 3d on r600 cards. 
thank you for clearing thisThis is without KMS:```
~$ dmesg|grep radeon
[   45.741984] [drm] radeon defaulting to userspace modesetting.
[   45.742705] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
[   46.026841] platform r600_cp.0: firmware: requesting radeon/RV635_pfp.bin
[   46.033598] platform r600_cp.0: firmware: requesting radeon/RV635_me.bin
~$ glxinfo|grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI R600 (RV635 9598) 20090101  TCL
```
Just to show that KMS is not necessary...

---

### Post by ranch hand on 2009-12-30
> **zika said:**
> You can, (almost) always, make xorg.conf, either automatically, either manually... Do You need it, that is another question. In most cases You do not.
I am aware of this.  That is why I was asking.  Just seemed a little strange.

---

### Post by n3had on 2009-12-30
ok so i'll uninstall radeonHD drivers and remove xorg.conf and install radeon drivers

EDIT: It is loading mesa drivers after i deleted xorg.conf and i am using .33rc2 kernel is there anything i am missing?

EDIT2: i am using radeon drivers instead of radeonHD and yay compiz is running fine no crashes so far and yes i did create an xorg.conf file wonder why it doesn't work without it.

---

### Post by n3had on 2009-12-30
> **ranch hand said:**
> How come do you have a xorg.conf file?

I switched from nVidia chipset which had 6200 onboard to Biostar 785G Chipset and i used to need xorg.cong back then and i have no idea how opensource drivers work.

---

### Post by ranch hand on 2009-12-31
Ah that would explain it.  I always use the generic drivers because there really is a lack of support for my card and I am happy with the results.

I also remember all the trouble we had in 9.10 testing with the existence of xorg.conf files in upgrades from 9.04.  Troubles that continued to some extent into the release version of 9.10.

Just kind of wondered why, with your original post which sounded like generic drivers, you would have a xorg.conf file.

Thank you for explaining the ordeal.

---

### Post by n3had on 2009-12-31
> **zika said:**
> This is without KMS:```
~$ dmesg|grep radeon
[   45.741984] [drm] radeon defaulting to userspace modesetting.
[   45.742705] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
[   46.026841] platform r600_cp.0: firmware: requesting radeon/RV635_pfp.bin
[   46.033598] platform r600_cp.0: firmware: requesting radeon/RV635_me.bin
~$ glxinfo|grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI R600 (RV635 9598) 20090101  TCL
```
Just to show that KMS is not necessary...

```
~$ dmesg|grep radeon
[   13.702735] [drm] radeon defaulting to userspace modesetting.
[   13.703454] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:05.0 on minor 0
[   14.032848] platform r600_cp.0: firmware: requesting radeon/RS780_pfp.bin
[   14.066739] platform r600_cp.0: firmware: requesting radeon/RS780_me.bin
~$ glxinfo|grep render
IRQ's not enabled, falling back to busy waits: 2 0
direct rendering: Yes
OpenGL renderer string: Mesa DRI R600 (RS880 9710) 20090101  TCL
~$ 


```

Can anyone throw some light on this?

```
IRQ's not enabled, falling back to busy waits: 2 0
```

---

### Post by zika on 2009-12-31
> **ranch hand said:**
> Ah that would explain it.  I always use the generic drivers because there really is a lack of support for my card and I am happy with the results.

I also remember all the trouble we had in 9.10 testing with the existence of xorg.conf files in upgrades from 9.04.  Troubles that continued to some extent into the release version of 9.10.

Just kind of wondered why, with your original post which sounded like generic drivers, you would have a xorg.conf file.

Thank you for explaining the ordeal.For me, if and when I need xorg.conf, the best way of generating one is through```
sudo Xorg --configure
```run in tty with X closed. Then, if and when needed, I put tweaks in such a file. Although, plain and clean xorg.conf with tweaks also works. Nevertheless with current state of opensource drivers for ATI and with driconf package I do not use xorg.conf anymore.

---

