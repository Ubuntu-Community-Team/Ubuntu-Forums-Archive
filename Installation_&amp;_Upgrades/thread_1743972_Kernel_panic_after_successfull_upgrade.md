---
title: "Kernel panic after successfull upgrade"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by kuovsk.anekask on 2011-04-29
I ran an upgrade to 11.04. It boots fine into KDE, then panics (flashing Caps lock) about a minute later. The Live CD runs fine. 

Here's the part of my syslog that looks related:
```
Apr 30 14:59:25 Alex-T61p pulseaudio[4662]: module-alsa-card.c: Failed to find a working profile.
Apr 30 14:59:25 Alex-T61p pulseaudio[4662]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="29" name="platform-thinkpad_acpi" card_name="alsa_card.platform-thinkpad_acpi" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Apr 30 14:59:29 Alex-T61p kernel: [  134.453243] BUG: unable to handle kernel paging request at 0000000000040004
Apr 30 14:59:29 Alex-T61p kernel: [  134.453250] IP: [<ffffffffa00d5bfe>] vhba_ctl_read+0x1fe/0x2e0 [vhba]
Apr 30 14:59:29 Alex-T61p kernel: [  134.453261] PGD a2c73067 PUD a73e5067 PMD 0 
Apr 30 14:59:29 Alex-T61p kernel: [  134.453265] Oops: 0000 [#1] SMP 
Apr 30 14:59:29 Alex-T61p kernel: [  134.453268] last sysfs file: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0/uevent
Apr 30 14:59:29 Alex-T61p kernel: [  134.453272] CPU 1 
Apr 30 14:59:29 Alex-T61p kernel: [  134.453273] Modules linked in: cryptd aes_x86_64 aes_generic snd_hrtimer vboxnetadp vboxnetflt vboxdrv rfcomm sco bnep l2cap binfmt_misc nfsd exportfs nfs parport_pc lockd ppdev fscache nfs_acl auth_rpcgss sunrpc dm_crypt joydev snd_hda_codec_analog nvidia(P) snd_hda_intel snd_hda_codec snd_hwdep snd_pcm arc4 thinkpad_acpi snd_seq_midi pcmcia iwlagn btusb iwlcore bluetooth snd_rawmidi snd_seq_midi_event mac80211 snd_seq snd_timer snd_seq_device yenta_socket cfg80211 pcmcia_rsrc snd r852 sm_common nand nand_ids nand_ecc mtd psmouse tpm_tis pcmcia_core serio_raw soundcore snd_page_alloc nvram tpm vhba tpm_bios lp parport usbhid hid uvesafb firewire_ohci video ahci sdhci_pci e1000e firewire_core crc_itu_t sdhci libahci
Apr 30 14:59:29 Alex-T61p kernel: [  134.453321] 
Apr 30 14:59:29 Alex-T61p kernel: [  134.453324] Pid: 4739, comm: cdemud Tainted: P            2.6.38-8-generic #42-Ubuntu LENOVO 64575KM/64575KM
Apr 30 14:59:29 Alex-T61p kernel: [  134.453329] RIP: 0010:[<ffffffffa00d5bfe>]  [<ffffffffa00d5bfe>] vhba_ctl_read+0x1fe/0x2e0 [vhba]
Apr 30 14:59:29 Alex-T61p kernel: [  134.453333] RSP: 0018:ffff8800a2defe38  EFLAGS: 00010202
Apr 30 14:59:29 Alex-T61p kernel: [  134.453335] RAX: 0000000000040004 RBX: ffff88010f458650 RCX: ffff8800a2d044a0
Apr 30 14:59:29 Alex-T61p kernel: [  134.453338] RDX: ffff8800a7237508 RSI: 0000000000000286 RDI: 0000000000000286
Apr 30 14:59:29 Alex-T61p kernel: [  134.453340] RBP: ffff8800a2defef8 R08: 0000000000000000 R09: 0000000000000000
Apr 30 14:59:29 Alex-T61p kernel: [  134.453342] R10: 00007f206c7e3790 R11: 0000000000000293 R12: ffff8800a7237504
Apr 30 14:59:29 Alex-T61p kernel: [  134.453344] R13: 0000000000000020 R14: ffff88010f458000 R15: ffff8800a7237518
Apr 30 14:59:29 Alex-T61p kernel: [  134.453346] FS:  00007f206c804700(0000) GS:ffff8800bfd00000(0000) knlGS:0000000000000000
Apr 30 14:59:29 Alex-T61p kernel: [  134.453348] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Apr 30 14:59:29 Alex-T61p kernel: [  134.453350] CR2: 0000000000040004 CR3: 00000000a2c6a000 CR4: 00000000000006e0
Apr 30 14:59:29 Alex-T61p kernel: [  134.453353] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Apr 30 14:59:29 Alex-T61p kernel: [  134.453355] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Apr 30 14:59:29 Alex-T61p kernel: [  134.453357] Process cdemud (pid: 4739, threadinfo ffff8800a2dee000, task ffff8800a2d044a0)
Apr 30 14:59:29 Alex-T61p kernel: [  134.453359] Stack:
Apr 30 14:59:29 Alex-T61p kernel: [  134.453360]  ffff88012dee2710 00020000815c6af8 ffff8800a2deff48 00007f206c7e3ad0
Apr 30 14:59:29 Alex-T61p kernel: [  134.453364]  0000000000020200 0000000000000286 0000000000000000 ffff8800a2d044a0
Apr 30 14:59:29 Alex-T61p kernel: [  134.453368]  ffffffff81087f30 ffff8800a2defe80 ffff8800a2defe80 0000000001672e70
Apr 30 14:59:29 Alex-T61p kernel: [  134.453371] Call Trace:
Apr 30 14:59:29 Alex-T61p kernel: [  134.453378]  [<ffffffff81087f30>] ? autoremove_wake_function+0x0/0x40
Apr 30 14:59:29 Alex-T61p kernel: [  134.453383]  [<ffffffff81279c13>] ? security_file_permission+0x93/0xb0
Apr 30 14:59:29 Alex-T61p kernel: [  134.453387]  [<ffffffff81164f73>] vfs_read+0xc3/0x180
Apr 30 14:59:29 Alex-T61p kernel: [  134.453389]  [<ffffffff81165081>] sys_read+0x51/0x90
Apr 30 14:59:29 Alex-T61p kernel: [  134.453393]  [<ffffffff8100c002>] system_call_fastpath+0x16/0x1b
Apr 30 14:59:29 Alex-T61p kernel: [  134.453395] Code: 00 00 48 81 c4 98 00 00 00 5b 41 5c 41 5d 41 5e 41 5f c9 c3 49 8b 46 30 89 45 a0 49 8b 06 8b 80 84 00 00 00 89 45 a4 49 8b 46 50 <48> 8b 10 48 89 55 a8 48 8b 40 08 48 89 45 b0 41 0f b7 46 4a 88 
Apr 30 14:59:29 Alex-T61p kernel: [  134.453425] RIP  [<ffffffffa00d5bfe>] vhba_ctl_read+0x1fe/0x2e0 [vhba]
Apr 30 14:59:29 Alex-T61p kernel: [  134.453429]  RSP <ffff8800a2defe38>
Apr 30 14:59:29 Alex-T61p kernel: [  134.453430] CR2: 0000000000040004
Apr 30 14:59:29 Alex-T61p kernel: [  134.453433] ---[ end trace 967f2e853379461c ]---
Apr 30 14:59:43 Alex-T61p pulseaudio[4662]: module-alsa-card.c: Failed to find a working profile.
Apr 30 14:59:44 Alex-T61p pulseaudio[4662]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="29" name="platform-thinkpad_acpi" card_name="alsa_card.platform-thinkpad_acpi" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.

```
Thanks in advance for any help.

---

### Post by kuovsk.anekask on 2011-04-30
Never mind, I ended up just doing a clean install and that works fine.

---

