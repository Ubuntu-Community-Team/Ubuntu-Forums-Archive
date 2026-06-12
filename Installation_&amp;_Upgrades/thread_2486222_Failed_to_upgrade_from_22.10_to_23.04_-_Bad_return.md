---
title: "Failed to upgrade from 22.10 to 23.04 - Bad return status for module build on kernel"
date: 2023-04-23
forum: Installation &amp; Upgrades
---

### Post by gmc1 on 2023-04-23
[FONT=Verdana]Tried to upgrade from 22.10 to 23.04 - after the upgrade I received a error about a issue with linux-image-6.2.0-20-generic[/FONT]

[FONT=Verdana]Rebooted and selected kernal 5.19.0-40 which got me back into the OS. When running a dist-upgrade I again get a error updating the kernal:

```
[/FONT]user@laptop:~$ sudo apt dist-upgradeReading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  dctrl-tools dh-dkms dh-elpa-helper gcc-12-base:i386 gir1.2-mutter-11
  gir1.2-nma-1.0 hip-runtime-amd hsa-rocr-dev hsakmt-roct-dev libabsl20210324
  libbpf0 libclang-cpp14 libclang1-14 libcupsfilters1 libevent-2.1-7a libflac8
  libflac8:i386 libfontembed1 libfwupdplugin7 libgs9-common libgssdp-1.2-0
  libgupnp-1.2-1 libhsa-runtime64-1 libhsakmt1 libicu71 libicu71:i386
  libjavascriptcoregtk-5.0-0 libldap-2.5-0 libldap-2.5-0:i386 liblerc3
  libllvm14 libmutter-11-0 libopenal1:i386 libpcre3:i386 libperl5.34
  libplacebo192 libpoppler123 libprotobuf-lite23 libprotobuf23
  libpython3.10-dev libqpdf28 libquazip5-1 librygel-core-2.6-2
  librygel-db-2.6-2 librygel-renderer-2.6-2 librygel-server-2.6-2
  libsndio7.0:i386 libstdc++-11-dev libtext-trim-perl libtiff5 libtiff5:i386
  libtiffxx5 libvkd3d-shader1 libvkd3d1 libwebkit2gtk-5.0-0 libwireshark15
  libwiretap12 libwsutil13 libykpers-1-1 libyubikey-udev libyubikey0
  linux-headers-5.19.0-38 netkit-telnet perl-modules-5.34 python3.10
  python3.10-dev python3.10-minimal rocm-llvm rocminfo
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED
  linux-headers-5.19.0-38-generic linux-image-5.19.0-38-generic
  linux-modules-5.19.0-38-generic linux-modules-extra-5.19.0-38-generic
0 to upgrade, 0 to newly install, 4 to remove and 0 not to upgrade.
6 not fully installed or removed.
After this operation, 645 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 424134 files and directories currently installed.)
Removing linux-headers-5.19.0-38-generic (5.19.0-38.39) ...
Removing linux-image-5.19.0-38-generic (5.19.0-38.39) ...
/etc/kernel/prerm.d/dkms:
dkms: removing: amdgpu 5.18.13-1510348.22.04 (5.19.0-38-generic) (x86_64)
Module amdgpu-5.18.13-1510348.22.04 for kernel 5.19.0-38-generic (x86_64).
Before uninstall, this module version was ACTIVE on this kernel.


amdgpu.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.19.0-38-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


amdttm.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.19.0-38-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


amdkcl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.19.0-38-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


amd-sched.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.19.0-38-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


amddrm_ttm_helper.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.19.0-38-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


Running the post_remove script:
ls: cannot access '/lib/firmware/updates': No such file or directory
depmod...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.19.0-38-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.2.0-20-generic
Found linux image: /boot/vmlinuz-5.19.0-40-generic
Found initrd image: /boot/initrd.img-5.19.0-40-generic
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.
Adding boot menu entry for UEFI Firmware Settings ...
done
Removing linux-modules-extra-5.19.0-38-generic (5.19.0-38.39) ...
Removing linux-modules-5.19.0-38-generic (5.19.0-38.39) ...
Setting up linux-image-6.2.0-20-generic (6.2.0-20.20) ...
I: /boot/initrd.img is now a symlink to initrd.img-6.2.0-20-generic
Setting up linux-headers-6.2.0-20-generic (6.2.0-20.20) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.2.0-20-generic
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der


Running the pre_build script:
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... x86_64-linux-gnu-gcc-12
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether the compiler supports GNU C... yes
checking whether x86_64-linux-gnu-gcc-12 accepts -g... yes
checking for x86_64-linux-gnu-gcc-12 option to enable C11 features... none neede
d
checking how to run the C preprocessor... x86_64-linux-gnu-gcc-12 -E
checking kernel source directory... /usr/src/linux-headers-6.2.0-20-generic
checking kernel build directory... /usr/src/linux-headers-6.2.0-20-generic
checking kernel source version... 6.2.0-20-generic
checking kernel file name for module symbols... Module.symvers
checking for linux/overflow.h... yes
checking for linux/sched/mm.h... yes
checking for linux/sched/task.h... yes
checking for linux/sched/signal.h... yes
checking for linux/nospec.h... yes
checking for linux/bits.h... yes
checking for linux/io-64-nonatomic-lo-hi.h... yes
checking for asm/set_memory.h... yes
checking for asm/fpu/api.h... yes
checking for uapi/linux/sched/types.h... yes
checking for linux/compiler_attributes.h... yes
checking for linux/dma-fence.h... yes
checking for linux/dma-resv.h... yes
checking for linux/mmap_lock.h... yes
checking for linux/pci-p2pdma.h... yes
checking for linux/dma-attrs.h... no
checking for linux/mem_encrypt.h... yes
checking for linux/dma-buf-map.h... no
checking for linux/iosys-map.h... yes
checking for linux/stdarg.h... yes
checking for linux/dma-fence-chain.h... yes
checking for linux/xarray.h... yes
checking for linux/container_of.h... yes
checking for linux/cc_platform.h... yes
checking for linux/processor.h... yes
checking for linux/dma-map-ops.h... yes
checking for drm/drm_backport.h... no
checking for drm/amdgpu_pciid.h... no
checking for drm/drm_auth.h... yes
checking for drm/drm_irq.h... no
checking for drm/drm_connector.h... yes
checking for drm/drm_encoder.h... yes
checking for drm/drm_plane.h... yes
checking for drm/drm_print.h... yes
checking for drm/drm_drv.h... yes
checking for drm/drm_file.h... yes
checking for drm/drm_debugfs.h... yes
checking for drm/drm_ioctl.h... yes
checking for drm/drm_vblank.h... yes
checking for drm/drm_device.h... yes
checking for drm/drm_gem_framebuffer_helper.h... yes
checking for drm/drm_hdcp.h... no
checking for drm/drm_audio_component.h... yes
checking for drm/drm_util.h... yes
checking for drm/drm_atomic_uapi.h... yes
checking for drm/drm_probe_helper.h... yes
checking for drm/drmP.h... no
checking for drm/task_barrier.h... yes
checking for drm/drm_managed.h... yes
checking for drm/amd_asic_type.h... yes
checking for drm/drm_aperture.h... yes
checking for drm/dp/drm_dp_helper.h... no
checking for drm/dp/drm_dp_mst_helper.h... no
checking for drm/display/drm_dp_helper.h... yes
checking for drm/display/drm_dp_mst_helper.h... yes
checking for drm/display/drm_dsc.h... yes
checking for drm/display/drm_dsc_helper.h... yes
checking for drm/display/drm_hdmi_helper.h... yes
checking for drm/display/drm_hdcp_helper.h... yes
checking for drm/display/drm_hdcp.h... yes
checking for drm/display/drm_dp.h... yes
checking for drm/drm_dsc.h... no
checking for linux/pgtable.h... yes
checking for drm/drm_simple_kms_helper.h... yes
checking for drm/drm_damage_helper.h... yes
checking for nproc... yes
checking for supported chips... done
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for module configuration... done
configure: creating ./config.status
config.status: creating config/config.h


Building module:
Cleaning build area...(bad exit status: 2)
make -j12 KERNELRELEASE=6.2.0-20-generic -j12 TTM_NAME=amdttm SCHED_NAME=amd-sch
ed -C /lib/modules/6.2.0-20-generic/build M=/var/lib/dkms/amdgpu/5.18.13-1510348
.22.04/build....(bad exit status: 2)
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/amdgpu-dkms.0.c
rash'
Error! Bad return status for module build on kernel: 6.2.0-20-generic (x86_64)
Consult /var/lib/dkms/amdgpu/5.18.13-1510348.22.04/build/make.log for more infor
mation.
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
   ...fail!
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 11
dpkg: error processing package linux-headers-6.2.0-20-generic (--configure):
 installed linux-headers-6.2.0-20-generic package post-installation script subpr
ocess returned error exit status 1
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-6.2.0-20-generic; however:
  Package linux-headers-6.2.0-20-generic is not configured yet.


dpkg: error processing package linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic-hwe-22.
04:
 linux-headers-generic-hwe-22.04 depends on linux-headers-6.2.0-20-generic; howe
ver:
  Package linux-headers-6.2.0-20-generic is not configured yet.


dpkg: error processing package linux-headers-generic-hwe-22.04 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-hwe-22.04:
 linux-generic-hwe-22.04 depends on linux-headers-generic-hwe-22.04 (= 6.2.0.20.
20); however:
  Package linux-headers-generic-hwe-22.04 is not configured yet.


dpkg: error processing package linux-generNo apport report written because the e
rror message indicates it's a follow-up error from a previous failure.
                                                                      No apport 
report written because the error message indicates it's a follow-up error from a
 previous failure.
                  No apport report written because MaxReports has already been r
eached
      No apport report written because MaxReports has already been reached
                                                                          ic-hwe
-22.04 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-headers-generic (= 6.2.0.20.20); however:
  Package linux-headers-generic is not configured yet.


dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for linux-image-6.2.0-20-generic (6.2.0-20.20) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.2.0-20-generic
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der


Running the pre_build script:
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... x86_64-linux-gnu-gcc-12
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether the compiler supports GNU C... yes
checking whether x86_64-linux-gnu-gcc-12 accepts -g... yes
checking for x86_64-linux-gnu-gcc-12 option to enable C11 features... none neede
d
checking how to run the C preprocessor... x86_64-linux-gnu-gcc-12 -E
checking kernel source directory... /usr/src/linux-headers-6.2.0-20-generic
checking kernel build directory... /usr/src/linux-headers-6.2.0-20-generic
checking kernel source version... 6.2.0-20-generic
checking kernel file name for module symbols... Module.symvers
checking for linux/overflow.h... yes
checking for linux/sched/mm.h... yes
checking for linux/sched/task.h... yes
checking for linux/sched/signal.h... yes
checking for linux/nospec.h... yes
checking for linux/bits.h... yes
checking for linux/io-64-nonatomic-lo-hi.h... yes
checking for asm/set_memory.h... yes
checking for asm/fpu/api.h... yes
checking for uapi/linux/sched/types.h... yes
checking for linux/compiler_attributes.h... yes
checking for linux/dma-fence.h... yes
checking for linux/dma-resv.h... yes
checking for linux/mmap_lock.h... yes
checking for linux/pci-p2pdma.h... yes
checking for linux/dma-attrs.h... no
checking for linux/mem_encrypt.h... yes
checking for linux/dma-buf-map.h... no
checking for linux/iosys-map.h... yes
checking for linux/stdarg.h... yes
checking for linux/dma-fence-chain.h... yes
checking for linux/xarray.h... yes
checking for linux/container_of.h... yes
checking for linux/cc_platform.h... yes
checking for linux/processor.h... yes
checking for linux/dma-map-ops.h... yes
checking for drm/drm_backport.h... no
checking for drm/amdgpu_pciid.h... no
checking for drm/drm_auth.h... yes
checking for drm/drm_irq.h... no
checking for drm/drm_connector.h... yes
checking for drm/drm_encoder.h... yes
checking for drm/drm_plane.h... yes
checking for drm/drm_print.h... yes
checking for drm/drm_drv.h... yes
checking for drm/drm_file.h... yes
checking for drm/drm_debugfs.h... yes
checking for drm/drm_ioctl.h... yes
checking for drm/drm_vblank.h... yes
checking for drm/drm_device.h... yes
checking for drm/drm_gem_framebuffer_helper.h... yes
checking for drm/drm_hdcp.h... no
checking for drm/drm_audio_component.h... yes
checking for drm/drm_util.h... yes
checking for drm/drm_atomic_uapi.h... yes
checking for drm/drm_probe_helper.h... yes
checking for drm/drmP.h... no
checking for drm/task_barrier.h... yes
checking for drm/drm_managed.h... yes
checking for drm/amd_asic_type.h... yes
checking for drm/drm_aperture.h... yes
checking for drm/dp/drm_dp_helper.h... no
checking for drm/dp/drm_dp_mst_helper.h... no
checking for drm/display/drm_dp_helper.h... yes
checking for drm/display/drm_dp_mst_helper.h... yes
checking for drm/display/drm_dsc.h... yes
checking for drm/display/drm_dsc_helper.h... yes
checking for drm/display/drm_hdmi_helper.h... yes
checking for drm/display/drm_hdcp_helper.h... yes
checking for drm/display/drm_hdcp.h... yes
checking for drm/display/drm_dp.h... yes
checking for drm/drm_dsc.h... no
checking for linux/pgtable.h... yes
checking for drm/drm_simple_kms_helper.h... yes
checking for drm/drm_damage_helper.h... yes
checking for nproc... yes
checking for supported chips... done
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for nproc... (cached) yes
checking for module configuration... done
configure: creating ./config.status
config.status: creating config/config.h


Building module:
Cleaning build area...(bad exit status: 2)
make -j12 KERNELRELEASE=6.2.0-20-generic -j12 TTM_NAME=amdttm SCHED_NAME=amd-sch
ed -C /lib/modules/6.2.0-20-generic/build M=/var/lib/dkms/amdgpu/5.18.13-1510348
.22.04/build....(bad exit status: 2)
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/amdgpu-dkms.0.c
rash'
Error! Bad return status for module build on kernel: 6.2.0-20-generic (x86_64)
Consult /var/lib/dkms/amdgpu/5.18.13-1510348.22.04/build/make.log for more infor
mation.
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
   ...fail!
run-parts: /etc/kernel/postinst.d/dkms exited with return code 11
dpkg: error processing package linux-image-6.2.0-20-generic (--configure):
 installed linux-image-6.2.0-20-generic package post-installation script subproc
ess returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Errors were 
encountered while processing:
 linux-headers-6.2.0-20-generic
 linux-headers-generic
 linux-headers-generic-hwe-22.04
 linux-generic-hwe-22.04
 linux-generic
 linux-image-6.2.0-20-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
[FONT=Verdana]
```

Anyone having similar issues and know of a fix?


[/FONT]

---

### Post by gmc1 on 2023-04-23
Looks like a common isse. Bug has also been reported by someone so don't think it will be too long before a fix it out. 

Will just stick to the older kernal for the meantime. 

[https://www.mail-archive.com/kernel-packages@lists.launchpad.net/msg502656.html](https://www.mail-archive.com/kernel-packages@lists.launchpad.net/msg502656.html)

---

### Post by filosofic on 2023-04-24
Same issue with me -- [https://ubuntuforums.org/showthread.php?t=2486221](https://ubuntuforums.org/showthread.php?t=2486221) -- hope a fix comes out soon.

---

### Post by idmbe on 2023-04-25
try this
```
 sudo apt remove aufs-dkms
```

then
```
 sudo apt autoremove
```

last
```
 sudo apt update && sudo apt dist-upgrade -y
```

---

### Post by gmc1 on 2023-04-28
No luck - same issue.

---

### Post by idmbe on 2023-04-28
So, try to reboot and select kernel 5.19.0-40 (recovery mode) after that enable network then select root
and try to repeat previous commands

[IMG]https://www.maketecheasier.com/assets/uploads/2019/03/mint-recovery-menu.jpg[/IMG]

---

