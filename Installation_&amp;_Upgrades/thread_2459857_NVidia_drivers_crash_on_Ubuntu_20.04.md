---
title: "NVidia drivers crash on Ubuntu 20.04"
date: 2021-03-27
forum: Installation &amp; Upgrades
---

### Post by dimitri-papadopoulos on 2021-03-27
Hi,
I have a Dell Precision Tower 3620 with the following graphics card:
01:00.0 VGA compatible controller: NVIDIA Corporation GM107GL [Quadro K1200] (rev a2)
running Ubuntu 16.04, 18.04 and now 20.04 on this machine, always with the Nouveau driver until now. I want to switch to the proprietary NVidia and have attempted multiple times to install the suggested **nvidia-driver-460** (and also **nvidia-driver-390** just in case) using software-properties-gtk. The proprietary drivers install smoothly. Then I reboot, enter login/password at the gdm prompt, and get a black screen. From the system log:
```

Mar 27 12:00:03 xxxxxxxx kernel: [   98.305905] BUG: kernel NULL pointer dereference, address: 0000000000000070
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305907] #PF: supervisor read access in kernel mode
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305908] #PF: error_code(0x0000) - not-present page
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305909] PGD 0 P4D 0 
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305910] Oops: 0000 [#1] SMP PTI
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305912] CPU: 6 PID: 2198 Comm: Xorg Tainted: P           O      5.4.0-70-generic #78-Ubuntu
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305913] Hardware name: Dell Inc. Precision Tower 3620/0MWYPT, BIOS 2.16.2 08/13/2020
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305927] RIP: 0010:_nv002691kms+0x18/0x70 [nvidia_modeset]
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305928] Code: 24 1f 01 eb b2 66 2e 0f 1f 84 00 00 00 00 00 0f 1f 00 41 54 55 49 89 fc 53 89 d5 41 b8 04 00 00 00 ba 02 01 02 00 48 83 ec 10 <8b> 46 70 8b 3d 4f e8 0c 00 48 8d 4c 24 0c 89 ee 89 44 24 0c e8 bf
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305929] RSP: 0018:ffffbd074173fc50 EFLAGS: 00010286
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305930] RAX: 0000000000000000 RBX: ffff9b70579d6008 RCX: 0000000000000073
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305931] RDX: 0000000000020102 RSI: 0000000000000000 RDI: ffff9b70579d6008
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305932] RBP: 0000000000010009 R08: 0000000000000004 R09: 0000000000000020
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305933] R10: 0000000000000000 R11: ffff9b7053d71098 R12: ffff9b70579d6008
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305933] R13: ffff9b70579d60a0 R14: 0000000000000fff R15: 0000000000010008
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305934] FS:  00007f2f02af9a40(0000) GS:ffff9b705db80000(0000) knlGS:0000000000000000
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305935] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305936] CR2: 0000000000000070 CR3: 000000040d736005 CR4: 00000000003606e0
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305936] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305937] DR3: 0000000000000000 DR6: 00000000fffe0ff0 DR7: 0000000000000400
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305937] Call Trace:
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305948]  ? _nv002690kms+0xb1/0x150 [nvidia_modeset]
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305957]  ? _nv002468kms+0x489/0x670 [nvidia_modeset]
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305960]  ? __check_object_size+0x13f/0x150
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305962]  ? _copy_from_user+0x3e/0x60
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305967]  ? _nv000451kms+0xa0/0xa0 [nvidia_modeset]
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305972]  ? _nv000657kms+0x34/0x50 [nvidia_modeset]
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305977]  ? nvKmsIoctl+0x96/0x1d0 [nvidia_modeset]
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305982]  ? nvkms_ioctl_common+0x42/0x80 [nvidia_modeset]
Mar 27 12:00:03 xxxxxxxx kernel: [   98.305986]  ? nvkms_ioctl+0xc4/0x100 [nvidia_modeset]
Mar 27 12:00:03 xxxxxxxx kernel: [   98.306097]  ? nvidia_frontend_unlocked_ioctl+0x3b/0x50 [nvidia]
Mar 27 12:00:03 xxxxxxxx kernel: [   98.306099]  ? do_vfs_ioctl+0x407/0x670
Mar 27 12:00:03 xxxxxxxx kernel: [   98.306101]  ? do_fcntl+0x22f/0x560
Mar 27 12:00:03 xxxxxxxx kernel: [   98.306102]  ? putname+0x4a/0x50
Mar 27 12:00:03 xxxxxxxx kernel: [   98.306103]  ? ksys_ioctl+0x67/0x90
Mar 27 12:00:03 xxxxxxxx kernel: [   98.306105]  ? __x64_sys_ioctl+0x1a/0x20
Mar 27 12:00:03 xxxxxxxx kernel: [   98.306107]  ? do_syscall_64+0x57/0x190
Mar 27 12:00:03 xxxxxxxx kernel: [   98.306109]  ? entry_SYSCALL_64_after_hwframe+0x44/0xa9
Mar 27 12:00:03 xxxxxxxx kernel: [   98.306110] Modules linked in: rfcomm wireguard ip6_udp_tunnel udp_tunnel ipt_REJECT nf_reject_ipv4 xt_multiport iptable_filter bpfilter cmac algif_hash algif_skcipher af_alg bnep binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi intel_rapl_msr mei_hdcp snd_hda_intel snd_intel_dspcfg dell_smm_hwmon snd_hda_codec intel_rapl_common snd_hda_core x86_pkg_temp_thermal intel_powerclamp btusb coretemp btrtl btbcm kvm_intel snd_seq_midi btintel snd_seq_midi_event bluetooth snd_usb_audio kvm snd_usbmidi_lib snd_hwdep mc dell_wmi ecdh_generic rapl dell_smbios ecc input_leds snd_rawmidi intel_cstate snd_pcm dcdbas snd_seq wmi_bmof sparse_keymap intel_wmi_thunderbolt dell_wmi_descriptor snd_seq_device snd_timer snd mei_me soundcore mei intel_pch_thermal ie31200_edac mac_hid acpi_pad nvidia_uvm(O) sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 dm_crypt hid_generic usbhid hid nvidia_drm(PO) nvidia_modeset(PO) nvidia(PO) crct10dif_pclmul crc32_pclmul nvme ghash_clmulni_intel aesni_intel
Mar 27 12:00:03 xxxxxxxx kernel: [   98.306128]  drm_kms_helper crypto_simd syscopyarea sysfillrect cryptd sysimgblt ahci glue_helper fb_sys_fops libahci e1000e drm nvme_core i2c_i801 wmi video [last unloaded: vboxdrv]
Mar 27 12:00:03 xxxxxxxx kernel: [   98.306134] CR2: 0000000000000070
Mar 27 12:00:03 xxxxxxxx kernel: [   98.306135] ---[ end trace 7be9061aad24484a ]---
Mar 27 12:00:03 xxxxxxxx kernel: [   98.331602] RIP: 0010:_nv002691kms+0x18/0x70 [nvidia_modeset]
Mar 27 12:00:03 xxxxxxxx kernel: [   98.331606] Code: 24 1f 01 eb b2 66 2e 0f 1f 84 00 00 00 00 00 0f 1f 00 41 54 55 49 89 fc 53 89 d5 41 b8 04 00 00 00 ba 02 01 02 00 48 83 ec 10 <8b> 46 70 8b 3d 4f e8 0c 00 48 8d 4c 24 0c 89 ee 89 44 24 0c e8 bf
Mar 27 12:00:03 xxxxxxxx kernel: [   98.331607] RSP: 0018:ffffbd074173fc50 EFLAGS: 00010286
Mar 27 12:00:03 xxxxxxxx kernel: [   98.331608] RAX: 0000000000000000 RBX: ffff9b70579d6008 RCX: 0000000000000073
Mar 27 12:00:03 xxxxxxxx kernel: [   98.331609] RDX: 0000000000020102 RSI: 0000000000000000 RDI: ffff9b70579d6008
Mar 27 12:00:03 xxxxxxxx kernel: [   98.331610] RBP: 0000000000010009 R08: 0000000000000004 R09: 0000000000000020
Mar 27 12:00:03 xxxxxxxx kernel: [   98.331610] R10: 0000000000000000 R11: ffff9b7053d71098 R12: ffff9b70579d6008
Mar 27 12:00:03 xxxxxxxx kernel: [   98.331611] R13: ffff9b70579d60a0 R14: 0000000000000fff R15: 0000000000010008
Mar 27 12:00:03 xxxxxxxx kernel: [   98.331612] FS:  00007f2f02af9a40(0000) GS:ffff9b705db80000(0000) knlGS:0000000000000000
Mar 27 12:00:03 xxxxxxxx kernel: [   98.331613] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Mar 27 12:00:03 xxxxxxxx kernel: [   98.331613] CR2: 0000000000000070 CR3: 000000040d736005 CR4: 00000000003606e0
Mar 27 12:00:03 xxxxxxxx kernel: [   98.331614] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Mar 27 12:00:03 xxxxxxxx kernel: [   98.331614] DR3: 0000000000000000 DR6: 00000000fffe0ff0 DR7: 0000000000000400
Mar 27 12:00:04 xxxxxxxx systemd[1]: Started Session 4 of user xxxxxxx.

```

Any clue? Any suggestion what I should be looking into?

---

### Post by CelticWarrior on 2021-03-28
The [COLOR=#000000]NVIDIA Corporation GM107GL [Quadro K1200] should work with the 460 series drivers, according to the manufacturer.
You need to disable Secure Boot in UEFI in order to use unsigned drivers.[/COLOR]

---

### Post by dimitri-papadopoulos on 2021-03-28
[COLOR=#000000]Unfortunately [/COLOR]disabling Secure Boot does not help. The error remains.

By the way, why should I disable [COLOR=#000000]Secure Boot in UEFI? I'm not certain that's what [Chapter 4. Installing the NVIDIA Driver]("https://download.nvidia.com/XFree86/Linux-x86_64/460.67/README/installdriver.html") implies. Also, I would expect such an error to be caught much earlier and with a different error message.

[/COLOR]

---

### Post by CelticWarrior on 2021-03-28
So you have been installing the driver downloaded from Nvidia all along?
Very likely that IS your problem. ALWAYS install the driver already in the Ubuntu repository. And yes, disable Secure Boot.

What you should do now is uninstall *everything* that you installed from Nvidia and then reboot and open Additional Drivers. Select and apply. Reboot. And again, disable Secure Boot.

---

### Post by dimitri-papadopoulos on 2021-03-28
No, I haven't been installing the driver downloaded from Nvidia. I have been installing using software-properties-gtk. Secure Boot has been disabled but disabling it doesn't help.

---

### Post by CelticWarrior on 2021-03-28
If so, first of all, [update UEFI]("https://www.dell.com/support/home/en-us/drivers/driversdetails?driverid=95nky&oscode=wb64a&productcode=precision-t3620-workstation").
Then run ```
sudo apt-get purge nvidia*
```
Reboot and install 460.

Is this a successively release upgraded system? If so better to do your backups and reinstall from scratch and this time make sure to select the option to install third-party drivers, firmware, etc. so the proper Nvidia drivers are installed automatically.

---

### Post by dimitri-papadopoulos on 2021-03-28
BIOS has always been up to date on this workstation. It used to be [2.16.2]("https://www.dell.com/support/home/drivers/driversdetails?driverid=w6f30"), and I have just updgraded to [2.17.1]("https://www.dell.com/support/home/drivers/driversdetails?driverid=95nky") to be on the safe side.

To fall back to the Nouveau driver after my unsuccessful attempts to install the NVidia proprietary drivers, I always run:
```

sudo apt purge nvidia-driver-460
sudo apt purge libnvidia-compute-460
sudo apt autopurge

```

This is a clean Ubuntu 20.04 installation, not an upgrade from a previous release. I have always reinstalled Ubuntu from scratch on my workstation (16.04, 18.04, 20.04).

Note that the Nouveau driver has its own issues ([Nouveau driver freezes]("https://ubuntuforums.org/showthread.php?t=2459862")), so I am wondering whether this could ba a hardware problem. Any clue how I could investigate that?

---

### Post by dimitri-papadopoulos on 2021-03-28
Here is the system log, just after I enter my password at the gdm prompt and hit Enter:
```

Mar 28 12:00:04 xxxxxxxx systemd[1]: Started Session 4 of user xxxxxxx.
Mar 28 12:00:05 xxxxxxxx /usr/lib/gdm3/gdm-x-session[1414]: (**) Option "fd" "41"
Mar 28 12:00:05 xxxxxxxx /usr/lib/gdm3/gdm-x-session[1414]: (II) event2  - Power Button: device removed
Mar 28 12:00:05 xxxxxxxx /usr/lib/gdm3/gdm-x-session[1414]: (**) Option "fd" "44"
Mar 28 12:00:05 xxxxxxxx /usr/lib/gdm3/gdm-x-session[1414]: (II) event1  - Power Button: device removed
Mar 28 12:00:05 xxxxxxxx /usr/lib/gdm3/gdm-x-session[1414]: (**) Option "fd" "45"
Mar 28 12:00:05 xxxxxxxx /usr/lib/gdm3/gdm-x-session[1414]: (II) event0  - Sleep Button: device removed
Mar 28 12:00:05 xxxxxxxx /usr/lib/gdm3/gdm-x-session[1414]: (**) Option "fd" "46"
Mar 28 12:00:05 xxxxxxxx /usr/lib/gdm3/gdm-x-session[1414]: (II) event3  - Dell Dell AC511 USB SoundBar: device removed
Mar 28 12:00:05 xxxxxxxx /usr/lib/gdm3/gdm-x-session[1414]: (**) Option "fd" "47"
Mar 28 12:00:05 xxxxxxxx /usr/lib/gdm3/gdm-x-session[1414]: (II) event4  - DELL Dell USB Entry Keyboard: device removed
Mar 28 12:00:05 xxxxxxxx /usr/lib/gdm3/gdm-x-session[1414]: (**) Option "fd" "48"
Mar 28 12:00:05 xxxxxxxx /usr/lib/gdm3/gdm-x-session[1414]: (II) event5  - PixArt Dell MS116 USB Optical Mouse: device removed
Mar 28 12:00:05 xxxxxxxx /usr/lib/gdm3/gdm-x-session[1414]: (**) Option "fd" "49"
Mar 28 12:00:05 xxxxxxxx /usr/lib/gdm3/gdm-x-session[1414]: (II) event6  - Dell WMI hotkeys: device removed
Mar 28 12:00:15 xxxxxxxx systemd[1]: fprintd.service: Succeeded.
Mar 28 12:00:19 xxxxxxxx kernel: [  264.281242] nvidia-modeset: ERROR: GPU:0: Display engine push buffer channel allocation failed: 0x65 (Call timed out [NV_ERR_TIMEOUT])
Mar 28 12:00:19 xxxxxxxx kernel: [  264.282028] nvidia-modeset: ERROR: GPU:0: Failed to allocate display engine core DMA push buffer
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[1414]: (II) systemd-logind: got pause for 13:70
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[1414]: (II) systemd-logind: got pause for 13:68
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[1414]: (II) systemd-logind: got pause for 13:66
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[1414]: (II) systemd-logind: got pause for 13:65
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[1414]: (II) systemd-logind: got pause for 13:67
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[1414]: (II) systemd-logind: got pause for 13:64
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[1414]: (II) systemd-logind: got pause for 13:69
Mar 28 12:00:23 xxxxxxxx kernel: [  268.294642] rfkill: input handler enabled
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: _XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: _XSERVTransMakeAllCOTSServerListeners: server already running
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (--) Log file renamed from "/var/log/Xorg.pid-3189.log" to "/var/log/Xorg.1.log"
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: X.Org X Server 1.20.9
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: X Protocol Version 11, Revision 0
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: Build Operating System: Linux 4.15.0-130-generic x86_64 Ubuntu
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: Current Operating System: Linux xxxxxxxx 5.4.0-70-generic #78-Ubuntu SMP Fri Mar 19 13:29:52 UTC 2021 x86_64
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: Kernel command line: BOOT_IMAGE=/vmlinuz-5.4.0-70-generic root=/dev/mapper/vgubuntu-root ro quiet splash vt.handoff=7
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: Build Date: 17 January 2021  09:13:31AM
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: xorg-server 2:1.20.9-2ubuntu1.2~20.04.1 (For technical support please see http://www.ubuntu.com/support)
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: Current version of pixman: 0.38.4
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011Before reporting problems, check http://wiki.x.org
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011to make sure that you have the latest version.
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: Markers: (--) probed, (**) from config file, (==) default setting,
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011(++) from command line, (!!) notice, (II) informational,
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) Log file: "/var/log/Xorg.1.log", Time: Sun Mar 28 12:00:23 2021
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) Using system config directory "/usr/share/X11/xorg.conf.d"
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) No Layout section.  Using the first Screen section.
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) No screen section available. Using defaults.
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (**) |-->Screen "Default Screen Section" (0)
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (**) |   |-->Monitor "<default monitor>"
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) No monitor specified for screen "Default Screen Section".
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011Using a default monitor configuration.
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) Automatically adding devices
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) Automatically enabling devices
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) Automatically adding GPU devices
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) Automatically binding GPU devices
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) Max clients allowed: 256, resource mask: 0x1fffff
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011Entry deleted from font path.
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011Entry deleted from font path.
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011Entry deleted from font path.
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/X11/Type1".
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011Entry deleted from font path.
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011(Run 'mkfontdir' on "/usr/share/fonts/X11/Type1").
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011Entry deleted from font path.
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011Entry deleted from font path.
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) FontPath set to:
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011/usr/share/fonts/X11/misc,
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011built-ins
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) ModulePath set to "/usr/lib/xorg/modules"
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) The server relies on udev to provide the list of input devices.
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011If no devices become available, reconfigure udev or disable AutoAddDevices.
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Loader magic: 0x555c3c943020
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Module ABI versions:
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011X.Org ANSI C Emulation: 0.4
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011X.Org Video Driver: 24.1
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011X.Org XInput driver : 24.1
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011X.Org Server Extension : 10.0
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (++) using VT number 2
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) systemd-logind: took control of session /org/freedesktop/login1/session/_34
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) xfree86: Adding drm device (/dev/dri/card0)
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) systemd-logind: got fd for /dev/dri/card0 226:0 fd 13 paused 0
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (**) OutputClass "nvidia" ModulePath extended to "/usr/lib/x86_64-linux-gnu/nvidia/xorg,/usr/lib/xorg/modules"
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (--) PCI:*(1@0:0:0) 10de:13bc:10de:1140 rev 162, Mem @ 0xee000000/16777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/131072
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) LoadModule: "glx"
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Module glx: vendor="X.Org Foundation"
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011compiled for 1.20.9, module version = 1.0.0
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011ABI class: X.Org Server Extension, version 10.0
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Applying OutputClass "nvidia" to /dev/dri/card0
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011loading driver: nvidia
Mar 28 12:00:23 xxxxxxxx rtkit-daemon[1425]: Supervising 3 threads of 1 processes of 1 users.
Mar 28 12:00:23 xxxxxxxx rtkit-daemon[1425]: Successfully made thread 3191 of process 2896 owned by '165978' RT at priority 5.
Mar 28 12:00:23 xxxxxxxx rtkit-daemon[1425]: Supervising 4 threads of 2 processes of 2 users.
Mar 28 12:00:23 xxxxxxxx rtkit-daemon[1425]: Supervising 4 threads of 2 processes of 2 users.
Mar 28 12:00:23 xxxxxxxx rtkit-daemon[1425]: Successfully made thread 3192 of process 2896 owned by '165978' RT at priority 5.
Mar 28 12:00:23 xxxxxxxx rtkit-daemon[1425]: Supervising 5 threads of 2 processes of 2 users.
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) Matched nvidia as autoconfigured driver 0
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) Matched nouveau as autoconfigured driver 1
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) Matched modesetting as autoconfigured driver 2
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) Matched fbdev as autoconfigured driver 3
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) Matched vesa as autoconfigured driver 4
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) Assigned the driver to the xf86ConfigLayout
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) LoadModule: "nvidia"
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Loading /usr/lib/x86_64-linux-gnu/nvidia/xorg/nvidia_drv.so
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Module nvidia: vendor="NVIDIA Corporation"
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011compiled for 1.6.99.901, module version = 1.0.0
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011Module class: X.Org Video Driver
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) LoadModule: "nouveau"
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Module nouveau: vendor="X.Org Foundation"
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011compiled for 1.20.3, module version = 1.0.16
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011Module class: X.Org Video Driver
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011ABI class: X.Org Video Driver, version 24.0
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) LoadModule: "modesetting"
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Module modesetting: vendor="X.Org Foundation"
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011compiled for 1.20.9, module version = 1.20.9
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011Module class: X.Org Video Driver
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011ABI class: X.Org Video Driver, version 24.1
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) LoadModule: "fbdev"
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (WW) Warning, couldn't open module fbdev
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (EE) Failed to load module "fbdev" (module does not exist, 0)
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) LoadModule: "vesa"
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (WW) Warning, couldn't open module vesa
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (EE) Failed to load module "vesa" (module does not exist, 0)
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Applying OutputClass "nvidia" to /dev/dri/card0
Mar 28 12:00:23 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011loading driver: nvidia
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) Matched nvidia as autoconfigured driver 0
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) Matched nouveau as autoconfigured driver 1
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) Matched modesetting as autoconfigured driver 2
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) Matched fbdev as autoconfigured driver 3
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) Matched vesa as autoconfigured driver 4
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) Assigned the driver to the xf86ConfigLayout
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) LoadModule: "nvidia"
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Loading /usr/lib/x86_64-linux-gnu/nvidia/xorg/nvidia_drv.so
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Module nvidia: vendor="NVIDIA Corporation"
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011compiled for 1.6.99.901, module version = 1.0.0
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011Module class: X.Org Video Driver
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) UnloadModule: "nvidia"
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Unloading nvidia
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Failed to load module "nvidia" (already loaded, 0)
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) LoadModule: "nouveau"
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Module nouveau: vendor="X.Org Foundation"
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011compiled for 1.20.3, module version = 1.0.16
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011Module class: X.Org Video Driver
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011ABI class: X.Org Video Driver, version 24.0
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) UnloadModule: "nouveau"
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Unloading nouveau
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Failed to load module "nouveau" (already loaded, 0)
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) LoadModule: "modesetting"
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Module modesetting: vendor="X.Org Foundation"
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011compiled for 1.20.9, module version = 1.20.9
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011Module class: X.Org Video Driver
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011ABI class: X.Org Video Driver, version 24.1
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) UnloadModule: "modesetting"
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Unloading modesetting
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Failed to load module "modesetting" (already loaded, 0)
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) LoadModule: "fbdev"
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (WW) Warning, couldn't open module fbdev
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (EE) Failed to load module "fbdev" (module does not exist, 0)
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) LoadModule: "vesa"
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (WW) Warning, couldn't open module vesa
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (EE) Failed to load module "vesa" (module does not exist, 0)
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) NVIDIA dlloader X Driver  460.39  Thu Jan 21 21:54:11 UTC 2021
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) NOUVEAU driver Date:   Mon Jan 28 23:25:58 2019 -0500
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) NOUVEAU driver for NVIDIA chipset families :
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011RIVA TNT            (NV04)
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011RIVA TNT2           (NV05)
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011GeForce 256         (NV10)
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011GeForce 2           (NV11, NV15)
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011GeForce 4MX         (NV17, NV18)
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011GeForce 3           (NV20)
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011GeForce 4Ti         (NV25, NV28)
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011GeForce FX          (NV3x)
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011GeForce 6           (NV4x)
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011GeForce 7           (G7x)
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011GeForce 8           (G8x)
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011GeForce 9           (G9x)
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011GeForce GTX 2xx/3xx (GT2xx)
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011GeForce GTX 4xx/5xx (GFxxx)
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011GeForce GTX 6xx/7xx (GKxxx)
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011GeForce GTX 9xx     (GMxxx)
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011GeForce GTX 10xx    (GPxxx)
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) modesetting: Driver for Modesetting Kernel Drivers: kms
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) systemd-logind: releasing fd for 226:0
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Loading sub module "fb"
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) LoadModule: "fb"
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Loading /usr/lib/xorg/modules/libfb.so
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Module fb: vendor="X.Org Foundation"
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011compiled for 1.20.9, module version = 1.0.0
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011ABI class: X.Org ANSI C Emulation, version 0.4
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Loading sub module "wfb"
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) LoadModule: "wfb"
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Loading /usr/lib/xorg/modules/libwfb.so
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Module wfb: vendor="X.Org Foundation"
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011compiled for 1.20.9, module version = 1.0.0
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011ABI class: X.Org ANSI C Emulation, version 0.4
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Loading sub module "ramdac"
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) LoadModule: "ramdac"
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Module "ramdac" already built-in
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (WW) Falling back to old probe method for modesetting
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) NVIDIA(0): Creating default Display subsection in Screen section
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011"Default Screen Section" for depth/fbbpp 24/32
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) NVIDIA(0): RGB weight 888
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) NVIDIA(0): Default visual is TrueColor
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Applying OutputClass "nvidia" options to /dev/dri/card0
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration"
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (**) NVIDIA(0): Enabling 2D acceleration
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Loading sub module "glxserver_nvidia"
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) LoadModule: "glxserver_nvidia"
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Loading /usr/lib/x86_64-linux-gnu/nvidia/xorg/libglxserver_nvidia.so
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) Module glxserver_nvidia: vendor="NVIDIA Corporation"
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011compiled for 1.6.99.901, module version = 1.0.0
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: #011Module class: X.Org Server Extension
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) NVIDIA GLX Module  460.39  Thu Jan 21 21:51:40 UTC 2021
Mar 28 12:00:24 xxxxxxxx /usr/lib/gdm3/gdm-x-session[3189]: (II) NVIDIA: The X server supports PRIME Render Offload.
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802883] BUG: kernel NULL pointer dereference, address: 0000000000000070
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802885] #PF: supervisor read access in kernel mode
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802886] #PF: error_code(0x0000) - not-present page
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802887] PGD 0 P4D 0 
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802890] Oops: 0000 [#1] SMP PTI
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802892] CPU: 3 PID: 3189 Comm: Xorg Tainted: P           O      5.4.0-70-generic #78-Ubuntu
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802893] Hardware name: Dell Inc. Precision Tower 3620/0MWYPT, BIOS 2.17.1 12/22/2020
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802910] RIP: 0010:_nv002691kms+0x18/0x70 [nvidia_modeset]
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802912] Code: 24 1f 01 eb b2 66 2e 0f 1f 84 00 00 00 00 00 0f 1f 00 41 54 55 49 89 fc 53 89 d5 41 b8 04 00 00 00 ba 02 01 02 00 48 83 ec 10 <8b> 46 70 8b 3d 4f e8 0c 00 48 8d 4c 24 0c 89 ee 89 44 24 0c e8 bf
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802913] RSP: 0018:ffffb60d8173fc50 EFLAGS: 00010286
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802915] RAX: 0000000000000000 RBX: ffff9bfbd3722008 RCX: 00000000000000da
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802916] RDX: 0000000000020102 RSI: 0000000000000000 RDI: ffff9bfbd3722008
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802917] RBP: 0000000000010009 R08: 0000000000000004 R09: 0000000000000020
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802918] R10: 0000000000000000 R11: ffff9bfbd22c9098 R12: ffff9bfbd3722008
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802919] R13: ffff9bfbd37220a0 R14: 0000000000000fff R15: 0000000000010008
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802921] FS:  00007f7c59bdba40(0000) GS:ffff9bfbddac0000(0000) knlGS:0000000000000000
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802922] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802923] CR2: 0000000000000070 CR3: 0000000406e7e006 CR4: 00000000003606e0
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802924] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802925] DR3: 0000000000000000 DR6: 00000000fffe0ff0 DR7: 0000000000000400
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802926] Call Trace:
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802941]  ? _nv002690kms+0xb1/0x150 [nvidia_modeset]
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802955]  ? _nv002468kms+0x489/0x670 [nvidia_modeset]
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802958]  ? __check_object_size+0x13f/0x150
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802961]  ? _copy_from_user+0x3e/0x60
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802970]  ? _nv000451kms+0xa0/0xa0 [nvidia_modeset]
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802979]  ? _nv000657kms+0x34/0x50 [nvidia_modeset]
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802988]  ? nvKmsIoctl+0x96/0x1d0 [nvidia_modeset]
Mar 28 12:00:24 xxxxxxxx kernel: [  268.802997]  ? nvkms_ioctl_common+0x42/0x80 [nvidia_modeset]
Mar 28 12:00:24 xxxxxxxx kernel: [  268.803006]  ? nvkms_ioctl+0xc4/0x100 [nvidia_modeset]
Mar 28 12:00:24 xxxxxxxx kernel: [  268.803141]  ? nvidia_frontend_unlocked_ioctl+0x3b/0x50 [nvidia]
Mar 28 12:00:24 xxxxxxxx kernel: [  268.803144]  ? do_vfs_ioctl+0x407/0x670
Mar 28 12:00:24 xxxxxxxx kernel: [  268.803146]  ? do_fcntl+0x22f/0x560
Mar 28 12:00:24 xxxxxxxx kernel: [  268.803148]  ? putname+0x4a/0x50
Mar 28 12:00:24 xxxxxxxx kernel: [  268.803150]  ? ksys_ioctl+0x67/0x90
Mar 28 12:00:24 xxxxxxxx kernel: [  268.803152]  ? __x64_sys_ioctl+0x1a/0x20
Mar 28 12:00:24 xxxxxxxx kernel: [  268.803154]  ? do_syscall_64+0x57/0x190
Mar 28 12:00:24 xxxxxxxx kernel: [  268.803157]  ? entry_SYSCALL_64_after_hwframe+0x44/0xa9
Mar 28 12:00:24 xxxxxxxx kernel: [  268.803159] Modules linked in: rfcomm wireguard ip6_udp_tunnel udp_tunnel cmac algif_hash algif_skcipher af_alg bnep binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi intel_rapl_msr mei_hdcp snd_hda_intel snd_intel_dspcfg snd_hda_codec snd_hda_core btusb snd_usb_audio btrtl snd_seq_midi snd_usbmidi_lib btbcm snd_seq_midi_event btintel snd_hwdep mc dell_smm_hwmon bluetooth intel_rapl_common x86_pkg_temp_thermal ecdh_generic intel_powerclamp snd_pcm ecc snd_rawmidi coretemp input_leds kvm_intel snd_seq dell_wmi dell_smbios dcdbas kvm sparse_keymap dell_wmi_descriptor intel_wmi_thunderbolt rapl intel_cstate wmi_bmof snd_seq_device snd_timer snd mei_me soundcore mei ie31200_edac intel_pch_thermal mac_hid acpi_pad nvidia_uvm(O) sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 dm_crypt hid_generic usbhid hid uas usb_storage nvidia_drm(PO) nvidia_modeset(PO) nvidia(PO) crct10dif_pclmul crc32_pclmul ghash_clmulni_intel nvme aesni_intel drm_kms_helper crypto_simd cryptd syscopyarea
Mar 28 12:00:24 xxxxxxxx kernel: [  268.803183]  sysfillrect glue_helper sysimgblt fb_sys_fops e1000e ahci drm nvme_core libahci i2c_i801 wmi video [last unloaded: vboxdrv]
Mar 28 12:00:24 xxxxxxxx kernel: [  268.803190] CR2: 0000000000000070
Mar 28 12:00:24 xxxxxxxx kernel: [  268.803191] ---[ end trace 0ed57fc96c94cd9e ]---
Mar 28 12:00:24 xxxxxxxx kernel: [  268.828895] RIP: 0010:_nv002691kms+0x18/0x70 [nvidia_modeset]
Mar 28 12:00:24 xxxxxxxx kernel: [  268.828899] Code: 24 1f 01 eb b2 66 2e 0f 1f 84 00 00 00 00 00 0f 1f 00 41 54 55 49 89 fc 53 89 d5 41 b8 04 00 00 00 ba 02 01 02 00 48 83 ec 10 <8b> 46 70 8b 3d 4f e8 0c 00 48 8d 4c 24 0c 89 ee 89 44 24 0c e8 bf
Mar 28 12:00:24 xxxxxxxx kernel: [  268.828900] RSP: 0018:ffffb60d8173fc50 EFLAGS: 00010286
Mar 28 12:00:24 xxxxxxxx kernel: [  268.828902] RAX: 0000000000000000 RBX: ffff9bfbd3722008 RCX: 00000000000000da
Mar 28 12:00:24 xxxxxxxx kernel: [  268.828903] RDX: 0000000000020102 RSI: 0000000000000000 RDI: ffff9bfbd3722008
Mar 28 12:00:24 xxxxxxxx kernel: [  268.828904] RBP: 0000000000010009 R08: 0000000000000004 R09: 0000000000000020
Mar 28 12:00:24 xxxxxxxx kernel: [  268.828905] R10: 0000000000000000 R11: ffff9bfbd22c9098 R12: ffff9bfbd3722008
Mar 28 12:00:24 xxxxxxxx kernel: [  268.828906] R13: ffff9bfbd37220a0 R14: 0000000000000fff R15: 0000000000010008
Mar 28 12:00:24 xxxxxxxx kernel: [  268.828907] FS:  00007f7c59bdba40(0000) GS:ffff9bfbddac0000(0000) knlGS:0000000000000000
Mar 28 12:00:24 xxxxxxxx kernel: [  268.828908] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Mar 28 12:00:24 xxxxxxxx kernel: [  268.828909] CR2: 0000000000000070 CR3: 0000000406e7e006 CR4: 00000000003606e0
Mar 28 12:00:24 xxxxxxxx kernel: [  268.828909] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Mar 28 12:00:24 xxxxxxxx kernel: [  268.828910] DR3: 0000000000000000 DR6: 00000000fffe0ff0 DR7: 0000000000000400
Mar 28 12:00:32 xxxxxxxx kernel: [  277.397324] NVRM: GPU at PCI:0000:01:00: GPU-0fc62206-e35e-1442-fdfb-f0e4bb824fd2
Mar 28 12:00:32 xxxxxxxx kernel: [  277.397362] NVRM: GPU Board Serial Number: 0323917047231
Mar 28 12:00:32 xxxxxxxx kernel: [  277.397372] NVRM: Xid (PCI:0000:01:00): 16, pid=0, Head 00000000 Count 000012e1
Mar 28 12:00:40 xxxxxxxx kernel: [  285.589251] NVRM: Xid (PCI:0000:01:00): 16, pid=0, Head 00000000 Count 000012e2
Mar 28 12:00:49 xxxxxxxx kernel: [  293.781313] NVRM: Xid (PCI:0000:01:00): 16, pid=0, Head 00000000 Count 000012e3
Mar 28 12:00:56 xxxxxxxx kernel: [  301.597807] bpfilter: Loaded bpfilter_umh pid 3205
Mar 28 12:00:56 xxxxxxxx kernel: [  301.598086] Started bpfilter
Mar 28 12:00:57 xxxxxxxx kernel: [  301.973328] NVRM: Xid (PCI:0000:01:00): 16, pid=0, Head 00000000 Count 000012e4
Mar 28 12:01:01 xxxxxxxx CRON[3225]: (root) CMD ([ -x /etc/init.d/anacron ] && if [ ! -d /run/systemd/system ]; then /usr/sbin/invoke-rc.d anacron start >/dev/null; fi)
Mar 28 12:01:05 xxxxxxxx kernel: [  310.165293] NVRM: Xid (PCI:0000:01:00): 16, pid=0, Head 00000000 Count 000012e5

```

After that failure I am still able to ssh into the machine. However, *sudo reboot* fails, I have to force a restart using the power button.

---

### Post by dimitri-papadopoulos on 2021-10-16
I eventually contacted Dell support and was sent a new GM107GL graphics card (under extended warranty). Double improvement:

[LIST]
[*]no more [freezing with the Nouveau driver]("https://ubuntuforums.org/showthread.php?t=2459862") (fingers crossed), 
[*]much less noise from the workstation (although I had cleaned the graphics card fan with compressed air). 
[/LIST]
  I will test soon whether the Nvidia driver works any better with the new GM107GL graphics card. It looks like the previous GM107GL graphics card really had been defective from the start.

---

### Post by MAFoElffen on 2021-10-16
Once you do... Please run the UbuntuForum's system-info script in my signature line to gather hardware and system settings information so that we can see which kernel you are usong, which desktop, and a lot of other graphics related information, so we are not just guessing what those are.

I, even though I have supported the Linux Graphics Layer for years, and NVidia Graphics (among others) in Linux... Know that the current HWE Hardware Enablement Stack is having issues with the NVidia Drivers on some hardware combinations. One of my desktops was one of those. Just saying that outfront. 

The above script also reports information if you have the HWE installed and what versions of... To diagnose that.

---

### Post by dimitri-papadopoulos on 2021-10-21
Unfortunately I'm still experiencing freezes with the new GM107GL under Nouveau. No reason it works any better with the Nvidia driver, but I'll give it a try.

Here is the requested info:
[https://paste.ubuntu.com/p/hKxhnwqHHB/](https://paste.ubuntu.com/p/hKxhnwqHHB/)

---

### Post by dimitri-papadopoulos on 2021-10-21
I attempted to install the Nvidia proprietary driver again, after the graphics card exchange.

Same problems:

[LIST]
[*]reboot after installing the Nvidia driver with **[FONT=courier new]software-properties-gtk[/FONT]** 
[*]I do see a graphical login screen after reboot 
[*]black screen from the moment I enter my password and hit Enter in the login screen, 
[*]still able to log into the workstation with SSH 
[*]able to uninstall the proprietary Nvidia driver from command line 
[*]unable to reboot with `sudo reboot`, had to power down using the power button 
[*]works fine after reboot with the Nouveau driver (except for the occasional freezes as already explained) 
[/LIST]

The Dell ePSA pre-boot diagnostics don't report any problem.

Finally, please note these Nvidia issue (and the Nouveau issue) has been going on for 3+ years, with ubuntu 16.04, Ubuntu 18.04, and Ubuntu 20.04.

---

### Post by dimitri-papadopoulos on 2021-10-21
Here is the kernel log:
[https://pastebin.ubuntu.com/p/RG76fdsppH/](https://pastebin.ubuntu.com/p/RG76fdsppH/)

The problems start here, right after I enter the password and hit Enter in the login screen:
```

[  106.236115] nvidia-modeset: ERROR: GPU:0: Display engine push buffer channel allocation failed: 0x65 (Call timed out [NV_ERR_TIMEOUT])
[  106.236981] nvidia-modeset: ERROR: GPU:0: Failed to allocate display engine core DMA push buffer
[  110.240735] rfkill: input handler enabled
[  110.518675] BUG: kernel NULL pointer dereference, address: 0000000000000070
[  110.518681] #PF: supervisor read access in kernel mode
[  110.518684] #PF: error_code(0x0000) - not-present page
[  110.518686] PGD 0 P4D 0 
[  110.518692] Oops: 0000 [#1] SMP PTI
[  110.518697] CPU: 7 PID: 2440 Comm: Xorg Tainted: P           O      5.4.0-89-generic #100-Ubuntu
[  110.518700] Hardware name: Dell Inc. Precision Tower 3620/0MWYPT, BIOS 2.18.1 07/09/2021
[  110.518741] RIP: 0010:_nv002523kms+0x18/0x70 [nvidia_modeset]
[  110.518745] Code: 24 1f 01 eb b2 66 2e 0f 1f 84 00 00 00 00 00 0f 1f 00 41 54 55 49 89 fc 53 89 d5 41 b8 04 00 00 00 ba 02 01 02 00 48 83 ec 10 <8b> 46 70 8b 3d 0f 73 0c 00 48 8d 4c 24 0c 89 ee 89 44 24 0c e8 cf
[  110.518748] RSP: 0018:ffffb10a41313c50 EFLAGS: 00010286
[  110.518752] RAX: 0000000000000000 RBX: ffff9a4993d50008 RCX: 00000000000000d4
[  110.518755] RDX: 0000000000020102 RSI: 0000000000000000 RDI: ffff9a4993d50008
[  110.518757] RBP: 0000000000010009 R08: 0000000000000004 R09: 00000000fffffffe
[  110.518760] R10: 0000000000000000 R11: 0000000000000001 R12: ffff9a4993d50008
[  110.518762] R13: ffff9a4993d500a0 R14: 0000000000000fff R15: 0000000000010008
[  110.518766] FS:  00007f501e1f3a40(0000) GS:ffff9a499dbc0000(0000) knlGS:0000000000000000
[  110.518769] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[  110.518771] CR2: 0000000000000070 CR3: 0000000407e94004 CR4: 00000000003606e0
[  110.518774] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  110.518776] DR3: 0000000000000000 DR6: 00000000fffe0ff0 DR7: 0000000000000400
[  110.518778] Call Trace:
[  110.518816]  ? _nv002522kms+0xb1/0x150 [nvidia_modeset]
[  110.518851]  ? _nv002301kms+0x489/0x670 [nvidia_modeset]
[  110.518859]  ? __check_object_size+0x13f/0x150
[  110.518866]  ? _copy_from_user+0x3e/0x60
[  110.518889]  ? _nv000451kms+0xa0/0xa0 [nvidia_modeset]
[  110.518911]  ? _nv000663kms+0x34/0x50 [nvidia_modeset]
[  110.518933]  ? nvKmsIoctl+0x96/0x1d0 [nvidia_modeset]
[  110.518957]  ? nvkms_ioctl_common+0x42/0x80 [nvidia_modeset]
[  110.518980]  ? nvkms_ioctl+0xc4/0x100 [nvidia_modeset]
[  110.519298]  ? nvidia_frontend_unlocked_ioctl+0x3b/0x50 [nvidia]
[  110.519306]  ? do_vfs_ioctl+0x407/0x670
[  110.519310]  ? do_fcntl+0x22f/0x560
[  110.519315]  ? putname+0x4a/0x50
[  110.519320]  ? ksys_ioctl+0x67/0x90
[  110.519325]  ? __x64_sys_ioctl+0x1a/0x20
[  110.519331]  ? do_syscall_64+0x57/0x190
[  110.519336]  ? entry_SYSCALL_64_after_hwframe+0x44/0xa9
[  110.519340] Modules linked in: rfcomm wireguard ip6_udp_tunnel udp_tunnel vboxnetadp(O) vboxnetflt(O) vboxdrv(O) cmac algif_hash algif_skcipher af_alg bnep binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi intel_rapl_msr mei_hdcp snd_hda_intel snd_intel_dspcfg snd_hda_codec snd_usb_audio snd_usbmidi_lib snd_hda_core snd_hwdep dell_smm_hwmon snd_seq_midi intel_rapl_common snd_seq_midi_event btusb x86_pkg_temp_thermal snd_rawmidi snd_seq btrtl intel_powerclamp btbcm coretemp btintel mc input_leds kvm_intel bluetooth dell_wmi kvm snd_pcm mei_me ecdh_generic ecc snd_seq_device rapl dell_smbios snd_timer mei intel_pch_thermal intel_cstate dcdbas dell_wmi_descriptor sparse_keymap snd intel_wmi_thunderbolt wmi_bmof ie31200_edac soundcore mac_hid acpi_pad nvidia_uvm(O) sch_fq_codel msr parport_pc ppdev lp parport ip_tables x_tables autofs4 dm_crypt hid_generic usbhid hid nvidia_drm(PO) nvidia_modeset(PO) nvidia(PO) crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel drm_kms_helper crypto_simd
[  110.519390]  nvme cryptd glue_helper syscopyarea sysfillrect sysimgblt fb_sys_fops e1000e i2c_i801 drm ahci nvme_core libahci wmi video
[  110.519406] CR2: 0000000000000070
[  110.519410] ---[ end trace aa620f0211b859d1 ]---
```

---

### Post by MAFoElffen on 2021-10-22
I don't see "anything" glaring out at me, from the system-info script report.

I see the system SMBIOS settings, which look all okay. I see that SecureBoot is off, like you said.

I see that you are updated to the latest BIOS available for that machine.

I see that you are running Gnome on XServer/X11 and that should be the best for that GPU.

I see what the specific GPu is... and that it is not only supported by NVidia Driver 460, but is also supported by 470.x: [https://www.nvidia.com/Download/driverResults.aspx/180475/en-us](https://www.nvidia.com/Download/driverResults.aspx/180475/en-us)

I see that it is an Ubuntu Certified Hardware platform, that is supported and safe to run HWE (the Hardware Enablement Stack), but that is not installed. That may help with your graphics...

I don't see anything blatantly hitting me in the face...

I see the kernel errors about nvidia_modeset errors, but not understanding really why that is occurring. What i find when I look into Null Pointer Deference errors with that address (0000000000000070), the only thing I see mentioned for that is a possible conflict with a network device, kinds of errors. Maybe post an lshw on wg0.

You are using XServer, but I do not see a posted xserver log. That may show something (hopefully).

---

### Post by dimitri-papadopoulos on 2021-10-25
I have just added the HWE:
```
sudo apt install --install-recommends linux-generic-hwe-20.04
```

I'll try again with 460 and 470 and send xservers logs - I seem to recall there's nothing interesting in them but you never know.

As far as I know, the two SDD disks are the only "exotic" thing on this workstation.
[LIST]
[*]PM961 NVMe SAMSUNG 512GB (I (think that was the default one on this workstation) 
[*]SK hynix SC300B SATA 512GB (I think that's the optional one but validated by Dell for this workstation) 
[/LIST]
 
Here is the output of **lshw**:
** lshw**: [https://pastebin.ubuntu.com/p/9TJ5jpQBCD/](https://pastebin.ubuntu.com/p/9TJ5jpQBCD/)

---

### Post by dimitri-papadopoulos on 2021-10-25
Doesn't work any better with the HWE 5.11 kernel. Again, I get a black screen right after entering the password and hitting Enter in the Gnome login screen, with both Nvidia drivers 460 and 470.

Again, here is the kernel log, as obtained with **dmesg**, right after the crash with driver 470:
```

[  191.636119] nvidia-modeset: ERROR: GPU:0: Display engine push buffer channel allocation failed: 0x65 (Call timed out [NV_ERR_TIMEOUT])
[  191.636769] nvidia-modeset: ERROR: GPU:0: Failed to allocate display engine core DMA push buffer
[  195.641869] rfkill: input handler enabled
[  195.920430] BUG: kernel NULL pointer dereference, address: 0000000000000070
[  195.920440] #PF: supervisor read access in kernel mode
[  195.920444] #PF: error_code(0x0000) - not-present page
[  195.920448] PGD 0 P4D 0 
[  195.920454] Oops: 0000 [#1] SMP PTI
[  195.920461] CPU: 0 PID: 2622 Comm: Xorg Tainted: P           O      5.11.0-38-generic #42~20.04.1-Ubuntu
[  195.920468] Hardware name: Dell Inc. Precision Tower 3620/0MWYPT, BIOS 2.18.1 07/09/2021
[  195.920471] RIP: 0010:_nv002523kms+0x18/0x70 [nvidia_modeset]
[  195.920532] Code: 24 1f 01 eb b2 66 2e 0f 1f 84 00 00 00 00 00 0f 1f 00 41 54 55 49 89 fc 53 89 d5 41 b8 04 00 00 00 ba 02 01 02 00 48 83 ec 10 <8b> 46 70 8b 3d ff 72 0c 00 48 8d 4c 24 0c 89 ee 89 44 24 0c e8 cf
[  195.920538] RSP: 0018:ffffad7ac095bcf0 EFLAGS: 00010286
[  195.920544] RAX: 0000000000000000 RBX: ffff8fc9cf203008 RCX: 00000000000007ac
[  195.920548] RDX: 0000000000020102 RSI: 0000000000000000 RDI: ffff8fc9cf203008
[  195.920552] RBP: 0000000000010009 R08: 0000000000000004 R09: ffffffffc05d8c00
[  195.920556] R10: 0000000000000000 R11: 0000000000000001 R12: ffff8fc9cf203008
[  195.920560] R13: ffff8fc9cf2030a0 R14: 0000000000000fff R15: 0000000000010008
[  195.920564] FS:  00007f2ea73d8a40(0000) GS:ffff8fccddc00000(0000) knlGS:0000000000000000
[  195.920569] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[  195.920574] CR2: 0000000000000070 CR3: 000000010bf66005 CR4: 00000000003706f0
[  195.920578] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  195.920582] DR3: 0000000000000000 DR6: 00000000fffe0ff0 DR7: 0000000000000400
[  195.920585] Call Trace:
[  195.920591]  ? _nv002522kms+0xb1/0x150 [nvidia_modeset]
[  195.920646]  ? _nv002301kms+0x489/0x670 [nvidia_modeset]
[  195.920700]  ? __kmalloc+0x430/0x470
[  195.920710]  ? __check_object_size+0x13f/0x150
[  195.920717]  ? _copy_from_user+0x3f/0x80
[  195.920725]  ? _nv000451kms+0xa0/0xa0 [nvidia_modeset]
[  195.920761]  ? _nv000663kms+0x34/0x50 [nvidia_modeset]
[  195.920795]  ? nvKmsIoctl+0x96/0x1d0 [nvidia_modeset]
[  195.920830]  ? nvkms_ioctl_common+0x42/0x80 [nvidia_modeset]
[  195.920866]  ? nvkms_ioctl+0xbf/0x110 [nvidia_modeset]
[  195.920900]  ? nvidia_frontend_unlocked_ioctl+0x3b/0x50 [nvidia]
[  195.921412]  ? __x64_sys_ioctl+0x91/0xc0
[  195.921420]  ? do_syscall_64+0x38/0x90
[  195.921426]  ? entry_SYSCALL_64_after_hwframe+0x44/0xa9
[  195.921437] Modules linked in: wireguard curve25519_x86_64 libchacha20poly1305 chacha_x86_64 poly1305_x86_64 libblake2s blake2s_x86_64 ip6_udp_tunnel udp_tunnel libcurve25519_generic libchacha libblake2s_generic vboxnetadp(O) vboxnetflt(O) vboxdrv(O) binfmt_misc nls_iso8859_1 snd_hda_codec_hdmi snd_hda_intel snd_intel_dspcfg soundwire_intel intel_rapl_msr soundwire_generic_allocation soundwire_cadence mei_hdcp snd_hda_codec snd_hda_core intel_rapl_common soundwire_bus x86_pkg_temp_thermal intel_powerclamp snd_soc_core coretemp snd_compress kvm_intel ac97_bus dell_smm_hwmon snd_pcm_dmaengine kvm snd_usb_audio dell_wmi dell_smbios snd_usbmidi_lib dcdbas snd_hwdep rapl mc intel_cstate snd_seq_midi snd_seq_midi_event input_leds snd_pcm sparse_keymap intel_wmi_thunderbolt snd_rawmidi wmi_bmof dell_wmi_descriptor efi_pstore snd_seq snd_seq_device snd_timer ee1004 snd mei_me soundcore mei intel_pch_thermal ie31200_edac mac_hid acpi_pad nvidia_uvm(PO) sch_fq_codel msr parport_pc ppdev lp
[  195.921548]  parport ip_tables x_tables autofs4 dm_crypt hid_generic usbhid hid nvidia_drm(PO) nvidia_modeset(PO) nvidia(PO) drm_kms_helper crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel crypto_simd syscopyarea sysfillrect sysimgblt cryptd fb_sys_fops glue_helper cec rc_core e1000e nvme drm i2c_i801 nvme_core ahci i2c_smbus xhci_pci libahci xhci_pci_renesas wmi video
[  195.921607] CR2: 0000000000000070
[  195.921612] ---[ end trace 520eb3b7391bf81b ]---
[  195.948213] RIP: 0010:_nv002523kms+0x18/0x70 [nvidia_modeset]
[  195.948273] Code: 24 1f 01 eb b2 66 2e 0f 1f 84 00 00 00 00 00 0f 1f 00 41 54 55 49 89 fc 53 89 d5 41 b8 04 00 00 00 ba 02 01 02 00 48 83 ec 10 <8b> 46 70 8b 3d ff 72 0c 00 48 8d 4c 24 0c 89 ee 89 44 24 0c e8 cf
[  195.948276] RSP: 0018:ffffad7ac095bcf0 EFLAGS: 00010286
[  195.948279] RAX: 0000000000000000 RBX: ffff8fc9cf203008 RCX: 00000000000007ac
[  195.948281] RDX: 0000000000020102 RSI: 0000000000000000 RDI: ffff8fc9cf203008
[  195.948282] RBP: 0000000000010009 R08: 0000000000000004 R09: ffffffffc05d8c00
[  195.948284] R10: 0000000000000000 R11: 0000000000000001 R12: ffff8fc9cf203008
[  195.948285] R13: ffff8fc9cf2030a0 R14: 0000000000000fff R15: 0000000000010008
[  195.948287] FS:  00007f2ea73d8a40(0000) GS:ffff8fccddc00000(0000) knlGS:0000000000000000
[  195.948289] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[  195.948291] CR2: 0000000000000070 CR3: 000000010bf66005 CR4: 00000000003706f0
[  195.948293] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  195.948294] DR3: 0000000000000000 DR6: 00000000fffe0ff0 DR7: 0000000000000400
[  204.058940] NVRM: GPU at PCI:0000:01:00: GPU-213658c7-a8f6-8ff8-0e64-bb1c57e0b47e
[  204.058985] NVRM: Xid (PCI:0000:01:00): 16, pid=0, Head 00000000 Count 00001465

```

Here is the whole kernel log:
**dmesg**: [https://pastebin.ubuntu.com/p/CVfNcBFSRw/](https://pastebin.ubuntu.com/p/CVfNcBFSRw/)

Here are the X server logs, **Xorg.0.log** which predates the login attempt and **Xorg.1.log** which is created right after the login attempt:
**Xorg.0.log**: [https://pastebin.ubuntu.com/p/MbnrMrFVGN/](https://pastebin.ubuntu.com/p/MbnrMrFVGN/)
**Xorg.1.log**: [https://pastebin.ubuntu.com/p/PFyKXgSFcM/](https://pastebin.ubuntu.com/p/PFyKXgSFcM/)

---

### Post by MAFoElffen on 2021-10-26
I looked through your xorg logs and I see something curoius that might be where it is wigging out.
```
[    26.988] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    26.988] (==) NVIDIA(0):     will be used as the requested mode. 
[    26.988] (==) NVIDIA(0):
[    26.988] (II) NVIDIA(0): Validated MetaModes: 
[    26.988] (II) NVIDIA(0):     "DFP-6:nvidia-auto-select"
[    26.988] (II) NVIDIA(0): Virtual screen size determined to be 3840 x 2160 
[    26.992] (--) NVIDIA(0): DPI set to (139, 137); computed from "UseEdidDpi" X config

```
I'm thinking your display does not support those modes... LOL That follows suit with the nvidia_modeset error you set in dmesg.

What happens ifyou create an xorg.conf file and set a default mode of 1920x1024? Or any mode that your display does support?

Or set it via KMS by setting a helper in the Grub defaults file, so it takes it early on in the Linux Kernel boot?

---

### Post by dimitri-papadopoulos on 2021-11-03
After changing the graphics card, Dell changed the motherboard last  week. Since then, I haven't experienced X server freezes with the  Nouveau driver, and I am able to use the proprietary Nvidia driver.

That doesn't necessarily mean it was hardware issue, but perhaps   different BIOS settings. Changing the mother board obviously reset the  BIOS settings. For comparison, here is the output of **system-info** after the upgrade:
[https://pastebin.ubuntu.com/p/2Yg3QFsnd4/](https://pastebin.ubuntu.com/p/2Yg3QFsnd4/)

The display itself is a [Dell UltraSharp 32 UP3216Q]("https://www.dell.com/support/home/product-support/product/dell-up3216q-monitor/overview") monitor, it is supposed to support its native 3[FONT=sans-serif]840 × 2160 resolution.[/FONT]

---

### Post by dimitri-papadopoulos on 2021-11-03
The main difference I see in the **system-info** output:

[LIST]
[*]Dell replaced the previous **A05** motherboard (**Size: 3615MHz**) with an **A01** motherboard (**Size: 2489MHz**).
[/LIST]
 
Here is the new **lshw** output:
[https://pastebin.ubuntu.com/p/Dy2NTghGvZ/](https://pastebin.ubuntu.com/p/Dy2NTghGvZ/)

Again, the main difference I see:
[LIST]
[*]For the new **A01** motherboard **size: 900MHz**, compared to the previous **A05** motherboard, for which **size: 2232MHz**.
[/LIST]

Here is a new **dmesg** output:
[URL="https://pastebin.ubuntu.com/p/TGM3XNTpYM/"]https://pastebin.ubuntu.com/p/TGM3XNTpYM/

[/URL]The main difference I see:
[LIST]
[*]I now have 4 cores (**setup_percpu: NR_CPUS:8192 nr_cpumask_bits:4 nr_cpu_ids:4 nr_node_ids:1**) instead of 8 cores previously (**setup_percpu: NR_CPUS:8192 nr_cpumask_bits:8 nr_cpu_ids:8 nr_node_ids:1**). I guess hyper-threading might be disabled in the BIOS or something like that.
[/LIST]

Should I first look into the hyper-threading BIOS setting, or whatever causes the difference in the number of CPUs?

---

### Post by dimitri-papadopoulos on 2021-11-03
Actually this difference of size seems related to the number of cores:
[https://en.wikipedia.org/wiki/Front-side_bus#CPU](https://en.wikipedia.org/wiki/Front-side_bus#CPU)

I will re-enable hyper-threading and check 1) how size changes and 2) whether I can reproduce the driver issue with hyper-threading.

---

### Post by dimitri-papadopoulos on 2021-11-03
After enabling hyper-threading in the BIOS settings, the Nvidia driver still works.

Perhaps it was a hardware issue after all.

---

### Post by dimitri-papadopoulos on 2021-11-06
Just for future reference, here is the output of **system-info** after enabling hyper-threading on the new **A01** motherboard:
[https://paste.ubuntu.com/p/fwP3rCsgxr/](https://paste.ubuntu.com/p/fwP3rCsgxr/)

No substantial differences!

Again, I suppose this was a hardware problem, solved by changing the motherboard.

---

