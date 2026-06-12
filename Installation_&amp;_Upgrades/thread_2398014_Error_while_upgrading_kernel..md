---
title: "Error while upgrading kernel."
date: 2018-08-06
forum: Installation &amp; Upgrades
---

### Post by chaturbauka on 2018-08-06
While fixing sound driver for my inspiron 5547 I got this error message:

kernel source for this kernel does not seems to be installed.

I tried installing kernel again using method given on

[http://ubuntuhandbook.org/index.php/2018/06/install-linux-kernel-4-17-ubuntu-18-04/](http://ubuntuhandbook.org/index.php/2018/06/install-linux-kernel-4-17-ubuntu-18-04/)

I got this error :

```
chaturbauka@chaturbauka-Inspiron-5547:/tmp$ sudo dpkg -i *.deb
[sudo] password for chaturbauka: 
Selecting previously unselected package linux-headers-4.17.0-041700-generic.
(Reading database ... 267185 files and directories currently installed.)
Preparing to unpack linux-headers-4.17.0-041700-generic_4.17.0-041700.201806041953_amd64.deb ...
Unpacking linux-headers-4.17.0-041700-generic (4.17.0-041700.201806041953) ...
Selecting previously unselected package linux-headers-4.17.0-041700.
Preparing to unpack linux-headers-4.17.0-041700_4.17.0-041700.201806041953_all.deb ...
Unpacking linux-headers-4.17.0-041700 (4.17.0-041700.201806041953) ...
Selecting previously unselected package linux-image-unsigned-4.17.0-041700-generic.
Preparing to unpack linux-image-unsigned-4.17.0-041700-generic_4.17.0-041700.201806041953_amd64.deb ...
Unpacking linux-image-unsigned-4.17.0-041700-generic (4.17.0-041700.201806041953) ...
Selecting previously unselected package linux-modules-4.17.0-041700-generic.
Preparing to unpack linux-modules-4.17.0-041700-generic_4.17.0-041700.201806041953_amd64.deb ...
Unpacking linux-modules-4.17.0-041700-generic (4.17.0-041700.201806041953) ...
Setting up linux-headers-4.17.0-041700 (4.17.0-041700.201806041953) ...
Setting up linux-modules-4.17.0-041700-generic (4.17.0-041700.201806041953) ...
Setting up linux-headers-4.17.0-041700-generic (4.17.0-041700.201806041953) ...
/etc/kernel/header_postinst.d/dkms:
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
Setting up linux-image-unsigned-4.17.0-041700-generic (4.17.0-041700.201806041953) ...
I: /vmlinuz.old is now a symlink to boot/vmlinuz-4.17.12-041712-generic
I: /initrd.img.old is now a symlink to boot/initrd.img-4.17.12-041712-generic
I: /vmlinuz is now a symlink to boot/vmlinuz-4.17.0-041700-generic
I: /initrd.img is now a symlink to boot/initrd.img-4.17.0-041700-generic
Processing triggers for linux-image-unsigned-4.17.0-041700-generic (4.17.0-041700.201806041953) ...
/etc/kernel/postinst.d/dkms:
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-4.17.0-041700-generic
cryptsetup: WARNING: target cryptswap1 has a random key, skipped
W: Possible missing firmware /lib/firmware/amdgpu/raven_gpu_info.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_gpu_info.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_asd.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_sos.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/raven_asd.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/polaris12_mec2_2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/polaris12_mec_2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/polaris12_me_2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/polaris12_pfp_2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/polaris12_ce_2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/polaris10_mec2_2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/polaris10_mec_2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/polaris10_me_2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/polaris10_pfp_2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/polaris10_ce_2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/polaris11_mec2_2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/polaris11_mec_2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/polaris11_me_2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/polaris11_pfp_2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/polaris11_ce_2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/raven_rlc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/raven_mec2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/raven_mec.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/raven_me.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/raven_pfp.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/raven_ce.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_rlc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_mec2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_mec.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_me.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_pfp.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_ce.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/raven_sdma.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_sdma1.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_sdma.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_uvd.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_vce.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/raven_vcn.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/vega12_smc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/i915/skl_dmc_ver1_27.bin for module i915
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_04.bin for module i915
W: Possible missing firmware /lib/firmware/i915/cnl_dmc_ver1_07.bin for module i915
W: Possible missing firmware /lib/firmware/i915/glk_dmc_ver1_04.bin for module i915
W: Possible missing firmware /lib/firmware/i915/kbl_guc_ver9_39.bin for module i915
W: Possible missing firmware /lib/firmware/i915/bxt_guc_ver9_29.bin for module i915
W: Possible missing firmware /lib/firmware/i915/skl_guc_ver9_33.bin for module i915
/sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf: No such file or directory
/etc/kernel/postinst.d/zz-update-grub:
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.17.12-041712-generic
Found initrd image: /boot/initrd.img-4.17.12-041712-generic
Found linux image: /boot/vmlinuz-4.17.0-041700-generic
Found initrd image: /boot/initrd.img-4.17.0-041700-generic
Found linux image: /boot/vmlinuz-4.13.0-46-generic
Found initrd image: /boot/initrd.img-4.13.0-46-generic
Found linux image: /boot/vmlinuz-4.13.0-16-generic
Found initrd image: /boot/initrd.img-4.13.0-16-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 10 on /dev/sda1
done
```

 Please help. Your help is appreciated.

---

