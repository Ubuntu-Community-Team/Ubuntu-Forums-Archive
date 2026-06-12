---
title: "Issue w/ update-initramfs &amp; fsck.lvm2 after boot-repair on lvm2 partition"
date: 2018-12-05
forum: Installation &amp; Upgrades
---

### Post by nick164 on 2018-12-05
Recently, grub had some issues which required me to rebuild it using boot-repair.  This turned out to be quite the challenge as I'm using an lvm encrypted partition.  Throughout the process of trying to resolve this, I tried many different things.  At one point, grub finally started at boot, but Ubuntu wasn't booting properly.  As one of the things that I tried to resolve the issue, I installed a newer kernel, 4.17.0-041700-generic.  Somehow, update-initramfs worked successfully with this kernel, but returned the following error with all others:
[B]
Warning: /sbin/fsck.LVM2_member doesn't exist, can't install to initramfs, ignoring.[/B]

After having spent half the day getting to this point, I was happy enough that it booted properly and I was able to boot normally again.  This was until I realized that Virtualbox isn't compatible with 4.17 kernels.  :roll:  I absolutely must have vbox working, so I've been attempting to install a 4.15 kernel and every attempt at running update-initramfs yields the following:

root@myuser:/sbin# update-initramfs -u -k all
update-initramfs: Generating /boot/initrd.img-4.17.0-041700-generic
W: Possible missing firmware /lib/firmware/amdgpu/vega12_gpu_info.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_asd.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_sos.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_rlc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_mec2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_mec.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_me.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_pfp.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_ce.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_sdma1.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_sdma.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_uvd.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_vce.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_smc.bin for module amdgpu
**Warning: /sbin/fsck.LVM2_member doesn't exist, can't install to initramfs, ignoring.**
update-initramfs: Generating /boot/initrd.img-4.15.0-42-lowlatency
**Warning: /sbin/fsck.LVM2_member doesn't exist, can't install to initramfs, ignoring.**
update-initramfs: Generating /boot/initrd.img-4.15.0-42-generic
[B]Warning: /sbin/fsck.LVM2_member doesn't exist, can't install to initramfs, ignoring.
[/B]

As you can see, it's even giving this error when updating the 4.17 kernel now.
Below you can see the warning message result section from running update-initramfs with verbose output:

Adding module /lib/modules/4.15.0-42-generic/kernel/drivers/gpu/drm/virtio/virtio-gpu.ko
Adding module /lib/modules/4.15.0-42-generic/kernel/drivers/video/vgastate.ko
Adding module /lib/modules/4.15.0-42-generic/kernel/drivers/video/fbdev/vga16fb.ko
Calling hook fsck
Adding binary /sbin/fsck
Adding library-link /lib/x86_64-linux-gnu/libmount.so.1
Adding library /lib/x86_64-linux-gnu/libmount.so.1.1.0
Adding binary /sbin/logsave
**Warning: /sbin/fsck.LVM2_member doesn't exist, can't install to initramfs, ignoring.**
Calling hook fuse
Adding binary /sbin/mount.fuse
Calling hook intel_microcode


I need to get an older kernel working on this system so I can use Virtualbox again.  Any help would be thoroughly appreciated.  Googling that warning returns something like 6 more or less useless results.  I'm pulling out my hair here.

Thanks in advance!

---

