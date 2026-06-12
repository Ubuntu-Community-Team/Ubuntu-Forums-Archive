---
title: "Kernel panics on AMD Athlon since upgrade from 5.10"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by rbeldin on 2006-06-09
I had an extremely stable AMD Athlon XP 1900+ with 1.5gb ram, 250mb seagate hd, and an older 64 mb Nvidia graphics card (name escapes me) running Breezy with all the latest updates and the K7 kernel and Nvidia drivers.   

I upgraded this system to Dapper (after June 1) using the 'update-manager' and despite one small interruption in the installation, apparently corrected by doing dpkg configure -a, all seemed well.  System booted cleanly, no errors from apt, network connections fine. 

I started noticing problem when *trying* to rebuild the kernel (2.6.15-23) for a vpn product I run.  It requires that I have CONFIG_REGPARMS set, which the Ubuntu kernel does not have.   After kicking off the build, the went about doing other things and left the system alone.   After 15 minutes or so I noticed that the cursor was frozen, yet the system was still responsive to a ping but I could not ssh into the system.   I didn't have a serial console and could not attach to a vt, so I ended up resetting the box. 

The messages log captured a piece of it: 

Jun  6 13:53:38 localhost kernel: [4301188.478000] PREEMPT 
Jun  6 13:53:38 localhost kernel: [4301188.478000] Modules linked in: rfcomm l2cap bluetooth ppdev cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi container button acpi_sbs battery ac i2c_acpi_ec ntfs nls_iso8859_1 nls_cp437 vfat fat ipv6 dm_mod md_mod lp rsrc_nonstatic pcmcia_core tsdev snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul analog snd_seq_dummy parport_pc parport rtc pcspkr serio_raw psmouse floppy snd_seq_oss i2c_viapro nvidia i2c_core snd_seq_midi snd_seq_midi_event snd_seq snd_emu10k1 snd_rawmidi snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_device snd_timer snd_page_alloc snd_util_mem snd_hwdep snd emu10k1_gp soundcore shpchp via_ircc tulip via_agp agpgart pci_hotplug gameport ltserial ltmodem irda crc_ccitt evdev ext3 jbd ide_generic uhci_hcd ehci_hcd ohci_hcd usbcore ide_cd cdrom ide_disk via82cxxx generic thermal processor fan capability commoncap vga16
Jun  6 13:53:38 localhost kernel: b vgastate fbcon tileblit font bitblit softcursor
Jun  6 13:53:38 localhost kernel: [4301188.478000] CPU:    0
Jun  6 13:53:38 localhost kernel: [4301188.478000] EIP:    0060:[pg0+112046082/1069368320]    Tainted: P      VLI
Jun  6 13:53:38 localhost kernel: [4301188.478000] EFLAGS: 00210046   (2.6.15-23-386) 
Jun  6 13:53:38 localhost kernel: [4301188.478000] EIP is at 0xc6f05002
Jun  6 13:53:38 localhost kernel: [4301188.478000] eax: 40898000   ebx: 40881d24   ecx: 00000000   edx: 00000018
Jun  6 13:53:38 localhost kernel: [4301188.478000] esi: 4088ed00   edi: 00000003   ebp: bfe42cd8   esp: e1431fdc
Jun  6 13:53:38 localhost kernel: [4301188.478000] ds: 007b   es: 007b   ss: 0068
Jun  6 13:53:38 localhost kernel: [4301188.478000] Process cc1 (pid: 15626, threadinfo=e1430000 task=dfdd8a90)
Jun  6 13:53:38 localhost kernel: [4301188.478000] Stack: c0116820 00000006 0830455c 00000073 00210282 bfe42cd0 0000007b 00000000 
Jun  6 13:53:38 localhost kernel: [4301188.478000]        00000000 
Jun  6 13:53:38 localhost kernel: [4301188.478000] Call Trace:
Jun  6 13:53:38 localhost kernel: [4301188.478000]  [do_page_fault+0/1562] do_page_fault+0x0/0x61a
Jun  6 13:53:38 localhost kernel: [4301188.478000] Code: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 <1f> 01 46 46 63 62 70 80 16 89 08 34 8e 84 1c 91 2a 89 2c e8 57 
Jun  6 14:06:25 localhost shutdown[15636]: shutting down for system reboot
Jun  6 14:06:30 localhost kernel: [4301188.478000]  <6>apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Jun  6 14:06:30 localhost kernel: [4301960.858000] apm: disabled on user request.
Jun  6 14:06:32 localhost kernel: Kernel logging (proc) stopped.
Jun  6 14:06:32 localhost kernel: Kernel log daemon terminating.
Jun  6 14:06:32 localhost exiting on signal 15

Highly imperfect I know, since it is just a partial trace.   I have seen at least two other instances of what might be the same issue, unfortunately no stack traces. 

I had similar problems on a VMware virtual machine that I upgraded in similar fashion. When I get to the point I can boot that, I'll post whatever kernel messages I have there. 

My questions: 

- are there ongoing panic issues with 2.6.15-23?

- I wondered about the stability of the nvidia drivers, so I purposely booted into single user mode to avoid their being loaded and disabled gdm.   I started my build up via ssh and the system hung with no console messages. 

Thoughts? 

Rick

---

### Post by crumja on 2006-06-09
I had similar problem a while ago upgrading from breezy -> dapper testing and again when upgrading a kernel. I added a new kernel and deleted the current (running one) and then rebooted. Turned out that the new kernel tries to get modules from the old one. At this stage, I just gave up. If anything happens midway through module compilation, it's tough to get it back. I tried manually readding modules and fixing stuff. Didn't work. Same thing happened on arch and debian upgrade.

---

### Post by rbeldin on 2006-06-10
[QUOTE=crumja]I had similar problem a while ago upgrading from breezy -> dapper testing and again when upgrading a kernel. I added a new kernel and deleted the current (running one) and then rebooted. Turned out that the new kernel tries to get modules from the old one. At this stage, I just gave up. If anything happens midway through module compilation, it's tough to get it back. I tried manually readding modules and fixing stuff. Didn't work. Same thing happened on arch and debian upgrade.[/QUOTE]

New kernel tried to get modules from the old one?  I don't see how that could happen and if it did, the kernel abi would prevent modules from being loaded if the kernel was built with module versioning, as the Ubuntu kernel is.   If you were trying to rebuild and *replace* the existing /lib/modules/`uname -r`, I can certainly see how that would happen.   In my case I am trying to make a completely new kernel, independent of the running kernel.   Needless to say, the act of compiling a new kernel should NOT cause the running kernel to panic.

---

### Post by rbeldin on 2006-06-11
I decided to try this again.  I was rebuilding the Ubuntu kernel  whilc running 2.6.15-23-386 using the gcc-3.4 compiler.   I got the following kernel oops, which did not panic the system, but nontheless.   

The command that I had issued was 

MAKEFLAGS="CC=/usr/bin/gcc-3.4" dpkg-buildpackage -us -us 

[4324027.703000] Unable to handle kernel paging request at virtual address 00004005
[4324027.703000]  printing eip:
[4324027.703000] bfbbb878
[4324027.703000] *pde = 00000000
[4324027.703000] Oops: 0000 [#1]
[4324027.703000] PREEMPT
[4324027.703000] Modules linked in: rfcomm l2cap bluetooth ppdev cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave cpufreq_ondemand cpufreq_conservative video tc1100_wmi sony_acpi pcc_acpi hotkey dev_acpi container button acpi_sbs battery ac i2c_acpi_ec ntfs nls_iso8859_1 nls_cp437 vfat fat dm_mod md_mod lp
rsrc_nonstatic pcmcia_core snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_emul snd_seq_dummy tsdev ipv6 snd_seq_oss pcspkr analog snd_seq_midi snd_seq_midi_event snd_seq snd_emu10k1 snd_rawmidi snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss i2c_viapro snd_pcm snd_seq_device snd_timer snd_page_alloc snd_util_mem snd_hwdep serio_raw rtc psmouse emu10k1_gp gameport parport_pc parport via_ircc snd irda soundcore crc_ccitt floppy nvidia i2c_core shpchp pci_hotplug via_agp agpgart tulip ltserial ltmodem evdev ext3 jbd ide_generic uhci_hcd ehci_hcd ohci_hcd usbcore ide_cd cdrom ide_disk via82cxxx generic thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
[4324027.703000] CPU:    0
[4324027.703000] EIP:    0060:[<bfbbb878>]    Tainted: P      VLI
[4324027.703000] EFLAGS: 00010046   (2.6.15-23-386)
[4324027.703000] EIP is at 0xbfbbb878
[4324027.703000] eax: 08556000   ebx: 08556c78   ecx: 00000000   edx: 08555000
[4324027.703000] esi: c174c620   edi: 00001000   ebp: ebf83e84   esp: ebf83da8
[4324027.703000] ds: 007b   es: 007b   ss: 0068
[4324027.703000] Process cc1 (pid: 19671, threadinfo=ebf82000 task=f7c91030)
[4324027.703000] Stack: c0116820 00000002 c01405ba 00000060 00010287 00001505 ebf82000 c174c620
[4324027.703000]        ebf83e40 00000000 c01403f7 ebf83e84 c174c620 00000000 00001000 00000000
[4324027.703000]        00000000 ebf82000 eeb14e98 00000001 00000000 00000002 00000002 ffffffff
[4324027.703000] Call Trace:
[4324027.703000]  [<c0116820>] do_page_fault+0x0/0x61a
[4324027.703000]  [<c01405ba>] file_read_actor+0x3a/0xc0
[4324027.703000]  [<c01403f7>] do_generic_mapping_read+0x357/0x4e0
[4324027.703000]  [<c01406db>] __generic_file_aio_read+0x9b/0x230
[4324027.703000]  [<c0140580>] file_read_actor+0x0/0xc0
[4324027.703000]  [<c01408b2>] generic_file_aio_read+0x42/0x60
[4324027.703000]  [<c015fada>] do_sync_read+0xba/0x120
[4324027.703000]  [<c0131170>] autoremove_wake_function+0x0/0x40
[4324027.703000]  [<c015fbd6>] vfs_read+0x96/0x150
[4324027.703000]  [<c015ff38>] sys_read+0x38/0x80
[4324027.703000]  [<c010302b>] sysenter_past_esp+0x54/0x79
[4324027.703000] Code:  Bad EIP value.
[4324027.703000]

I'm sure the tainted flag comes from the Nvidia drivers.  I was not running the Xserver at the and was doing all of this at the console. 

Are there other forums for what is clearly a kernel problem?

---

