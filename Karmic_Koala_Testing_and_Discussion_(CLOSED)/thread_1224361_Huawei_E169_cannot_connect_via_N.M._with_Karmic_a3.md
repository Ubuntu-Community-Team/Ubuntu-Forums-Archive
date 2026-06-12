---
title: "Huawei E169 cannot connect via N.M. with Karmic a3+kernel 2.6.31-4"
date: 2009-07-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by GeorgeVita on 2009-07-27
**UPDATE:** Solved (E169 can connect) using kernel **2.6.31-999-generic #1248771614** and recent updates!
**********

Hi,
I have Ubuntu 9.10 Alpha 3 installation (clean, single boot, HD formatted to ext4) to my Asus EeePC1000H, fully updated one hour ago, kernel is **2.6.31-4.22**

After the update I cannot connect with Huawei E169 3G mobile broadband modem (with Network Manager 0.7.1).

**Below is part of daemon.log with NO connection (pppd timeout)**
```
Jul 27 16:49:50 KKa3 NetworkManager: <info>  (ttyUSB1): ignoring due to lack of mobile broadband capabilties
Jul 27 16:49:50 KKa3 NetworkManager: <info>  (ttyUSB2): ignoring due to lack of mobile broadband capabilties
Jul 27 16:49:51 KKa3 nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/usb_device_12d1_1001________________________________________if0_serial_usb_0, iface: (null)): iface not found
Jul 27 16:49:51 KKa3 NetworkManager: <info>  (ttyUSB0): found serial port (udev:GSM  hal:GSM)
Jul 27 16:49:51 KKa3 NetworkManager: <info>  (ttyUSB0): new Modem device (driver: 'option')
Jul 27 16:49:51 KKa3 NetworkManager: <info>  (ttyUSB0): exported as /org/freedesktop/Hal/devices/usb_device_12d1_1001________________________________________if0_serial_usb_0
Jul 27 16:49:55 KKa3 NetworkManager: <info>  (ttyUSB0): device state change: 1 -> 2
Jul 27 16:49:55 KKa3 NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 2).
Jul 27 16:49:55 KKa3 NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Jul 27 16:49:55 KKa3 NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
Jul 27 16:49:55 KKa3 NetworkManager: <info>  (ttyUSB0): device state change: 2 -> 3
Jul 27 16:49:59 KKa3 NetworkManager: <info>  Activation (ttyUSB0) starting connection 'TIM'
Jul 27 16:49:59 KKa3 NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4
Jul 27 16:49:59 KKa3 NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 27 16:49:59 KKa3 NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Jul 27 16:49:59 KKa3 NetworkManager: <debug> [1248702599.604089] nm_serial_device_open(): (ttyUSB0) opening device...
Jul 27 16:49:59 KKa3 NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Jul 27 16:49:59 KKa3 NetworkManager: <info>  (ttyUSB0): powering up...
Jul 27 16:50:03 KKa3 NetworkManager: <info>  Registered on Home network
Jul 27 16:50:03 KKa3 NetworkManager: <info>  Associated with network: +COPS: 0,2,"20210",2
Jul 27 16:50:03 KKa3 NetworkManager: <info>  Connected, Woo!
Jul 27 16:50:03 KKa3 NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled...
Jul 27 16:50:03 KKa3 NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting...
Jul 27 16:50:03 KKa3 NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 5
Jul 27 16:50:03 KKa3 NetworkManager: <info>  Starting pppd connection
Jul 27 16:50:03 KKa3 NetworkManager: <debug> [1248702603.286672] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute user web ttyUSB0 noipdefault noauth refuse-eap refuse-mschap refuse-mschap-v2 usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/0 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so
Jul 27 16:50:03 KKa3 NetworkManager: <debug> [1248702603.323171] nm_ppp_manager_start(): ppp started with pid 3134
Jul 27 16:50:03 KKa3 NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete.
Jul 27 16:50:19 KKa3 NetworkManager: <WARN>  pppd_timed_out(): Looks like pppd didn't initialize our dbus module
Jul 27 16:50:19 KKa3 NetworkManager: <info>  (ttyUSB0): device state change: 5 -> 9
Jul 27 16:50:19 KKa3 NetworkManager: <debug> [1248702619.001549] nm_serial_device_close(): Closing device 'ttyUSB0'
Jul 27 16:50:19 KKa3 NetworkManager: <info>  Marking connection 'TIM' invalid.
Jul 27 16:50:19 KKa3 NetworkManager: <info>  Activation (ttyUSB0) failed.
Jul 27 16:50:19 KKa3 NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3
Jul 27 16:50:19 KKa3 NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0).
Jul 27 16:50:19 KKa3 NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Jul 27 16:50:19 KKa3 NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
Jul 27 16:50:21 KKa3 NetworkManager: <debug> [1248702621.000927] ensure_killed(): waiting for ppp pid 3134 to exit
Jul 27 16:50:21 KKa3 NetworkManager: <debug> [1248702621.001175] ensure_killed(): ppp pid 3134 cleaned up
Jul 27 16:50:24 KKa3 NetworkManager: <info>  Activation (ttyUSB0) starting connection 'TIM'
Jul 27 16:50:24 KKa3 NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4
Jul 27 16:50:24 KKa3 NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 27 16:50:24 KKa3 NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Jul 27 16:50:24 KKa3 NetworkManager: <debug> [1248702624.819134] nm_serial_device_open(): (ttyUSB0) opening device...
Jul 27 16:50:24 KKa3 NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Jul 27 16:50:25 KKa3 NetworkManager: <info>  (ttyUSB0): powering up...
Jul 27 16:50:25 KKa3 NetworkManager: <info>  Registered on Home network
Jul 27 16:50:25 KKa3 NetworkManager: <info>  Associated with network: +COPS: 0,2,"20210",2
Jul 27 16:50:25 KKa3 NetworkManager: <info>  Connected, Woo!
Jul 27 16:50:25 KKa3 NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled...
Jul 27 16:50:25 KKa3 NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting...
Jul 27 16:50:25 KKa3 NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 5
Jul 27 16:50:25 KKa3 NetworkManager: <info>  Starting pppd connection
Jul 27 16:50:25 KKa3 NetworkManager: <debug> [1248702625.292585] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute user web ttyUSB0 noipdefault noauth refuse-eap refuse-mschap refuse-mschap-v2 usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/1 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so
Jul 27 16:50:25 KKa3 NetworkManager: <debug> [1248702625.296816] nm_ppp_manager_start(): ppp started with pid 3164
Jul 27 16:50:25 KKa3 NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete.
Jul 27 16:50:41 KKa3 NetworkManager: <WARN>  pppd_timed_out(): Looks like pppd didn't initialize our dbus module
Jul 27 16:50:41 KKa3 NetworkManager: <info>  (ttyUSB0): device state change: 5 -> 9
Jul 27 16:50:41 KKa3 NetworkManager: <debug> [1248702641.003452] nm_serial_device_close(): Closing device 'ttyUSB0'
Jul 27 16:50:41 KKa3 NetworkManager: <info>  Marking connection 'TIM' invalid.
Jul 27 16:50:41 KKa3 NetworkManager: <info>  Activation (ttyUSB0) failed.
Jul 27 16:50:41 KKa3 NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3
Jul 27 16:50:41 KKa3 NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0).
Jul 27 16:50:41 KKa3 NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Jul 27 16:50:41 KKa3 NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
Jul 27 16:50:43 KKa3 NetworkManager: <debug> [1248702643.001675] ensure_killed(): waiting for ppp pid 3164 to exit
Jul 27 16:50:43 KKa3 NetworkManager: <debug> [1248702643.001900] ensure_killed(): ppp pid 3164 cleaned up

```

Booting kernel **2.6.31-3.19** (included with Alpha3) the connection can be done.

**This is the part of daemon.log showing the connection:**
```
Jul 27 17:06:43 KKa3 wpa_supplicant[2231]: CTRL-EVENT-SCAN-RESULTS 
Jul 27 17:07:13 KKa3 wpa_supplicant[2231]: CTRL-EVENT-SCAN-RESULTS 
Jul 27 17:07:22 KKa3 NetworkManager: <info>  (ttyUSB1): ignoring due to lack of mobile broadband capabilties
Jul 27 17:07:22 KKa3 NetworkManager: <info>  (ttyUSB2): ignoring due to lack of mobile broadband capabilties
Jul 27 17:07:22 KKa3 nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/usb_device_12d1_1001________________________________________if0_serial_usb_0, iface: (null)): iface not found
Jul 27 17:07:22 KKa3 NetworkManager: <info>  (ttyUSB0): found serial port (udev:GSM  hal:GSM)
Jul 27 17:07:22 KKa3 NetworkManager: <info>  (ttyUSB0): new Modem device (driver: 'option')
Jul 27 17:07:22 KKa3 NetworkManager: <info>  (ttyUSB0): exported as /org/freedesktop/Hal/devices/usb_device_12d1_1001________________________________________if0_serial_usb_0
Jul 27 17:07:27 KKa3 NetworkManager: <info>  (ttyUSB0): device state change: 1 -> 2
Jul 27 17:07:27 KKa3 NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 2).
Jul 27 17:07:27 KKa3 NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Jul 27 17:07:27 KKa3 NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
Jul 27 17:07:27 KKa3 NetworkManager: <info>  (ttyUSB0): device state change: 2 -> 3
Jul 27 17:07:35 KKa3 NetworkManager: <info>  (ra0): device state change: 3 -> 2
Jul 27 17:07:35 KKa3 NetworkManager: <info>  (ra0): deactivating device (reason: 0).
Jul 27 17:07:35 KKa3 NetworkManager: <info>  (ra0): taking down device.
Jul 27 17:07:35 KKa3 avahi-daemon[2237]: Withdrawing address record for fe80::222:43ff:fe5d:d5c1 on ra0.
Jul 27 17:07:35 KKa3 wpa_supplicant[2231]: Failed to disable WPA in the driver.
Jul 27 17:08:02 KKa3 NetworkManager: <info>  Activation (ttyUSB0) starting connection 'TIM'
Jul 27 17:08:02 KKa3 NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4
Jul 27 17:08:02 KKa3 NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Jul 27 17:08:02 KKa3 NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Jul 27 17:08:02 KKa3 NetworkManager: <debug> [1248703682.761850] nm_serial_device_open(): (ttyUSB0) opening device...
Jul 27 17:08:02 KKa3 NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Jul 27 17:08:03 KKa3 NetworkManager: <info>  (ttyUSB0): powering up...
Jul 27 17:08:03 KKa3 NetworkManager: <info>  Registered on Home network
Jul 27 17:08:03 KKa3 NetworkManager: <info>  Associated with network: +COPS: 0,2,"20210",2
Jul 27 17:08:03 KKa3 NetworkManager: <info>  Connected, Woo!
Jul 27 17:08:03 KKa3 NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled...
Jul 27 17:08:03 KKa3 NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting...
Jul 27 17:08:03 KKa3 NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 5
Jul 27 17:08:03 KKa3 NetworkManager: <info>  Starting pppd connection
Jul 27 17:08:03 KKa3 NetworkManager: <debug> [1248703683.260928] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute user web ttyUSB0 noipdefault noauth refuse-eap refuse-mschap refuse-mschap-v2 usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/0 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so
Jul 27 17:08:03 KKa3 NetworkManager: <debug> [1248703683.283954] nm_ppp_manager_start(): ppp started with pid 3029
Jul 27 17:08:03 KKa3 NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete.
Jul 27 17:08:03 KKa3 NetworkManager: <info>  (ttyUSB0): device state change: 5 -> 6
Jul 27 17:08:06 KKa3 NetworkManager: <info>  (ttyUSB0): device state change: 6 -> 7
Jul 27 17:08:09 KKa3 NetworkManager: <info>  PPP manager(IP Config Get) reply received.
Jul 27 17:08:09 KKa3 NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP Configure Get) scheduled...
Jul 27 17:08:09 KKa3 NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP Configure Get) started...
Jul 27 17:08:09 KKa3 NetworkManager: <info>  Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jul 27 17:08:09 KKa3 NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP Configure Get) complete.
Jul 27 17:08:09 KKa3 NetworkManager: <info>  Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) started...
Jul 27 17:08:10 KKa3 NetworkManager: <info>  (ttyUSB0): device state change: 7 -> 8
Jul 27 17:08:10 KKa3 NetworkManager: <info>  Policy set 'TIM' (ppp0) as default for routing and DNS.
Jul 27 17:08:10 KKa3 NetworkManager: <info>  Activation (ttyUSB0) successful, device activated.
Jul 27 17:08:10 KKa3 NetworkManager: <info>  Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) complete.
Jul 27 17:08:13 KKa3 ntpdate[3125]: adjust time server 91.189.94.4 offset -0.101954 sec

```
Does anybody used the recent kernel with any Huawei 3G modem?

Regards,
George

P.S. I cannot post any 'bug' report due to TimeOut errors at Launchpad (Error ID: OOPS-1304B1453)

---

### Post by taavikko on 2009-07-27
Just tested with huawei E160E

```
[   69.324112] usb 2-3: new high speed USB device using ehci_hcd and address 3
[   69.468047] usb 2-3: configuration #1 chosen from 1 choice
[   69.528516] Initializing USB Mass Storage driver...
[   69.529260] usbcore: registered new interface driver usb-storage
[   69.529429] USB Mass Storage support registered.
[   69.531443] usb 2-3: USB disconnect, address 3
[   76.812104] usb 2-3: new high speed USB device using ehci_hcd and address 4
[   76.956218] usb 2-3: configuration #1 chosen from 1 choice
[   77.006842] usbcore: registered new interface driver usbserial
[   77.006878] USB Serial support registered for generic
[   77.007044] usbcore: registered new interface driver usbserial_generic
[   77.007049] usbserial: USB Serial Driver core
[   77.024265] USB Serial support registered for GSM modem (1-port)
[   77.024410] option 2-3:1.0: GSM modem (1-port) converter detected
[   77.024520] usb 2-3: GSM modem (1-port) converter now attached to ttyUSB0
[   77.024520] option 2-3:1.1: GSM modem (1-port) converter detected
[   77.024520] usb 2-3: GSM modem (1-port) converter now attached to ttyUSB1
[   77.024520] usbcore: registered new interface driver option
[   77.024520] option: v0.7.2:USB Driver for GSM modems
[  104.602669] ------------[ cut here ]------------
[  104.602721] WARNING: at /build/buildd/linux-2.6.31/drivers/usb/serial/usb-serial.c:436 serial_ioctl+0xb5/0xc0 [usbserial]()
[  104.602736] Hardware name: HP Pavilion dv5 Notebook PC
[  104.602744] Modules linked in: option usbserial usb_storage cryptd aes_x86_64 aes_generic binfmt_misc bridge stp bnep lp parport snd_hda_codec_atihdmi snd_hda_codec_idt snd_hda_intel snd_pcm_oss arc4 snd_hda_codec snd_mixer_oss ecb snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi ath9k snd_rawmidi snd_seq_midi_event uvcvideo mac80211 videodev snd_seq sdhci_pci snd_timer v4l1_compat sdhci snd_seq_device joydev ath v4l2_compat_ioctl32 radeon psmouse hp_accel snd lis3lv02d ttm btusb amd64_edac_mod soundcore edac_core input_polldev serio_raw pcspkr i2c_piix4 snd_page_alloc led_class cfg80211 ohci1394 ieee1394 r8169 mii dm_raid45 xor fbcon tileblit font bitblit softcursor i915 drm i2c_algo_bit video output intel_agp
[  104.602955] Pid: 2459, comm: NetworkManager Not tainted 2.6.31-4-generic #22-Ubuntu
[  104.602967] Call Trace:
[  104.602999]  [<ffffffff81058f08>] warn_slowpath_common+0x78/0xb0
[  104.603016]  [<ffffffff81058f4f>] warn_slowpath_null+0xf/0x20
[  104.603041]  [<ffffffffa04af6d5>] serial_ioctl+0xb5/0xc0 [usbserial]
[  104.603059]  [<ffffffff812ebbbd>] tty_ioctl+0x9d/0x6e0
[  104.603077]  [<ffffffff8112702d>] vfs_ioctl+0x1d/0xa0
[  104.603095]  [<ffffffff8126feca>] ? __up_read+0x9a/0xc0
[  104.603109]  [<ffffffff81127659>] do_vfs_ioctl+0x79/0x370
[  104.603126]  [<ffffffff81077159>] ? up_read+0x9/0x10
[  104.603144]  [<ffffffff8151fd64>] ? do_page_fault+0x194/0x370
[  104.603158]  [<ffffffff811279d1>] sys_ioctl+0x81/0xa0
[  104.603176]  [<ffffffff81011fc2>] system_call_fastpath+0x16/0x1b
[  104.603187] ---[ end trace 85d164a3d7b30171 ]---
[  104.603231] BUG: unable to handle kernel NULL pointer dereference at 0000000000000020
[  104.603248] IP: [<ffffffffa04afacd>] serial_set_termios+0x2d/0xc0 [usbserial]
[  104.603276] PGD 134df8067 PUD 134df9067 PMD 0 
[  104.603292] Oops: 0000 [#1] SMP 
[  104.603304] last sysfs file: /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/charge_full
[  104.603318] CPU 0 
[  104.603325] Modules linked in: option usbserial usb_storage cryptd aes_x86_64 aes_generic binfmt_misc bridge stp bnep lp parport snd_hda_codec_atihdmi snd_hda_codec_idt snd_hda_intel snd_pcm_oss arc4 snd_hda_codec snd_mixer_oss ecb snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi ath9k snd_rawmidi snd_seq_midi_event uvcvideo mac80211 videodev snd_seq sdhci_pci snd_timer v4l1_compat sdhci snd_seq_device joydev ath v4l2_compat_ioctl32 radeon psmouse hp_accel snd lis3lv02d ttm btusb amd64_edac_mod soundcore edac_core input_polldev serio_raw pcspkr i2c_piix4 snd_page_alloc led_class cfg80211 ohci1394 ieee1394 r8169 mii dm_raid45 xor fbcon tileblit font bitblit softcursor i915 drm i2c_algo_bit video output intel_agp
[  104.603512] Pid: 2459, comm: NetworkManager Tainted: G        W  2.6.31-4-generic #22-Ubuntu HP Pavilion dv5 Notebook PC
[  104.603524] RIP: 0010:[<ffffffffa04afacd>]  [<ffffffffa04afacd>] serial_set_termios+0x2d/0xc0 [usbserial]
[  104.603554] RSP: 0018:ffff880134d2bbf8  EFLAGS: 00010246
[  104.603563] RAX: ffffffffa04afaa0 RBX: 0000000000000000 RCX: ffff880134d2bc4c
[  104.603573] RDX: ffff88012a5987f3 RSI: ffff880134d2bc28 RDI: ffff88013946d800
[  104.603584] RBP: ffff880134d2bc18 R08: 0000000000000034 R09: 0000000000000000
[  104.603594] R10: 0000000000000005 R11: 0000000000000001 R12: ffff88013946d800
[  104.603604] R13: ffff880134d2bc28 R14: ffff880134d2bca8 R15: 000000000215a120
[  104.603618] FS:  00007f943d16c730(0000) GS:ffff880028022000(0000) knlGS:0000000000000000
[  104.603629] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[  104.603638] CR2: 0000000000000020 CR3: 0000000134ddf000 CR4: 00000000000006b0
[  104.603650] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  104.603660] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  104.603672] Process NetworkManager (pid: 2459, threadinfo ffff880134d2a000, task ffff880134e0ad60)
[  104.603681] Stack:
[  104.603687]  ffff880134d2bc18 ffff88013946d800 ffff88013946d848 ffff880134d2bca8
[  104.603702] <0> ffff880134d2bc88 ffffffff812f0843 0000000000000005 00000000000004bd
[  104.603719] <0> 010001157f1c0300 170f12001a131100 0000258000000016 ffff880100002580
[  104.603738] Call Trace:
[  104.603753]  [<ffffffff812f0843>] change_termios+0x163/0x2c0
[  104.603769]  [<ffffffff812f0d3a>] set_termios+0x12a/0x220
[  104.603784]  [<ffffffff812f110e>] tty_mode_ioctl+0x11e/0x580
[  104.603807]  [<ffffffffa04af6d5>] ? serial_ioctl+0xb5/0xc0 [usbserial]
[  104.603827]  [<ffffffff8151a94c>] ? printk+0x3c/0x40
[  104.603842]  [<ffffffff81015e50>] ? show_trace+0x10/0x20
[  104.603859]  [<ffffffff81032419>] ? default_spin_lock_flags+0x9/0x10
[  104.603874]  [<ffffffff812f15a5>] n_tty_ioctl_helper+0x35/0x1b0
[  104.603888]  [<ffffffff812f1dc3>] ? tty_ldisc_ref_wait+0x13/0xc0
[  104.603902]  [<ffffffff812edf5e>] n_tty_ioctl+0x1e/0xe0
[  104.603915]  [<ffffffff812ebbf6>] tty_ioctl+0xd6/0x6e0
[  104.603930]  [<ffffffff8112702d>] vfs_ioctl+0x1d/0xa0
[  104.603943]  [<ffffffff8126feca>] ? __up_read+0x9a/0xc0
[  104.603957]  [<ffffffff81127659>] do_vfs_ioctl+0x79/0x370
[  104.603971]  [<ffffffff81077159>] ? up_read+0x9/0x10
[  104.603985]  [<ffffffff8151fd64>] ? do_page_fault+0x194/0x370
[  104.604000]  [<ffffffff811279d1>] sys_ioctl+0x81/0xa0
[  104.604016]  [<ffffffff81011fc2>] system_call_fastpath+0x16/0x1b
[  104.604026] Code: 89 e5 48 83 ec 20 44 8b 0d d9 94 00 00 4c 89 65 f0 4c 89 6d f8 49 89 fc 48 89 5d e8 49 89 f5 48 8b 9f 00 02 00 00 45 85 c9 75 5d <44> 8b 43 20 45 85 c0 74 41 48 8b 03 48 8b 40 08 48 8b 80 20 01 
[  104.604154] RIP  [<ffffffffa04afacd>] serial_set_termios+0x2d/0xc0 [usbserial]
[  104.604179]  RSP <ffff880134d2bbf8>
[  104.604186] CR2: 0000000000000020
[  104.604199] ---[ end trace 85d164a3d7b30172 ]---
[  104.603737] BUG: unable to handle kernel NULL pointer dereference at 0000000000000020
[  104.603772] IP: [<ffffffffa04af339>] serial_tiocmset+0x39/0xc0 [usbserial]
[  104.603819] PGD 12a5bc067 PUD 1261e5067 PMD 0 
[  104.603840] Oops: 0000 [#2] SMP 
[  104.603855] last sysfs file: /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/charge_full
[  104.603878] CPU 1 
[  104.603892] Modules linked in: option usbserial usb_storage cryptd aes_x86_64 aes_generic binfmt_misc bridge stp bnep lp parport snd_hda_codec_atihdmi snd_hda_codec_idt snd_hda_intel snd_pcm_oss arc4 snd_hda_codec snd_mixer_oss ecb snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi ath9k snd_rawmidi snd_seq_midi_event uvcvideo mac80211 videodev snd_seq sdhci_pci snd_timer v4l1_compat sdhci snd_seq_device joydev ath v4l2_compat_ioctl32 radeon psmouse hp_accel snd lis3lv02d ttm btusb amd64_edac_mod soundcore edac_core input_polldev serio_raw pcspkr i2c_piix4 snd_page_alloc led_class cfg80211 ohci1394 ieee1394 r8169 mii dm_raid45 xor fbcon tileblit font bitblit softcursor i915 drm i2c_algo_bit video output intel_agp
[  104.604102] Pid: 3203, comm: pppd Tainted: G      D W  2.6.31-4-generic #22-Ubuntu HP Pavilion dv5 Notebook PC
[  104.604115] RIP: 0010:[<ffffffffa04af339>]  [<ffffffffa04af339>] serial_tiocmset+0x39/0xc0 [usbserial]
[  104.604146] RSP: 0018:ffff88012614de08  EFLAGS: 00010246
[  104.604156] RAX: ffffffffa04b3700 RBX: 0000000000000000 RCX: 0000000000000002
[  104.604166] RDX: 0000000000000000 RSI: ffff8801260726c0 RDI: ffff88013946d800
[  104.604177] RBP: ffff88012614de38 R08: ffffffff81564be0 R09: 0000000000000000
[  104.604188] R10: 0000000000000001 R11: 0000000000000206 R12: ffff88013946d800
[  104.604198] R13: 0000000000000000 R14: 0000000000000002 R15: ffff8801260726c0
[  104.604211] FS:  00007f1cf2b796f0(0000) GS:ffff88002803f000(0000) knlGS:0000000000000000
[  104.604222] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[  104.604232] CR2: 0000000000000020 CR3: 000000012603b000 CR4: 00000000000006a0
[  104.604243] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  104.604253] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  104.604265] Process pppd (pid: 3203, threadinfo ffff88012614c000, task ffff880126078000)
[  104.604274] Stack:
[  104.604280]  ffff88012614de38 ffff88013946d800 0000000000000000 ffff8801260726c0
[  104.604296] <0> 0000000000005417 ffff88013946d800 ffff88012614de98 ffffffff812ebeaf
[  104.604313] <0> 00000000000000bc ffff88012614df48 0000000002307748 0000000000000000
[  104.604332] Call Trace:
[  104.604357]  [<ffffffff812ebeaf>] tty_ioctl+0x38f/0x6e0
[  104.604378]  [<ffffffff8112702d>] vfs_ioctl+0x1d/0xa0
[  104.604399]  [<ffffffff8101b378>] ? restore_i387_xstate+0x148/0x1d0
[  104.604414]  [<ffffffff81130242>] ? alloc_fd+0x102/0x150
[  104.604429]  [<ffffffff81127659>] do_vfs_ioctl+0x79/0x370
[  104.604444]  [<ffffffff811279d1>] sys_ioctl+0x81/0xa0
[  104.604462]  [<ffffffff81011fc2>] system_call_fastpath+0x16/0x1b
[  104.604470] Code: d5 8b 15 73 9c 00 00 4c 89 65 e0 4c 89 75 f0 49 89 fc 4c 89 7d f8 48 89 5d d8 49 89 f7 85 d2 41 89 ce 48 8b 9f 00 02 00 00 75 43 <8b> 43 20 85 c0 74 61 48 8b 03 48 8b 40 08 48 8b 98 50 01 00 00 
[  104.604593] RIP  [<ffffffffa04af339>] serial_tiocmset+0x39/0xc0 [usbserial]
[  104.604619]  RSP <ffff88012614de08>
[  104.604626] CR2: 0000000000000020
[  104.604654] ---[ end trace 85d164a3d7b30173 ]---
[  247.872903] usb 4-3: USB disconnect, address 2
[  247.873775] btusb_bulk_complete: hci0 urb ffff8801385dcb40 failed to resubmit (19)
[  247.873802] btusb_intr_complete: hci0 urb ffff8801385dc6c0 failed to resubmit (19)
[  247.874774] btusb_bulk_complete: hci0 urb ffff8801385dc300 failed to resubmit (19)
[  247.875256] btusb_send_frame: hci0 urb ffff8801260f5000 submission failed
[  250.532599] usb 4-3: new full speed USB device using ohci_hcd and address 3
[  250.714653] usb 4-3: configuration #1 chosen from 1 choice
[  250.880167] usb 4-3: USB disconnect, address 3
[  250.880248] btusb_bulk_complete: hci0 urb ffff880122862480 failed to resubmit (19)
[  250.880273] btusb_intr_complete: hci0 urb ffff880122862f00 failed to resubmit (19)
[  250.881249] btusb_bulk_complete: hci0 urb ffff880122862c00 failed to resubmit (19)
[  250.881754] btusb_send_frame: hci0 urb ffff880138927600 submission failed
[  252.252173] usb 4-3: new full speed USB device using ohci_hcd and address 4
[  252.434954] usb 4-3: configuration #1 chosen from 1 choice
[  299.164506] usb 2-3: USB disconnect, address 4
[  299.164676] option: option_instat_callback: error -108
[  299.165574] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  299.165634] option 2-3:1.0: device disconnected
[  299.166203] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  299.166287] option 2-3:1.1: device disconnected

```

so no dice.

---

### Post by GeorgeVita on 2009-07-27
Thanks **taavikko**.

My **dmesg** with kernel **2.6.31-4.22** on EeePC 1000H (which is NOT connecting):
```
[  123.740194] usb 2-2: new full speed USB device using uhci_hcd and address 4
[  123.960595] usb 2-2: configuration #1 chosen from 1 choice
[  124.152256] usb 2-2: USB disconnect, address 4
[  124.888232] usb 2-2: new full speed USB device using uhci_hcd and address 5
[  125.053593] usb 2-2: configuration #1 chosen from 1 choice
[  125.113811] usbcore: registered new interface driver usbserial
[  125.114328] USB Serial support registered for generic
[  125.114683] usbcore: registered new interface driver usbserial_generic
[  125.114692] usbserial: USB Serial Driver core
[  125.127593] USB Serial support registered for GSM modem (1-port)
[  125.127753] option 2-2:1.0: GSM modem (1-port) converter detected
[  125.127958] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[  125.127991] option 2-2:1.1: GSM modem (1-port) converter detected
[  125.128133] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[  125.128167] option 2-2:1.2: GSM modem (1-port) converter detected
[  125.128323] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[  125.128383] usbcore: registered new interface driver option
[  125.128391] option: v0.7.2:USB Driver for GSM modems
[  156.716925] ------------[ cut here ]------------
[  156.716978] WARNING: at /build/buildd/linux-2.6.31/drivers/usb/serial/usb-serial.c:436 serial_ioctl+0x98/0xa0 [usbserial]()
[  156.716997] Hardware name: 1000H
[  156.717007] Modules linked in: option usbserial usb_storage binfmt_misc ppdev bridge stp bnep lp parport joydev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq uvcvideo snd_timer snd_seq_device videodev v4l1_compat btusb psmouse snd rt2860sta(C) serio_raw pcspkr soundcore snd_page_alloc eeepc_laptop atl1e fbcon tileblit font bitblit softcursor i915 drm i2c_algo_bit video output intel_agp agpgart
[  156.717257] Pid: 2208, comm: NetworkManager Tainted: G         C 2.6.31-4-generic #22-Ubuntu
[  156.717272] Call Trace:
[  156.717307]  [<c013fd7d>] warn_slowpath_common+0x6d/0xa0
[  156.717348]  [<f816e618>] ? serial_ioctl+0x98/0xa0 [usbserial]
[  156.717387]  [<f816e618>] ? serial_ioctl+0x98/0xa0 [usbserial]
[  156.717415]  [<c013fdc5>] warn_slowpath_null+0x15/0x20
[  156.717452]  [<f816e618>] serial_ioctl+0x98/0xa0 [usbserial]
[  156.717479]  [<c014e5b9>] ? kill_something_info+0x29/0x110
[  156.717517]  [<f816e580>] ? serial_ioctl+0x0/0xa0 [usbserial]
[  156.717546]  [<c03774f7>] tty_ioctl+0x77/0x620
[  156.717570]  [<c0377480>] ? tty_ioctl+0x0/0x620
[  156.717596]  [<c01ee1cc>] vfs_ioctl+0x1c/0x90
[  156.717618]  [<c01ee4f1>] do_vfs_ioctl+0x71/0x310
[  156.717640]  [<c01ee7ef>] sys_ioctl+0x5f/0x80
[  156.717665]  [<c010334c>] syscall_call+0x7/0xb
[  156.717684] ---[ end trace c0eda8995757e4b2 ]---
[  156.717707] ------------[ cut here ]------------
[  156.717745] WARNING: at /build/buildd/linux-2.6.31/drivers/usb/serial/usb-serial.c:452 serial_set_termios+0x6e/0xa0 [usbserial]()
[  156.717762] Hardware name: 1000H
[  156.717772] Modules linked in: option usbserial usb_storage binfmt_misc ppdev bridge stp bnep lp parport joydev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq uvcvideo snd_timer snd_seq_device videodev v4l1_compat btusb psmouse snd rt2860sta(C) serio_raw pcspkr soundcore snd_page_alloc eeepc_laptop atl1e fbcon tileblit font bitblit softcursor i915 drm i2c_algo_bit video output intel_agp agpgart
[  156.717940] Pid: 2208, comm: NetworkManager Tainted: G        WC 2.6.31-4-generic #22-Ubuntu
[  156.717950] Call Trace:
[  156.717969]  [<c013fd7d>] warn_slowpath_common+0x6d/0xa0
[  156.717996]  [<f816ea2e>] ? serial_set_termios+0x6e/0xa0 [usbserial]
[  156.718021]  [<f816ea2e>] ? serial_set_termios+0x6e/0xa0 [usbserial]
[  156.718038]  [<c013fdc5>] warn_slowpath_null+0x15/0x20
[  156.718062]  [<f816ea2e>] serial_set_termios+0x6e/0xa0 [usbserial]
[  156.718081]  [<c037baa9>] change_termios+0x169/0x2c0
[  156.718098]  [<c037bdf8>] set_termios+0xd8/0x1d0
[  156.718115]  [<c037c155>] tty_mode_ioctl+0xf5/0x4c0
[  156.718132]  [<c010661a>] ? show_trace+0x1a/0x20
[  156.718150]  [<c0568e0b>] ? printk+0x18/0x1d
[  156.718166]  [<c013fb8a>] ? print_oops_end_marker+0x2a/0x30
[  156.718182]  [<c013fd8f>] ? warn_slowpath_common+0x7f/0xa0
[  156.718214]  [<c01244b8>] ? default_spin_lock_flags+0x8/0x10
[  156.718232]  [<c056b1ca>] ? _spin_lock_irqsave+0x2a/0x40
[  156.718249]  [<c037c555>] n_tty_ioctl_helper+0x35/0x180
[  156.718265]  [<c03794de>] n_tty_ioctl+0x2e/0xe0
[  156.718280]  [<c037752e>] tty_ioctl+0xae/0x620
[  156.718295]  [<c03794b0>] ? n_tty_ioctl+0x0/0xe0
[  156.718310]  [<c0377480>] ? tty_ioctl+0x0/0x620
[  156.718324]  [<c01ee1cc>] vfs_ioctl+0x1c/0x90
[  156.718339]  [<c01ee4f1>] do_vfs_ioctl+0x71/0x310
[  156.718354]  [<c01ee7ef>] sys_ioctl+0x5f/0x80
[  156.718369]  [<c010334c>] syscall_call+0x7/0xb
[  156.718380] ---[ end trace c0eda8995757e4b3 ]---
[  156.744022] BUG: unable to handle kernel NULL pointer dereference at 00000014
[  156.744041] IP: [<f816e2e3>] serial_tiocmset+0x23/0xa0 [usbserial]
[  156.744068] *pde = 7e064067 
[  156.744077] Oops: 0000 [#1] SMP 
[  156.744085] last sysfs file: /sys/devices/platform/eeepc/rfkill/rfkill0/state
[  156.744094] Modules linked in: option usbserial usb_storage binfmt_misc ppdev bridge stp bnep lp parport joydev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq uvcvideo snd_timer snd_seq_device videodev v4l1_compat btusb psmouse snd rt2860sta(C) serio_raw pcspkr soundcore snd_page_alloc eeepc_laptop atl1e fbcon tileblit font bitblit softcursor i915 drm i2c_algo_bit video output intel_agp agpgart
[  156.744205] 
[  156.744216] Pid: 3078, comm: pppd Tainted: G        WC (2.6.31-4-generic #22-Ubuntu) 1000H
[  156.744227] EIP: 0060:[<f816e2e3>] EFLAGS: 00010246 CPU: 1
[  156.744244] EIP is at serial_tiocmset+0x23/0xa0 [usbserial]
[  156.744253] EAX: f609d000 EBX: f609d000 ECX: 00000000 EDX: 00000000
[  156.744262] ESI: 00000000 EDI: f5330300 EBP: f51c7f1c ESP: f51c7efc
[  156.744271]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[  156.744282] Process pppd (pid: 3078, ti=f51c6000 task=f532bed0 task.ti=f51c6000)
[  156.744289] Stack:
[  156.744294]  00000000 f51c7f1c c030cb24 00000000 c012e58d f8171fe0 f609d000 f5330300
[  156.744315] <0> f51c7f50 c0377798 00000002 f532bed0 f609d000 bf8d1c94 00005417 00000000
[  156.744336] <0> f51c7f5c c0132d17 c0377480 c05984e0 bf8d1c94 f51c7f70 c01ee1cc f532bed0
[  156.744360] Call Trace:
[  156.744377]  [<c030cb24>] ? rb_erase+0xb4/0x120
[  156.744392]  [<c012e58d>] ? __enqueue_entity+0x9d/0xc0
[  156.744408]  [<c0377798>] ? tty_ioctl+0x318/0x620
[  156.744422]  [<c0132d17>] ? finish_task_switch+0x57/0xe0
[  156.744433]  [<c0377480>] ? tty_ioctl+0x0/0x620
[  156.744444]  [<c01ee1cc>] ? vfs_ioctl+0x1c/0x90
[  156.744459]  [<c056936c>] ? schedule+0x40c/0x730
[  156.744469]  [<c01ee4f1>] ? do_vfs_ioctl+0x71/0x310
[  156.744480]  [<c01ee7ef>] ? sys_ioctl+0x5f/0x80
[  156.744492]  [<c010334c>] ? syscall_call+0x7/0xb
[  156.744499] Code: 00 8d bc 27 00 00 00 00 55 89 e5 83 ec 20 89 7d fc 89 d7 8b 15 24 68 17 f8 89 5d f4 89 c3 89 75 f8 8b b0 3c 01 00 00 85 d2 75 34 <8b> 46 14 85 c0 74 59 8b 06 8b 40 04 8b b0 a8 00 00 00 b8 ea ff 
[  156.744615] EIP: [<f816e2e3>] serial_tiocmset+0x23/0xa0 [usbserial] SS:ESP 0068:f51c7efc
[  156.744640] CR2: 0000000000000014
[  156.744649] ---[ end trace c0eda8995757e4b4 ]---
```
I am updating using the mobile broadband connection with:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Can I check system file's integrity? Is there other safer method to 'upgrade' after a clean Alpha 3 install?

Thanks in advance,
George

---

### Post by GeorgeVita on 2009-07-28
UPDATE: Solved

I download kernel 2.6.31-999-generic #1248771614 (daily 28/July/09) and now CONNECTED with the Huawei E169. Double checked that the problem exists by booting on 2.6.31-4.22 and -4.23

Now using network manager PPA version and all Karmic pre-released updates.

G

---

