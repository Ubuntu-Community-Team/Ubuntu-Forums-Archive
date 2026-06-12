---
title: "Kubuntu 7.10 problems with ACPI on an Athlon 64 X2 - Kernel Oops"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by TDFKAOlli on 2007-11-21
Hi,

I was escaping from OpenSuse10.3 to Kubuntu 7.10 after problems with TV card and bluetooth, but does seem to have luck with Linux. After installation of x64_86 Kubuntu with standard kernel I couldn't use network or audio and whole system was quite unstable. I found following problem in syslog:

```
Nov 16 19:50:10 olli kernel: [   84.804509] ACPI: Power Button (CM) [PWRB]
Nov 16 19:50:10 olli kernel: [   85.020256] powernow-k8: Found 2 AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ processors (version 2.00.00)
Nov 16 19:50:10 olli kernel: [   85.020023] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0xa
Nov 16 19:50:10 olli kernel: [   85.020028] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xa
Nov 16 19:50:10 olli kernel: [   85.020030] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xc
Nov 16 19:50:10 olli kernel: [   85.020033] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
Nov 16 19:50:10 olli kernel: [   85.020514] Unable to handle kernel paging request at ffff81083e30c3f8 RIP: 
Nov 16 19:50:10 olli kernel: [   85.020559]  [_end+131124600/2130332920] :cpufreq_stats:cpufreq_stats_update+0x40/0x70
Nov 16 19:50:10 olli kernel: [   85.020677] PGD 8063 PUD 0 
Nov 16 19:50:10 olli kernel: [   85.020759] Oops: 0002 [1] SMP 
Nov 16 19:50:10 olli kernel: [   85.020841] CPU 0 
Nov 16 19:50:10 olli kernel: [   85.020899] Modules linked in: powernow_k8 cpufreq_powersave cpufreq_stats cpufreq_userspace cpufreq_ondemand cpufreq_conservative freq_table video container sbs button dock ac battery ipv6 lp loop snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event parport_pc snd_seq cinergyT2 dvb_core hci_usb snd_timer snd_seq_device bluetooth pcspkr parport k8temp psmouse serio_raw af_packet shpchp pci_hotplug i2c_nforce2 i2c_core snd soundcore snd_page_alloc evdev usbhid hid ide_cd cdrom reiserfs sg sd_mod floppy ehci_hcd sata_nv forcedeth ohci_hcd amd74xx ide_core ata_generic libata scsi_mod usbcore thermal processor fan fuse apparmor commoncap
Nov 16 19:50:10 olli kernel: [   85.022792] Pid: 5117, comm: modprobe Not tainted 2.6.22-14-generic #1
Nov 16 19:50:10 olli kernel: [   85.022835] RIP: 0010:[_end+131124600/2130332920]  [_end+131124600/2130332920] :cpufreq_stats:cpufreq_stats_update+0x40/0x70
Nov 16 19:50:10 olli kernel: [   85.022916] RSP: 0018:ffff810036fc1ae8  EFLAGS: 00010246
Nov 16 19:50:10 olli kernel: [   85.022957] RAX: 0000000000000000 RBX: 0000000000000000 RCX: ffff81003e30c400
Nov 16 19:50:10 olli kernel: [   85.023000] RDX: 00000000ffffffff RSI: ffff810039f73380 RDI: ffffffff88369f80
Nov 16 19:50:10 olli kernel: [   85.023043] RBP: 00000000ffff00ce R08: 0000000000000004 R09: 0000000000000004
Nov 16 19:50:10 olli kernel: [   85.023085] R10: 0000000000000000 R11: 0000000000200b20 R12: 0000000000000000
Nov 16 19:50:10 olli kernel: [   85.023128] R13: 00000000ffffffff R14: 0000000000000001 R15: 0000000000000000
Nov 16 19:50:10 olli kernel: [   85.023172] FS:  00002ac8c56916e0(0000) GS:ffffffff80560000(0000) knlGS:0000000000000000
Nov 16 19:50:10 olli kernel: [   85.023225] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Nov 16 19:50:10 olli kernel: [   85.023267] CR2: ffff81083e30c3f8 CR3: 0000000036a17000 CR4: 00000000000006e0
Nov 16 19:50:10 olli kernel: [   85.023310] Process modprobe (pid: 5117, threadinfo ffff810036fc0000, task ffff810036ff6000)
Nov 16 19:50:10 olli kernel: [   85.023363] Stack:  ffffffff883698c0 ffff810036fc1bd8 ffff810039f73380 ffffffff88368122
Nov 16 19:50:10 olli kernel: [   85.023531]  ffff810036ff6000 00000000fffffffd 0000000000000000 0000000000000000
Nov 16 19:50:10 olli kernel: [   85.023675]  ffff810036fc1bd8 ffffffff80434e45 ffffffff80654aa0 ffff810036fc1bd8
Nov 16 19:50:10 olli kernel: [   85.023787] Call Trace:
Nov 16 19:50:10 olli kernel: [   85.023859]  [_end+131124762/2130332920] :cpufreq_stats:cpufreq_stat_notifier_trans+0x72/0xc0
Nov 16 19:50:10 olli kernel: [   85.023919]  [notifier_call_chain+69/144] notifier_call_chain+0x45/0x90
Nov 16 19:50:10 olli kernel: [   85.023965]  [__srcu_notifier_call_chain+90/144] __srcu_notifier_call_chain+0x5a/0x90
Nov 16 19:50:10 olli kernel: [   85.024012]  [cpufreq_notify_transition+125/176] cpufreq_notify_transition+0x7d/0xb0
Nov 16 19:50:10 olli kernel: [   85.024058]  [_end+131139337/2130332920] :powernow_k8:powernowk8_target+0x2c1/0x6b0
Nov 16 19:50:10 olli kernel: [   85.024108]  [cpufreq_governor_performance+34/48] cpufreq_governor_performance+0x22/0x30
Nov 16 19:50:10 olli kernel: [   85.024152]  [__cpufreq_governor+84/176] __cpufreq_governor+0x54/0xb0
Nov 16 19:50:10 olli kernel: [   85.024195]  [__cpufreq_set_policy+296/384] __cpufreq_set_policy+0x128/0x180
Nov 16 19:50:10 olli kernel: [   85.024240]  [cpufreq_add_dev+1035/1232] cpufreq_add_dev+0x40b/0x4d0
Nov 16 19:50:10 olli kernel: [   85.024288]  [handle_update+0/16] handle_update+0x0/0x10
Nov 16 19:50:10 olli kernel: [   85.024343]  [sysdev_driver_register+150/256] sysdev_driver_register+0x96/0x100
Nov 16 19:50:10 olli kernel: [   85.024388]  [cpufreq_register_driver+140/336] cpufreq_register_driver+0x8c/0x150
Nov 16 19:50:10 olli kernel: [   85.024433]  [sys_init_module+411/6576] sys_init_module+0x19b/0x19b0
Nov 16 19:50:10 olli kernel: [   85.024485]  [__up_write+33/304] __up_write+0x21/0x130
Nov 16 19:50:10 olli kernel: [   85.024532]  [system_call+126/131] system_call+0x7e/0x83
Nov 16 19:50:10 olli kernel: [   85.024578] 
Nov 16 19:50:10 olli kernel: [   85.024612] 
Nov 16 19:50:10 olli kernel: [   85.024613] Code: 48 01 04 d1 48 89 6e 08 c7 05 ee 1e 00 00 01 00 00 00 48 8b 
Nov 16 19:50:10 olli kernel: [   85.025169] RIP  [_end+131124600/2130332920] :cpufreq_stats:cpufreq_stats_update+0x40/0x70
Nov 16 19:50:10 olli kernel: [   85.025246]  RSP <ffff810036fc1ae8>
Nov 16 19:50:10 olli kernel: [   85.025284] CR2: ffff81083e30c3f8

```

I have tried to boot with ```
acpi=off noapic noalpic
``` and then it worked fine. Also disabling startup of "acpid" in system services seem to help.

Unfortunately the powerNow stuff is not working as well as suspend to RAM. (Of course also machine doesn't turn off automatically).

Is there any chance to get acpi support running without the Kernel problem ? At least that worked fine on OpenSuse10.3 ;)

TDFKAOlli

---

