---
title: "ACPI problem in ubuntu 8.10"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by fallucch on 2008-11-10
hi,

I have an HP compaq dc5800, i have upgrade ubuntu linux from 8.04 to 8.10 and there are problem with acpi kernel support:

 ------------[ cut here ]------------
[  339.113145] WARNING: at /build/buildd/linux-2.6.27/fs/sysfs/dir.c:463 sysfs_add_one+0x4e/0x50()
[  339.113150] sysfs: duplicate filename '1' can not be created
[  339.113155] Modules linked in: pci_slot(+) sbs sbshc af_packet i915 drm rfcomm sco bridge stp bnep l2cap bluetooth ppdev ipv6 dahdi_echocan_mg2 xpp_usb xpp wcb4xxp wctdm wcfxo wctdm24xxp wcte11xp wct1xxp wcte12xp wct4xxp dahdi acpi_cpufreq cpufreq_stats cpufreq_userspace cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative battery nfs lockd nfs_acl sunrpc iptable_filter ip_tables x_tables ac parport_pc lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event tpm_infineon snd_seq hisax evdev crc_ccitt psmouse snd_timer isdn snd_seq_device video serio_raw tpm output tpm_bios intel_agp snd slhc agpgart pcspkr soundcore wmi iTCO_wdt button snd_page_alloc iTCO_vendor_support shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif sg usbhid hid ata_piix pata_acpi ata_generic libata scsi_mod dock uhci_hcd ehci_hcd usbcore e1000e thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  339.113308] Pid: 11572, comm: modprobe Not tainted 2.6.27-7-generic #1
[  339.113314]  [<c0131d65>] warn_slowpath+0x65/0x90
[  339.113322]  [<c0253600>] ? vsnprintf+0x400/0x7b0
[  339.113330]  [<c024d9ca>] ? idr_get_empty_slot+0xda/0x250
[  339.113338]  [<c024dbc4>] ? ida_get_new_above+0x84/0x1c0
[  339.113344]  [<c01c724e>] ? find_inode+0xe/0x70
[  339.113351]  [<c01ffc30>] ? sysfs_ilookup_test+0x0/0x20
[  339.113357]  [<c01ffc30>] ? sysfs_ilookup_test+0x0/0x20
[  339.113363]  [<c02541f2>] ? strcmp+0x12/0x40
[  339.113370]  [<c01fff59>] ? sysfs_find_dirent+0x29/0x40
[  339.113377]  [<c0200018>] ? __sysfs_add_one+0x18/0x90
[  339.113383]  [<c02001ee>] sysfs_add_one+0x4e/0x50
[  339.113389]  [<c0200cde>] create_dir+0x4e/0x90
[  339.113394]  [<c0200d50>] sysfs_create_dir+0x30/0x50
[  339.113400]  [<c024e833>] kobject_add_internal+0xc3/0x1b0
[  339.113406]  [<c024e9f1>] kobject_add_varg+0x31/0x50
[  339.113411]  [<c024ea37>] kobject_init_and_add+0x27/0x30
[  339.113417]  [<c02626c4>] pci_create_slot+0xb4/0x110
[  339.113424]  [<f9215459>] register_slot+0x75/0x110 [pci_slot]
[  339.113440]  [<c014c0f0>] ? up+0x30/0x50
[  339.113447]  [<c0287609>] acpi_ns_walk_namespace+0xa0/0x117
[  339.113454]  [<c0285e12>] acpi_walk_namespace+0x4b/0x6b
[  339.113459]  [<f92153e4>] ? register_slot+0x0/0x110 [pci_slot]
[  339.113467]  [<f92152c4>] walk_p2p_bridge+0xbc/0xed [pci_slot]
[  339.113474]  [<f92153e4>] ? register_slot+0x0/0x110 [pci_slot]
[  339.113481]  [<f92153e4>] ? register_slot+0x0/0x110 [pci_slot]
[  339.113487]  [<f92153e4>] ? register_slot+0x0/0x110 [pci_slot]
[  339.113494]  [<c0287609>] acpi_ns_walk_namespace+0xa0/0x117
[  339.113500]  [<c0285e12>] acpi_walk_namespace+0x4b/0x6b
[  339.113506]  [<f9215208>] ? walk_p2p_bridge+0x0/0xed [pci_slot]
[  339.113513]  [<f92153e4>] ? register_slot+0x0/0x110 [pci_slot]
[  339.113520]  [<f92151a1>] walk_root_bridge+0x10a/0x139 [pci_slot]
[  339.113526]  [<f9215208>] ? walk_p2p_bridge+0x0/0xed [pci_slot]
[  339.113533]  [<f92153e4>] ? register_slot+0x0/0x110 [pci_slot]
[  339.113546]  [<f92151e3>] acpi_pci_slot_add+0x13/0x38 [pci_slot]
[  339.113553]  [<c0292152>] acpi_pci_register_driver+0x3e/0x55
[  339.113560]  [<f8897000>] ? acpi_pci_slot_init+0x0/0x20 [pci_slot]
[  339.113567]  [<f889701c>] acpi_pci_slot_init+0x1c/0x20 [pci_slot]
[  339.113573]  [<c0101120>] _stext+0x30/0x160
[  339.113585]  [<c014c604>] ? __blocking_notifier_call_chain+0x14/0x70
[  339.113598]  [<c015c208>] sys_init_module+0x88/0x1b0
[  339.113606]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
[  339.113612]  =======================
[  339.113615] ---[ end trace ed3da6631d28a4dc ]---
[  339.113620] kobject_add_internal failed for 1 with -EEXIST, don't try to register things with the same name in the same directory.
[  339.113627] Pid: 11572, comm: modprobe Tainted: G        W 2.6.27-7-generic #1
[  339.113631]  [<c037c406>] ? printk+0x1d/0x1f
[  339.113639]  [<c024e877>] kobject_add_internal+0x107/0x1b0
[  339.113645]  [<c024e9f1>] kobject_add_varg+0x31/0x50
[  339.113651]  [<c024ea37>] kobject_init_and_add+0x27/0x30
[  339.113656]  [<c02626c4>] pci_create_slot+0xb4/0x110
[  339.113662]  [<f9215459>] register_slot+0x75/0x110 [pci_slot]
[  339.113674]  [<c014c0f0>] ? up+0x30/0x50
[  339.113681]  [<c0287609>] acpi_ns_walk_namespace+0xa0/0x117
[  339.113687]  [<c0285e12>] acpi_walk_namespace+0x4b/0x6b
[  339.113692]  [<f92153e4>] ? register_slot+0x0/0x110 [pci_slot]
[  339.113699]  [<f92152c4>] walk_p2p_bridge+0xbc/0xed [pci_slot]
[  339.113705]  [<f92153e4>] ? register_slot+0x0/0x110 [pci_slot]
[  339.113713]  [<f92153e4>] ? register_slot+0x0/0x110 [pci_slot]
[  339.113720]  [<f92153e4>] ? register_slot+0x0/0x110 [pci_slot]
[  339.113727]  [<c0287609>] acpi_ns_walk_namespace+0xa0/0x117
[  339.113733]  [<c0285e12>] acpi_walk_namespace+0x4b/0x6b
[  339.113739]  [<f9215208>] ? walk_p2p_bridge+0x0/0xed [pci_slot]
[  339.113746]  [<f92153e4>] ? register_slot+0x0/0x110 [pci_slot]
[  339.113753]  [<f92151a1>] walk_root_bridge+0x10a/0x139 [pci_slot]
[  339.113759]  [<f9215208>] ? walk_p2p_bridge+0x0/0xed [pci_slot]
[  339.113766]  [<f92153e4>] ? register_slot+0x0/0x110 [pci_slot]
[  339.113778]  [<f92151e3>] acpi_pci_slot_add+0x13/0x38 [pci_slot]
[  339.113784]  [<c0292152>] acpi_pci_register_driver+0x3e/0x55
[  339.113790]  [<f8897000>] ? acpi_pci_slot_init+0x0/0x20 [pci_slot]
[  339.113798]  [<f889701c>] acpi_pci_slot_init+0x1c/0x20 [pci_slot]
[  339.113803]  [<c0101120>] _stext+0x30/0x160
[  339.113815]  [<c014c604>] ? __blocking_notifier_call_chain+0x14/0x70
[  339.113828]  [<c015c208>] sys_init_module+0x88/0x1b0
[  339.113834]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
[  339.113840]  =======================
[  339.113844] Unable to register kobject 1
[  339.113847] pci_slot: pci_create_slot returned -17
[  339.113925] ------------[ cut here ]------------
[  339.113929] WARNING: at /build/buildd/linux-2.6.27/fs/sysfs/dir.c:463 sysfs_add_one+0x4e/0x50()
[  339.113934] sysfs: duplicate filename '2' can not be created
[  339.113938] Modules linked in: pci_slot(+) sbs sbshc af_packet i915 drm rfcomm sco bridge stp bnep l2cap bluetooth ppdev ipv6 dahdi_echocan_mg2 xpp_usb xpp wcb4xxp wctdm wcfxo wctdm24xxp wcte11xp wct1xxp wcte12xp wct4xxp dahdi acpi_cpufreq cpufreq_stats cpufreq_userspace cpufreq_powersave cpufreq_ondemand freq_table cpufreq_conservative battery nfs lockd nfs_acl sunrpc iptable_filter ip_tables x_tables ac parport_pc lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event tpm_infineon snd_seq hisax evdev crc_ccitt psmouse snd_timer isdn snd_seq_device video serio_raw tpm output tpm_bios intel_agp snd slhc agpgart pcspkr soundcore wmi iTCO_wdt button snd_page_alloc iTCO_vendor_support shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif sg usbhid hid ata_piix pata_acpi ata_generic libata scsi_mod dock uhci_hcd ehci_hcd usbcore e1000e thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  339.114080] Pid: 11572, comm: modprobe Tainted: G        W 2.6.27-7-generic #1
[  339.114085]  [<c0131d65>] warn_slowpath+0x65/0x90
[  339.114092]  [<c0253600>] ? vsnprintf+0x400/0x7b0
[  339.114099]  [<c024d9ca>] ? idr_get_empty_slot+0xda/0x250
[  339.114106]  [<c024dbc4>] ? ida_get_new_above+0x84/0x1c0
[  339.114113]  [<c01c724e>] ? find_inode+0xe/0x70
[  339.114119]  [<c01ffc30>] ? sysfs_ilookup_test+0x0/0x20
[  339.114126]  [<c01ffc30>] ? sysfs_ilookup_test+0x0/0x20
[  339.114132]  [<c02541f2>] ? strcmp+0x12/0x40
[  339.114138]  [<c01fff59>] ? sysfs_find_dirent+0x29/0x40
[  339.114144]  [<c0200018>] ? __sysfs_add_one+0x18/0x90
[  339.114150]  [<c02001ee>] sysfs_add_one+0x4e/0x50
[  339.114155]  [<c0200cde>] create_dir+0x4e/0x90
[  339.114161]  [<c0200d50>] sysfs_create_dir+0x30/0x50
[  339.114166]  [<c024e833>] kobject_add_internal+0xc3/0x1b0
[  339.114172]  [<c024e9f1>] kobject_add_varg+0x31/0x50
[  339.114177]  [<c024ea37>] kobject_init_and_add+0x27/0x30
[  339.114183]  [<c02626c4>] pci_create_slot+0xb4/0x110
[  339.114188]  [<f9215459>] register_slot+0x75/0x110 [pci_slot]
[  339.114201]  [<c014c0f0>] ? up+0x30/0x50
[  339.114208]  [<c0287609>] acpi_ns_walk_namespace+0xa0/0x117
[  339.114214]  [<c0285e12>] acpi_walk_namespace+0x4b/0x6b
[  339.114219]  [<f92153e4>] ? register_slot+0x0/0x110 [pci_slot]
[  339.114226]  [<f92152c4>] walk_p2p_bridge+0xbc/0xed [pci_slot]
[  339.114232]  [<f92153e4>] ? register_slot+0x0/0x110 [pci_slot]
[  339.114239]  [<f92153e4>] ? register_slot+0x0/0x110 [pci_slot]
[  339.114245]  [<f92153e4>] ? register_slot+0x0/0x110 [pci_slot]
[  339.114252]  [<c0287609>] acpi_ns_walk_namespace+0xa0/0x117
[  339.114259]  [<c0285e12>] acpi_walk_namespace+0x4b/0x6b
[  339.114264]  [<f9215208>] ? walk_p2p_bridge+0x0/0xed [pci_slot]
[  339.114271]  [<f92153e4>] ? register_slot+0x0/0x110 [pci_slot]
[  339.114277]  [<f92151a1>] walk_root_bridge+0x10a/0x139 [pci_slot]
[  339.114284]  [<f9215208>] ? walk_p2p_bridge+0x0/0xed [pci_slot]
[  339.114290]  [<f92153e4>] ? register_slot+0x0/0x110 [pci_slot]
[  339.114303]  [<f92151e3>] acpi_pci_slot_add+0x13/0x38 [pci_slot]
[  339.114309]  [<c0292152>] acpi_pci_register_driver+0x3e/0x55
[  339.114315]  [<f8897000>] ? acpi_pci_slot_init+0x0/0x20 [pci_slot]
[  339.114323]  [<f889701c>] acpi_pci_slot_init+0x1c/0x20 [pci_slot]
[  339.114329]  [<c0101120>] _stext+0x30/0x160
[  339.114339]  [<c014c604>] ? __blocking_notifier_call_chain+0x14/0x70
[  339.114352]  [<c015c208>] sys_init_module+0x88/0x1b0
[  339.114359]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
[  339.114364]  =======================
[  339.114367] ---[ end trace ed3da6631d28a4dc ]---
[  339.114372] kobject_add_internal failed for 2 with -EEXIST, don't try to register things with the same name in the same directory.
[  339.114378] Pid: 11572, comm: modprobe Tainted: G        W 2.6.27-7-generic #1
[  339.114383]  [<c037c406>] ? printk+0x1d/0x1f
[  339.114390]  [<c024e877>] kobject_add_internal+0x107/0x1b0
[  339.114396]  [<c024e9f1>] kobject_add_varg+0x31/0x50
[  339.114402]  [<c024ea37>] kobject_init_and_add+0x27/0x30
[  339.114408]  [<c02626c4>] pci_create_slot+0xb4/0x110
[  339.114413]  [<f9215459>] register_slot+0x75/0x110 [pci_slot]
[  339.114427]  [<c014c0f0>] ? up+0x30/0x50
[  339.114433]  [<c0287609>] acpi_ns_walk_namespace+0xa0/0x117
[  339.114439]  [<c0285e12>] acpi_walk_namespace+0x4b/0x6b
[  339.114444]  [<f92153e4>] ? register_slot+0x0/0x110 [pci_slot]
[  339.114452]  [<f92152c4>] walk_p2p_bridge+0xbc/0xed [pci_slot]
[  339.114458]  [<f92153e4>] ? register_slot+0x0/0x110 [pci_slot]
[  339.114465]  [<f92153e4>] ? register_slot+0x0/0x110 [pci_slot]
[  339.114472]  [<f92153e4>] ? register_slot+0x0/0x110 [pci_slot]
[  339.114478]  [<c0287609>] acpi_ns_walk_namespace+0xa0/0x117
[  339.114485]  [<c0285e12>] acpi_walk_namespace+0x4b/0x6b
[  339.114490]  [<f9215208>] ? walk_p2p_bridge+0x0/0xed [pci_slot]
[  339.114497]  [<f92153e4>] ? register_slot+0x0/0x110 [pci_slot]
[  339.114504]  [<f92151a1>] walk_root_bridge+0x10a/0x139 [pci_slot]
[  339.114510]  [<f9215208>] ? walk_p2p_bridge+0x0/0xed [pci_slot]
[  339.114517]  [<f92153e4>] ? register_slot+0x0/0x110 [pci_slot]
[  339.114528]  [<f92151e3>] acpi_pci_slot_add+0x13/0x38 [pci_slot]
[  339.114534]  [<c0292152>] acpi_pci_register_driver+0x3e/0x55
[  339.114540]  [<f8897000>] ? acpi_pci_slot_init+0x0/0x20 [pci_slot]
[  339.114547]  [<f889701c>] acpi_pci_slot_init+0x1c/0x20 [pci_slot]
[  339.114553]  [<c0101120>] _stext+0x30/0x160
[  339.114564]  [<c014c604>] ? __blocking_notifier_call_chain+0x14/0x70
[  339.114577]  [<c015c208>] sys_init_module+0x88/0x1b0
[  339.114583]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
[  339.114589]  =======================
[  339.114593] Unable to register kobject 2
[  339.114597] pci_slot: pci_create_slot returned -17


If I exec acpid on boot, the system don't do the shutdown. The problem occurs only with the latest kernel 2.6.27-7, but non with 2.6.24-21.
there is any solution for this problem?

---

