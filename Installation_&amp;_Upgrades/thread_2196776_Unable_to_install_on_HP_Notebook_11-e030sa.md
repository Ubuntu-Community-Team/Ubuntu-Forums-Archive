---
title: "Unable to install on HP Notebook 11-e030sa"
date: 2013-12-31
forum: Installation &amp; Upgrades
---

### Post by penguintutor on 2013-12-31
I have installed Linux (mainly one of the variants of Ubuntu) onto lots of computers, but this new laptop has really got me stuck.

I have a HP Pavilion TouchSmart 11" Notebook PC.

It came pre-installed with Windows 8 and I've been trying to set it up as dual boot with Linux for several days. 


Technical details are (perhaps the video is the most relevant) 


Processor family
        AMD Dual-Core A Series processsor
Processor
    AMD Dual-Core A4-1250 APU with Radeon HD 8210 Graphics (1 GHz, 1 MB cache) 
Display
    29,4 cm (11.6") diagonal HD anti-glare WLED (1366x768) (3.6mm) WVA Touchscreen 
Graphics
    AMD Radeon HD 8210 Graphics 

Secure Boot is disabled
Legacy Boot is disabled


My first attempt to install Ubuntu 13.10 failed after which I have tested using various distributions and versions but have not been able to get a working Linux distribution installed.

With Ubuntu 13.10 when attemping to boot into "Try Ubuntu before installing" the computer ends up with a blank screen.

Some errors I have seen (only brief snippets) - much of the code scrolls off the screen


**Ubuntu 12.10**

This is the same as seen when using xubuntu 13.10
X appears to fail and then drop to a command shell. Starting X gives the following error:

```

xorg-server 2:1.13.3-0ubuntu6~precise2 
Current version of pixman: 0.24.4
(==) Using system config directory "/user/share/X11/xorg.conf.d"
Initializing built-in extension Generic Event Extension
...
Initializing built-in extension DRI2
Loading extensions GLX

fatal server error:
no screens found
(EE)
...
Server terminated with error (1). Closing log file
```



**On SuSE **
Obviously this is not directly relevant to the Ubuntu, but shows that other Linux distributions are having problems and with different error messages.

```
Code: Bad RIP value.
RIP [<         (null)>]       (null)
RSP <ffff80010dbbcb0>
CRZ: 00000000000000000
BUG: unable to handle kernel paging request at ffffffffffffffd0
...
Lots of similar messages 
...
Kernel panic - not syncing: Watchdog detected hard LOCKUP on cpu 1
Shutting down cpus with MMI
drm_kms_helper: panic occurred, switching back to test console

```


The closest I have got is with Fedora 20 which installed and worked until the next day (presumbly with an update installed) but then gave a similar error to the SuSE message above. It did the same after installing a second time.

It is obviously Ubuntu I'd like to install, but the other is provided in case that provides some relevant information as well.

I believe this may be a problem with the video driver. I have tried with external screens connected as well (both to the HDMI port and the VGA port) but still get the same error. 


Does anyone have any suggestions of how I can get Ubuntu to install?

---

### Post by sudodus on 2013-12-31
I think it can be problems with the graphics driver too. Have you tried with some [boot options]("https://help.ubuntu.com/community/BootOptions")? I suggest that you start with ***nomodeset***, but try with some other options too.

---

### Post by joshua.korin on 2013-12-31
i think you should make ubuntu live usb

---

### Post by penguintutor on 2013-12-31
Thanks for the suggestion, but I've already tried nomodeset and a couple of other options.

I forgot to mention that I do get an intial X display with the ubuntu logo, but it's after then that it fails. 

For example if I add radeon.modeset=0 
then I see the boot splash screeen and then a screen full of start / stop messages (eg. 

```
* Stopping Failsafe Boot Delay
* Starting System V initialisation compatibility
* Starting 
* Starting
* Starting ACPI daemon
* Starting 
* Starting
* Starting save kernel messages
* Starting
* Starting
* Starting regular background program processing daemon
...
* Starting load fallback graphics devices
* Stopping save kernel messages
...
* Stopping System V runlevel compatibility
* Starting
* Starting
* Stopping
* Stopping enable remaining boot-time encrypted block devices

```

I can get to a shell prompt (CTRL-F1), but when trying to start X I get

```
(II) [KMS] drm report modesetting isn't supported.
(II) [KMS] drm report modesetting isn't supported.
(II) [KMS] drm report modesetting isn't supported.
(II) [KMS] drm report modesetting isn't supported.
(II) [KMS] drm report modesetting isn't supported.
(EE)
Fatal server error:
(EE) no screens found(EE)
(EE)
...
(EE) Server terminated with error (1). Closing log file.
xinit: giving up
xinit unable to connect to X server: Connection refused
xinit: server error
```


I have also tried video=VGA:800x600  (with monitor connected to video port)
but that doesn't appear to have any effect - still uses the internal screen for the boot screen then symptoms as above.




I get the same error using Ubuntu Live DVD (external DVD drive) and Ubuntu Live USB.

---

### Post by sudodus on 2013-12-31
Try with the boot option ***text*** to get only text (no graphics). Then you can try to install a proprietary driver for the graphics card and reboot.

*Edit*: add boot options according to this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by longlivexue on 2014-01-01
> **penguintutor said:**
> I have installed Linux (mainly one of the variants of Ubuntu) onto lots of computers, but this new laptop has really got me stuck.

I have a HP Pavilion TouchSmart 11" Notebook PC.

It came pre-installed with Windows 8 and I've been trying to set it up as dual boot with Linux for several days. 


Technical details are (perhaps the video is the most relevant) 


Processor family
        AMD Dual-Core A Series processsor
Processor
    AMD Dual-Core A4-1250 APU with Radeon HD 8210 Graphics (1 GHz, 1 MB cache) 
Display
    29,4 cm (11.6") diagonal HD anti-glare WLED (1366x768) (3.6mm) WVA Touchscreen 
Graphics
    AMD Radeon HD 8210 Graphics 

Secure Boot is disabled
Legacy Boot is disabled


My first attempt to install Ubuntu 13.10 failed after which I have tested using various distributions and versions but have not been able to get a working Linux distribution installed.

With Ubuntu 13.10 when attemping to boot into "Try Ubuntu before installing" the computer ends up with a blank screen.

Some errors I have seen (only brief snippets) - much of the code scrolls off the screen


**Ubuntu 12.10**

This is the same as seen when using xubuntu 13.10
X appears to fail and then drop to a command shell. Starting X gives the following error:

```

xorg-server 2:1.13.3-0ubuntu6~precise2 
Current version of pixman: 0.24.4
(==) Using system config directory "/user/share/X11/xorg.conf.d"
Initializing built-in extension Generic Event Extension
...
Initializing built-in extension DRI2
Loading extensions GLX

fatal server error:
no screens found
(EE)
...
Server terminated with error (1). Closing log file
```



**On SuSE **
Obviously this is not directly relevant to the Ubuntu, but shows that other Linux distributions are having problems and with different error messages.

```
Code: Bad RIP value.
RIP [<         (null)>]       (null)
RSP <ffff80010dbbcb0>
CRZ: 00000000000000000
BUG: unable to handle kernel paging request at ffffffffffffffd0
...
Lots of similar messages 
...
Kernel panic - not syncing: Watchdog detected hard LOCKUP on cpu 1
Shutting down cpus with MMI
drm_kms_helper: panic occurred, switching back to test console

```


The closest I have got is with Fedora 20 which installed and worked until the next day (presumbly with an update installed) but then gave a similar error to the SuSE message above. It did the same after installing a second time.

It is obviously Ubuntu I'd like to install, but the other is provided in case that provides some relevant information as well.

I believe this may be a problem with the video driver. I have tried with external screens connected as well (both to the HDMI port and the VGA port) but still get the same error. 


Does anyone have any suggestions of how I can get Ubuntu to install?

Shake hands!

I got stuck with same problem with a new HP - [COLOR=#191918][FONT=Arial]HP Pavilion 15-n077so
[/FONT][/COLOR][http://www.gigantti.fi/product/tietokoneet/kannettavat-tietokoneet/HP15N077EO/hp-pavilion-15-n077so-15-6-kannettava](http://www.gigantti.fi/product/tietokoneet/kannettavat-tietokoneet/HP15N077EO/hp-pavilion-15-n077so-15-6-kannettava)

I also ended up with black screen in Windows 8's UEFI mode when intending to install Ubuntu

---

### Post by penguintutor on 2014-01-01
> **sudodus said:**
> Try with the boot option ***text*** to get only text (no graphics). Then you can try to install a proprietary driver for the graphics card and reboot.

*Edit*: add boot options according to this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Does Ubuntu still include a text based installer on the Desktop image? I think it has been dropped.

I am looking at a similar thing though - using the server based distro which uses a text based installer, then installing ubuntu-desktop from the command line. That should  give me the ability to either add a proprietary driver or changing the xorg.conf file to try and find a value that works. I didn't want to go down that path if I could help it, but running out of other ideas.

---

### Post by sudodus on 2014-01-01
It is possible to start from Ubuntu Server, but also from Ubuntu ***mini.iso,*** which has a text based installer, and from there you can select any of the desktop flavours. See [URL="https://help.ubuntu.com/community/Installation/MinimalCD"]this link
[/URL]
*Edit*: Lubuntu is still maintaining a text based installer, the alternate iso, but the other desktop flavours have dropped it. But these text based installers cannot create systems that boot in UEFI mode.

---

### Post by penguintutor on 2014-01-01
Propriatary drivers installed, but still no luck.

i have installed text based Ubuntu and it worked for a few minutes. Then as I tried and install the Ubuntu Desktop files it then has a Kernel panic. 


```
Jan  1 18:40:46 silverlink kernel: [   12.528408] EDAC amd64: DRAM ECC disabled.
Jan  1 18:40:46 silverlink kernel: [   12.528428] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Jan  1 18:40:46 silverlink kernel: [   12.528428]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Jan  1 18:40:46 silverlink kernel: [   12.528428]  (Note that use of the override may cause unknown side effects.)
Jan  1 18:40:46 silverlink kernel: [   12.565888] r8169 0000:01:00.0 p1p1: unable to load firmware patch rtl_nic/rtl8106e-1.fw (-2)
Jan  1 18:40:46 silverlink kernel: [   12.671805] BUG: unable to handle kernel NULL pointer dereference at 0000000000000208
Jan  1 18:40:46 silverlink kernel: [   12.671963] IP: [<ffffffffa01fb6c9>] radeon_vm_bo_add+0xa9/0xd0 [radeon]
Jan  1 18:40:46 silverlink kernel: [   12.672129] PGD 118e1c067 PUD 118436067 PMD 0 
Jan  1 18:40:46 silverlink kernel: [   12.672222] Oops: 0000 [#1] SMP 
Jan  1 18:40:46 silverlink kernel: [   12.672289] Modules linked in: joydev(F) amd_freq_sensitivity kvm_amd(F) kvm(F) crct10dif_pclmul(F) crc32_pclmul(F) ghash_clmulni_intel(F) aesni_intel(F) aes_x86_64(F) lrw(F) gf128mul(F) glue_helper(F) ablk_helper(F) cryptd(F) hp_wmi sparse_keymap microcode(F) psmouse(F) arc4(F) rt2800pci serio_raw(F) rt2800lib fam15h_power rt2x00pci rt2x00mmio k10temp rt2x00lib uvcvideo snd_hda_codec_realtek videobuf2_vmalloc mac80211 edac_core videobuf2_memops edac_mce_amd videobuf2_core snd_hda_codec_hdmi videodev rtsx_pci_ms cfg80211 radeon i2c_piix4 snd_hda_intel memstick ohci_pci ttm snd_hda_codec drm_kms_helper drm snd_hwdep(F) snd_pcm(F) snd_page_alloc(F) eeprom_93cx6 crc_ccitt(F) snd_timer(F) i2c_algo_bit snd(F) soundcore(F) wmi video(F) mac_hid lp(F) parport(F) rtsx_pci_sdmmc usb_storage(F) sdhci_pci sdhci ahci(F) libahci(F) rtsx_pci r8169 mii(F)
Jan  1 18:40:46 silverlink kernel: [   12.673864] CPU: 1 PID: 171 Comm: plymouthd Tainted: GF            3.11.0-12-generic #19-Ubuntu
Jan  1 18:40:46 silverlink kernel: [   12.674000] Hardware name: Hewlett-Packard HP Pavilion TS 11 Notebook PC/2178, BIOS F.05 08/16/2013
Jan  1 18:40:46 silverlink kernel: [   12.674139] task: ffff88011584aee0 ti: ffff880118e76000 task.ti: ffff880118e76000
Jan  1 18:40:46 silverlink kernel: [   12.674256] RIP: 0010:[<ffffffffa01fb6c9>]  [<ffffffffa01fb6c9>] radeon_vm_bo_add+0xa9/0xd0 [radeon]
Jan  1 18:40:46 silverlink kernel: [   12.674445] RSP: 0018:ffff880118e77b80  EFLAGS: 00010246
Jan  1 18:40:46 silverlink kernel: [   12.674530] RAX: ffff880118157910 RBX: ffff88011812d1e0 RCX: ffff880118e77fd8
Jan  1 18:40:46 silverlink kernel: [   12.674641] RDX: 0000000000000000 RSI: 0000000000000000 RDI: ffff880118157940
Jan  1 18:40:46 silverlink kernel: [   12.674752] RBP: ffff880118e77ba8 R08: 0000000000017380 R09: ffff88011812d1e0
Jan  1 18:40:46 silverlink kernel: [   12.674862] R10: 0000000000000002 R11: ffff88011584aee0 R12: ffff880118157900
Jan  1 18:40:46 silverlink kernel: [   12.674973] R13: 0000000000000200 R14: ffff88011812d210 R15: ffff880118157940
Jan  1 18:40:46 silverlink kernel: [   12.675085] FS:  00007f7153939740(0000) GS:ffff88011ec80000(0000) knlGS:0000000000000000
Jan  1 18:40:46 silverlink kernel: [   12.675209] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jan  1 18:40:46 silverlink kernel: [   12.675300] CR2: 0000000000000208 CR3: 0000000115bf7000 CR4: 00000000000407e0
Jan  1 18:40:46 silverlink kernel: [   12.675409] Stack:
Jan  1 18:40:46 silverlink kernel: [   12.679884]  ffff880118408000 ffff8801184ad400 0000000000000000 ffff880118157900
Jan  1 18:40:46 silverlink kernel: [   12.684530]  ffff8801184ad420 ffff880118e77be0 ffffffffa01e0bc3 ffff880118e77bd0
Jan  1 18:40:46 silverlink kernel: [   12.689170]  ffff8801184ad400 ffff880115ab82f0 ffff880117cc1c00 ffff880118d29800
Jan  1 18:40:46 silverlink kernel: [   12.693789] Call Trace:
Jan  1 18:40:46 silverlink kernel: [   12.698399]  [<ffffffffa01e0bc3>] radeon_driver_open_kms+0x83/0xf0 [radeon]
Jan  1 18:40:46 silverlink kernel: [   12.703061]  [<ffffffffa00e91f6>] drm_open+0x296/0x7d0 [drm]
Jan  1 18:40:46 silverlink kernel: [   12.707700]  [<ffffffffa00e983a>] drm_stub_open+0x10a/0x1a0 [drm]
Jan  1 18:40:46 silverlink kernel: [   12.712322]  [<ffffffff811ab833>] chrdev_open+0xa3/0x1b0
Jan  1 18:40:46 silverlink kernel: [   12.716932]  [<ffffffff811a4cab>] do_dentry_open+0x1eb/0x280
Jan  1 18:40:46 silverlink kernel: [   12.721508]  [<ffffffff811ab790>] ? cdev_put+0x30/0x30
Jan  1 18:40:46 silverlink kernel: [   12.726029]  [<ffffffff811a4dc9>] vfs_open+0x49/0x50
Jan  1 18:40:46 silverlink kernel: [   12.730522]  [<ffffffff811b4111>] do_last+0x1c1/0xe40
Jan  1 18:40:46 silverlink kernel: [   12.734991]  [<ffffffff8118d938>] ? kmem_cache_alloc_trace+0x108/0x130
Jan  1 18:40:46 silverlink kernel: [   12.739475]  [<ffffffff81316db3>] ? apparmor_file_alloc_security+0x23/0x40
Jan  1 18:40:46 silverlink kernel: [   12.743927]  [<ffffffff811b5981>] path_openat+0xc1/0x630
Jan  1 18:40:46 silverlink kernel: [   12.748366]  [<ffffffff811b5f12>] ? final_putname+0x22/0x50
Jan  1 18:40:46 silverlink kernel: [   12.752795]  [<ffffffff811b6119>] ? putname+0x29/0x40
Jan  1 18:40:46 silverlink kernel: [   12.757223]  [<ffffffff811b6cfa>] do_filp_open+0x3a/0x90
Jan  1 18:40:46 silverlink kernel: [   12.761579]  [<ffffffff816ec57e>] ? _raw_spin_lock+0xe/0x20
Jan  1 18:40:46 silverlink kernel: [   12.765860]  [<ffffffff811c3687>] ? __alloc_fd+0xa7/0x130
Jan  1 18:40:46 silverlink kernel: [   12.770079]  [<ffffffff811a5fac>] do_sys_open+0x12c/0x270
Jan  1 18:40:46 silverlink kernel: [   12.774249]  [<ffffffff811a610e>] SyS_open+0x1e/0x20
Jan  1 18:40:46 silverlink kernel: [   12.778382]  [<ffffffff816f521d>] system_call_fastpath+0x1a/0x1f
Jan  1 18:40:46 silverlink kernel: [   12.782508] Code: 4c 89 70 30 4c 89 70 38 e8 45 d2 4e e1 49 8b 44 24 10 4c 89 ff 4c 89 70 08 48 89 43 30 49 8d 44 24 10 48 89 43 38 4d 89 74 24 10 <49> 8b 45 08 49 89 5d 08 4c 89 2b 48 89 43 08 48 89 18 e8 b0 d1 
Jan  1 18:40:46 silverlink kernel: [   12.791533] RIP  [<ffffffffa01fb6c9>] radeon_vm_bo_add+0xa9/0xd0 [radeon]
Jan  1 18:40:46 silverlink kernel: [   12.795914]  RSP <ffff880118e77b80>
Jan  1 18:40:46 silverlink kernel: [   12.800213] CR2: 0000000000000208
Jan  1 18:40:46 silverlink kernel: [   12.804408] ---[ end trace ff119efb50122f6d ]---
Jan  1 18:40:46 silverlink kernel: [   12.805521] r8169 0000:01:00.0 p1p1: link down
Jan  1 18:40:46 silverlink kernel: [   12.805590] IPv6: ADDRCONF(NETDEV_UP): p1p1: link is not ready
Jan  1 18:40:46 silverlink kernel: [   12.816393] r8169 0000:01:00.0 p1p1: link down
Jan  1 18:40:46 silverlink kernel: [   13.116491] usb 6-2: new full-speed USB device number 2 using ohci-pci
Jan  1 18:40:46 silverlink kernel: [   13.302137] usb 6-2: New USB device found, idVendor=03eb, idProduct=8434
Jan  1 18:40:46 silverlink kernel: [   13.305602] usb 6-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Jan  1 18:40:46 silverlink kernel: [   13.308954] usb 6-2: Product: Atmel maXTouch Digitizer
Jan  1 18:40:46 silverlink kernel: [   13.312243] usb 6-2: Manufacturer: Atmel
Jan  1 18:40:46 silverlink kernel: [   13.338294] hidraw: raw HID events driver (C) Jiri Kosina
Jan  1 18:40:46 silverlink kernel: [   13.360519] usbcore: registered new interface driver usbhid
Jan  1 18:40:46 silverlink kernel: [   13.363874] usbhid: USB HID core driver
Jan  1 18:40:46 silverlink kernel: [   13.383122] hid-generic 0003:03EB:8434.0002: hiddev0,hidraw0: USB HID v1.11 Device [Atmel Atmel maXTouch Digitizer] on usb-0000:00:13.0-2/input1
Jan  1 18:40:46 silverlink kernel: [   13.395908] input: Atmel Atmel maXTouch Digitizer as /devices/pci0000:00/0000:00:13.0/usb6/6-2/6-2:1.0/input/input11
Jan  1 18:40:46 silverlink kernel: [   13.402822] hid-multitouch 0003:03EB:8434.0001: input,hiddev0,hidraw1: USB HID v1.11 Device [Atmel Atmel maXTouch Digitizer] on usb-0000:00:13.0-2/input0
Jan  1 18:40:46 silverlink kernel: [   14.370940] r8169 0000:01:00.0 p1p1: link up
Jan  1 18:40:46 silverlink kernel: [   14.374682] IPv6: ADDRCONF(NETDEV_CHANGE): p1p1: link becomes ready
Jan  1 18:40:46 silverlink dbus[731]: [system] AppArmor D-Bus mediation is enabled
Jan  1 18:40:46 silverlink kernel: [   17.973039] audit_printk_skb: 6 callbacks suppressed
Jan  1 18:40:46 silverlink kernel: [   17.973043] type=1400 audit(1388601646.645:14): apparmor="STATUS" operation="profile_replace" parent=771 profile="unconfined" name="/sbin/dhclient" pid=776 comm="apparmor_parser"
Jan  1 18:40:46 silverlink kernel: [   17.973061] type=1400 audit(1388601646.645:15): apparmor="STATUS" operation="profile_replace" parent=771 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=776 comm="apparmor_parser"
Jan  1 18:40:46 silverlink kernel: [   17.973074] type=1400 audit(1388601646.645:16): apparmor="STATUS" operation="profile_replace" parent=771 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=776 comm="apparmor_parser"
Jan  1 18:40:46 silverlink kernel: [   17.974833] type=1400 audit(1388601646.645:17): apparmor="STATUS" operation="profile_replace" parent=771 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=776 comm="apparmor_parser"
Jan  1 18:40:46 silverlink kernel: [   17.974846] type=1400 audit(1388601646.645:18): apparmor="STATUS" operation="profile_replace" parent=771 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=776 comm="apparmor_parser"
Jan  1 18:40:46 silverlink kernel: [   17.975807] type=1400 audit(1388601646.645:19): apparmor="STATUS" operation="profile_replace" parent=771 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=776 comm="apparmor_parser"
Jan  1 18:40:46 silverlink kernel: [   18.136166] type=1400 audit(1388601646.809:20): apparmor="STATUS" operation="profile_load" parent=771 profile="unconfined" name="/usr/sbin/tcpdump" pid=778 comm="apparmor_parser"
Jan  1 18:40:47 silverlink acpid: starting up with proc fs
Jan  1 18:40:47 silverlink acpid: 1 rule loaded
Jan  1 18:40:47 silverlink acpid: waiting for events: event logging is off
Jan  1 18:40:47 silverlink cron[812]: (CRON) INFO (pidfile fd = 3)
Jan  1 18:40:47 silverlink cron[873]: (CRON) STARTUP (fork ok)
Jan  1 18:40:47 silverlink cron[873]: (CRON) INFO (Running @reboot jobs)
Jan  1 18:40:49 silverlink whoopsie[854]: whoopsie 0.2.24.1 starting up.
Jan  1 18:40:49 silverlink whoopsie[854]: Using lock path: /var/lock/whoopsie/lock
Jan  1 18:40:50 silverlink whoopsie[916]: Could not get the Network Manager state:
Jan  1 18:40:50 silverlink whoopsie[916]: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files
Jan  1 18:40:51 silverlink ntpdate[621]: adjust time server 91.189.89.199 offset -0.015086 sec
Jan  1 18:41:06 silverlink ntpdate[975]: adjust time server 91.189.89.199 offset -0.009802 sec
Jan  1 18:53:03 silverlink dbus[731]: [system] Reloaded configuration
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
```


I kept rebooting with a dpkg --configure -a and apt-get install ubuntu-desktop and on about the 4th attempt finally got them installed. Also installed xinit and fglrx

Had to download the drivers on another computer as to add insult to injury AMD does not allow you to download the drvers using either wget (does not allow direct download without going through the previous selection screen) or with Lynx (does not allow selection without Javascript). 


Drivers appeared to install, although I had to use --force due to a fglrx warning (wouldn't install without fglrx being installed and then complained when it was). Installed with a warning about DKMS (although appeared to install kernel drivers OK - I think).

When I try to start X I get the same no screens found error message.

Next step is to try with a custom xorg.conf file, but that will need to wait until another day...

---

### Post by penguintutor on 2014-01-13
Didn't have much success with the custom xorg.conf file. 

Finally making progress using Ubuntu 14.04 rather than 13.10.

Used the daily build of 14.04 and it installed without hitch.

Only problem now is with the HP BIOS which will only default booting into Windows 8 when there are two operating systems installed.
If Ubuntu is the only operating system then it works great, but as long as Windows 8 is installed it always boots that.

I can boot into Ubuntu by pressing F9 for the boot menu, but the HP BIOS does not allow me to select a default boot option.

I have changed the default boot order of UEFI using efibootmgr, but it is ignored and then the boot order is set back to Windows. 

Sounds like others have had similar problems with HP. 

After this and the other problems I've had with HP in the past I'm regretting ever buying a HP.

---

### Post by mastablasta on 2014-01-14
should have bough HP with linux preinstalled. no problems there it seems... at least not yet. we will see what happens when AMD drops support for the card they use in those.

---

### Post by penguintutor on 2014-01-14
As far as I'm aware HP don't sell any laptops with Linux installed in the UK though :-( 
Unless you count the Chromebook - but the lack of storage meant it wasn't suitable for what I needed.

I can now install Linux and have it as the only OS, but not boot into Linux except by interrupting the boot with an alternative boot menu selection. I have also got a Dell laptop (the HP is actually my daughter's) and that allows me to select Ubuntu as by default boot, which can then boot into Windows if required via GRUB (used rarely). I don't think Dell have the best support for Linux either, but my Dell did install Linux without any major issues but the ability to select Ubuntu as the primary boot drive puts it ahead of HP.

---

