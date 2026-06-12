---
title: "Kernel Oops in install"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by dkasak on 2008-05-19
Greetings. I'm putting Ubuntu on an old laptop.

After X starts, I select my region, and then X dies and I get a flashing cursor. Not so good. So I switch to another console, and check the kernel messages. I find this:

```
[ 2751.013779] kernel BUG at /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/f
s/unionfs/rename.c:270!
[ 2751.013793] invalid opcode: 0000 [#1] SMP 
[ 2751.013801] Modules linked in: ipv6 af_packet rfcomm l2cap bluetooth ppdev lp speedstep_lib cpufreq_use
rspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative sbs sbshc containe
r dock iptable_filter ip_tables x_tables 8139cp 8139too mii joydev pcmcia snd_via82xx gameport snd_ac97_co
dec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_mpu401_uart video output snd_seq_dummy s
erio_raw battery ac button snd_seq_oss snd_seq_midi snd_rawmidi via686a snd_seq_midi_event snd_seq via_agp
 i2c_viapro snd_timer shpchp yenta_socket snd_seq_device parport_pc i2c_core evdev agpgart rsrc_nonstatic 
pcmcia_core parport pci_hotplug snd soundcore psmouse pcspkr squashfs loop unionfs nls_cp437 isofs ext3 jb
d mbcache sg sr_mod sd_mod cdrom floppy pata_via pata_acpi ata_generic uhci_hcd libata usbcore scsi_mod th
ermal processor fan fbcon tileblit font bitblit softcursor fuse
[ 2751.013974] 
[ 2751.013984] Pid: 8212, comm: ubiquity Not tainted (2.6.24-16-generic #1)
[ 2751.013995] EIP: 0060:[<cc19a2b3>] EFLAGS: 00010246 CPU: 0
[ 2751.014058] EIP is at unionfs_rename+0x733/0xa50 [unionfs]
[ 2751.014066] EAX: 00000000 EBX: 00000002 ECX: c3879d48 EDX: 00000001
[ 2751.014075] ESI: caa18c38 EDI: 00000001 EBP: ffffffe4 ESP: c380de0c
[ 2751.014084]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[ 2751.014095] Process ubiquity (pid: 8212, ti=c380c000 task=cb18a5a0 task.ti=c380c000)
[ 2751.014103] Stack: 00000000 00000000 0000077f 00000000 00000000 c095bdb0 c3879d48 c095bdb0 
[ 2751.014122]        c96b3b20 c3bcd220 00000001 ffffffff 00000001 00000000 00000002 c3848330 
[ 2751.014141]        00000000 00000000 00000000 00000001 fffffffc fffffffe 00000000 00000001 
[ 2751.014159] Call Trace:
[ 2751.014244]  [<c019575f>] vfs_rename+0x42f/0x470
[ 2751.014309]  [<c0194b39>] __lookup_hash+0xb9/0xf0
[ 2751.014339]  [<c0197675>] sys_renameat+0x1d5/0x210
[ 2751.014394]  [<c017941c>] handle_mm_fault+0x57c/0x730
[ 2751.014431]  [<c018b613>] do_filp_open+0x33/0x60
[ 2751.014483]  [<c031922f>] do_page_fault+0x13f/0x730
[ 2751.014540]  [<c018b6fe>] do_sys_open+0xbe/0xe0
[ 2751.014561]  [<c01976d7>] sys_rename+0x27/0x30
[ 2751.014582]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[ 2751.014624]  [<c0310000>] vcc_getsockopt+0x150/0x170
[ 2751.014678]  =======================
[ 2751.014683] Code: 00 0f 84 6d 01 00 00 8b 44 24 4c 39 44 24 5c 0f 84 3d 01 00 00 8b 44 24 64 85 c0 74 0e 3d 00 f0 ff ff 77 07 8b 50 0c 85 d2 74 29 <0f> 0b eb fe 8b 54 24 24 8b 4a 54 e9 ee fa ff ff 8b 7c 24 5c eb 
[ 2751.014769] EIP: [<cc19a2b3>] unionfs_rename+0x733/0xa50 [unionfs] SS:ESP 0068:c380de0c
[ 2751.014813] ---[ end trace 6c5bb55a53d376f5 ]---
```

I've tried with the default startup options, and also with the 'safe' video mode ( or whatever it's called ). Same thing either way.

What's going on? As far as I know, there are no hardware issues. This laptop has Debian ( an old version ) on it at the moment, and I'm ***told*** it's working OK.

---

### Post by zvacet on 2008-05-20
Did you checked [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") and disc integrity?If you find any errors download same iso with torrent and point download to the folder where your iso is.Torrent will check your iso and replace corrupted files with good ones.After that check md5sum again,burn at lower possible speed and check disc integrity.Ir all goes well install it.

---

### Post by dkasak on 2008-05-31
Yeah I did after this started happening. But I'd used this disc to install one system before, and also now one system after. It's only this old laptop that oopses.

Since I had no idea if I could fix it or not, I installed Gentoo on it instead. I'm sure some people here would smile if I told you that I just finished installing it now, after about a week of compiling :) No matter. It's going now.

---

### Post by zvacet on 2008-05-31
You could install Sabayon instead.

---

