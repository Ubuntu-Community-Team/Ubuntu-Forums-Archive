---
title: "upgrading kernel 4.10.10 to 4.11.12 errors"
date: 2017-10-20
forum: Installation &amp; Upgrades
---

### Post by alain.roger on 2017-10-20
Hi,

i'm trying to upgrade my kernel from v4.10.10 to 4.11.12.
While doing this i got the following error:
```
[FONT=monospace][COLOR=#000000]Selecting previously unselected package linux-headers-4.11.12-041112.[/COLOR]
(Reading database ... 396818 files and directories currently installed.)
Preparing to unpack linux-headers-4.11.12-041112_4.11.12-041112.201707210350_all.deb ...
Unpacking linux-headers-4.11.12-041112 (4.11.12-041112.201707210350) ...
Selecting previously unselected package linux-headers-4.11.12-041112-generic.
Preparing to unpack linux-headers-4.11.12-041112-generic_4.11.12-041112.201707210350_amd64.deb ...
Unpacking linux-headers-4.11.12-041112-generic (4.11.12-041112.201707210350) ...
Selecting previously unselected package linux-image-4.11.12-041112-generic.
Preparing to unpack linux-image-4.11.12-041112-generic_4.11.12-041112.201707210350_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.11.12-041112-generic /boot/vmlinuz-4.11.12-041112-generic
Done.
Unpacking linux-image-4.11.12-041112-generic (4.11.12-041112.201707210350) ...
Setting up linux-headers-4.11.12-041112 (4.11.12-041112.201707210350) ...
Setting up linux-headers-4.11.12-041112-generic (4.11.12-041112.201707210350) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.11.12-041112-generic /boot/vmlinuz-4.11.12-041112-generic
ERROR (dkms apport): kernel package linux-headers-4.11.12-041112-generic is not supported
Error! Bad return status for module build on kernel: 4.11.12-041112-generic (x86_64)
Consult /var/lib/dkms/nvidia-378/378.13/build/make.log for more information.
Setting up linux-image-4.11.12-041112-generic (4.11.12-041112.201707210350) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.11.12-041112-generic /boot/vmlinuz-4.11.12-041112-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.11.12-041112-generic /boot/vmlinuz-4.11.12-041112-generic
ERROR (dkms apport): kernel package linux-headers-4.11.12-041112-generic is not supported
Error! Bad return status for module build on kernel: 4.11.12-041112-generic (x86_64)
Consult /var/lib/dkms/nvidia-378/378.13/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.11.12-041112-generic /boot/vmlinuz-4.11.12-041112-generic
update-initramfs: Generating /boot/initrd.img-4.11.12-041112-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.11.12-041112-generic /boot/vmlinuz-4.11.12-041112-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.11.12-041112-generic /boot/vmlinuz-4.11.12-041112-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.11.12-041112-generic /boot/vmlinuz-4.11.12-041112-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.11.12-041112-generic /boot/vmlinuz-4.11.12-041112-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.13.0-16-generic
Found initrd image: /boot/initrd.img-4.13.0-16-generic
Found linux image: /boot/vmlinuz-4.11.12-041112-generic
Found initrd image: /boot/initrd.img-4.11.12-041112-generic
Found linux image: /boot/vmlinuz-4.10.10-041010-generic
Found initrd image: /boot/initrd.img-4.10.10-041010-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done

[/FONT]
```

it seems nvidia is the cause ([FONT=monospace]Consult /var/lib/dkms/nvidia-378/378.13/build/make.log for more information.)

[/FONT]therefore i checked the nvidia making log and i go this:

```
DKMS make.log for nvidia-378-378.13 for kernel 4.11.12-041112-generic (x86_64)vendredi 20 octobre 2017, 08:42:24 (UTC+0200)
make "CC=cc"  KBUILD_VERBOSE= -C /lib/modules/4.11.12-041112-generic/build M=/var/lib/dkms/nvidia-378/378.13/build ARCH=x86_64 NV_KERNEL_SOURCES=/lib/modules/4.11.12-041112-generic/build NV_KERNEL_OUTPUT=/lib/modules/4.11.12-041112-generic/build NV_KERNEL_MODULES="nvidia nvidia-uvm nvidia-modeset nvidia-drm" INSTALL_MOD_DIR=kernel/drivers/video modules
make[1]: Entering directory '/usr/src/linux-headers-4.11.12-041112-generic'
  SYMLINK /var/lib/dkms/nvidia-378/378.13/build/nvidia/nv-kernel.o
  SYMLINK /var/lib/dkms/nvidia-378/378.13/build/nvidia-modeset/nv-modeset-kernel.o
 CONFTEST: remap_pfn_range
 CONFTEST: follow_pfn
 CONFTEST: vmap
 CONFTEST: set_pages_uc
 CONFTEST: set_memory_uc
 CONFTEST: set_memory_array_uc
 CONFTEST: change_page_attr
 CONFTEST: INIT_WORK
 CONFTEST: pci_get_class
 CONFTEST: pci_choose_state
 CONFTEST: vm_insert_page
 CONFTEST: acpi_device_id
 CONFTEST: acquire_console_sem
 CONFTEST: console_lock
 CONFTEST: kmem_cache_create
 CONFTEST: on_each_cpu
 CONFTEST: smp_call_function
 CONFTEST: acpi_evaluate_integer
 CONFTEST: ioremap_cache
 CONFTEST: ioremap_wc
 CONFTEST: acpi_walk_namespace
 CONFTEST: pci_domain_nr
 CONFTEST: pci_dma_mapping_error
 CONFTEST: sg_alloc_table
 CONFTEST: sg_init_table
 CONFTEST: pci_get_domain_bus_and_slot
 CONFTEST: get_num_physpages
 CONFTEST: efi_enabled
 CONFTEST: proc_create_data
 CONFTEST: pde_data
 CONFTEST: proc_remove
 CONFTEST: pm_vt_switch_required
 CONFTEST: drm_driver_has_set_busid
 CONFTEST: drm_driver_has_gem_prime_res_obj
 CONFTEST: xen_ioemu_inject_msi
 CONFTEST: phys_to_dma
 CONFTEST: write_cr4
 CONFTEST: get_dma_ops
 CONFTEST: of_parse_phandle
 CONFTEST: for_each_online_node
 CONFTEST: node_end_pfn
 CONFTEST: pci_stop_and_remove_bus_device
 CONFTEST: pci_bus_address
 CONFTEST: pci_remove_bus_device
 CONFTEST: request_threaded_irq
 CONFTEST: remap_page_range
 CONFTEST: address_space_init_once
 CONFTEST: kbasename
 CONFTEST: fatal_signal_pending
 CONFTEST: list_cut_position
 CONFTEST: vzalloc
 CONFTEST: wait_on_bit_lock_argument_count
 CONFTEST: bitmap_clear
 CONFTEST: radix_tree_empty
 CONFTEST: usleep_range
 CONFTEST: drm_dev_unref
 CONFTEST: drm_reinit_primary_mode_group
 CONFTEST: drm_atomic_set_mode_for_crtc
 CONFTEST: drm_atomic_clean_old_fb
 CONFTEST: get_user_pages_remote
 CONFTEST: drm_gem_object_lookup
 CONFTEST: drm_atomic_state_free
 CONFTEST: i2c_adapter
 CONFTEST: pm_message_t
 CONFTEST: irq_handler_t
 CONFTEST: acpi_device_ops
 CONFTEST: acpi_op_remove
 CONFTEST: outer_flush_all
 CONFTEST: proc_dir_entry
 CONFTEST: scatterlist
 CONFTEST: sg_table
 CONFTEST: file_operations
 CONFTEST: vm_operations_struct
 CONFTEST: atomic_long_type
 CONFTEST: file_inode
 CONFTEST: task_struct
 CONFTEST: pci_save_state
 CONFTEST: kuid_t
 CONFTEST: dma_ops
 CONFTEST: dma_map_ops
 CONFTEST: noncoherent_swiotlb_dma_ops
 CONFTEST: vm_fault_present
 CONFTEST: fault_flags
 CONFTEST: atomic64_type
 CONFTEST: address_space
 CONFTEST: backing_dev_info
 CONFTEST: kernel_write
 CONFTEST: strnstr
 CONFTEST: iterate_dir
 CONFTEST: mm_context_t
 CONFTEST: kstrtoull
 CONFTEST: vm_fault_has_address
 CONFTEST: vm_ops_fault_removed_vma_arg
 CONFTEST: drm_bus_present
 CONFTEST: drm_bus_has_bus_type
 CONFTEST: drm_bus_has_get_irq
 CONFTEST: drm_bus_has_get_name
 CONFTEST: drm_driver_has_legacy_dev_list
 CONFTEST: drm_crtc_state_has_connectors_changed
 CONFTEST: drm_mode_connector_list_update_has_merge_type_bits_arg
 CONFTEST: drm_init_functions_have_name_arg
 CONFTEST: drm_master_drop_has_from_release_arg
 CONFTEST: drm_helper_mode_fill_fb_struct_has_const_mode_cmd_arg
 CONFTEST: drm_mode_config_funcs_has_atomic_state_alloc
 CONFTEST: dom0_kernel_present
 CONFTEST: drm_available
 CONFTEST: nvidia_vgpu_kvm_build
 CONFTEST: nvidia_grid_build
 CONFTEST: drm_atomic_available
 CONFTEST: drm_atomic_modeset_nonblocking_commit_available
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/nv-frontend.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/nv-instance.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/nv.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/nv-acpi.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/nv-chrdev.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/nv-cray.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/nv-dma.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/nv-gvi.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/nv-i2c.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/nv-mempool.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/nv-mmap.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/nv-p2p.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/nv-pat.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/nv-procfs.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/nv-usermap.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/nv-vm.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/nv-vtophys.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/os-interface.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/os-mlock.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/os-pci.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/os-registry.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/os-usermap.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/nv-modeset-interface.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/nv-pci-table.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/nv-kthread-q.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/nv-kthread-q-selftest.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/nv_uvm_interface.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/nvlink_pci.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/nvlink_linux.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/ibmnpu_linux.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia/ebridge_linux.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_utils.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_common.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_page_migration.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_page_migration_stubs.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_page_migration_kepler.o
  CC [M]  /var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_page_migration_maxwell.o
In file included from ./include/asm-generic/bug.h:4:0,
                 from ./arch/x86/include/asm/bug.h:35,
                 from ./include/linux/bug.h:4,
                 from ./include/linux/mmdebug.h:4,
                 from ./include/linux/mm.h:8,
                 from /var/lib/dkms/nvidia-378/378.13/build/common/inc/nv-pgprot.h:17,
                 from /var/lib/dkms/nvidia-378/378.13/build/common/inc/nv-linux.h:17,
                 from /var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.h:39,
                 from /var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_utils.c:25:
/var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.h: In function &#8216;__fatal_signal_pending&#8217;:
/var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.h:212:25: error: implicit declaration of function &#8216;sigismember&#8217; [-Werror=implicit-function-declaration]
         return unlikely(sigismember(&p->pending.signal, SIGKILL));
                         ^
./include/linux/compiler.h:179:42: note: in definition of macro &#8216;unlikely&#8217;
 # define unlikely(x) __builtin_expect(!!(x), 0)
                                          ^
In file included from /var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_utils.c:25:0:
/var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.h: In function &#8216;fatal_signal_pending&#8217;:
/var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.h:217:16: error: implicit declaration of function &#8216;signal_pending&#8217;; did you mean &#8216;timer_pending&#8217;? [-Werror=implicit-function-declaration]
         return signal_pending(p) && __fatal_signal_pending(p);
                ^~~~~~~~~~~~~~
                timer_pending
cc1: some warnings being treated as errors
scripts/Makefile.build:294: recipe for target '/var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_utils.o' failed
make[2]: *** [/var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_utils.o] Error 1
make[2]: *** Waiting for unfinished jobs....
In file included from ./include/asm-generic/bug.h:4:0,
                 from ./arch/x86/include/asm/bug.h:35,
                 from ./include/linux/bug.h:4,
                 from ./include/linux/mmdebug.h:4,
                 from ./include/linux/mm.h:8,
                 from /var/lib/dkms/nvidia-378/378.13/build/common/inc/nv-pgprot.h:17,
                 from /var/lib/dkms/nvidia-378/378.13/build/common/inc/nv-linux.h:17,
                 from /var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.h:39,
                 from /var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_common.h:62,
                 from /var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_common.c:29:
/var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.h: In function &#8216;__fatal_signal_pending&#8217;:
/var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.h:212:25: error: implicit declaration of function &#8216;sigismember&#8217; [-Werror=implicit-function-declaration]
         return unlikely(sigismember(&p->pending.signal, SIGKILL));
                         ^
./include/linux/compiler.h:179:42: note: in definition of macro &#8216;unlikely&#8217;
 # define unlikely(x) __builtin_expect(!!(x), 0)
                                          ^
In file included from /var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_common.h:62:0,
                 from /var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_common.c:29:
/var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.h: In function &#8216;fatal_signal_pending&#8217;:
/var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.h:217:16: error: implicit declaration of function &#8216;signal_pending&#8217;; did you mean &#8216;timer_pending&#8217;? [-Werror=implicit-function-declaration]
         return signal_pending(p) && __fatal_signal_pending(p);
                ^~~~~~~~~~~~~~
                timer_pending
cc1: some warnings being treated as errors
scripts/Makefile.build:294: recipe for target '/var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_common.o' failed
make[2]: *** [/var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_common.o] Error 1
In file included from ./include/asm-generic/bug.h:4:0,
                 from ./arch/x86/include/asm/bug.h:35,
                 from ./include/linux/bug.h:4,
                 from ./include/linux/mmdebug.h:4,
                 from ./include/linux/mm.h:8,
                 from /var/lib/dkms/nvidia-378/378.13/build/common/inc/nv-pgprot.h:17,
                 from /var/lib/dkms/nvidia-378/378.13/build/common/inc/nv-linux.h:17,
                 from /var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.h:39,
                 from /var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.c:24:
/var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.h: In function &#8216;__fatal_signal_pending&#8217;:
/var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.h:212:25: error: implicit declaration of function &#8216;sigismember&#8217; [-Werror=implicit-function-declaration]
         return unlikely(sigismember(&p->pending.signal, SIGKILL));
                         ^
./include/linux/compiler.h:179:42: note: in definition of macro &#8216;unlikely&#8217;
 # define unlikely(x) __builtin_expect(!!(x), 0)
                                          ^
In file included from /var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.c:24:0:
/var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.h: In function &#8216;fatal_signal_pending&#8217;:
/var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.h:217:16: error: implicit declaration of function &#8216;signal_pending&#8217;; did you mean &#8216;timer_pending&#8217;? [-Werror=implicit-function-declaration]
         return signal_pending(p) && __fatal_signal_pending(p);
                ^~~~~~~~~~~~~~
                timer_pending
cc1: some warnings being treated as errors
scripts/Makefile.build:294: recipe for target '/var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.o' failed
make[2]: *** [/var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.o] Error 1
In file included from ./include/asm-generic/bug.h:4:0,
                 from ./arch/x86/include/asm/bug.h:35,
                 from ./include/linux/bug.h:4,
                 from ./include/linux/mmdebug.h:4,
                 from ./include/linux/mm.h:8,
                 from /var/lib/dkms/nvidia-378/378.13/build/common/inc/nv-pgprot.h:17,
                 from /var/lib/dkms/nvidia-378/378.13/build/common/inc/nv-linux.h:17,
                 from /var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.h:39,
                 from /var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_page_migration.c:31:
/var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.h: In function &#8216;__fatal_signal_pending&#8217;:
/var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.h:212:25: error: implicit declaration of function &#8216;sigismember&#8217; [-Werror=implicit-function-declaration]
         return unlikely(sigismember(&p->pending.signal, SIGKILL));
                         ^
./include/linux/compiler.h:179:42: note: in definition of macro &#8216;unlikely&#8217;
 # define unlikely(x) __builtin_expect(!!(x), 0)
                                          ^
In file included from /var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_page_migration.c:31:0:
/var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.h: In function &#8216;fatal_signal_pending&#8217;:
/var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_linux.h:217:16: error: implicit declaration of function &#8216;signal_pending&#8217;; did you mean &#8216;timer_pending&#8217;? [-Werror=implicit-function-declaration]
         return signal_pending(p) && __fatal_signal_pending(p);
                ^~~~~~~~~~~~~~
                timer_pending
cc1: some warnings being treated as errors
scripts/Makefile.build:294: recipe for target '/var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_page_migration.o' failed
make[2]: *** [/var/lib/dkms/nvidia-378/378.13/build/nvidia-uvm/uvm_page_migration.o] Error 1
Makefile:1492: recipe for target '_module_/var/lib/dkms/nvidia-378/378.13/build' failed
make[1]: *** [_module_/var/lib/dkms/nvidia-378/378.13/build] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.11.12-041112-generic'
Makefile:81: recipe for target 'modules' failed
make: *** [modules] Error 2



```

i use the Nvidia-378 so i upgraded to Nvidia-387 as recommended... however, nothing changed so far.

and now i'm stuck :(

any idea what should i do ?
thx

---

### Post by alain.roger on 2017-10-20
Upgrade of driver nvidia-387 has not been done till the end. Now it works well after i relaunch the Nvidia-387 upgrade

---

### Post by dino99 on 2017-10-20
back to 4.10

---

