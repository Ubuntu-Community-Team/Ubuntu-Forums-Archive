---
title: "Mounting NFS Shares Causes System Freeze After Kernel Update"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by donalo on 2007-12-19
I just upgraded my Ubuntu server and Desktop with the latest kernel updates (19-12-2007) and when I try to mount my NFS shares my desktop pc freezes causing me to do a hard reboot everytime.

Anyone else having this problem?

---

### Post by Astrophobos on 2007-12-19
Hi donalo,

I'm experiencing the same problem. Since a upgrade last night the computer freeze when it's connected to a nfs share.

Do you know if a bug is open for this in launchpad?

---

### Post by donalo on 2007-12-19
Hi Astrophobos,

I haven't had a chance to look at launchpad yet. I'll see if a bug is logged against it and if not create one.

---

### Post by donalo on 2007-12-19
I posted a bug report on Launchpad here [https://bugs.launchpad.net/ubuntu/+bug/177439]("https://bugs.launchpad.net/ubuntu/+bug/177439")

---

### Post by Slim Backwater on 2007-12-19
Same problem here, but on a client (not a server)  My /home is on an NFS4 share so it's really killed it for me.  My system freezes at around the time X initializes..

I booted up in Diagnostics (ESC at the grub menu) and I saw a kernel BUG: message related to NFS during boot..  When I tried to mount /home manually as root,  I got the same kernel bug.

Moments after that I get another kernel bug that says something like "detected soft CPU crash" and then the system locks.

I didn't know it was a kernel update, as I just recently configured Synaptic to autoinstall updates so there would be less maintenance hassle, so  I'm going to go try booting with a previous kernel and report back.

I just looked at the launchpad bug, yep, that's very close, if not exactly what I'm seeing.

._.

Edit: booting to 2.6.20-15 got my machine running,  Any suggestions as to how to rollback the latest update? (not knowing what the update was)

Oh,  /var/log/unattended-upgrades/unattended-upgrades.log

```

2007-12-19 07:33:27,238 INFO Initial blacklisted packages: 
2007-12-19 07:33:27,239 INFO Starting unattended upgrades script
2007-12-19 07:33:27,240 INFO Allowed origins are: ["['Ubuntu', 'feisty-security']"]
2007-12-19 07:33:40,650 INFO Packages that are upgraded: samba-common linux-image-2.6.20-16-generic linux-headers-2.6.20-16-generic linux-headers-2.6.20-16 libsmbclient smbclient
2007-12-19 07:33:40,651 INFO Writing dpkg log to '/var/log/unattended-upgrades/unattended-upgrades-dpkg_2007-12-19_07:33:40.651402.log'
2007-12-19 07:34:48,659 INFO All upgrades installed

```

```

Preconfiguring packages ...
(Reading database ... 117444 files and directories currently installed.)
Preparing to replace linux-headers-2.6.20-16 2.6.20-16.32 (using .../linux-headers-2.6.20-16_2.6.20-16.33_i386.deb) ...
Unpacking replacement linux-headers-2.6.20-16 ...
Preparing to replace linux-headers-2.6.20-16-generic 2.6.20-16.32 (using .../linux-headers-2.6.20-16-generic_2.6.20-16.33_i386.deb) ...
Unpacking replacement linux-headers-2.6.20-16-generic ...
Preparing to replace linux-image-2.6.20-16-generic 2.6.20-16.32 (using .../linux-image-2.6.20-16-generic_2.6.20-16.33_i386.deb) ...
The directory /lib/modules/2.6.20-16-generic still exists. Continuing as directed.
Done.
Unpacking replacement linux-image-2.6.20-16-generic ...
Running postrm hook script /sbin/update-grub.
You shouldn't call /sbin/update-grub. Please call /usr/sbin/update-grub instead!

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.20-16-generic
Found kernel: /vmlinuz-2.6.20-15-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Preparing to replace smbclient 3.0.24-2ubuntu1.4 (using .../smbclient_3.0.24-2ubuntu1.5_i386.deb) ...
Unpacking replacement smbclient ...
Preparing to replace samba-common 3.0.24-2ubuntu1.4 (using .../samba-common_3.0.24-2ubuntu1.5_i386.deb) ...
Unpacking replacement samba-common ...
Preparing to replace libsmbclient 3.0.24-2ubuntu1.4 (using .../libsmbclient_3.0.24-2ubuntu1.5_i386.deb) ...
Unpacking replacement libsmbclient ...
Setting up linux-headers-2.6.20-16 (2.6.20-16.33) ...

Setting up linux-headers-2.6.20-16-generic (2.6.20-16.33) ...
Setting up linux-image-2.6.20-16-generic (2.6.20-16.33) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.20-16.32 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.20-16.32 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
You shouldn't call /sbin/update-grub. Please call /usr/sbin/update-grub instead!

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.20-16-generic
Found kernel: /vmlinuz-2.6.20-15-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done


Setting up samba-common (3.0.24-2ubuntu1.5) ...

Setting up smbclient (3.0.24-2ubuntu1.5) ...
Setting up libsmbclient (3.0.24-2ubuntu1.5) ...

```

So it sould be just a matter of using synaptic to install one previous version of each of samba-common linux-image-2.6.20-16-generic linux-headers-2.6.20-16-generic linux-headers-2.6.20-16 libsmbclient smbclient?

Interesting.

---

### Post by erlguta on 2007-12-19
I'm experiencing the same problem on one NFS client
I think is one important bug.

---

### Post by bouchecl on 2007-12-19
Same problem here with the newest Gutsy kernel and NFSv4 client (but no Kerberos). My temporary workaround was to comment out my nfs mounts in /etc/fstab (obviously it won't help those mounting /home from a nfs server...). Here's a snippet of my /var/log/kern.log:

```
Dec 19 09:17:34 apollon kernel: [   31.980000] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000038
Dec 19 09:17:34 apollon kernel: [   31.980000]  printing eip:
Dec 19 09:17:34 apollon kernel: [   31.980000] f8c3a040
Dec 19 09:17:34 apollon kernel: [   31.980000] *pde = 00000000
Dec 19 09:17:34 apollon kernel: [   31.980000] Oops: 0000 [#1]
Dec 19 09:17:34 apollon kernel: [   31.980000] SMP 
Dec 19 09:17:34 apollon kernel: [   31.980000] Modules linked in: af_packet vmnet(P) vmblock(P) vmmon(P) ppdev ipv6 cpufreq_userspace cpufreq_powersave cpufreq_stats cpufreq_ondemand freq_table cpufreq_conservative sbs ac dock video container button battery nfs lockd sunrpc parport_pc lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device nvidia(P) xpad snd k8temp serio_raw agpgart i2c_nforce2 pcspkr psmouse soundcore snd_page_alloc shpchp pci_hotplug i2c_core evdev ext3 jbd mbcache sg sr_mod sd_mod cdrom usbhid hid sata_nv amd74xx ide_core ata_generic forcedeth libata scsi_mod ehci_hcd ohci_hcd usbcore thermal processor fan fuse apparmor commoncap
Dec 19 09:17:34 apollon kernel: [   31.980000] CPU:    0
Dec 19 09:17:34 apollon kernel: [   31.980000] EIP:    0060:[<f8c3a040>]    Tainted: P       VLI
Dec 19 09:17:34 apollon kernel: [   31.980000] EFLAGS: 00010206   (2.6.22-14-generic #1)
Dec 19 09:17:34 apollon kernel: [   31.980000] EIP is at nfs_fhget+0xd0/0x3e0 [nfs]
Dec 19 09:17:34 apollon kernel: [   31.980000] eax: 00000000   ebx: 00000000   ecx: f72f0674   edx: 00004180
Dec 19 09:17:34 apollon kernel: [   31.980000] esi: f72f0600   edi: f6b49bd4   ebp: f6b17128   esp: f6b49b88
Dec 19 09:17:34 apollon kernel: [   31.980000] ds: 007b   es: 007b   fs: 00d8  gs: 0033  ss: 0068
Dec 19 09:17:34 apollon kernel: [   31.980000] Process mount.nfs4 (pid: 6094, ti=f6b48000 task=f717c530 task.ti=f6b48000)
Dec 19 09:17:34 apollon kernel: [   31.980000] Stack: f8c39f10 f6b49bac 00000020 c0133462 c03d9de0 f6b17000 fffefa43 c02bd89d 
Dec 19 09:17:34 apollon kernel: [   31.980000]        00000282 f6b49c66 f6b49bd4 f6b49bd4 f72f0600 f6b49c64 f6b49d1e f8c388d7 
Dec 19 09:17:34 apollon kernel: [   31.980000]        f717c6f0 c1f07000 f72f0200 00000002 00000000 00000000 00000000 00000000 
```

---

### Post by Slim Backwater on 2007-12-19
Just to clarify, my machine is an Feisty 7.04 desktop, I never got around to updating it.

Here's my /var/log/kern.log for the nfs bug, but I can't find a log with the "soft lockup detected" I just saw it on the screen. 

```

Dec 19 08:03:35 precision360 kernel: [   33.735267] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000038
Dec 19 08:03:35 precision360 kernel: [   33.735275]  printing eip:
Dec 19 08:03:35 precision360 kernel: [   33.735277] f8e1cbb6
Dec 19 08:03:35 precision360 kernel: [   33.735279] *pde = 00000000
Dec 19 08:03:35 precision360 kernel: [   33.735282] Oops: 0000 [#1]
Dec 19 08:03:35 precision360 kernel: [   33.735284] SMP 
Dec 19 08:03:35 precision360 kernel: [   33.735289] Modules linked in: nfs lockd sunrpc sbp2 lp fuse snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mix
er_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd psmouse soundcore iTCO_wdt iTCO_ven
dor_support snd_page_alloc serio_raw parport_pc parport intel_agp pcspkr agpgart shpchp pci_hotplug af_packet tsdev evdev reiserfs sg sd_mod sr_mod cdrom gen
eric ata_piix usbhid hid ohci_hcd e1000 floppy ata_generic ohci1394 ieee1394 libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan dm_mod fbcon til
eblit font bitblit softcursor vesafb capability commoncap
Dec 19 08:03:35 precision360 kernel: [   33.735366] CPU:    0
Dec 19 08:03:35 precision360 kernel: [   33.735367] EIP:    0060:[<f8e1cbb6>]    Not tainted VLI
Dec 19 08:03:35 precision360 kernel: [   33.735369] EFLAGS: 00010206   (2.6.20-16-generic #2)
Dec 19 08:03:35 precision360 kernel: [   33.735388] EIP is at nfs_fhget+0xc6/0x3d0 [nfs]
Dec 19 08:03:35 precision360 kernel: [   33.735391] eax: 00000000   ebx: 00000000   ecx: c23b0c74   edx: 00004180
Dec 19 08:03:35 precision360 kernel: [   33.735395] esi: c23b0c00   edi: f7a11bd8   ebp: c23b1da0   esp: f7a11b90Dec 19 08:03:35 precision360 kernel: [   33.735267] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000038
Dec 19 08:03:35 precision360 kernel: [   33.735275]  printing eip:
Dec 19 08:03:35 precision360 kernel: [   33.735277] f8e1cbb6
Dec 19 08:03:35 precision360 kernel: [   33.735279] *pde = 00000000
Dec 19 08:03:35 precision360 kernel: [   33.735282] Oops: 0000 [#1]
Dec 19 08:03:35 precision360 kernel: [   33.735284] SMP 
Dec 19 08:03:35 precision360 kernel: [   33.735289] Modules linked in: nfs lockd sunrpc sbp2 lp fuse snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mix
er_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd psmouse soundcore iTCO_wdt iTCO_ven
dor_support snd_page_alloc serio_raw parport_pc parport intel_agp pcspkr agpgart shpchp pci_hotplug af_packet tsdev evdev reiserfs sg sd_mod sr_mod cdrom gen
eric ata_piix usbhid hid ohci_hcd e1000 floppy ata_generic ohci1394 ieee1394 libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan dm_mod fbcon til
eblit font bitblit softcursor vesafb capability commoncap
Dec 19 08:03:35 precision360 kernel: [   33.735366] CPU:    0
Dec 19 08:03:35 precision360 kernel: [   33.735367] EIP:    0060:[<f8e1cbb6>]    Not tainted VLI
Dec 19 08:03:35 precision360 kernel: [   33.735369] EFLAGS: 00010206   (2.6.20-16-generic #2)
Dec 19 08:03:35 precision360 kernel: [   33.735388] EIP is at nfs_fhget+0xc6/0x3d0 [nfs]
Dec 19 08:03:35 precision360 kernel: [   33.735391] eax: 00000000   ebx: 00000000   ecx: c23b0c74   edx: 00004180
Dec 19 08:03:35 precision360 kernel: [   33.735395] esi: c23b0c00   edi: f7a11bd8   ebp: c23b1da0   esp: f7a11b90
Dec 19 08:03:35 precision360 kernel: [   33.735398] ds: 007b   es: 007b   ss: 0068
Dec 19 08:03:35 precision360 kernel: [   33.735402] Process mount (pid: 4257, ti=f7a10000 task=df99c560 task.ti=f7a10000)
Dec 19 08:03:35 precision360 kernel: [   33.735404] Stack: f8e1ca90 f7a11bb0 0000000a f7a11c6a c23b0c00 c23b1c78 f7a11d22 00000000 
Dec 19 08:03:35 precision360 kernel: [   33.735415]        f7a11c6a f7a11bd8 f7a11bd8 c23b0c00 f7a11c68 f7a11d22 f8e1b4b7 00000000 
Dec 19 08:03:35 precision360 kernel: [   33.735426]        df99c560 df8b7600 00000002 00000000 00000000 00000000 00000000 00000000 
Dec 19 08:03:35 precision360 kernel: [   33.735436] Call Trace:
Dec 19 08:03:35 precision360 kernel: [   33.735439]  [<f8e1ca90>] nfs_init_locked+0x0/0x60 [nfs]
Dec 19 08:03:35 precision360 kernel: [   33.735476]  [<f8e1b4b7>] nfs4_get_root+0x177/0x260 [nfs]
Dec 19 08:03:35 precision360 kernel: [   33.735606]  [<f8e1e9bd>] nfs4_get_sb+0x28d/0x350 [nfs]
Dec 19 08:03:35 precision360 kernel: [   33.735705]  [vfs_kern_mount+182/304] vfs_kern_mount+0xb6/0x130
Dec 19 08:03:35 precision360 kernel: [   33.735729]  [do_kern_mount+57/96] do_kern_mount+0x39/0x60
Dec 19 08:03:35 precision360 kernel: [   33.735742]  [do_mount+762/1808] do_mount+0x2fa/0x710
Dec 19 08:03:35 precision360 kernel: [   33.735755]  [kfree_skbmem+8/128] kfree_skbmem+0x8/0x80
Dec 19 08:03:35 precision360 kernel: [   33.735765]  [<f88be66c>] e1000_unmap_and_free_tx_resource+0x1c/0x30 [e1000]
Dec 19 08:03:35 precision360 kernel: [   33.735779]  [<f88c0425>] e1000_clean_tx_irq+0xb5/0x2f0 [e1000]
Dec 19 08:03:35 precision360 kernel: [   33.735789]  [sock_common_recvmsg+71/112] sock_common_recvmsg+0x47/0x70
Dec 19 08:03:35 precision360 kernel: [   33.735831]  [<f88c2da0>] e1000_clean_rx_irq+0x0/0x4c0 [e1000]
Dec 19 08:03:35 precision360 kernel: [   33.735846]  [<f88c1fdd>] e1000_clean+0x1dd/0x2e0 [e1000]
Dec 19 08:03:35 precision360 kernel: [   33.735904]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Dec 19 08:03:35 precision360 kernel: [   33.735931]  [copy_mount_options+64/336] copy_mount_options+0x40/0x150
Dec 19 08:03:35 precision360 kernel: [   33.735951]  [sys_mount+119/192] sys_mount+0x77/0xc0
Dec 19 08:03:35 precision360 kernel: [   33.735966]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9
Dec 19 08:03:35 precision360 kernel: [   33.735984]  [xfrm_state_find+803/1392] xfrm_state_find+0x323/0x570
Dec 19 08:03:35 precision360 kernel: [   33.736002]  =======================
Dec 19 08:03:35 precision360 kernel: [   33.736005] Code: 00 00 8d 80 d8 fe ff ff 89 44 24 14 81 8d 3c 01 00 00 82 00 00 00 89 5d 20 8b 57 20 66 89 55 6a 8b 
86 60 01 00 00 0f b7 d2 8b 00 <8b> 40 38 8b 40 0c 89 85 90 00 00 00 89 d0 25 00 f0 00 00 3d 00 
Dec 19 08:03:35 precision360 kernel: [   33.736064] EIP: [<f8e1cbb6>] nfs_fhget+0xc6/0x3d0 [nfs] SS:ESP 0068:f7a11b90
Dec 19 08:03:35 precision360 kernel: [   33.736081]  <6>NET: Registered protocol family 10
Dec 19 08:03:35 precision360 kernel: [   33.883277] lo: Disabled Privacy Extensions

Dec 19 08:03:35 precision360 kernel: [   33.735398] ds: 007b   es: 007b   ss: 0068
Dec 19 08:03:35 precision360 kernel: [   33.735402] Process mount (pid: 4257, ti=f7a10000 task=df99c560 task.ti=f7a10000)
Dec 19 08:03:35 precision360 kernel: [   33.735404] Stack: f8e1ca90 f7a11bb0 0000000a f7a11c6a c23b0c00 c23b1c78 f7a11d22 00000000 
Dec 19 08:03:35 precision360 kernel: [   33.735415]        f7a11c6a f7a11bd8 f7a11bd8 c23b0c00 f7a11c68 f7a11d22 f8e1b4b7 00000000 
Dec 19 08:03:35 precision360 kernel: [   33.735426]        df99c560 df8b7600 00000002 00000000 00000000 00000000 00000000 00000000 
Dec 19 08:03:35 precision360 kernel: [   33.735436] Call Trace:
Dec 19 08:03:35 precision360 kernel: [   33.735439]  [<f8e1ca90>] nfs_init_locked+0x0/0x60 [nfs]
Dec 19 08:03:35 precision360 kernel: [   33.735476]  [<f8e1b4b7>] nfs4_get_root+0x177/0x260 [nfs]
Dec 19 08:03:35 precision360 kernel: [   33.735606]  [<f8e1e9bd>] nfs4_get_sb+0x28d/0x350 [nfs]
Dec 19 08:03:35 precision360 kernel: [   33.735705]  [vfs_kern_mount+182/304] vfs_kern_mount+0xb6/0x130
Dec 19 08:03:35 precision360 kernel: [   33.735729]  [do_kern_mount+57/96] do_kern_mount+0x39/0x60
Dec 19 08:03:35 precision360 kernel: [   33.735742]  [do_mount+762/1808] do_mount+0x2fa/0x710
Dec 19 08:03:35 precision360 kernel: [   33.735755]  [kfree_skbmem+8/128] kfree_skbmem+0x8/0x80
Dec 19 08:03:35 precision360 kernel: [   33.735765]  [<f88be66c>] e1000_unmap_and_free_tx_resource+0x1c/0x30 [e1000]
Dec 19 08:03:35 precision360 kernel: [   33.735779]  [<f88c0425>] e1000_clean_tx_irq+0xb5/0x2f0 [e1000]
Dec 19 08:03:35 precision360 kernel: [   33.735789]  [sock_common_recvmsg+71/112] sock_common_recvmsg+0x47/0x70
Dec 19 08:03:35 precision360 kernel: [   33.735831]  [<f88c2da0>] e1000_clean_rx_irq+0x0/0x4c0 [e1000]
Dec 19 08:03:35 precision360 kernel: [   33.735846]  [<f88c1fdd>] e1000_clean+0x1dd/0x2e0 [e1000]
Dec 19 08:03:35 precision360 kernel: [   33.735904]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Dec 19 08:03:35 precision360 kernel: [   33.735931]  [copy_mount_options+64/336] copy_mount_options+0x40/0x150
Dec 19 08:03:35 precision360 kernel: [   33.735951]  [sys_mount+119/192] sys_mount+0x77/0xc0
Dec 19 08:03:35 precision360 kernel: [   33.735966]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9
Dec 19 08:03:35 precision360 kernel: [   33.735984]  [xfrm_state_find+803/1392] xfrm_state_find+0x323/0x570
Dec 19 08:03:35 precision360 kernel: [   33.736002]  =======================
Dec 19 08:03:35 precision360 kernel: [   33.736005] Code: 00 00 8d 80 d8 fe ff ff 89 44 24 14 81 8d 3c 01 00 00 82 00 00 00 89 5d 20 8b 57 20 66 89 55 6a 8b 
86 60 01 00 00 0f b7 d2 8b 00 <8b> 40 38 8b 40 0c 89 85 90 00 00 00 89 d0 25 00 f0 00 00 3d 00 
Dec 19 08:03:35 precision360 kernel: [   33.736064] EIP: [<f8e1cbb6>] nfs_fhget+0xc6/0x3d0 [nfs] SS:ESP 0068:f7a11b90
Dec 19 08:03:35 precision360 kernel: [   33.736081]  <6>NET: Registered protocol family 10
Dec 19 08:03:35 precision360 kernel: [   33.883277] lo: Disabled Privacy Extensions


```

---

### Post by donalo on 2007-12-19
I managed to revert to Version 2.6.22-14.46 using Synaptic and all is well again :)

Oddly one of the fixes in the update is "NFS: Fix the mount regression" :(

---

### Post by bouchecl on 2007-12-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/164231/comments/15](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/164231/comments/15) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The problem is a regression bug introduced by a patch to fix a security issue. It seems to affect people using NFSv4. See [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/164231/comments/15](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/164231/comments/15) for an explanation.

Reverting to 2.6.22-14.46 (which can be done with Synaptic, as Donalo said) or turning off NFS shares is the best you can do until a new version of the kernel is released.

---

### Post by Slim Backwater on 2007-12-20
Thanks for the link bouchecl.

Now, can anyone give me some tips on rolling back with synaptic?  I thought I could figure it out, but I can only see 2.6.20-16.33 (Feisty-security) under "available versions" for linux-image-2.6.20-16-generic; nothing else.  Could 2.6.20-16.32 have been removed from th repository?  I'm running Feisty.

Thanks,

._.

---

### Post by blueorder on 2007-12-20
Is this only happening NFSv4 or with both NFSv4 and regular ole' NFS (I'm using nfs and not nfs4 to mount my shares)?

I've held back upgrading the kernel to 33 (I'm on Feisty) after reading a couple of threads here in the forums.

Thanks

---

### Post by erlguta on 2007-12-25
Yes it seems only to affect NFSv4 version.
I fixed it by now making a regression of the linux-image package with synaptic as Donalo says.
It is very interesting the opinion of Drew:
[https://bugs.launchpad.net/ubuntu/+bug/177439](https://bugs.launchpad.net/ubuntu/+bug/177439)
I think the same. It is normal thing to have errors and bugs in new and testing software as Compiz, new functions, etc...but it is very annoying to see, very often, that things that was working perfect, stops to work after every upgrade...and you must wait for the next version to see it fixed. One new version who cames with another bugs in packages that was stable.
It is a common thing in the ubuntu way. I have never seen this kind of things in Debian.
I think something must have to change in ubuntu.
It is only my opinion.
Happy Christmas!

PD: Excuse my horrible English ;)

---

### Post by obrouni on 2008-01-04
Does anybody know if anything is going to be done about this? Bug hasn't been updated for ages.

---

### Post by erlguta on 2008-01-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/164231](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/164231) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				In the bug 164231:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/164231](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/164231)
Philip Walls says that you can apply one patch to the kernel 2.6.22-14.47
How can i do this?
Is somebody working in this important bug?

---

### Post by erlguta on 2008-02-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/164231](https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/164231) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				It seems that it is now fixed with the new kernel 2.6.22-14.51 in gutsy and 2.6.20-16.34 in feisty.

---

