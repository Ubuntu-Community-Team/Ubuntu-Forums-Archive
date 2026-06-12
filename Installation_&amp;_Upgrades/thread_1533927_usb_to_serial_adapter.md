---
title: "usb to serial adapter"
date: 2010-07-18
forum: Installation &amp; Upgrades
---

### Post by Neliel on 2010-07-18
I'm having the hardest time trying to get my microcontroller working under this serial-usb adapter in ubuntu 10.04. I have tried lsusb in terminal and i do not get anything at all.
the dmesg command gives me the following
[    1.974000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.974048] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.974082] sd 0:0:0:0: [sda] Write Protect is off
[    1.974085] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.974102] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.974226]  sda:
[    1.975785] scsi 6:0:0:0: CD-ROM            SONY     DVD RW DRU-V200A 1.60 PQ: 0 ANSI: 5
[    1.980027]  sda1 sda2 <sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.980649] Uniform CD-ROM driver Revision: 3.20
[    1.980745] sr 6:0:0:0: Attached scsi CD-ROM sr0
[    1.980799] sr 6:0:0:0: Attached scsi generic sg1 type 5
[    1.980869] ata8: port disabled. ignoring.
[    2.002803]  sda5 >
[    2.003031] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.006519] usbcore: registered new interface driver hiddev
[    2.012139] input: MosArt Optical Mouse as /devices/pci0000:00/0000:00:04.0/usb4/4-6/4-6:1.0/input/input5
[    2.012240] generic-usb 0003:13EE:0003.0001: input,hidraw0: USB HID v1.10 Mouse [MosArt Optical Mouse] on usb-0000:00:04.0-6/input0
[    2.012264] usbcore: registered new interface driver usbhid
[    2.012267] usbhid: v2.6:USB HID core driver
[    2.458814] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.750139] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0001d4d60f]
[    7.214539] udev: starting version 151
[    7.226405] lp: driver loaded but no devices found
[    7.252411] Adding 19803128k swap on /dev/sda5.  Priority:-1 extents:1 across:19803128k 
[    7.261937] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[    7.261945] ACPI: resource nForce2_smbus [0x1c40-0x1c7f] conflicts with ACPI region SM00 [0x001c40-0x001c7f]
[    7.261947] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    7.261950] nForce2_smbus 0000:00:01.1: Error probing SMB2.
[    7.366462] nvidia: module license 'NVIDIA' taints kernel.
[    7.366467] Disabling lock debugging due to kernel taint
[    7.391490] type=1505 audit(1279477248.668:2):  operation="profile_load" pid=858 name="/sbin/dhclient3"
[    7.391743] type=1505 audit(1279477248.668:3):  operation="profile_load" pid=858 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    7.391883] type=1505 audit(1279477248.668:4):  operation="profile_load" pid=858 name="/usr/lib/connman/scripts/dhclient-script"
[    7.647363] type=1505 audit(1279477248.928:5):  operation="profile_load" pid=958 name="/usr/share/gdm/guest-session/Xsession"
[    7.648735] type=1505 audit(1279477248.928:6):  operation="profile_replace" pid=959 name="/sbin/dhclient3"
[    7.648996] type=1505 audit(1279477248.928:7):  operation="profile_replace" pid=959 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    7.649146] type=1505 audit(1279477248.928:8):  operation="profile_replace" pid=959 name="/usr/lib/connman/scripts/dhclient-script"
[    7.692169]   alloc irq_desc for 29 on node 0
[    7.692172]   alloc kstat_irqs on node 0
[    7.692182] forcedeth 0000:00:0a.0: irq 29 for MSI/MSI-X
[    7.750700] type=1505 audit(1279477249.028:9):  operation="profile_load" pid=960 name="/usr/bin/evince"
[    7.753950] type=1505 audit(1279477249.038:10):  operation="profile_load" pid=960 name="/usr/bin/evince-previewer"
[    7.755939] type=1505 audit(1279477249.038:11):  operation="profile_load" pid=960 name="/usr/bin/evince-thumbnailer"
[    7.765991] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    7.770603] EDAC MC: Ver: 2.1.0 Jun 11 2010
[    7.791271] EDAC amd64_edac:  Ver: 3.2.0 Jun 11 2010
[    7.794902] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[    7.794913] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    7.794914]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    7.794916]  (Note that use of the override may cause unknown side effects.)
[    7.794943] amd64_edac: probe of 0000:00:18.2 failed with error -22
[    7.851618] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[    7.851624]   alloc irq_desc for 18 on node 0
[    7.851626]   alloc kstat_irqs on node 0
[    7.851638] CA0106 0000:01:0b.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[    7.851672] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102
[    7.863180] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[    7.863183] HDA Intel 0000:00:07.0: PCI INT A -> Link[AAZA] -> GSI 21 (level, low) -> IRQ 21
[    7.863186] hda_intel: Disable MSI for Nvidia chipset
[    7.863355] HDA Intel 0000:00:07.0: setting latency timer to 64
[    8.015781] nvidia 0000:02:00.0: enabling device (0000 -> 0003)
[    8.016240] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 20
[    8.016246] nvidia 0000:02:00.0: PCI INT A -> Link[AIGP] -> GSI 20 (level, low) -> IRQ 20
[    8.016254] nvidia 0000:02:00.0: setting latency timer to 64
[    8.016259] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=none
[    8.016504] nvidia 0000:03:00.0: PCI INT A -> Link[AE0A] -> GSI 16 (level, low) -> IRQ 16
[    8.016509] nvidia 0000:03:00.0: setting latency timer to 64
[    8.016512] vgaarb: device changed decodes: PCI:0000:03:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    8.016682] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
[    8.110158] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[    8.110162] vboxdrv: Successfully done.
[    8.110164] vboxdrv: Found 4 processor cores.
[    8.110362] VBoxDrv: dbg - g_abExecMemory=ffffffffa0da2c60
[    8.110424] vboxdrv: fAsync=0 offMin=0x51f offMax=0x1fef
[    8.110647] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[    8.110649] vboxdrv: Successfully loaded version 3.2.4 (interface 0x00140001).
[   11.502782] ppdev: user-space parallel port driver
[   12.160080] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:07.0/input/input6
[   18.321262] eth0: no IPv6 routers present
[   48.432839] Intel AES-NI instructions are not detected.
[   48.470839] padlock: VIA PadLock not detected.
[  125.391690] __ratelimit: 9 callbacks suppressed
[  125.391696] npviewer.bin[1845]: segfault at 0 ip 00000000f6195041 sp 00000000ffd538d0 error 4 in libflashplayer.so[f5df6000+b04000]
[ 1632.962084] hda-intel: spurious response 0x0:0x3, last cmd=0x30c20000
[ 1632.962122] hda-intel: spurious response 0x0:0x3, last cmd=0x30c20000
[ 1632.962497] hda-intel: spurious response 0x0:0x3, last cmd=0x30c20000
[ 1633.040136] hda-intel: spurious response 0x0:0x3, last cmd=0x30c20000
[ 1633.040156] hda-intel: spurious response 0x0:0x3, last cmd=0x30c20000
[ 1633.202595] hda-intel: spurious response 0x0:0x3, last cmd=0x30c20000
[ 1634.172331] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[ 1634.172336] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[ 2186.070027] usb 3-6: new full speed USB device using ohci_hcd and address 2
[ 2186.301082] usb 3-6: configuration #1 chosen from 1 choice
[ 2186.346447] usbcore: registered new interface driver usbserial
[ 2186.346461] USB Serial support registered for generic
[ 2186.346491] usbcore: registered new interface driver usbserial_generic
[ 2186.346493] usbserial: USB Serial Driver core
[ 2186.357582] USB Serial support registered for pl2303
[ 2186.357602] pl2303 3-6:1.0: pl2303 converter detected
[ 2186.389037] usb 3-6: pl2303 converter now attached to ttyUSB0
[ 2186.389050] usbcore: registered new interface driver pl2303
[ 2186.389052] pl2303: Prolific PL2303 USB to serial adaptor driver
[ 2354.903188] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[ 2367.654738] device eth0 entered promiscuous mode
[ 2401.021292] INFO: task modem-manager:976 blocked for more than 120 seconds.
[ 2401.021296] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 2401.021299] modem-manager D 00000000ffffffff     0   976      1 0x00000000
[ 2401.021304]  ffff880226cc7978 0000000000000082 0000000000015bc0 0000000000015bc0
[ 2401.021308]  ffff880226cc83c0 ffff880226cc7fd8 0000000000015bc0 ffff880226cc8000
[ 2401.021312]  0000000000015bc0 ffff880226cc7fd8 0000000000015bc0 ffff880226cc83c0
[ 2401.021315] Call Trace:
[ 2401.021324]  [<ffffffff813d6ae5>] usb_kill_urb+0x85/0xc0
[ 2401.021330]  [<ffffffff81085430>] ? autoremove_wake_function+0x0/0x40
[ 2401.021333]  [<ffffffff813d7f40>] usb_start_wait_urb+0xe0/0x100
[ 2401.021336]  [<ffffffff813d7228>] ? usb_init_urb+0x28/0x40
[ 2401.021339]  [<ffffffff813d863e>] usb_control_msg+0xee/0x180
[ 2401.021344]  [<ffffffffa0bb583c>] set_control_lines+0x4c/0x90 [pl2303]
[ 2401.021348]  [<ffffffffa0bb58e3>] pl2303_dtr_rts+0x63/0x90 [pl2303]
[ 2401.021353]  [<ffffffffa0ba3056>] serial_dtr_rts+0x26/0x30 [usbserial]
[ 2401.021358]  [<ffffffff81333fcd>] tty_port_raise_dtr_rts+0x1d/0x20
[ 2401.021361]  [<ffffffff813344c8>] tty_port_block_til_ready+0x228/0x2f0
[ 2401.021363]  [<ffffffff813d6bfd>] ? usb_submit_urb+0xdd/0x240
[ 2401.021367]  [<ffffffffa0bb6c77>] ? pl2303_open+0x107/0x250 [pl2303]
[ 2401.021370]  [<ffffffff81085430>] ? autoremove_wake_function+0x0/0x40
[ 2401.021374]  [<ffffffffa0ba3d44>] serial_open+0x94/0x160 [usbserial]
[ 2401.021377]  [<ffffffff8132d8a9>] __tty_open+0x209/0x510
[ 2401.021380]  [<ffffffff8132dbdc>] tty_open+0x2c/0x40
[ 2401.021385]  [<ffffffff8114789a>] chrdev_open+0x13a/0x240
[ 2401.021388]  [<ffffffff81147760>] ? chrdev_open+0x0/0x240
[ 2401.021391]  [<ffffffff81141ba3>] __dentry_open+0x113/0x370
[ 2401.021395]  [<ffffffff8125330f>] ? security_inode_permission+0x1f/0x30
[ 2401.021398]  [<ffffffff8114df3f>] ? inode_permission+0xaf/0xd0
[ 2401.021401]  [<ffffffff81141f17>] nameidata_to_filp+0x57/0x70
[ 2401.021404]  [<ffffffff8115217a>] do_filp_open+0x2da/0xba0
[ 2401.021407]  [<ffffffff810ff741>] ? lru_cache_add_lru+0x21/0x40
[ 2401.021412]  [<ffffffff8144e0c5>] ? sys_sendto+0x125/0x180
[ 2401.021416]  [<ffffffff8111615f>] ? handle_mm_fault+0x31f/0x3c0
[ 2401.021419]  [<ffffffff8115dcfa>] ? alloc_fd+0x10a/0x150
[ 2401.021422]  [<ffffffff81141919>] do_sys_open+0x69/0x170
[ 2401.021425]  [<ffffffff81141a60>] sys_open+0x20/0x30
[ 2401.021429]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
[ 2521.021290] INFO: task modem-manager:976 blocked for more than 120 seconds.
[ 2521.021294] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 2521.021297] modem-manager D 00000000ffffffff     0   976      1 0x00000000
[ 2521.021302]  ffff880226cc7978 0000000000000082 0000000000015bc0 0000000000015bc0
[ 2521.021306]  ffff880226cc83c0 ffff880226cc7fd8 0000000000015bc0 ffff880226cc8000
[ 2521.021310]  0000000000015bc0 ffff880226cc7fd8 0000000000015bc0 ffff880226cc83c0
[ 2521.021313] Call Trace:
[ 2521.021322]  [<ffffffff813d6ae5>] usb_kill_urb+0x85/0xc0
[ 2521.021328]  [<ffffffff81085430>] ? autoremove_wake_function+0x0/0x40
[ 2521.021331]  [<ffffffff813d7f40>] usb_start_wait_urb+0xe0/0x100
[ 2521.021334]  [<ffffffff813d7228>] ? usb_init_urb+0x28/0x40
[ 2521.021337]  [<ffffffff813d863e>] usb_control_msg+0xee/0x180
[ 2521.021342]  [<ffffffffa0bb583c>] set_control_lines+0x4c/0x90 [pl2303]
[ 2521.021346]  [<ffffffffa0bb58e3>] pl2303_dtr_rts+0x63/0x90 [pl2303]
[ 2521.021351]  [<ffffffffa0ba3056>] serial_dtr_rts+0x26/0x30 [usbserial]
[ 2521.021355]  [<ffffffff81333fcd>] tty_port_raise_dtr_rts+0x1d/0x20
[ 2521.021358]  [<ffffffff813344c8>] tty_port_block_til_ready+0x228/0x2f0
[ 2521.021361]  [<ffffffff813d6bfd>] ? usb_submit_urb+0xdd/0x240
[ 2521.021364]  [<ffffffffa0bb6c77>] ? pl2303_open+0x107/0x250 [pl2303]
[ 2521.021367]  [<ffffffff81085430>] ? autoremove_wake_function+0x0/0x40
[ 2521.021372]  [<ffffffffa0ba3d44>] serial_open+0x94/0x160 [usbserial]
[ 2521.021375]  [<ffffffff8132d8a9>] __tty_open+0x209/0x510
[ 2521.021377]  [<ffffffff8132dbdc>] tty_open+0x2c/0x40
[ 2521.021382]  [<ffffffff8114789a>] chrdev_open+0x13a/0x240
[ 2521.021385]  [<ffffffff81147760>] ? chrdev_open+0x0/0x240
[ 2521.021388]  [<ffffffff81141ba3>] __dentry_open+0x113/0x370
[ 2521.021392]  [<ffffffff8125330f>] ? security_inode_permission+0x1f/0x30
[ 2521.021395]  [<ffffffff8114df3f>] ? inode_permission+0xaf/0xd0
[ 2521.021398]  [<ffffffff81141f17>] nameidata_to_filp+0x57/0x70
[ 2521.021401]  [<ffffffff8115217a>] do_filp_open+0x2da/0xba0
[ 2521.021404]  [<ffffffff810ff741>] ? lru_cache_add_lru+0x21/0x40
[ 2521.021409]  [<ffffffff8144e0c5>] ? sys_sendto+0x125/0x180
[ 2521.021412]  [<ffffffff8111615f>] ? handle_mm_fault+0x31f/0x3c0
[ 2521.021416]  [<ffffffff8115dcfa>] ? alloc_fd+0x10a/0x150
[ 2521.021418]  [<ffffffff81141919>] do_sys_open+0x69/0x170
[ 2521.021421]  [<ffffffff81141a60>] sys_open+0x20/0x30
[ 2521.021425]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
[ 2587.063348] usb 3-6: USB disconnect, address 2
[ 2641.021293] INFO: task modem-manager:976 blocked for more than 120 seconds.
[ 2641.021297] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 2641.021300] modem-manager D 00000000ffffffff     0   976      1 0x00000000
[ 2641.021306]  ffff880226cc7978 0000000000000082 0000000000015bc0 0000000000015bc0
[ 2641.021310]  ffff880226cc83c0 ffff880226cc7fd8 0000000000015bc0 ffff880226cc8000
[ 2641.021313]  0000000000015bc0 ffff880226cc7fd8 0000000000015bc0 ffff880226cc83c0
[ 2641.021317] Call Trace:
[ 2641.021326]  [<ffffffff813d6ae5>] usb_kill_urb+0x85/0xc0
[ 2641.021332]  [<ffffffff81085430>] ? autoremove_wake_function+0x0/0x40
[ 2641.021335]  [<ffffffff813d7f40>] usb_start_wait_urb+0xe0/0x100
[ 2641.021338]  [<ffffffff813d7228>] ? usb_init_urb+0x28/0x40
[ 2641.021341]  [<ffffffff813d863e>] usb_control_msg+0xee/0x180
[ 2641.021346]  [<ffffffffa0bb583c>] set_control_lines+0x4c/0x90 [pl2303]
[ 2641.021350]  [<ffffffffa0bb58e3>] pl2303_dtr_rts+0x63/0x90 [pl2303]
[ 2641.021355]  [<ffffffffa0ba3056>] serial_dtr_rts+0x26/0x30 [usbserial]
[ 2641.021359]  [<ffffffff81333fcd>] tty_port_raise_dtr_rts+0x1d/0x20
[ 2641.021362]  [<ffffffff813344c8>] tty_port_block_til_ready+0x228/0x2f0
[ 2641.021365]  [<ffffffff813d6bfd>] ? usb_submit_urb+0xdd/0x240
[ 2641.021368]  [<ffffffffa0bb6c77>] ? pl2303_open+0x107/0x250 [pl2303]
[ 2641.021371]  [<ffffffff81085430>] ? autoremove_wake_function+0x0/0x40
[ 2641.021376]  [<ffffffffa0ba3d44>] serial_open+0x94/0x160 [usbserial]
[ 2641.021379]  [<ffffffff8132d8a9>] __tty_open+0x209/0x510
[ 2641.021382]  [<ffffffff8132dbdc>] tty_open+0x2c/0x40
[ 2641.021387]  [<ffffffff8114789a>] chrdev_open+0x13a/0x240
[ 2641.021390]  [<ffffffff81147760>] ? chrdev_open+0x0/0x240
[ 2641.021393]  [<ffffffff81141ba3>] __dentry_open+0x113/0x370
[ 2641.021397]  [<ffffffff8125330f>] ? security_inode_permission+0x1f/0x30
[ 2641.021400]  [<ffffffff8114df3f>] ? inode_permission+0xaf/0xd0
[ 2641.021403]  [<ffffffff81141f17>] nameidata_to_filp+0x57/0x70
[ 2641.021406]  [<ffffffff8115217a>] do_filp_open+0x2da/0xba0
[ 2641.021409]  [<ffffffff810ff741>] ? lru_cache_add_lru+0x21/0x40
[ 2641.021414]  [<ffffffff8144e0c5>] ? sys_sendto+0x125/0x180
[ 2641.021417]  [<ffffffff8111615f>] ? handle_mm_fault+0x31f/0x3c0
[ 2641.021421]  [<ffffffff8115dcfa>] ? alloc_fd+0x10a/0x150
[ 2641.021423]  [<ffffffff81141919>] do_sys_open+0x69/0x170
[ 2641.021426]  [<ffffffff81141a60>] sys_open+0x20/0x30
[ 2641.021430]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
[ 2761.021284] INFO: task khubd:44 blocked for more than 120 seconds.
[ 2761.021288] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 2761.021291] khubd         D 0000000000000000     0    44      2 0x00000000
[ 2761.021296]  ffff880234d63bb0 0000000000000046 0000000000015bc0 0000000000015bc0
[ 2761.021300]  ffff880234d59ab0 ffff880234d63fd8 0000000000015bc0 ffff880234d596f0
[ 2761.021304]  0000000000015bc0 ffff880234d63fd8 0000000000015bc0 ffff880234d59ab0
[ 2761.021307] Call Trace:
[ 2761.021316]  [<ffffffff813d6ae5>] usb_kill_urb+0x85/0xc0
[ 2761.021322]  [<ffffffff81085430>] ? autoremove_wake_function+0x0/0x40
[ 2761.021325]  [<ffffffff813d6d7b>] ? usb_get_urb+0x1b/0x30
[ 2761.021328]  [<ffffffff813d5403>] usb_hcd_flush_endpoint+0x133/0x140
[ 2761.021331]  [<ffffffff813d775d>] usb_disable_endpoint+0x5d/0x90
[ 2761.021334]  [<ffffffff813d77c0>] usb_disable_device+0x30/0x130
[ 2761.021338]  [<ffffffff813d15d2>] usb_disconnect+0xd2/0x170
[ 2761.021341]  [<ffffffff813d1c3f>] hub_port_connect_change+0x8f/0x980
[ 2761.021344]  [<ffffffff813d2f32>] hub_events+0x3b2/0x5a0
[ 2761.021348]  [<ffffffff81540f40>] ? thread_return+0x48/0x418
[ 2761.021351]  [<ffffffff813d3175>] hub_thread+0x55/0x190
[ 2761.021354]  [<ffffffff81085430>] ? autoremove_wake_function+0x0/0x40
[ 2761.021357]  [<ffffffff813d3120>] ? hub_thread+0x0/0x190
[ 2761.021360]  [<ffffffff810850b6>] kthread+0x96/0xa0
[ 2761.021363]  [<ffffffff810141ea>] child_rip+0xa/0x20
[ 2761.021366]  [<ffffffff81085020>] ? kthread+0x0/0xa0
[ 2761.021369]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
[ 2761.021379] INFO: task modem-manager:976 blocked for more than 120 seconds.
[ 2761.021381] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 2761.021383] modem-manager D 00000000ffffffff     0   976      1 0x00000000
[ 2761.021389]  ffff880226cc7978 0000000000000082 0000000000015bc0 0000000000015bc0
[ 2761.021393]  ffff880226cc83c0 ffff880226cc7fd8 0000000000015bc0 ffff880226cc8000
[ 2761.021396]  0000000000015bc0 ffff880226cc7fd8 0000000000015bc0 ffff880226cc83c0
[ 2761.021399] Call Trace:
[ 2761.021401]  [<ffffffff813d6ae5>] usb_kill_urb+0x85/0xc0
[ 2761.021405]  [<ffffffff81085430>] ? autoremove_wake_function+0x0/0x40
[ 2761.021408]  [<ffffffff813d7f40>] usb_start_wait_urb+0xe0/0x100
[ 2761.021410]  [<ffffffff813d7228>] ? usb_init_urb+0x28/0x40
[ 2761.021413]  [<ffffffff813d863e>] usb_control_msg+0xee/0x180
[ 2761.021418]  [<ffffffffa0bb583c>] set_control_lines+0x4c/0x90 [pl2303]
[ 2761.021422]  [<ffffffffa0bb58e3>] pl2303_dtr_rts+0x63/0x90 [pl2303]
[ 2761.021427]  [<ffffffffa0ba3056>] serial_dtr_rts+0x26/0x30 [usbserial]
[ 2761.021431]  [<ffffffff81333fcd>] tty_port_raise_dtr_rts+0x1d/0x20
[ 2761.021434]  [<ffffffff813344c8>] tty_port_block_til_ready+0x228/0x2f0
[ 2761.021436]  [<ffffffff813d6bfd>] ? usb_submit_urb+0xdd/0x240
[ 2761.021440]  [<ffffffffa0bb6c77>] ? pl2303_open+0x107/0x250 [pl2303]
[ 2761.021443]  [<ffffffff81085430>] ? autoremove_wake_function+0x0/0x40
[ 2761.021447]  [<ffffffffa0ba3d44>] serial_open+0x94/0x160 [usbserial]
[ 2761.021450]  [<ffffffff8132d8a9>] __tty_open+0x209/0x510
[ 2761.021453]  [<ffffffff8132dbdc>] tty_open+0x2c/0x40
[ 2761.021457]  [<ffffffff8114789a>] chrdev_open+0x13a/0x240
[ 2761.021460]  [<ffffffff81147760>] ? chrdev_open+0x0/0x240
[ 2761.021463]  [<ffffffff81141ba3>] __dentry_open+0x113/0x370
[ 2761.021467]  [<ffffffff8125330f>] ? security_inode_permission+0x1f/0x30
[ 2761.021471]  [<ffffffff8114df3f>] ? inode_permission+0xaf/0xd0
[ 2761.021473]  [<ffffffff81141f17>] nameidata_to_filp+0x57/0x70
[ 2761.021476]  [<ffffffff8115217a>] do_filp_open+0x2da/0xba0
[ 2761.021480]  [<ffffffff810ff741>] ? lru_cache_add_lru+0x21/0x40
[ 2761.021484]  [<ffffffff8144e0c5>] ? sys_sendto+0x125/0x180
[ 2761.021487]  [<ffffffff8111615f>] ? handle_mm_fault+0x31f/0x3c0
[ 2761.021490]  [<ffffffff8115dcfa>] ? alloc_fd+0x10a/0x150
[ 2761.021493]  [<ffffffff81141919>] do_sys_open+0x69/0x170
[ 2761.021496]  [<ffffffff81141a60>] sys_open+0x20/0x30
[ 2761.021499]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
[ 2771.672154] eth0: link down.
[ 2801.549544] eth0: link up.
[ 2881.021002] INFO: task khubd:44 blocked for more than 120 seconds.
[ 2881.021007] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 2881.021009] khubd         D 0000000000000000     0    44      2 0x00000000
[ 2881.021014]  ffff880234d63bb0 0000000000000046 0000000000015bc0 0000000000015bc0
[ 2881.021019]  ffff880234d59ab0 ffff880234d63fd8 0000000000015bc0 ffff880234d596f0
[ 2881.021022]  0000000000015bc0 ffff880234d63fd8 0000000000015bc0 ffff880234d59ab0
[ 2881.021026] Call Trace:
[ 2881.021034]  [<ffffffff813d6ae5>] usb_kill_urb+0x85/0xc0
[ 2881.021040]  [<ffffffff81085430>] ? autoremove_wake_function+0x0/0x40
[ 2881.021043]  [<ffffffff813d6d7b>] ? usb_get_urb+0x1b/0x30
[ 2881.021046]  [<ffffffff813d5403>] usb_hcd_flush_endpoint+0x133/0x140
[ 2881.021049]  [<ffffffff813d775d>] usb_disable_endpoint+0x5d/0x90
[ 2881.021052]  [<ffffffff813d77c0>] usb_disable_device+0x30/0x130
[ 2881.021056]  [<ffffffff813d15d2>] usb_disconnect+0xd2/0x170
[ 2881.021059]  [<ffffffff813d1c3f>] hub_port_connect_change+0x8f/0x980
[ 2881.021063]  [<ffffffff813d2f32>] hub_events+0x3b2/0x5a0
[ 2881.021067]  [<ffffffff81540f40>] ? thread_return+0x48/0x418
[ 2881.021070]  [<ffffffff813d3175>] hub_thread+0x55/0x190
[ 2881.021073]  [<ffffffff81085430>] ? autoremove_wake_function+0x0/0x40
[ 2881.021076]  [<ffffffff813d3120>] ? hub_thread+0x0/0x190
[ 2881.021078]  [<ffffffff810850b6>] kthread+0x96/0xa0
[ 2881.021082]  [<ffffffff810141ea>] child_rip+0xa/0x20
[ 2881.021084]  [<ffffffff81085020>] ? kthread+0x0/0xa0
[ 2881.021087]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
[ 2881.021097] INFO: task modem-manager:976 blocked for more than 120 seconds.
[ 2881.021099] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 2881.021101] modem-manager D 00000000ffffffff     0   976      1 0x00000000
[ 2881.021107]  ffff880226cc7978 0000000000000082 0000000000015bc0 0000000000015bc0
[ 2881.021111]  ffff880226cc83c0 ffff880226cc7fd8 0000000000015bc0 ffff880226cc8000
[ 2881.021114]  0000000000015bc0 ffff880226cc7fd8 0000000000015bc0 ffff880226cc83c0
[ 2881.021116] Call Trace:
[ 2881.021119]  [<ffffffff813d6ae5>] usb_kill_urb+0x85/0xc0
[ 2881.021122]  [<ffffffff81085430>] ? autoremove_wake_function+0x0/0x40
[ 2881.021125]  [<ffffffff813d7f40>] usb_start_wait_urb+0xe0/0x100
[ 2881.021128]  [<ffffffff813d7228>] ? usb_init_urb+0x28/0x40
[ 2881.021130]  [<ffffffff813d863e>] usb_control_msg+0xee/0x180
[ 2881.021135]  [<ffffffffa0bb583c>] set_control_lines+0x4c/0x90 [pl2303]
[ 2881.021139]  [<ffffffffa0bb58e3>] pl2303_dtr_rts+0x63/0x90 [pl2303]
[ 2881.021144]  [<ffffffffa0ba3056>] serial_dtr_rts+0x26/0x30 [usbserial]
[ 2881.021148]  [<ffffffff81333fcd>] tty_port_raise_dtr_rts+0x1d/0x20
[ 2881.021151]  [<ffffffff813344c8>] tty_port_block_til_ready+0x228/0x2f0
[ 2881.021154]  [<ffffffff813d6bfd>] ? usb_submit_urb+0xdd/0x240
[ 2881.021157]  [<ffffffffa0bb6c77>] ? pl2303_open+0x107/0x250 [pl2303]
[ 2881.021160]  [<ffffffff81085430>] ? autoremove_wake_function+0x0/0x40
[ 2881.021165]  [<ffffffffa0ba3d44>] serial_open+0x94/0x160 [usbserial]
[ 2881.021168]  [<ffffffff8132d8a9>] __tty_open+0x209/0x510
[ 2881.021170]  [<ffffffff8132dbdc>] tty_open+0x2c/0x40
[ 2881.021174]  [<ffffffff8114789a>] chrdev_open+0x13a/0x240
[ 2881.021177]  [<ffffffff81147760>] ? chrdev_open+0x0/0x240
[ 2881.021180]  [<ffffffff81141ba3>] __dentry_open+0x113/0x370
[ 2881.021184]  [<ffffffff8125330f>] ? security_inode_permission+0x1f/0x30
[ 2881.021188]  [<ffffffff8114df3f>] ? inode_permission+0xaf/0xd0
[ 2881.021190]  [<ffffffff81141f17>] nameidata_to_filp+0x57/0x70
[ 2881.021193]  [<ffffffff8115217a>] do_filp_open+0x2da/0xba0
[ 2881.021197]  [<ffffffff810ff741>] ? lru_cache_add_lru+0x21/0x40
[ 2881.021201]  [<ffffffff8144e0c5>] ? sys_sendto+0x125/0x180
[ 2881.021204]  [<ffffffff8111615f>] ? handle_mm_fault+0x31f/0x3c0
[ 2881.021208]  [<ffffffff8115dcfa>] ? alloc_fd+0x10a/0x150
[ 2881.021210]  [<ffffffff81141919>] do_sys_open+0x69/0x170
[ 2881.021213]  [<ffffffff81141a60>] sys_open+0x20/0x30
[ 2881.021217]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
[ 2889.299611] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[ 2889.299649] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[ 3001.021283] INFO: task khubd:44 blocked for more than 120 seconds.
[ 3001.021288] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 3001.021290] khubd         D 0000000000000000     0    44      2 0x00000000
[ 3001.021295]  ffff880234d63bb0 0000000000000046 0000000000015bc0 0000000000015bc0
[ 3001.021300]  ffff880234d59ab0 ffff880234d63fd8 0000000000015bc0 ffff880234d596f0
[ 3001.021303]  0000000000015bc0 ffff880234d63fd8 0000000000015bc0 ffff880234d59ab0
[ 3001.021306] Call Trace:
[ 3001.021315]  [<ffffffff813d6ae5>] usb_kill_urb+0x85/0xc0
[ 3001.021321]  [<ffffffff81085430>] ? autoremove_wake_function+0x0/0x40
[ 3001.021324]  [<ffffffff813d6d7b>] ? usb_get_urb+0x1b/0x30
[ 3001.021327]  [<ffffffff813d5403>] usb_hcd_flush_endpoint+0x133/0x140
[ 3001.021330]  [<ffffffff813d775d>] usb_disable_endpoint+0x5d/0x90
[ 3001.021333]  [<ffffffff813d77c0>] usb_disable_device+0x30/0x130
[ 3001.021337]  [<ffffffff813d15d2>] usb_disconnect+0xd2/0x170
[ 3001.021340]  [<ffffffff813d1c3f>] hub_port_connect_change+0x8f/0x980
[ 3001.021343]  [<ffffffff813d2f32>] hub_events+0x3b2/0x5a0
[ 3001.021347]  [<ffffffff81540f40>] ? thread_return+0x48/0x418
[ 3001.021350]  [<ffffffff813d3175>] hub_thread+0x55/0x190
[ 3001.021353]  [<ffffffff81085430>] ? autoremove_wake_function+0x0/0x40
[ 3001.021356]  [<ffffffff813d3120>] ? hub_thread+0x0/0x190
[ 3001.021359]  [<ffffffff810850b6>] kthread+0x96/0xa0
[ 3001.021362]  [<ffffffff810141ea>] child_rip+0xa/0x20
[ 3001.021365]  [<ffffffff81085020>] ? kthread+0x0/0xa0
[ 3001.021367]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
[ 3001.021378] INFO: task modem-manager:976 blocked for more than 120 seconds.
[ 3001.021380] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 3001.021381] modem-manager D 00000000ffffffff     0   976      1 0x00000000
[ 3001.021385]  ffff880226cc7978 0000000000000082 0000000000015bc0 0000000000015bc0
[ 3001.021389]  ffff880226cc83c0 ffff880226cc7fd8 0000000000015bc0 ffff880226cc8000
[ 3001.021392]  0000000000015bc0 ffff880226cc7fd8 0000000000015bc0 ffff880226cc83c0
[ 3001.021395] Call Trace:
[ 3001.021397]  [<ffffffff813d6ae5>] usb_kill_urb+0x85/0xc0
[ 3001.021400]  [<ffffffff81085430>] ? autoremove_wake_function+0x0/0x40
[ 3001.021403]  [<ffffffff813d7f40>] usb_start_wait_urb+0xe0/0x100
[ 3001.021406]  [<ffffffff813d7228>] ? usb_init_urb+0x28/0x40
[ 3001.021409]  [<ffffffff813d863e>] usb_control_msg+0xee/0x180
[ 3001.021414]  [<ffffffffa0bb583c>] set_control_lines+0x4c/0x90 [pl2303]
[ 3001.021417]  [<ffffffffa0bb58e3>] pl2303_dtr_rts+0x63/0x90 [pl2303]
[ 3001.021422]  [<ffffffffa0ba3056>] serial_dtr_rts+0x26/0x30 [usbserial]
[ 3001.021426]  [<ffffffff81333fcd>] tty_port_raise_dtr_rts+0x1d/0x20
[ 3001.021429]  [<ffffffff813344c8>] tty_port_block_til_ready+0x228/0x2f0
[ 3001.021432]  [<ffffffff813d6bfd>] ? usb_submit_urb+0xdd/0x240
[ 3001.021435]  [<ffffffffa0bb6c77>] ? pl2303_open+0x107/0x250 [pl2303]
[ 3001.021438]  [<ffffffff81085430>] ? autoremove_wake_function+0x0/0x40
[ 3001.021443]  [<ffffffffa0ba3d44>] serial_open+0x94/0x160 [usbserial]
[ 3001.021446]  [<ffffffff8132d8a9>] __tty_open+0x209/0x510
[ 3001.021448]  [<ffffffff8132dbdc>] tty_open+0x2c/0x40
[ 3001.021453]  [<ffffffff8114789a>] chrdev_open+0x13a/0x240
[ 3001.021456]  [<ffffffff81147760>] ? chrdev_open+0x0/0x240
[ 3001.021458]  [<ffffffff81141ba3>] __dentry_open+0x113/0x370
[ 3001.021462]  [<ffffffff8125330f>] ? security_inode_permission+0x1f/0x30
[ 3001.021466]  [<ffffffff8114df3f>] ? inode_permission+0xaf/0xd0
[ 3001.021468]  [<ffffffff81141f17>] nameidata_to_filp+0x57/0x70
[ 3001.021471]  [<ffffffff8115217a>] do_filp_open+0x2da/0xba0
[ 3001.021474]  [<ffffffff810ff741>] ? lru_cache_add_lru+0x21/0x40
[ 3001.021478]  [<ffffffff8144e0c5>] ? sys_sendto+0x125/0x180
[ 3001.021482]  [<ffffffff8111615f>] ? handle_mm_fault+0x31f/0x3c0
[ 3001.021485]  [<ffffffff8115dcfa>] ? alloc_fd+0x10a/0x150
[ 3001.021488]  [<ffffffff81141919>] do_sys_open+0x69/0x170
[ 3001.021490]  [<ffffffff81141a60>] sys_open+0x20/0x30
[ 3001.021494]  [<ffffffff810131b2>] system_call_fastpath+0x16/0x1b
[ 3121.020298] INFO: task khubd:44 blocked for more than 120 seconds.
[ 3121.020303] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 3121.020305] khubd         D 0000000000000000     0    44      2 0x00000000
[ 3121.020311]  ffff880234d63bb0 0000000000000046 0000000000015bc0 0000000000015bc0
[ 3121.020315]  ffff880234d59ab0 ffff880234d63fd8 0000000000015bc0 ffff880234d596f0
[ 3121.020319]  0000000000015bc0 ffff880234d63fd8 0000000000015bc0 ffff880234d59ab0
[ 3121.020322] Call Trace:
[ 3121.020332]  [<ffffffff813d6ae5>] usb_kill_urb+0x85/0xc0
[ 3121.020338]  [<ffffffff81085430>] ? autoremove_wake_function+0x0/0x40
[ 3121.020341]  [<ffffffff813d6d7b>] ? usb_get_urb+0x1b/0x30
[ 3121.020344]  [<ffffffff813d5403>] usb_hcd_flush_endpoint+0x133/0x140
[ 3121.020347]  [<ffffffff813d775d>] usb_disable_endpoint+0x5d/0x90
[ 3121.020350]  [<ffffffff813d77c0>] usb_disable_device+0x30/0x130
[ 3121.020354]  [<ffffffff813d15d2>] usb_disconnect+0xd2/0x170
[ 3121.020357]  [<ffffffff813d1c3f>] hub_port_connect_change+0x8f/0x980
[ 3121.020361]  [<ffffffff813d2f32>] hub_events+0x3b2/0x5a0
[ 3121.020365]  [<ffffffff81540f40>] ? thread_return+0x48/0x418
[ 3121.020368]  [<ffffffff813d3175>] hub_thread+0x55/0x190
[ 3121.020371]  [<ffffffff81085430>] ? autoremove_wake_function+0x0/0x40
[ 3121.020374]  [<ffffffff813d3120>] ? hub_thread+0x0/0x190
[ 3121.020377]  [<ffffffff810850b6>] kthread+0x96/0xa0
[ 3121.020380]  [<ffffffff810141ea>] child_rip+0xa/0x20
[ 3121.020383]  [<ffffffff81085020>] ? kthread+0x0/0xa0
[ 3121.020385]  [<ffffffff810141e0>] ? child_rip+0x0/0x20
[ 5462.014196] type=1503 audit(1279482699.599:15):  operation="open" pid=3230 parent=3218 profile="/usr/sbin/cupsd" requested_mask="w::" denied_mask="w::" fsuid=0 ouid=0 name="/dev/ttyUSB0"
[ 5492.108447] type=1503 audit(1279482729.689:16):  operation="open" pid=3314 parent=3302 profile="/usr/sbin/cupsd" requested_mask="w::" denied_mask="w::" fsuid=0 ouid=0 name="/dev/ttyUSB0"
[ 6210.066810] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 6210.077991] ISOFS: changing to secondary root
[ 9425.643931] npviewer.bin[1882]: segfault at 418 ip 00000000f60d9a56 sp 00000000ffcd59e8 error 6 in libflashplayer.so[f5e8b000+b04000]


I am sort of still new to ubuntu and do not know how to work around this, can anyone give me some tips on how to activate the drivers for this or get it to work?

---

### Post by davidmohammed on 2010-07-18
the trace indicates that your usb - serial adapter is working and recognised.  Immediately after however, a "modem-manager" connected to a USB port immediately crashes a kernel module.

What serial device have you got connected? - is it this "modem-manager" the trace is indicating.

---

### Post by Neliel on 2010-07-18
its a microcontroller for robots right now but i would like to use my servo controller as well, but i need to get this working first, its a sabrent usb to serial cable, and a lynxmotion bot board 2 microcontroller

---

### Post by davidmohammed on 2010-07-19
have you compiled the correct drivers - assuming there are linux drivers for your device?  From where?

What software would you expect to control your device - e.g. was the software that came with it a Windows only thing?

---

### Post by PresenceofMind on 2010-07-19
> **Neliel said:**
> I do not believe there are any drivers for the  microcontroller, but there are for the adapter, but it is only the  redhat version, and i have no idea if i would even be able to use it,  and i was planning on using the microcontroller through windows  virualization or wine but i need to get the adapter to work  first.

Hello,

Are you using the Intel 8051/52 (or based-on) by any chance? I have a project next year so I want to look into the capabilities. 

I tried to control a set of LEDs that I soldered together using a similar adapter (it was a PCI Express to Parallel) connected to the laptop. It didn't work. The mapping was all different because of the conversion between the two types of connectors. So if you managed to get it to work..please let me know.

Thanks :D

PS: Oh nearly forgot.... which Assembly compiler or IDE did you use in Linux?

---

### Post by Neliel on 2010-07-19
I do not believe there are any drivers for the microcontroller, but there are for the adapter, but it is only the redhat version, and i have no idea if i would even be able to use it, and i was planning on using the microcontroller through windows virualization or wine but i need to get the adapter to work first.

---

### Post by davidmohammed on 2010-07-19
if you insert the adapter without the serial device connected, does dmesg still have a stack fault after

 2186.346461] USB Serial support registered for generic
[ 2186.346491] usbcore: registered new interface driver usbserial_generic
[ 2186.346493] usbserial: USB Serial Driver core
[ 2186.357582] USB Serial support registered for pl2303
[ 2186.357602] pl2303 3-6:1.0: pl2303 converter detected
[ 2186.389037] usb 3-6: pl2303 converter now attached to ttyUSB0
[ 2186.389050] usbcore: registered new interface driver pl2303
[ 2186.389052] pl2303: Prolific PL2303 USB to serial adaptor driver

is reported?

If there is no stack fault that your adapter I would summise is working fine - its your serial device that is causing the issue.

---

### Post by Neliel on 2010-07-19
I got the following with just the adapter in.

[    0.960973] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[    0.960975] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[    0.960978] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.960980] system 00:0c: iomem range 0xfeff0000-0xfeff00ff has been reserved
[    0.960983] system 00:0c: iomem range 0xafee0000-0xafefffff could not be reserved
[    0.960985] system 00:0c: iomem range 0xffff0000-0xffffffff has been reserved
[    0.960988] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.960991] system 00:0c: iomem range 0x100000-0xafedffff could not be reserved
[    0.960993] system 00:0c: iomem range 0xafff0000-0xbffeffff could not be reserved
[    0.960996] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.960999] system 00:0c: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.961001] system 00:0c: iomem range 0xfefff000-0xfeffffff has been reserved
[    0.961004] system 00:0c: iomem range 0xfff80000-0xfff80fff has been reserved
[    0.961007] system 00:0c: iomem range 0xfff90000-0xfffbffff has been reserved
[    0.961009] system 00:0c: iomem range 0xfffed000-0xfffeffff has been reserved
[    0.965816] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.965819] pci 0000:00:08.0:   IO window: 0xe000-0xefff
[    0.965823] pci 0000:00:08.0:   MEM window: 0xfde00000-0xfdefffff
[    0.965826] pci 0000:00:08.0:   PREFETCH window: 0xfdd00000-0xfddfffff
[    0.965834] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
[    0.965836] pci 0000:00:0b.0:   IO window: 0xd000-0xdfff
[    0.965839] pci 0000:00:0b.0:   MEM window: 0xfb000000-0xfcffffff
[    0.965842] pci 0000:00:0b.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.965846] pci 0000:00:10.0: PCI bridge, secondary bus 0000:03
[    0.965850] pci 0000:00:10.0:   IO window: 0xc000-0xcfff
[    0.965860] pci 0000:00:10.0:   MEM window: 0xf6000000-0xf9ffffff
[    0.965867] pci 0000:00:10.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.965879] pci 0000:00:12.0: PCI bridge, secondary bus 0000:04
[    0.965884] pci 0000:00:12.0:   IO window: 0xb000-0xbfff
[    0.965893] pci 0000:00:12.0:   MEM window: 0xfdc00000-0xfdcfffff
[    0.965900] pci 0000:00:12.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
[    0.965913] pci 0000:00:13.0: PCI bridge, secondary bus 0000:05
[    0.965917] pci 0000:00:13.0:   IO window: 0xa000-0xafff
[    0.965927] pci 0000:00:13.0:   MEM window: 0xfda00000-0xfdafffff
[    0.965934] pci 0000:00:13.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
[    0.965946] pci 0000:00:14.0: PCI bridge, secondary bus 0000:06
[    0.965951] pci 0000:00:14.0:   IO window: 0x9000-0x9fff
[    0.965960] pci 0000:00:14.0:   MEM window: 0xfd800000-0xfd8fffff
[    0.965968] pci 0000:00:14.0:   PREFETCH window: 0x000000fd700000-0x000000fd7fffff
[    0.965986] pci 0000:00:08.0: setting latency timer to 64
[    0.965992] pci 0000:00:0b.0: setting latency timer to 64
[    0.966411] ACPI: PCI Interrupt Link [AE0A] enabled at IRQ 16
[    0.966415]   alloc irq_desc for 16 on node 0
[    0.966417]   alloc kstat_irqs on node 0
[    0.966426] pci 0000:00:10.0: PCI INT A -> Link[AE0A] -> GSI 16 (level, low) -> IRQ 16
[    0.966434] pci 0000:00:10.0: setting latency timer to 64
[    0.966829] ACPI: PCI Interrupt Link [AE2A] enabled at IRQ 16
[    0.966836] pci 0000:00:12.0: PCI INT A -> Link[AE2A] -> GSI 16 (level, low) -> IRQ 16
[    0.966844] pci 0000:00:12.0: setting latency timer to 64
[    0.967242] ACPI: PCI Interrupt Link [AE3A] enabled at IRQ 16
[    0.967245] pci 0000:00:13.0: PCI INT A -> Link[AE3A] -> GSI 16 (level, low) -> IRQ 16
[    0.967253] pci 0000:00:13.0: setting latency timer to 64
[    0.967646] ACPI: PCI Interrupt Link [AE4A] enabled at IRQ 16
[    0.967653] pci 0000:00:14.0: PCI INT A -> Link[AE4A] -> GSI 16 (level, low) -> IRQ 16
[    0.967661] pci 0000:00:14.0: setting latency timer to 64
[    0.967667] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.967670] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.967672] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.967675] pci_bus 0000:01: resource 1 mem: [0xfde00000-0xfdefffff]
[    0.967677] pci_bus 0000:01: resource 2 pref mem [0xfdd00000-0xfddfffff]
[    0.967679] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.967681] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.967684] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.967686] pci_bus 0000:02: resource 1 mem: [0xfb000000-0xfcffffff]
[    0.967688] pci_bus 0000:02: resource 2 pref mem [0xe0000000-0xefffffff]
[    0.967690] pci_bus 0000:03: resource 0 io:  [0xc000-0xcfff]
[    0.967692] pci_bus 0000:03: resource 1 mem: [0xf6000000-0xf9ffffff]
[    0.967695] pci_bus 0000:03: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.967697] pci_bus 0000:04: resource 0 io:  [0xb000-0xbfff]
[    0.967699] pci_bus 0000:04: resource 1 mem: [0xfdc00000-0xfdcfffff]
[    0.967701] pci_bus 0000:04: resource 2 pref mem [0xfdb00000-0xfdbfffff]
[    0.967704] pci_bus 0000:05: resource 0 io:  [0xa000-0xafff]
[    0.967706] pci_bus 0000:05: resource 1 mem: [0xfda00000-0xfdafffff]
[    0.967708] pci_bus 0000:05: resource 2 pref mem [0xfd900000-0xfd9fffff]
[    0.967710] pci_bus 0000:06: resource 0 io:  [0x9000-0x9fff]
[    0.967712] pci_bus 0000:06: resource 1 mem: [0xfd800000-0xfd8fffff]
[    0.967715] pci_bus 0000:06: resource 2 pref mem [0xfd700000-0xfd7fffff]
[    0.967756] NET: Registered protocol family 2
[    0.968019] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.969600] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.972694] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.973066] TCP: Hash tables configured (established 524288 bind 65536)
[    0.973069] TCP reno registered
[    0.973172] NET: Registered protocol family 1
[    1.029819] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.029921] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.030026] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.030137] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.030247] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    1.030489] pci 0000:03:00.0: Boot video device
[    1.030758] PCI-DMA: Disabling AGP.
[    1.030856] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    1.030858] PCI-DMA: using GART IOMMU.
[    1.030862] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.032584] Scanning for low memory corruption every 60 seconds
[    1.032704] audit: initializing netlink socket (disabled)
[    1.032716] type=2000 audit(1279537272.029:1): initialized
[    1.041227] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.042658] VFS: Disk quotas dquot_6.5.2
[    1.042709] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.043329] fuse init (API version 7.13)
[    1.043410] msgmni has been set to 15498
[    1.043662] alg: No test for stdrng (krng)
[    1.043720] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.043723] io scheduler noop registered
[    1.043725] io scheduler anticipatory registered
[    1.043726] io scheduler deadline registered
[    1.043760] io scheduler cfq registered (default)
[    1.044146]   alloc irq_desc for 24 on node 0
[    1.044148]   alloc kstat_irqs on node 0
[    1.044168] pcieport 0000:00:10.0: irq 24 for MSI/MSI-X
[    1.044188] pcieport 0000:00:10.0: setting latency timer to 64
[    1.044581]   alloc irq_desc for 25 on node 0
[    1.044583]   alloc kstat_irqs on node 0
[    1.044599] pcieport 0000:00:12.0: irq 25 for MSI/MSI-X
[    1.044617] pcieport 0000:00:12.0: setting latency timer to 64
[    1.044997]   alloc irq_desc for 26 on node 0
[    1.044999]   alloc kstat_irqs on node 0
[    1.045014] pcieport 0000:00:13.0: irq 26 for MSI/MSI-X
[    1.045032] pcieport 0000:00:13.0: setting latency timer to 64
[    1.045412]   alloc irq_desc for 27 on node 0
[    1.045413]   alloc kstat_irqs on node 0
[    1.045429] pcieport 0000:00:14.0: irq 27 for MSI/MSI-X
[    1.045447] pcieport 0000:00:14.0: setting latency timer to 64
[    1.045599] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.045619] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.045718] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.045722] ACPI: Power Button [PWRB]
[    1.045790] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.045792] ACPI: Power Button [PWRF]
[    1.045845] fan PNP0C0B:00: registered as cooling_device0
[    1.045849] ACPI: Fan [FAN] (on)
[    1.046527] processor LNXCPU:00: registered as cooling_device1
[    1.046556] processor LNXCPU:01: registered as cooling_device2
[    1.046583] processor LNXCPU:02: registered as cooling_device3
[    1.046611] processor LNXCPU:03: registered as cooling_device4
[    1.057160] ACPI Warning for \_TZ_.THRM._PSL: Return Package type mismatch at index 0 - found [NULL Object Descriptor], expected Reference (20090903/nspredef-1012)
[    1.057168] ACPI: Expecting a [Reference] package element, found type 0
[    1.057169] ACPI: Invalid passive threshold
[    1.057658] thermal LNXTHERM:01: registered as thermal_zone0
[    1.057665] ACPI: Thermal Zone [THRM] (40 C)
[    1.058872] Linux agpgart interface v0.103
[    1.058904] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.058997] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.059271] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.060160] brd: module loaded
[    1.060558] loop: module loaded
[    1.060625] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.060812] pata_acpi 0000:00:06.0: setting latency timer to 64
[    1.061296] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    1.061300]   alloc irq_desc for 23 on node 0
[    1.061302]   alloc kstat_irqs on node 0
[    1.061311] pata_acpi 0000:00:09.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.061329] pata_acpi 0000:00:09.0: setting latency timer to 64
[    1.061335] pata_acpi 0000:00:09.0: PCI INT A disabled
[    1.061628] Fixed MDIO Bus: probed
[    1.061655] PPP generic driver version 2.4.2
[    1.061691] tun: Universal TUN/TAP device driver, 1.6
[    1.061693] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.061764] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.062198] ACPI: PCI Interrupt Link [AUB2] enabled at IRQ 22
[    1.062200]   alloc irq_desc for 22 on node 0
[    1.062201]   alloc kstat_irqs on node 0
[    1.062209] ehci_hcd 0000:00:02.1: PCI INT B -> Link[AUB2] -> GSI 22 (level, low) -> IRQ 22
[    1.062227] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    1.062230] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    1.062259] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    1.062285] ehci_hcd 0000:00:02.1: debug port 1
[    1.062293] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    1.062314] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
[    1.080027] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    1.080095] usb usb1: configuration #1 chosen from 1 choice
[    1.080122] hub 1-0:1.0: USB hub found
[    1.080128] hub 1-0:1.0: 6 ports detected
[    1.080454] ACPI: PCI Interrupt Link [AU2B] disabled and referenced, BIOS bug
[    1.080607] ACPI: PCI Interrupt Link [AU2B] enabled at IRQ 21
[    1.080615]   alloc irq_desc for 21 on node 0
[    1.080616]   alloc kstat_irqs on node 0
[    1.080623] ehci_hcd 0000:00:04.1: PCI INT B -> Link[AU2B] -> GSI 21 (level, low) -> IRQ 21
[    1.080632] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    1.080635] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    1.080661] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    1.080679] ehci_hcd 0000:00:04.1: debug port 1
[    1.080686] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    1.080701] ehci_hcd 0000:00:04.1: irq 21, io mem 0xfe02c000
[    1.100019] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    1.100081] usb usb2: configuration #1 chosen from 1 choice
[    1.100101] hub 2-0:1.0: USB hub found
[    1.100106] hub 2-0:1.0: 6 ports detected
[    1.100164] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.100593] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 20
[    1.100595]   alloc irq_desc for 20 on node 0
[    1.100597]   alloc kstat_irqs on node 0
[    1.100604] ohci_hcd 0000:00:02.0: PCI INT A -> Link[AUBA] -> GSI 20 (level, low) -> IRQ 20
[    1.100615] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    1.100618] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    1.100644] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    1.100664] ohci_hcd 0000:00:02.0: irq 20, io mem 0xfe02f000
[    1.162085] usb usb3: configuration #1 chosen from 1 choice
[    1.162107] hub 3-0:1.0: USB hub found
[    1.162114] hub 3-0:1.0: 6 ports detected
[    1.162576] ACPI: PCI Interrupt Link [AU1B] enabled at IRQ 23
[    1.162579] ohci_hcd 0000:00:04.0: PCI INT A -> Link[AU1B] -> GSI 23 (level, low) -> IRQ 23
[    1.162589] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    1.162591] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    1.162617] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    1.162640] ohci_hcd 0000:00:04.0: irq 23, io mem 0xfe02d000
[    1.222084] usb usb4: configuration #1 chosen from 1 choice
[    1.222106] hub 4-0:1.0: USB hub found
[    1.222112] hub 4-0:1.0: 6 ports detected
[    1.222165] uhci_hcd: USB Universal Host Controller Interface driver
[    1.222222] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.222224] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.222366] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.222442] mice: PS/2 mouse device common for all mice
[    1.222528] rtc_cmos 00:05: RTC can wake from S4
[    1.222556] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.222615] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.222732] device-mapper: uevent: version 1.0.3
[    1.222826] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.222938] device-mapper: multipath: version 1.1.0 loaded
[    1.222940] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.223177] cpuidle: using governor ladder
[    1.223179] cpuidle: using governor menu
[    1.223537] TCP cubic registered
[    1.223668] NET: Registered protocol family 10
[    1.224140] lo: Disabled Privacy Extensions
[    1.224436] NET: Registered protocol family 17
[    1.224474] powernow-k8: Found 1 AMD Phenom(tm) 9500 Quad-Core Processor processors (4 cpu cores) (version 2.20.00)
[    1.224482] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    1.224483] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
[    1.224567] PM: Resume from disk failed.
[    1.224577] registered taskstats version 1
[    1.225187]   Magic number: 2:560:24
[    1.225190] misc cpu_dma_latency: hash matches
[    1.225319] rtc_cmos 00:05: setting system clock to 2010-07-19 11:01:13 UTC (1279537273)
[    1.225322] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.225323] EDD information not available.
[    1.225371] Freeing unused kernel memory: 880k freed
[    1.225667] Write protecting the kernel read-only data: 7692k
[    1.242811] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.243245] udev: starting version 151
[    1.265606] vga16fb: initializing
[    1.265610] vga16fb: mapped to 0xffff8800000a0000
[    1.265666] fb0: VGA16 VGA frame buffer device
[    1.272819] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.273315] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[    1.273322] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
[    1.273327] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.296875] [Firmware Bug]: ACPI(IGPU) defines _DOD but not _DOS
[    1.297154] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0f/LNXVIDEO:00/input/input4
[    1.297204] ACPI: Video Device [IGPU] (multi-head: yes  rom: no  post: no)
[    1.301961] Floppy drive(s): fd0 is 1.44M
[    1.302592] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    1.302599]   alloc irq_desc for 19 on node 0
[    1.302601]   alloc kstat_irqs on node 0
[    1.302613] ohci1394 0000:01:0a.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    1.326734] FDC 0 is a post-1991 82077
[    1.351310] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:24:8c:69:e4:ba
[    1.351314] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt gbit lnktim msi desc-v3
[    1.351457] pata_amd 0000:00:06.0: version 0.4.1
[    1.351499] pata_amd 0000:00:06.0: setting latency timer to 64
[    1.351637] scsi0 : pata_amd
[    1.351751] scsi1 : pata_amd
[    1.352556] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    1.352559] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    1.352651] ahci 0000:00:09.0: version 3.0
[    1.352661] ahci 0000:00:09.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.352722]   alloc irq_desc for 28 on node 0
[    1.352724]   alloc kstat_irqs on node 0
[    1.352732] ahci 0000:00:09.0: irq 28 for MSI/MSI-X
[    1.352792] ahci 0000:00:09.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl IDE mode
[    1.352795] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio boh 
[    1.352798] ahci 0000:00:09.0: setting latency timer to 64
[    1.353186] scsi2 : ahci
[    1.353268] scsi3 : ahci
[    1.353325] scsi4 : ahci
[    1.353382] scsi5 : ahci
[    1.353441] scsi6 : ahci
[    1.353500] scsi7 : ahci
[    1.353662] ata3: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026100 irq 28
[    1.353665] ata4: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026180 irq 28
[    1.353667] ata5: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026200 irq 28
[    1.353669] ata6: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026280 irq 28
[    1.353671] ata7: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026300 irq 28
[    1.353673] ata8: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026380 irq 28
[    1.362071] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    1.502290] Console: switching to colour frame buffer device 80x30
[    1.530352] ata1.00: ATAPI: SONY    DVD RW DRU-V200A, 1.60, max UDMA/66
[    1.530382] ata1: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)
[    1.570293] ata1.00: configured for UDMA/66
[    1.572839] scsi 0:0:0:0: CD-ROM            SONY     DVD RW DRU-V200A 1.60 PQ: 0 ANSI: 5
[    1.575439] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.575441] Uniform CD-ROM driver Revision: 3.20
[    1.575543] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.575603] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.575681] ata2: port disabled. ignoring.
[    1.700023] ata7: SATA link down (SStatus 0 SControl 300)
[    1.700050] ata4: SATA link down (SStatus 0 SControl 300)
[    1.700055] ata6: SATA link down (SStatus 0 SControl 300)
[    1.700070] ata5: SATA link down (SStatus 0 SControl 300)
[    1.700077] ata8: SATA link down (SStatus 0 SControl 300)
[    1.800019] usb 4-6: new low speed USB device using ohci_hcd and address 2
[    1.880019] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.889164] ata3.00: ATA-8: WDC WD5000AAJS-00A8B2, 01.03B01, max UDMA/133
[    1.889167] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.890692] ata3.00: configured for UDMA/133
[    1.890779] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000AAJS-0 01.0 PQ: 0 ANSI: 5
[    1.890932] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.890955] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.890967] sd 2:0:0:0: [sda] Write Protect is off
[    1.890970] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.890989] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.891121]  sda: sda1 sda2 < sda5 >
[    1.920123] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.027111] usb 4-6: configuration #1 chosen from 1 choice
[    2.038924] usbcore: registered new interface driver hiddev
[    2.044195] input: MosArt Optical Mouse as /devices/pci0000:00/0000:00:04.0/usb4/4-6/4-6:1.0/input/input5
[    2.044285] generic-usb 0003:13EE:0003.0001: input,hidraw0: USB HID v1.10 Mouse [MosArt Optical Mouse] on usb-0000:00:04.0-6/input0
[    2.044306] usbcore: registered new interface driver usbhid
[    2.044309] usbhid: v2.6:USB HID core driver
[    2.349782] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.349788] EXT4-fs (sda1): write access will be enabled during recovery
[    2.370018] usb 3-6: new full speed USB device using ohci_hcd and address 2
[    2.607124] usb 3-6: configuration #1 chosen from 1 choice
[    2.680189] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0001d4d60f]
[    2.834783] EXT4-fs (sda1): orphan cleanup on readonly fs
[    2.834793] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 20474716
[    2.834874] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 20473449
[    2.834910] EXT4-fs (sda1): 2 orphan inodes deleted
[    2.834913] EXT4-fs (sda1): recovery complete
[    3.235374] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    7.656390] udev: starting version 151
[    7.699375] Adding 19803128k swap on /dev/sda5.  Priority:-1 extents:1 across:19803128k 
[    7.736747] lp: driver loaded but no devices found
[    7.748915] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[    7.748922] ACPI: resource nForce2_smbus [0x1c40-0x1c7f] conflicts with ACPI region SM00 [0x001c40-0x001c7f]
[    7.748924] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    7.748927] nForce2_smbus 0000:00:01.1: Error probing SMB2.
[    7.767064] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    7.808163] nvidia: module license 'NVIDIA' taints kernel.
[    7.808167] Disabling lock debugging due to kernel taint
[    7.819951] type=1505 audit(1279551680.084:2):  operation="profile_load" pid=817 name="/sbin/dhclient3"
[    7.820203] type=1505 audit(1279551680.094:3):  operation="profile_load" pid=817 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    7.820343] type=1505 audit(1279551680.094:4):  operation="profile_load" pid=817 name="/usr/lib/connman/scripts/dhclient-script"
[    7.904549] type=1505 audit(1279551680.174:5):  operation="profile_load" pid=937 name="/usr/share/gdm/guest-session/Xsession"
[    7.905929] type=1505 audit(1279551680.174:6):  operation="profile_replace" pid=938 name="/sbin/dhclient3"
[    7.906194] type=1505 audit(1279551680.174:7):  operation="profile_replace" pid=938 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    7.906342] type=1505 audit(1279551680.174:8):  operation="profile_replace" pid=938 name="/usr/lib/connman/scripts/dhclient-script"
[    7.926623]   alloc irq_desc for 29 on node 0
[    7.926626]   alloc kstat_irqs on node 0
[    7.926636] forcedeth 0000:00:0a.0: irq 29 for MSI/MSI-X
[    8.010088] type=1505 audit(1279551680.284:9):  operation="profile_load" pid=939 name="/usr/bin/evince"
[    8.013415] type=1505 audit(1279551680.284:10):  operation="profile_load" pid=939 name="/usr/bin/evince-previewer"
[    8.015416] type=1505 audit(1279551680.284:11):  operation="profile_load" pid=939 name="/usr/bin/evince-thumbnailer"
[    8.210952] EDAC MC: Ver: 2.1.0 Jun 11 2010
[    8.221879] usbcore: registered new interface driver usbserial
[    8.221897] USB Serial support registered for generic
[    8.221924] usbcore: registered new interface driver usbserial_generic
[    8.221926] usbserial: USB Serial Driver core
[    8.225111] EDAC amd64_edac:  Ver: 3.2.0 Jun 11 2010
[    8.225484] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[    8.225495] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    8.225496]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    8.225497]  (Note that use of the override may cause unknown side effects.)
[    8.225511] amd64_edac: probe of 0000:00:18.2 failed with error -22
[    8.300427] USB Serial support registered for pl2303
[    8.300611] pl2303 3-6:1.0: pl2303 converter detected
[    8.307235] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[    8.307243] HDA Intel 0000:00:07.0: PCI INT A -> Link[AAZA] -> GSI 21 (level, low) -> IRQ 21
[    8.307247] hda_intel: Disable MSI for Nvidia chipset
[    8.307366] HDA Intel 0000:00:07.0: setting latency timer to 64
[    8.332039] usb 3-6: pl2303 converter now attached to ttyUSB0
[    8.332059] usbcore: registered new interface driver pl2303
[    8.332061] pl2303: Prolific PL2303 USB to serial adaptor driver
[    8.370651] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[    8.370657]   alloc irq_desc for 18 on node 0
[    8.370659]   alloc kstat_irqs on node 0
[    8.370670] CA0106 0000:01:0b.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[    8.370702] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102
[    8.456728] nvidia 0000:02:00.0: enabling device (0000 -> 0003)
[    8.457179] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 20
[    8.457185] nvidia 0000:02:00.0: PCI INT A -> Link[AIGP] -> GSI 20 (level, low) -> IRQ 20
[    8.457193] nvidia 0000:02:00.0: setting latency timer to 64
[    8.457198] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=none
[    8.457407] nvidia 0000:03:00.0: PCI INT A -> Link[AE0A] -> GSI 16 (level, low) -> IRQ 16
[    8.457412] nvidia 0000:03:00.0: setting latency timer to 64
[    8.457415] vgaarb: device changed decodes: PCI:0000:03:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    8.457567] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
[    8.549187] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[    8.549191] vboxdrv: Successfully done.
[    8.549194] vboxdrv: Found 4 processor cores.
[    8.549321] VBoxDrv: dbg - g_abExecMemory=ffffffffa0d7ac60
[    8.549398] vboxdrv: fAsync=0 offMin=0x547 offMax=0x2437
[    8.549721] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[    8.549723] vboxdrv: Successfully loaded version 3.2.4 (interface 0x00140001).
[   11.354395] ppdev: user-space parallel port driver
[   12.210092] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:07.0/input/input6
[   18.491255] eth0: no IPv6 routers present
[   21.105861] hda-intel: spurious response 0x10de0101:0x3, last cmd=0x304f0d00
[   33.022529] Intel AES-NI instructions are not detected.
[   33.110572] padlock: VIA PadLock not detected.
[   36.801223] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   44.060867] ISO 9660 Extensions: Microsoft Joliet Level 3
[   44.099485] ISOFS: changing to secondary root
[  489.931747] __ratelimit: 9 callbacks suppressed
[  489.931753] npviewer.bin[1851]: segfault at 418 ip 00000000f60e0a56 sp 00000000fff42268 error 6 in libflashplayer.so[f5e92000+b04000]
[  705.669617] npviewer.bin[2016]: segfault at 418 ip 00000000f6030a56 sp 00000000ffad9798 error 6 in libflashplayer.so[f5de2000+b04000]
[  715.083732] npviewer.bin[2220]: segfault at 418 ip 00000000f60baa56 sp 00000000ff9edf58 error 6 in libflashplayer.so[f5e6c000+b04000]
[ 6673.891949] npviewer.bin[2259]: segfault at 418 ip 00000000f60dda56 sp 00000000ff876488 error 6 in libflashplayer.so[f5e8f000+b04000]
[11592.019850] hub 4-0:1.0: port 6 disabled by hub (EMI?), re-enabling...
[11592.019857] usb 4-6: USB disconnect, address 2
[11592.539709] usb 4-6: new low speed USB device using ohci_hcd and address 3
[11592.774936] usb 4-6: configuration #1 chosen from 1 choice
[11592.785001] input: MosArt Optical Mouse as /devices/pci0000:00/0000:00:04.0/usb4/4-6/4-6:1.0/input/input7
[11592.785098] generic-usb 0003:13EE:0003.0002: input,hidraw0: USB HID v1.10 Mouse [MosArt Optical Mouse] on usb-0000:00:04.0-6/input0
[13611.857879] npviewer.bin[2637]: segfault at f334d04c ip 00000000f6178057 sp 00000000ff890d00 error 4 in libflashplayer.so[f5dd9000+b04000]

---

### Post by Neliel on 2010-07-19
and here is the dmesg with the servo controller attached, (different device from the original)


[    0.960988] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.960991] system 00:0c: iomem range 0x100000-0xafedffff could not be reserved
[    0.960993] system 00:0c: iomem range 0xafff0000-0xbffeffff could not be reserved
[    0.960996] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.960999] system 00:0c: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.961001] system 00:0c: iomem range 0xfefff000-0xfeffffff has been reserved
[    0.961004] system 00:0c: iomem range 0xfff80000-0xfff80fff has been reserved
[    0.961007] system 00:0c: iomem range 0xfff90000-0xfffbffff has been reserved
[    0.961009] system 00:0c: iomem range 0xfffed000-0xfffeffff has been reserved
[    0.965816] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.965819] pci 0000:00:08.0:   IO window: 0xe000-0xefff
[    0.965823] pci 0000:00:08.0:   MEM window: 0xfde00000-0xfdefffff
[    0.965826] pci 0000:00:08.0:   PREFETCH window: 0xfdd00000-0xfddfffff
[    0.965834] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
[    0.965836] pci 0000:00:0b.0:   IO window: 0xd000-0xdfff
[    0.965839] pci 0000:00:0b.0:   MEM window: 0xfb000000-0xfcffffff
[    0.965842] pci 0000:00:0b.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.965846] pci 0000:00:10.0: PCI bridge, secondary bus 0000:03
[    0.965850] pci 0000:00:10.0:   IO window: 0xc000-0xcfff
[    0.965860] pci 0000:00:10.0:   MEM window: 0xf6000000-0xf9ffffff
[    0.965867] pci 0000:00:10.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.965879] pci 0000:00:12.0: PCI bridge, secondary bus 0000:04
[    0.965884] pci 0000:00:12.0:   IO window: 0xb000-0xbfff
[    0.965893] pci 0000:00:12.0:   MEM window: 0xfdc00000-0xfdcfffff
[    0.965900] pci 0000:00:12.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
[    0.965913] pci 0000:00:13.0: PCI bridge, secondary bus 0000:05
[    0.965917] pci 0000:00:13.0:   IO window: 0xa000-0xafff
[    0.965927] pci 0000:00:13.0:   MEM window: 0xfda00000-0xfdafffff
[    0.965934] pci 0000:00:13.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
[    0.965946] pci 0000:00:14.0: PCI bridge, secondary bus 0000:06
[    0.965951] pci 0000:00:14.0:   IO window: 0x9000-0x9fff
[    0.965960] pci 0000:00:14.0:   MEM window: 0xfd800000-0xfd8fffff
[    0.965968] pci 0000:00:14.0:   PREFETCH window: 0x000000fd700000-0x000000fd7fffff
[    0.965986] pci 0000:00:08.0: setting latency timer to 64
[    0.965992] pci 0000:00:0b.0: setting latency timer to 64
[    0.966411] ACPI: PCI Interrupt Link [AE0A] enabled at IRQ 16
[    0.966415]   alloc irq_desc for 16 on node 0
[    0.966417]   alloc kstat_irqs on node 0
[    0.966426] pci 0000:00:10.0: PCI INT A -> Link[AE0A] -> GSI 16 (level, low) -> IRQ 16
[    0.966434] pci 0000:00:10.0: setting latency timer to 64
[    0.966829] ACPI: PCI Interrupt Link [AE2A] enabled at IRQ 16
[    0.966836] pci 0000:00:12.0: PCI INT A -> Link[AE2A] -> GSI 16 (level, low) -> IRQ 16
[    0.966844] pci 0000:00:12.0: setting latency timer to 64
[    0.967242] ACPI: PCI Interrupt Link [AE3A] enabled at IRQ 16
[    0.967245] pci 0000:00:13.0: PCI INT A -> Link[AE3A] -> GSI 16 (level, low) -> IRQ 16
[    0.967253] pci 0000:00:13.0: setting latency timer to 64
[    0.967646] ACPI: PCI Interrupt Link [AE4A] enabled at IRQ 16
[    0.967653] pci 0000:00:14.0: PCI INT A -> Link[AE4A] -> GSI 16 (level, low) -> IRQ 16
[    0.967661] pci 0000:00:14.0: setting latency timer to 64
[    0.967667] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.967670] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.967672] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.967675] pci_bus 0000:01: resource 1 mem: [0xfde00000-0xfdefffff]
[    0.967677] pci_bus 0000:01: resource 2 pref mem [0xfdd00000-0xfddfffff]
[    0.967679] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.967681] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.967684] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.967686] pci_bus 0000:02: resource 1 mem: [0xfb000000-0xfcffffff]
[    0.967688] pci_bus 0000:02: resource 2 pref mem [0xe0000000-0xefffffff]
[    0.967690] pci_bus 0000:03: resource 0 io:  [0xc000-0xcfff]
[    0.967692] pci_bus 0000:03: resource 1 mem: [0xf6000000-0xf9ffffff]
[    0.967695] pci_bus 0000:03: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.967697] pci_bus 0000:04: resource 0 io:  [0xb000-0xbfff]
[    0.967699] pci_bus 0000:04: resource 1 mem: [0xfdc00000-0xfdcfffff]
[    0.967701] pci_bus 0000:04: resource 2 pref mem [0xfdb00000-0xfdbfffff]
[    0.967704] pci_bus 0000:05: resource 0 io:  [0xa000-0xafff]
[    0.967706] pci_bus 0000:05: resource 1 mem: [0xfda00000-0xfdafffff]
[    0.967708] pci_bus 0000:05: resource 2 pref mem [0xfd900000-0xfd9fffff]
[    0.967710] pci_bus 0000:06: resource 0 io:  [0x9000-0x9fff]
[    0.967712] pci_bus 0000:06: resource 1 mem: [0xfd800000-0xfd8fffff]
[    0.967715] pci_bus 0000:06: resource 2 pref mem [0xfd700000-0xfd7fffff]
[    0.967756] NET: Registered protocol family 2
[    0.968019] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.969600] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.972694] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.973066] TCP: Hash tables configured (established 524288 bind 65536)
[    0.973069] TCP reno registered
[    0.973172] NET: Registered protocol family 1
[    1.029819] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.029921] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.030026] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.030137] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.030247] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    1.030489] pci 0000:03:00.0: Boot video device
[    1.030758] PCI-DMA: Disabling AGP.
[    1.030856] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    1.030858] PCI-DMA: using GART IOMMU.
[    1.030862] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.032584] Scanning for low memory corruption every 60 seconds
[    1.032704] audit: initializing netlink socket (disabled)
[    1.032716] type=2000 audit(1279537272.029:1): initialized
[    1.041227] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.042658] VFS: Disk quotas dquot_6.5.2
[    1.042709] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.043329] fuse init (API version 7.13)
[    1.043410] msgmni has been set to 15498
[    1.043662] alg: No test for stdrng (krng)
[    1.043720] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.043723] io scheduler noop registered
[    1.043725] io scheduler anticipatory registered
[    1.043726] io scheduler deadline registered
[    1.043760] io scheduler cfq registered (default)
[    1.044146]   alloc irq_desc for 24 on node 0
[    1.044148]   alloc kstat_irqs on node 0
[    1.044168] pcieport 0000:00:10.0: irq 24 for MSI/MSI-X
[    1.044188] pcieport 0000:00:10.0: setting latency timer to 64
[    1.044581]   alloc irq_desc for 25 on node 0
[    1.044583]   alloc kstat_irqs on node 0
[    1.044599] pcieport 0000:00:12.0: irq 25 for MSI/MSI-X
[    1.044617] pcieport 0000:00:12.0: setting latency timer to 64
[    1.044997]   alloc irq_desc for 26 on node 0
[    1.044999]   alloc kstat_irqs on node 0
[    1.045014] pcieport 0000:00:13.0: irq 26 for MSI/MSI-X
[    1.045032] pcieport 0000:00:13.0: setting latency timer to 64
[    1.045412]   alloc irq_desc for 27 on node 0
[    1.045413]   alloc kstat_irqs on node 0
[    1.045429] pcieport 0000:00:14.0: irq 27 for MSI/MSI-X
[    1.045447] pcieport 0000:00:14.0: setting latency timer to 64
[    1.045599] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.045619] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.045718] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.045722] ACPI: Power Button [PWRB]
[    1.045790] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.045792] ACPI: Power Button [PWRF]
[    1.045845] fan PNP0C0B:00: registered as cooling_device0
[    1.045849] ACPI: Fan [FAN] (on)
[    1.046527] processor LNXCPU:00: registered as cooling_device1
[    1.046556] processor LNXCPU:01: registered as cooling_device2
[    1.046583] processor LNXCPU:02: registered as cooling_device3
[    1.046611] processor LNXCPU:03: registered as cooling_device4
[    1.057160] ACPI Warning for \_TZ_.THRM._PSL: Return Package type mismatch at index 0 - found [NULL Object Descriptor], expected Reference (20090903/nspredef-1012)
[    1.057168] ACPI: Expecting a [Reference] package element, found type 0
[    1.057169] ACPI: Invalid passive threshold
[    1.057658] thermal LNXTHERM:01: registered as thermal_zone0
[    1.057665] ACPI: Thermal Zone [THRM] (40 C)
[    1.058872] Linux agpgart interface v0.103
[    1.058904] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.058997] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.059271] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.060160] brd: module loaded
[    1.060558] loop: module loaded
[    1.060625] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.060812] pata_acpi 0000:00:06.0: setting latency timer to 64
[    1.061296] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    1.061300]   alloc irq_desc for 23 on node 0
[    1.061302]   alloc kstat_irqs on node 0
[    1.061311] pata_acpi 0000:00:09.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.061329] pata_acpi 0000:00:09.0: setting latency timer to 64
[    1.061335] pata_acpi 0000:00:09.0: PCI INT A disabled
[    1.061628] Fixed MDIO Bus: probed
[    1.061655] PPP generic driver version 2.4.2
[    1.061691] tun: Universal TUN/TAP device driver, 1.6
[    1.061693] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.061764] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.062198] ACPI: PCI Interrupt Link [AUB2] enabled at IRQ 22
[    1.062200]   alloc irq_desc for 22 on node 0
[    1.062201]   alloc kstat_irqs on node 0
[    1.062209] ehci_hcd 0000:00:02.1: PCI INT B -> Link[AUB2] -> GSI 22 (level, low) -> IRQ 22
[    1.062227] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    1.062230] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    1.062259] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    1.062285] ehci_hcd 0000:00:02.1: debug port 1
[    1.062293] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    1.062314] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
[    1.080027] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    1.080095] usb usb1: configuration #1 chosen from 1 choice
[    1.080122] hub 1-0:1.0: USB hub found
[    1.080128] hub 1-0:1.0: 6 ports detected
[    1.080454] ACPI: PCI Interrupt Link [AU2B] disabled and referenced, BIOS bug
[    1.080607] ACPI: PCI Interrupt Link [AU2B] enabled at IRQ 21
[    1.080615]   alloc irq_desc for 21 on node 0
[    1.080616]   alloc kstat_irqs on node 0
[    1.080623] ehci_hcd 0000:00:04.1: PCI INT B -> Link[AU2B] -> GSI 21 (level, low) -> IRQ 21
[    1.080632] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    1.080635] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    1.080661] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    1.080679] ehci_hcd 0000:00:04.1: debug port 1
[    1.080686] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    1.080701] ehci_hcd 0000:00:04.1: irq 21, io mem 0xfe02c000
[    1.100019] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    1.100081] usb usb2: configuration #1 chosen from 1 choice
[    1.100101] hub 2-0:1.0: USB hub found
[    1.100106] hub 2-0:1.0: 6 ports detected
[    1.100164] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.100593] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 20
[    1.100595]   alloc irq_desc for 20 on node 0
[    1.100597]   alloc kstat_irqs on node 0
[    1.100604] ohci_hcd 0000:00:02.0: PCI INT A -> Link[AUBA] -> GSI 20 (level, low) -> IRQ 20
[    1.100615] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    1.100618] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    1.100644] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    1.100664] ohci_hcd 0000:00:02.0: irq 20, io mem 0xfe02f000
[    1.162085] usb usb3: configuration #1 chosen from 1 choice
[    1.162107] hub 3-0:1.0: USB hub found
[    1.162114] hub 3-0:1.0: 6 ports detected
[    1.162576] ACPI: PCI Interrupt Link [AU1B] enabled at IRQ 23
[    1.162579] ohci_hcd 0000:00:04.0: PCI INT A -> Link[AU1B] -> GSI 23 (level, low) -> IRQ 23
[    1.162589] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    1.162591] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    1.162617] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    1.162640] ohci_hcd 0000:00:04.0: irq 23, io mem 0xfe02d000
[    1.222084] usb usb4: configuration #1 chosen from 1 choice
[    1.222106] hub 4-0:1.0: USB hub found
[    1.222112] hub 4-0:1.0: 6 ports detected
[    1.222165] uhci_hcd: USB Universal Host Controller Interface driver
[    1.222222] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.222224] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.222366] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.222442] mice: PS/2 mouse device common for all mice
[    1.222528] rtc_cmos 00:05: RTC can wake from S4
[    1.222556] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.222615] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.222732] device-mapper: uevent: version 1.0.3
[    1.222826] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.222938] device-mapper: multipath: version 1.1.0 loaded
[    1.222940] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.223177] cpuidle: using governor ladder
[    1.223179] cpuidle: using governor menu
[    1.223537] TCP cubic registered
[    1.223668] NET: Registered protocol family 10
[    1.224140] lo: Disabled Privacy Extensions
[    1.224436] NET: Registered protocol family 17
[    1.224474] powernow-k8: Found 1 AMD Phenom(tm) 9500 Quad-Core Processor processors (4 cpu cores) (version 2.20.00)
[    1.224482] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    1.224483] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
[    1.224567] PM: Resume from disk failed.
[    1.224577] registered taskstats version 1
[    1.225187]   Magic number: 2:560:24
[    1.225190] misc cpu_dma_latency: hash matches
[    1.225319] rtc_cmos 00:05: setting system clock to 2010-07-19 11:01:13 UTC (1279537273)
[    1.225322] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.225323] EDD information not available.
[    1.225371] Freeing unused kernel memory: 880k freed
[    1.225667] Write protecting the kernel read-only data: 7692k
[    1.242811] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.243245] udev: starting version 151
[    1.265606] vga16fb: initializing
[    1.265610] vga16fb: mapped to 0xffff8800000a0000
[    1.265666] fb0: VGA16 VGA frame buffer device
[    1.272819] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.273315] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[    1.273322] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
[    1.273327] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.296875] [Firmware Bug]: ACPI(IGPU) defines _DOD but not _DOS
[    1.297154] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0f/LNXVIDEO:00/input/input4
[    1.297204] ACPI: Video Device [IGPU] (multi-head: yes  rom: no  post: no)
[    1.301961] Floppy drive(s): fd0 is 1.44M
[    1.302592] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    1.302599]   alloc irq_desc for 19 on node 0
[    1.302601]   alloc kstat_irqs on node 0
[    1.302613] ohci1394 0000:01:0a.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    1.326734] FDC 0 is a post-1991 82077
[    1.351310] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:24:8c:69:e4:ba
[    1.351314] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt gbit lnktim msi desc-v3
[    1.351457] pata_amd 0000:00:06.0: version 0.4.1
[    1.351499] pata_amd 0000:00:06.0: setting latency timer to 64
[    1.351637] scsi0 : pata_amd
[    1.351751] scsi1 : pata_amd
[    1.352556] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    1.352559] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    1.352651] ahci 0000:00:09.0: version 3.0
[    1.352661] ahci 0000:00:09.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.352722]   alloc irq_desc for 28 on node 0
[    1.352724]   alloc kstat_irqs on node 0
[    1.352732] ahci 0000:00:09.0: irq 28 for MSI/MSI-X
[    1.352792] ahci 0000:00:09.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl IDE mode
[    1.352795] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio boh 
[    1.352798] ahci 0000:00:09.0: setting latency timer to 64
[    1.353186] scsi2 : ahci
[    1.353268] scsi3 : ahci
[    1.353325] scsi4 : ahci
[    1.353382] scsi5 : ahci
[    1.353441] scsi6 : ahci
[    1.353500] scsi7 : ahci
[    1.353662] ata3: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026100 irq 28
[    1.353665] ata4: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026180 irq 28
[    1.353667] ata5: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026200 irq 28
[    1.353669] ata6: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026280 irq 28
[    1.353671] ata7: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026300 irq 28
[    1.353673] ata8: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026380 irq 28
[    1.362071] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    1.502290] Console: switching to colour frame buffer device 80x30
[    1.530352] ata1.00: ATAPI: SONY    DVD RW DRU-V200A, 1.60, max UDMA/66
[    1.530382] ata1: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)
[    1.570293] ata1.00: configured for UDMA/66
[    1.572839] scsi 0:0:0:0: CD-ROM            SONY     DVD RW DRU-V200A 1.60 PQ: 0 ANSI: 5
[    1.575439] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.575441] Uniform CD-ROM driver Revision: 3.20
[    1.575543] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.575603] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.575681] ata2: port disabled. ignoring.
[    1.700023] ata7: SATA link down (SStatus 0 SControl 300)
[    1.700050] ata4: SATA link down (SStatus 0 SControl 300)
[    1.700055] ata6: SATA link down (SStatus 0 SControl 300)
[    1.700070] ata5: SATA link down (SStatus 0 SControl 300)
[    1.700077] ata8: SATA link down (SStatus 0 SControl 300)
[    1.800019] usb 4-6: new low speed USB device using ohci_hcd and address 2
[    1.880019] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.889164] ata3.00: ATA-8: WDC WD5000AAJS-00A8B2, 01.03B01, max UDMA/133
[    1.889167] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.890692] ata3.00: configured for UDMA/133
[    1.890779] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000AAJS-0 01.0 PQ: 0 ANSI: 5
[    1.890932] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.890955] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.890967] sd 2:0:0:0: [sda] Write Protect is off
[    1.890970] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.890989] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.891121]  sda: sda1 sda2 < sda5 >
[    1.920123] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.027111] usb 4-6: configuration #1 chosen from 1 choice
[    2.038924] usbcore: registered new interface driver hiddev
[    2.044195] input: MosArt Optical Mouse as /devices/pci0000:00/0000:00:04.0/usb4/4-6/4-6:1.0/input/input5
[    2.044285] generic-usb 0003:13EE:0003.0001: input,hidraw0: USB HID v1.10 Mouse [MosArt Optical Mouse] on usb-0000:00:04.0-6/input0
[    2.044306] usbcore: registered new interface driver usbhid
[    2.044309] usbhid: v2.6:USB HID core driver
[    2.349782] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.349788] EXT4-fs (sda1): write access will be enabled during recovery
[    2.370018] usb 3-6: new full speed USB device using ohci_hcd and address 2
[    2.607124] usb 3-6: configuration #1 chosen from 1 choice
[    2.680189] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0001d4d60f]
[    2.834783] EXT4-fs (sda1): orphan cleanup on readonly fs
[    2.834793] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 20474716
[    2.834874] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 20473449
[    2.834910] EXT4-fs (sda1): 2 orphan inodes deleted
[    2.834913] EXT4-fs (sda1): recovery complete
[    3.235374] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    7.656390] udev: starting version 151
[    7.699375] Adding 19803128k swap on /dev/sda5.  Priority:-1 extents:1 across:19803128k 
[    7.736747] lp: driver loaded but no devices found
[    7.748915] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[    7.748922] ACPI: resource nForce2_smbus [0x1c40-0x1c7f] conflicts with ACPI region SM00 [0x001c40-0x001c7f]
[    7.748924] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    7.748927] nForce2_smbus 0000:00:01.1: Error probing SMB2.
[    7.767064] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    7.808163] nvidia: module license 'NVIDIA' taints kernel.
[    7.808167] Disabling lock debugging due to kernel taint
[    7.819951] type=1505 audit(1279551680.084:2):  operation="profile_load" pid=817 name="/sbin/dhclient3"
[    7.820203] type=1505 audit(1279551680.094:3):  operation="profile_load" pid=817 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    7.820343] type=1505 audit(1279551680.094:4):  operation="profile_load" pid=817 name="/usr/lib/connman/scripts/dhclient-script"
[    7.904549] type=1505 audit(1279551680.174:5):  operation="profile_load" pid=937 name="/usr/share/gdm/guest-session/Xsession"
[    7.905929] type=1505 audit(1279551680.174:6):  operation="profile_replace" pid=938 name="/sbin/dhclient3"
[    7.906194] type=1505 audit(1279551680.174:7):  operation="profile_replace" pid=938 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    7.906342] type=1505 audit(1279551680.174:8):  operation="profile_replace" pid=938 name="/usr/lib/connman/scripts/dhclient-script"
[    7.926623]   alloc irq_desc for 29 on node 0
[    7.926626]   alloc kstat_irqs on node 0
[    7.926636] forcedeth 0000:00:0a.0: irq 29 for MSI/MSI-X
[    8.010088] type=1505 audit(1279551680.284:9):  operation="profile_load" pid=939 name="/usr/bin/evince"
[    8.013415] type=1505 audit(1279551680.284:10):  operation="profile_load" pid=939 name="/usr/bin/evince-previewer"
[    8.015416] type=1505 audit(1279551680.284:11):  operation="profile_load" pid=939 name="/usr/bin/evince-thumbnailer"
[    8.210952] EDAC MC: Ver: 2.1.0 Jun 11 2010
[    8.221879] usbcore: registered new interface driver usbserial
[    8.221897] USB Serial support registered for generic
[    8.221924] usbcore: registered new interface driver usbserial_generic
[    8.221926] usbserial: USB Serial Driver core
[    8.225111] EDAC amd64_edac:  Ver: 3.2.0 Jun 11 2010
[    8.225484] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[    8.225495] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    8.225496]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    8.225497]  (Note that use of the override may cause unknown side effects.)
[    8.225511] amd64_edac: probe of 0000:00:18.2 failed with error -22
[    8.300427] USB Serial support registered for pl2303
[    8.300611] pl2303 3-6:1.0: pl2303 converter detected
[    8.307235] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[    8.307243] HDA Intel 0000:00:07.0: PCI INT A -> Link[AAZA] -> GSI 21 (level, low) -> IRQ 21
[    8.307247] hda_intel: Disable MSI for Nvidia chipset
[    8.307366] HDA Intel 0000:00:07.0: setting latency timer to 64
[    8.332039] usb 3-6: pl2303 converter now attached to ttyUSB0
[    8.332059] usbcore: registered new interface driver pl2303
[    8.332061] pl2303: Prolific PL2303 USB to serial adaptor driver
[    8.370651] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[    8.370657]   alloc irq_desc for 18 on node 0
[    8.370659]   alloc kstat_irqs on node 0
[    8.370670] CA0106 0000:01:0b.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[    8.370702] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102
[    8.456728] nvidia 0000:02:00.0: enabling device (0000 -> 0003)
[    8.457179] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 20
[    8.457185] nvidia 0000:02:00.0: PCI INT A -> Link[AIGP] -> GSI 20 (level, low) -> IRQ 20
[    8.457193] nvidia 0000:02:00.0: setting latency timer to 64
[    8.457198] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=none
[    8.457407] nvidia 0000:03:00.0: PCI INT A -> Link[AE0A] -> GSI 16 (level, low) -> IRQ 16
[    8.457412] nvidia 0000:03:00.0: setting latency timer to 64
[    8.457415] vgaarb: device changed decodes: PCI:0000:03:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    8.457567] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
[    8.549187] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[    8.549191] vboxdrv: Successfully done.
[    8.549194] vboxdrv: Found 4 processor cores.
[    8.549321] VBoxDrv: dbg - g_abExecMemory=ffffffffa0d7ac60
[    8.549398] vboxdrv: fAsync=0 offMin=0x547 offMax=0x2437
[    8.549721] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[    8.549723] vboxdrv: Successfully loaded version 3.2.4 (interface 0x00140001).
[   11.354395] ppdev: user-space parallel port driver
[   12.210092] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:07.0/input/input6
[   18.491255] eth0: no IPv6 routers present
[   21.105861] hda-intel: spurious response 0x10de0101:0x3, last cmd=0x304f0d00
[   33.022529] Intel AES-NI instructions are not detected.
[   33.110572] padlock: VIA PadLock not detected.
[   36.801223] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   44.060867] ISO 9660 Extensions: Microsoft Joliet Level 3
[   44.099485] ISOFS: changing to secondary root
[  489.931747] __ratelimit: 9 callbacks suppressed
[  489.931753] npviewer.bin[1851]: segfault at 418 ip 00000000f60e0a56 sp 00000000fff42268 error 6 in libflashplayer.so[f5e92000+b04000]
[  705.669617] npviewer.bin[2016]: segfault at 418 ip 00000000f6030a56 sp 00000000ffad9798 error 6 in libflashplayer.so[f5de2000+b04000]
[  715.083732] npviewer.bin[2220]: segfault at 418 ip 00000000f60baa56 sp 00000000ff9edf58 error 6 in libflashplayer.so[f5e6c000+b04000]
[ 6673.891949] npviewer.bin[2259]: segfault at 418 ip 00000000f60dda56 sp 00000000ff876488 error 6 in libflashplayer.so[f5e8f000+b04000]
[11592.019850] hub 4-0:1.0: port 6 disabled by hub (EMI?), re-enabling...
[11592.019857] usb 4-6: USB disconnect, address 2
[11592.539709] usb 4-6: new low speed USB device using ohci_hcd and address 3
[11592.774936] usb 4-6: configuration #1 chosen from 1 choice
[11592.785001] input: MosArt Optical Mouse as /devices/pci0000:00/0000:00:04.0/usb4/4-6/4-6:1.0/input/input7
[11592.785098] generic-usb 0003:13EE:0003.0002: input,hidraw0: USB HID v1.10 Mouse [MosArt Optical Mouse] on usb-0000:00:04.0-6/input0
[13611.857879] npviewer.bin[2637]: segfault at f334d04c ip 00000000f6178057 sp 00000000ff890d00 error 4 in libflashplayer.so[f5dd9000+b04000]
[15433.419045] usb 3-6: USB disconnect, address 2
[15433.419270] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[15433.419290] pl2303 3-6:1.0: device disconnected
[15519.760011] usb 3-6: new full speed USB device using ohci_hcd and address 3
[15519.987107] usb 3-6: configuration #1 chosen from 1 choice
[15519.990281] pl2303 3-6:1.0: pl2303 converter detected
[15520.023085] usb 3-6: pl2303 converter now attached to ttyUSB0

---

### Post by Neliel on 2010-07-19
and here is the dmesg with the servo controller attached, (different device from the original) and i have no idea if this one is working or not


[    0.960988] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.960991] system 00:0c: iomem range 0x100000-0xafedffff could not be reserved
[    0.960993] system 00:0c: iomem range 0xafff0000-0xbffeffff could not be reserved
[    0.960996] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.960999] system 00:0c: iomem range 0xfee00000-0xfeefffff has been reserved
[    0.961001] system 00:0c: iomem range 0xfefff000-0xfeffffff has been reserved
[    0.961004] system 00:0c: iomem range 0xfff80000-0xfff80fff has been reserved
[    0.961007] system 00:0c: iomem range 0xfff90000-0xfffbffff has been reserved
[    0.961009] system 00:0c: iomem range 0xfffed000-0xfffeffff has been reserved
[    0.965816] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.965819] pci 0000:00:08.0:   IO window: 0xe000-0xefff
[    0.965823] pci 0000:00:08.0:   MEM window: 0xfde00000-0xfdefffff
[    0.965826] pci 0000:00:08.0:   PREFETCH window: 0xfdd00000-0xfddfffff
[    0.965834] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
[    0.965836] pci 0000:00:0b.0:   IO window: 0xd000-0xdfff
[    0.965839] pci 0000:00:0b.0:   MEM window: 0xfb000000-0xfcffffff
[    0.965842] pci 0000:00:0b.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.965846] pci 0000:00:10.0: PCI bridge, secondary bus 0000:03
[    0.965850] pci 0000:00:10.0:   IO window: 0xc000-0xcfff
[    0.965860] pci 0000:00:10.0:   MEM window: 0xf6000000-0xf9ffffff
[    0.965867] pci 0000:00:10.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.965879] pci 0000:00:12.0: PCI bridge, secondary bus 0000:04
[    0.965884] pci 0000:00:12.0:   IO window: 0xb000-0xbfff
[    0.965893] pci 0000:00:12.0:   MEM window: 0xfdc00000-0xfdcfffff
[    0.965900] pci 0000:00:12.0:   PREFETCH window: 0x000000fdb00000-0x000000fdbfffff
[    0.965913] pci 0000:00:13.0: PCI bridge, secondary bus 0000:05
[    0.965917] pci 0000:00:13.0:   IO window: 0xa000-0xafff
[    0.965927] pci 0000:00:13.0:   MEM window: 0xfda00000-0xfdafffff
[    0.965934] pci 0000:00:13.0:   PREFETCH window: 0x000000fd900000-0x000000fd9fffff
[    0.965946] pci 0000:00:14.0: PCI bridge, secondary bus 0000:06
[    0.965951] pci 0000:00:14.0:   IO window: 0x9000-0x9fff
[    0.965960] pci 0000:00:14.0:   MEM window: 0xfd800000-0xfd8fffff
[    0.965968] pci 0000:00:14.0:   PREFETCH window: 0x000000fd700000-0x000000fd7fffff
[    0.965986] pci 0000:00:08.0: setting latency timer to 64
[    0.965992] pci 0000:00:0b.0: setting latency timer to 64
[    0.966411] ACPI: PCI Interrupt Link [AE0A] enabled at IRQ 16
[    0.966415]   alloc irq_desc for 16 on node 0
[    0.966417]   alloc kstat_irqs on node 0
[    0.966426] pci 0000:00:10.0: PCI INT A -> Link[AE0A] -> GSI 16 (level, low) -> IRQ 16
[    0.966434] pci 0000:00:10.0: setting latency timer to 64
[    0.966829] ACPI: PCI Interrupt Link [AE2A] enabled at IRQ 16
[    0.966836] pci 0000:00:12.0: PCI INT A -> Link[AE2A] -> GSI 16 (level, low) -> IRQ 16
[    0.966844] pci 0000:00:12.0: setting latency timer to 64
[    0.967242] ACPI: PCI Interrupt Link [AE3A] enabled at IRQ 16
[    0.967245] pci 0000:00:13.0: PCI INT A -> Link[AE3A] -> GSI 16 (level, low) -> IRQ 16
[    0.967253] pci 0000:00:13.0: setting latency timer to 64
[    0.967646] ACPI: PCI Interrupt Link [AE4A] enabled at IRQ 16
[    0.967653] pci 0000:00:14.0: PCI INT A -> Link[AE4A] -> GSI 16 (level, low) -> IRQ 16
[    0.967661] pci 0000:00:14.0: setting latency timer to 64
[    0.967667] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.967670] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.967672] pci_bus 0000:01: resource 0 io:  [0xe000-0xefff]
[    0.967675] pci_bus 0000:01: resource 1 mem: [0xfde00000-0xfdefffff]
[    0.967677] pci_bus 0000:01: resource 2 pref mem [0xfdd00000-0xfddfffff]
[    0.967679] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.967681] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.967684] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.967686] pci_bus 0000:02: resource 1 mem: [0xfb000000-0xfcffffff]
[    0.967688] pci_bus 0000:02: resource 2 pref mem [0xe0000000-0xefffffff]
[    0.967690] pci_bus 0000:03: resource 0 io:  [0xc000-0xcfff]
[    0.967692] pci_bus 0000:03: resource 1 mem: [0xf6000000-0xf9ffffff]
[    0.967695] pci_bus 0000:03: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.967697] pci_bus 0000:04: resource 0 io:  [0xb000-0xbfff]
[    0.967699] pci_bus 0000:04: resource 1 mem: [0xfdc00000-0xfdcfffff]
[    0.967701] pci_bus 0000:04: resource 2 pref mem [0xfdb00000-0xfdbfffff]
[    0.967704] pci_bus 0000:05: resource 0 io:  [0xa000-0xafff]
[    0.967706] pci_bus 0000:05: resource 1 mem: [0xfda00000-0xfdafffff]
[    0.967708] pci_bus 0000:05: resource 2 pref mem [0xfd900000-0xfd9fffff]
[    0.967710] pci_bus 0000:06: resource 0 io:  [0x9000-0x9fff]
[    0.967712] pci_bus 0000:06: resource 1 mem: [0xfd800000-0xfd8fffff]
[    0.967715] pci_bus 0000:06: resource 2 pref mem [0xfd700000-0xfd7fffff]
[    0.967756] NET: Registered protocol family 2
[    0.968019] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.969600] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.972694] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.973066] TCP: Hash tables configured (established 524288 bind 65536)
[    0.973069] TCP reno registered
[    0.973172] NET: Registered protocol family 1
[    1.029819] pci 0000:00:07.0: Enabling HT MSI Mapping
[    1.029921] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.030026] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.030137] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.030247] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    1.030489] pci 0000:03:00.0: Boot video device
[    1.030758] PCI-DMA: Disabling AGP.
[    1.030856] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    1.030858] PCI-DMA: using GART IOMMU.
[    1.030862] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    1.032584] Scanning for low memory corruption every 60 seconds
[    1.032704] audit: initializing netlink socket (disabled)
[    1.032716] type=2000 audit(1279537272.029:1): initialized
[    1.041227] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.042658] VFS: Disk quotas dquot_6.5.2
[    1.042709] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.043329] fuse init (API version 7.13)
[    1.043410] msgmni has been set to 15498
[    1.043662] alg: No test for stdrng (krng)
[    1.043720] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.043723] io scheduler noop registered
[    1.043725] io scheduler anticipatory registered
[    1.043726] io scheduler deadline registered
[    1.043760] io scheduler cfq registered (default)
[    1.044146]   alloc irq_desc for 24 on node 0
[    1.044148]   alloc kstat_irqs on node 0
[    1.044168] pcieport 0000:00:10.0: irq 24 for MSI/MSI-X
[    1.044188] pcieport 0000:00:10.0: setting latency timer to 64
[    1.044581]   alloc irq_desc for 25 on node 0
[    1.044583]   alloc kstat_irqs on node 0
[    1.044599] pcieport 0000:00:12.0: irq 25 for MSI/MSI-X
[    1.044617] pcieport 0000:00:12.0: setting latency timer to 64
[    1.044997]   alloc irq_desc for 26 on node 0
[    1.044999]   alloc kstat_irqs on node 0
[    1.045014] pcieport 0000:00:13.0: irq 26 for MSI/MSI-X
[    1.045032] pcieport 0000:00:13.0: setting latency timer to 64
[    1.045412]   alloc irq_desc for 27 on node 0
[    1.045413]   alloc kstat_irqs on node 0
[    1.045429] pcieport 0000:00:14.0: irq 27 for MSI/MSI-X
[    1.045447] pcieport 0000:00:14.0: setting latency timer to 64
[    1.045599] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.045619] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.045718] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    1.045722] ACPI: Power Button [PWRB]
[    1.045790] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.045792] ACPI: Power Button [PWRF]
[    1.045845] fan PNP0C0B:00: registered as cooling_device0
[    1.045849] ACPI: Fan [FAN] (on)
[    1.046527] processor LNXCPU:00: registered as cooling_device1
[    1.046556] processor LNXCPU:01: registered as cooling_device2
[    1.046583] processor LNXCPU:02: registered as cooling_device3
[    1.046611] processor LNXCPU:03: registered as cooling_device4
[    1.057160] ACPI Warning for \_TZ_.THRM._PSL: Return Package type mismatch at index 0 - found [NULL Object Descriptor], expected Reference (20090903/nspredef-1012)
[    1.057168] ACPI: Expecting a [Reference] package element, found type 0
[    1.057169] ACPI: Invalid passive threshold
[    1.057658] thermal LNXTHERM:01: registered as thermal_zone0
[    1.057665] ACPI: Thermal Zone [THRM] (40 C)
[    1.058872] Linux agpgart interface v0.103
[    1.058904] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.058997] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.059271] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.060160] brd: module loaded
[    1.060558] loop: module loaded
[    1.060625] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.060812] pata_acpi 0000:00:06.0: setting latency timer to 64
[    1.061296] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    1.061300]   alloc irq_desc for 23 on node 0
[    1.061302]   alloc kstat_irqs on node 0
[    1.061311] pata_acpi 0000:00:09.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.061329] pata_acpi 0000:00:09.0: setting latency timer to 64
[    1.061335] pata_acpi 0000:00:09.0: PCI INT A disabled
[    1.061628] Fixed MDIO Bus: probed
[    1.061655] PPP generic driver version 2.4.2
[    1.061691] tun: Universal TUN/TAP device driver, 1.6
[    1.061693] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.061764] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.062198] ACPI: PCI Interrupt Link [AUB2] enabled at IRQ 22
[    1.062200]   alloc irq_desc for 22 on node 0
[    1.062201]   alloc kstat_irqs on node 0
[    1.062209] ehci_hcd 0000:00:02.1: PCI INT B -> Link[AUB2] -> GSI 22 (level, low) -> IRQ 22
[    1.062227] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    1.062230] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    1.062259] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    1.062285] ehci_hcd 0000:00:02.1: debug port 1
[    1.062293] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    1.062314] ehci_hcd 0000:00:02.1: irq 22, io mem 0xfe02e000
[    1.080027] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    1.080095] usb usb1: configuration #1 chosen from 1 choice
[    1.080122] hub 1-0:1.0: USB hub found
[    1.080128] hub 1-0:1.0: 6 ports detected
[    1.080454] ACPI: PCI Interrupt Link [AU2B] disabled and referenced, BIOS bug
[    1.080607] ACPI: PCI Interrupt Link [AU2B] enabled at IRQ 21
[    1.080615]   alloc irq_desc for 21 on node 0
[    1.080616]   alloc kstat_irqs on node 0
[    1.080623] ehci_hcd 0000:00:04.1: PCI INT B -> Link[AU2B] -> GSI 21 (level, low) -> IRQ 21
[    1.080632] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    1.080635] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    1.080661] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    1.080679] ehci_hcd 0000:00:04.1: debug port 1
[    1.080686] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    1.080701] ehci_hcd 0000:00:04.1: irq 21, io mem 0xfe02c000
[    1.100019] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    1.100081] usb usb2: configuration #1 chosen from 1 choice
[    1.100101] hub 2-0:1.0: USB hub found
[    1.100106] hub 2-0:1.0: 6 ports detected
[    1.100164] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.100593] ACPI: PCI Interrupt Link [AUBA] enabled at IRQ 20
[    1.100595]   alloc irq_desc for 20 on node 0
[    1.100597]   alloc kstat_irqs on node 0
[    1.100604] ohci_hcd 0000:00:02.0: PCI INT A -> Link[AUBA] -> GSI 20 (level, low) -> IRQ 20
[    1.100615] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    1.100618] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    1.100644] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    1.100664] ohci_hcd 0000:00:02.0: irq 20, io mem 0xfe02f000
[    1.162085] usb usb3: configuration #1 chosen from 1 choice
[    1.162107] hub 3-0:1.0: USB hub found
[    1.162114] hub 3-0:1.0: 6 ports detected
[    1.162576] ACPI: PCI Interrupt Link [AU1B] enabled at IRQ 23
[    1.162579] ohci_hcd 0000:00:04.0: PCI INT A -> Link[AU1B] -> GSI 23 (level, low) -> IRQ 23
[    1.162589] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    1.162591] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    1.162617] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    1.162640] ohci_hcd 0000:00:04.0: irq 23, io mem 0xfe02d000
[    1.222084] usb usb4: configuration #1 chosen from 1 choice
[    1.222106] hub 4-0:1.0: USB hub found
[    1.222112] hub 4-0:1.0: 6 ports detected
[    1.222165] uhci_hcd: USB Universal Host Controller Interface driver
[    1.222222] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.222224] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.222366] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.222442] mice: PS/2 mouse device common for all mice
[    1.222528] rtc_cmos 00:05: RTC can wake from S4
[    1.222556] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.222615] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.222732] device-mapper: uevent: version 1.0.3
[    1.222826] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    1.222938] device-mapper: multipath: version 1.1.0 loaded
[    1.222940] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.223177] cpuidle: using governor ladder
[    1.223179] cpuidle: using governor menu
[    1.223537] TCP cubic registered
[    1.223668] NET: Registered protocol family 10
[    1.224140] lo: Disabled Privacy Extensions
[    1.224436] NET: Registered protocol family 17
[    1.224474] powernow-k8: Found 1 AMD Phenom(tm) 9500 Quad-Core Processor processors (4 cpu cores) (version 2.20.00)
[    1.224482] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    1.224483] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
[    1.224567] PM: Resume from disk failed.
[    1.224577] registered taskstats version 1
[    1.225187]   Magic number: 2:560:24
[    1.225190] misc cpu_dma_latency: hash matches
[    1.225319] rtc_cmos 00:05: setting system clock to 2010-07-19 11:01:13 UTC (1279537273)
[    1.225322] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.225323] EDD information not available.
[    1.225371] Freeing unused kernel memory: 880k freed
[    1.225667] Write protecting the kernel read-only data: 7692k
[    1.242811] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.243245] udev: starting version 151
[    1.265606] vga16fb: initializing
[    1.265610] vga16fb: mapped to 0xffff8800000a0000
[    1.265666] fb0: VGA16 VGA frame buffer device
[    1.272819] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.273315] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 22
[    1.273322] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
[    1.273327] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.296875] [Firmware Bug]: ACPI(IGPU) defines _DOD but not _DOS
[    1.297154] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0f/LNXVIDEO:00/input/input4
[    1.297204] ACPI: Video Device [IGPU] (multi-head: yes  rom: no  post: no)
[    1.301961] Floppy drive(s): fd0 is 1.44M
[    1.302592] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    1.302599]   alloc irq_desc for 19 on node 0
[    1.302601]   alloc kstat_irqs on node 0
[    1.302613] ohci1394 0000:01:0a.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    1.326734] FDC 0 is a post-1991 82077
[    1.351310] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 3, addr 00:24:8c:69:e4:ba
[    1.351314] forcedeth 0000:00:0a.0: highdma csum pwrctl mgmt gbit lnktim msi desc-v3
[    1.351457] pata_amd 0000:00:06.0: version 0.4.1
[    1.351499] pata_amd 0000:00:06.0: setting latency timer to 64
[    1.351637] scsi0 : pata_amd
[    1.351751] scsi1 : pata_amd
[    1.352556] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    1.352559] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
[    1.352651] ahci 0000:00:09.0: version 3.0
[    1.352661] ahci 0000:00:09.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.352722]   alloc irq_desc for 28 on node 0
[    1.352724]   alloc kstat_irqs on node 0
[    1.352732] ahci 0000:00:09.0: irq 28 for MSI/MSI-X
[    1.352792] ahci 0000:00:09.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl IDE mode
[    1.352795] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio boh 
[    1.352798] ahci 0000:00:09.0: setting latency timer to 64
[    1.353186] scsi2 : ahci
[    1.353268] scsi3 : ahci
[    1.353325] scsi4 : ahci
[    1.353382] scsi5 : ahci
[    1.353441] scsi6 : ahci
[    1.353500] scsi7 : ahci
[    1.353662] ata3: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026100 irq 28
[    1.353665] ata4: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026180 irq 28
[    1.353667] ata5: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026200 irq 28
[    1.353669] ata6: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026280 irq 28
[    1.353671] ata7: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026300 irq 28
[    1.353673] ata8: SATA max UDMA/133 abar m8192@0xfe026000 port 0xfe026380 irq 28
[    1.362071] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[fdeff000-fdeff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    1.502290] Console: switching to colour frame buffer device 80x30
[    1.530352] ata1.00: ATAPI: SONY    DVD RW DRU-V200A, 1.60, max UDMA/66
[    1.530382] ata1: nv_mode_filter: 0x1f39f&0x1f39f->0x1f39f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)
[    1.570293] ata1.00: configured for UDMA/66
[    1.572839] scsi 0:0:0:0: CD-ROM            SONY     DVD RW DRU-V200A 1.60 PQ: 0 ANSI: 5
[    1.575439] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.575441] Uniform CD-ROM driver Revision: 3.20
[    1.575543] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.575603] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.575681] ata2: port disabled. ignoring.
[    1.700023] ata7: SATA link down (SStatus 0 SControl 300)
[    1.700050] ata4: SATA link down (SStatus 0 SControl 300)
[    1.700055] ata6: SATA link down (SStatus 0 SControl 300)
[    1.700070] ata5: SATA link down (SStatus 0 SControl 300)
[    1.700077] ata8: SATA link down (SStatus 0 SControl 300)
[    1.800019] usb 4-6: new low speed USB device using ohci_hcd and address 2
[    1.880019] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.889164] ata3.00: ATA-8: WDC WD5000AAJS-00A8B2, 01.03B01, max UDMA/133
[    1.889167] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.890692] ata3.00: configured for UDMA/133
[    1.890779] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000AAJS-0 01.0 PQ: 0 ANSI: 5
[    1.890932] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.890955] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.890967] sd 2:0:0:0: [sda] Write Protect is off
[    1.890970] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.890989] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.891121]  sda: sda1 sda2 < sda5 >
[    1.920123] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.027111] usb 4-6: configuration #1 chosen from 1 choice
[    2.038924] usbcore: registered new interface driver hiddev
[    2.044195] input: MosArt Optical Mouse as /devices/pci0000:00/0000:00:04.0/usb4/4-6/4-6:1.0/input/input5
[    2.044285] generic-usb 0003:13EE:0003.0001: input,hidraw0: USB HID v1.10 Mouse [MosArt Optical Mouse] on usb-0000:00:04.0-6/input0
[    2.044306] usbcore: registered new interface driver usbhid
[    2.044309] usbhid: v2.6:USB HID core driver
[    2.349782] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.349788] EXT4-fs (sda1): write access will be enabled during recovery
[    2.370018] usb 3-6: new full speed USB device using ohci_hcd and address 2
[    2.607124] usb 3-6: configuration #1 chosen from 1 choice
[    2.680189] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0001d4d60f]
[    2.834783] EXT4-fs (sda1): orphan cleanup on readonly fs
[    2.834793] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 20474716
[    2.834874] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 20473449
[    2.834910] EXT4-fs (sda1): 2 orphan inodes deleted
[    2.834913] EXT4-fs (sda1): recovery complete
[    3.235374] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    7.656390] udev: starting version 151
[    7.699375] Adding 19803128k swap on /dev/sda5.  Priority:-1 extents:1 across:19803128k 
[    7.736747] lp: driver loaded but no devices found
[    7.748915] i2c i2c-0: nForce2 SMBus adapter at 0x1c00
[    7.748922] ACPI: resource nForce2_smbus [0x1c40-0x1c7f] conflicts with ACPI region SM00 [0x001c40-0x001c7f]
[    7.748924] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    7.748927] nForce2_smbus 0000:00:01.1: Error probing SMB2.
[    7.767064] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    7.808163] nvidia: module license 'NVIDIA' taints kernel.
[    7.808167] Disabling lock debugging due to kernel taint
[    7.819951] type=1505 audit(1279551680.084:2):  operation="profile_load" pid=817 name="/sbin/dhclient3"
[    7.820203] type=1505 audit(1279551680.094:3):  operation="profile_load" pid=817 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    7.820343] type=1505 audit(1279551680.094:4):  operation="profile_load" pid=817 name="/usr/lib/connman/scripts/dhclient-script"
[    7.904549] type=1505 audit(1279551680.174:5):  operation="profile_load" pid=937 name="/usr/share/gdm/guest-session/Xsession"
[    7.905929] type=1505 audit(1279551680.174:6):  operation="profile_replace" pid=938 name="/sbin/dhclient3"
[    7.906194] type=1505 audit(1279551680.174:7):  operation="profile_replace" pid=938 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    7.906342] type=1505 audit(1279551680.174:8):  operation="profile_replace" pid=938 name="/usr/lib/connman/scripts/dhclient-script"
[    7.926623]   alloc irq_desc for 29 on node 0
[    7.926626]   alloc kstat_irqs on node 0
[    7.926636] forcedeth 0000:00:0a.0: irq 29 for MSI/MSI-X
[    8.010088] type=1505 audit(1279551680.284:9):  operation="profile_load" pid=939 name="/usr/bin/evince"
[    8.013415] type=1505 audit(1279551680.284:10):  operation="profile_load" pid=939 name="/usr/bin/evince-previewer"
[    8.015416] type=1505 audit(1279551680.284:11):  operation="profile_load" pid=939 name="/usr/bin/evince-thumbnailer"
[    8.210952] EDAC MC: Ver: 2.1.0 Jun 11 2010
[    8.221879] usbcore: registered new interface driver usbserial
[    8.221897] USB Serial support registered for generic
[    8.221924] usbcore: registered new interface driver usbserial_generic
[    8.221926] usbserial: USB Serial Driver core
[    8.225111] EDAC amd64_edac:  Ver: 3.2.0 Jun 11 2010
[    8.225484] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[    8.225495] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    8.225496]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    8.225497]  (Note that use of the override may cause unknown side effects.)
[    8.225511] amd64_edac: probe of 0000:00:18.2 failed with error -22
[    8.300427] USB Serial support registered for pl2303
[    8.300611] pl2303 3-6:1.0: pl2303 converter detected
[    8.307235] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[    8.307243] HDA Intel 0000:00:07.0: PCI INT A -> Link[AAZA] -> GSI 21 (level, low) -> IRQ 21
[    8.307247] hda_intel: Disable MSI for Nvidia chipset
[    8.307366] HDA Intel 0000:00:07.0: setting latency timer to 64
[    8.332039] usb 3-6: pl2303 converter now attached to ttyUSB0
[    8.332059] usbcore: registered new interface driver pl2303
[    8.332061] pl2303: Prolific PL2303 USB to serial adaptor driver
[    8.370651] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[    8.370657]   alloc irq_desc for 18 on node 0
[    8.370659]   alloc kstat_irqs on node 0
[    8.370670] CA0106 0000:01:0b.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[    8.370702] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102
[    8.456728] nvidia 0000:02:00.0: enabling device (0000 -> 0003)
[    8.457179] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 20
[    8.457185] nvidia 0000:02:00.0: PCI INT A -> Link[AIGP] -> GSI 20 (level, low) -> IRQ 20
[    8.457193] nvidia 0000:02:00.0: setting latency timer to 64
[    8.457198] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=none
[    8.457407] nvidia 0000:03:00.0: PCI INT A -> Link[AE0A] -> GSI 16 (level, low) -> IRQ 16
[    8.457412] nvidia 0000:03:00.0: setting latency timer to 64
[    8.457415] vgaarb: device changed decodes: PCI:0000:03:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    8.457567] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
[    8.549187] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[    8.549191] vboxdrv: Successfully done.
[    8.549194] vboxdrv: Found 4 processor cores.
[    8.549321] VBoxDrv: dbg - g_abExecMemory=ffffffffa0d7ac60
[    8.549398] vboxdrv: fAsync=0 offMin=0x547 offMax=0x2437
[    8.549721] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[    8.549723] vboxdrv: Successfully loaded version 3.2.4 (interface 0x00140001).
[   11.354395] ppdev: user-space parallel port driver
[   12.210092] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:07.0/input/input6
[   18.491255] eth0: no IPv6 routers present
[   21.105861] hda-intel: spurious response 0x10de0101:0x3, last cmd=0x304f0d00
[   33.022529] Intel AES-NI instructions are not detected.
[   33.110572] padlock: VIA PadLock not detected.
[   36.801223] hda-intel: spurious response 0x0:0x0, last cmd=0x870600
[   44.060867] ISO 9660 Extensions: Microsoft Joliet Level 3
[   44.099485] ISOFS: changing to secondary root
[  489.931747] __ratelimit: 9 callbacks suppressed
[  489.931753] npviewer.bin[1851]: segfault at 418 ip 00000000f60e0a56 sp 00000000fff42268 error 6 in libflashplayer.so[f5e92000+b04000]
[  705.669617] npviewer.bin[2016]: segfault at 418 ip 00000000f6030a56 sp 00000000ffad9798 error 6 in libflashplayer.so[f5de2000+b04000]
[  715.083732] npviewer.bin[2220]: segfault at 418 ip 00000000f60baa56 sp 00000000ff9edf58 error 6 in libflashplayer.so[f5e6c000+b04000]
[ 6673.891949] npviewer.bin[2259]: segfault at 418 ip 00000000f60dda56 sp 00000000ff876488 error 6 in libflashplayer.so[f5e8f000+b04000]
[11592.019850] hub 4-0:1.0: port 6 disabled by hub (EMI?), re-enabling...
[11592.019857] usb 4-6: USB disconnect, address 2
[11592.539709] usb 4-6: new low speed USB device using ohci_hcd and address 3
[11592.774936] usb 4-6: configuration #1 chosen from 1 choice
[11592.785001] input: MosArt Optical Mouse as /devices/pci0000:00/0000:00:04.0/usb4/4-6/4-6:1.0/input/input7
[11592.785098] generic-usb 0003:13EE:0003.0002: input,hidraw0: USB HID v1.10 Mouse [MosArt Optical Mouse] on usb-0000:00:04.0-6/input0
[13611.857879] npviewer.bin[2637]: segfault at f334d04c ip 00000000f6178057 sp 00000000ff890d00 error 4 in libflashplayer.so[f5dd9000+b04000]
[15433.419045] usb 3-6: USB disconnect, address 2
[15433.419270] pl2303 ttyUSB0: pl2303 converter now disconnected from ttyUSB0
[15433.419290] pl2303 3-6:1.0: device disconnected
[15519.760011] usb 3-6: new full speed USB device using ohci_hcd and address 3
[15519.987107] usb 3-6: configuration #1 chosen from 1 choice
[15519.990281] pl2303 3-6:1.0: pl2303 converter detected
[15520.023085] usb 3-6: pl2303 converter now attached to ttyUSB0

---

### Post by davidmohammed on 2010-07-20
thats good news - your adapter is working fine without any errors (the trace indicates its mapped as ttyUSB0).

I would suggest you first look at something like minicom (command line interface to read your serial port) or cutecom (gui based version of minicom).

---

