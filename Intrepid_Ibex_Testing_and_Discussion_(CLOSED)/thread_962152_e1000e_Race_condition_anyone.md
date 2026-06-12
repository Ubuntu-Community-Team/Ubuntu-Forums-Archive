---
title: "e1000e Race condition anyone?"
date: 2008-10-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by likuidkewl on 2008-10-29
Is anyone else getting a race from the e1000e driver(evident in syslog)?  Just curious before I fix up a bug report tomorrow.

Some possible culprits, 
all related to power saving(R61 - 773219u):
"blacklist uhci_hcd", "blacklist pcmcia", "blacklist yenta_socket"
ethtool -s eth0 wol d

Linux Test 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux

---

### Post by ltmon on 2008-10-30
Just searched to see if anyone else had the same problem.

Fully up-to-date Kubuntu Intrepid, upgraded from Hardy via the upgrade tool.

My irrational fear is that this is related somehow to the recent EEPROM/NVR overwriting bug, and the hardware has been scrambled.

My main symptom was that the network interface is shown as "NO CARRIER" even when plugged in to a perfectly good line.

Now it seems my "eth0" has disappeared altogether (based on "ifconfig -a"), but an inoperative "pan0" ethernet device has turned up. eth0 seems to appear in "lshw" still however:

```

# sudo lshw -C network
  *-network UNCLAIMED                              
       description: Ethernet controller            
       product: 82566MM Gigabit Network Connection 
       vendor: Intel Corporation                   
       physical id: 19                             
       bus info: pci@0000:00:19.0                  
       version: 03                                 
       width: 32 bits                              
       clock: 33MHz                                
       capabilities: cap_list                      
       configuration: latency=0                    
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:1d:e0:27:58:0b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.65 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:0e:33:bb:5f:02
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

```

# sudo ifconfig -a
lo        Link encap:Local Loopback                                                                                             
          inet addr:127.0.0.1  Mask:255.0.0.0                                                                                   
          inet6 addr: ::1/128 Scope:Host                                                                                        
          UP LOOPBACK RUNNING  MTU:16436  Metric:1                                                                              
          RX packets:23941 errors:0 dropped:0 overruns:0 frame:0                                                                
          TX packets:23941 errors:0 dropped:0 overruns:0 carrier:0                                                              
          collisions:0 txqueuelen:0                                                                                             
          RX bytes:1206624 (1.2 MB)  TX bytes:1206624 (1.2 MB)                                                                  

pan0      Link encap:Ethernet  HWaddr 46:0e:33:bb:5f:02  
          BROADCAST MULTICAST  MTU:1500  Metric:1        
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:27:58:0b
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:fe27:580b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:240024 errors:0 dropped:0 overruns:0 frame:0
          TX packets:166047 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:276765548 (276.7 MB)  TX bytes:15483906 (15.4 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-E0-27-58-0B-38-30-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Relevant part of syslog when loading the e1000e driver:

```

ct 30 12:57:59 pastorius kernel: [ 6532.506551] WARNING: at /build/buildd/linux-2.6.27/drivers/net/e1000e/ich8lan.c:403 e1000_acquire_swflag_ich8lan+0x47/0xd0 [e1000e]()
Oct 30 12:57:59 pastorius kernel: [ 6532.506554] e1000e mutex contention. Owned by pid -1
Oct 30 12:57:59 pastorius kernel: [ 6532.506555] Modules linked in: ipv6 af_packet binfmt_misc rfcomm sco bridge stp bnep l2cap ppdev acpi_cpufreq cpufreq_ondemand cpufreq_conservative cpufreq_stats freq_table cpufreq_powersave cpufreq_userspace pci_slot sbs sbshc container iptable_filter ip_tables x_tables coretemp hdaps input_polldev sbp2 lp joydev snd_hda_intel arc4 snd_usb_audio ecb snd_pcm_oss snd_mixer_oss crypto_blkcipher pcmcia snd_pcm snd_seq_dummy iwlagn iwlcore snd_usb_lib snd_seq_oss usbhid psmouse thinkpad_acpi snd_seq_midi hid yenta_socket snd_rawmidi btusb ricoh_mmc rfkill nvram rsrc_nonstatic sdhci_pci led_class iTCO_wdt iTCO_vendor_support serio_raw snd_seq_midi_event pcspkr bluetooth sdhci snd_hwdep pcmcia_core evdev mac80211 mmc_core nvidia(P) snd_seq ac cfg80211 i2c_core battery video parport_pc output parport snd_timer snd_seq_device wmi snd intel_agp agpgart soundcore shpchp pci_hotplug button snd_page_alloc ext3 jbd mbcache sr_mod cdrom ata_generic sd_mod crc_t10dif sg ata_piix ahci pata_acp
Oct 30 12:57:59 pastorius kernel:  libata scsi_mod ohci1394 ieee1394 ehci_hcd uhci_hcd usbcore e1000e(-) dock thermal processor fan fbcon tileblit font bitblit softcursor fuse
Oct 30 12:57:59 pastorius kernel: [ 6532.506634] Pid: 8644, comm: rmmod Tainted: P        W 2.6.27-7-generic #1
Oct 30 12:57:59 pastorius kernel: [ 6532.506636]  [<c0131d65>] warn_slowpath+0x65/0x90
Oct 30 12:57:59 pastorius kernel: [ 6532.506641]  [<c037c989>] ? schedule+0x429/0x790
Oct 30 12:57:59 pastorius kernel: [ 6532.506644]  [<c01376e6>] ? __do_softirq+0xf6/0x120
Oct 30 12:57:59 pastorius kernel: [ 6532.506648]  [<c01050f8>] ? apic_timer_interrupt+0x28/0x30
Oct 30 12:57:59 pastorius kernel: [ 6532.506651]  [<c0253dde>] ? delay_tsc+0xe/0x70
Oct 30 12:57:59 pastorius kernel: [ 6532.506656]  [<c0253ea1>] ? __const_udelay+0x31/0x40
Oct 30 12:57:59 pastorius kernel: [ 6532.506660]  [<f88c443c>] ? e1000_flash_cycle_ich8lan+0x4c/0x70 [e1000e]
Oct 30 12:57:59 pastorius kernel: [ 6532.506667]  [<c037d3e9>] ? mutex_trylock+0x9/0x30
Oct 30 12:57:59 pastorius kernel: [ 6532.506671]  [<f88c4c17>] e1000_acquire_swflag_ich8lan+0x47/0xd0 [e1000e]
Oct 30 12:57:59 pastorius kernel: [ 6532.506680]  [<f88c9502>] e1000e_write_phy_reg_igp+0x22/0x70 [e1000e]
Oct 30 12:57:59 pastorius kernel: [ 6532.506688]  [<f88c4932>] e1000_phy_hw_reset_ich8lan+0x182/0x1b0 [e1000e]
Oct 30 12:57:59 pastorius kernel: [ 6532.506696]  [<f88d4c10>] e1000_remove+0xc8/0xca [e1000e]
Oct 30 12:57:59 pastorius kernel: [ 6532.506703]  [<c02630be>] pci_device_remove+0x1e/0x40
Oct 30 12:57:59 pastorius kernel: [ 6532.506706]  [<c02c3a19>] __device_release_driver+0x79/0xc0
Oct 30 12:57:59 pastorius kernel: [ 6532.506710]  [<c02c3aff>] driver_detach+0x9f/0xb0
Oct 30 12:57:59 pastorius kernel: [ 6532.506714]  [<c02c2d1b>] bus_remove_driver+0x7b/0xb0
Oct 30 12:57:59 pastorius kernel: [ 6532.506719]  [<c02c4009>] driver_unregister+0x39/0x40
Oct 30 12:57:59 pastorius kernel: [ 6532.506723]  [<c02632e9>] pci_unregister_driver+0x29/0x80
Oct 30 12:57:59 pastorius kernel: [ 6532.506726]  [<c013366b>] ? put_online_cpus+0x3b/0x50
Oct 30 12:57:59 pastorius kernel: [ 6532.506731]  [<f88d4b37>] e1000_exit_module+0x12/0x23 [e1000e]
Oct 30 12:57:59 pastorius kernel: [ 6532.506737]  [<c015ad07>] sys_delete_module+0x167/0x230
Oct 30 12:57:59 pastorius kernel: [ 6532.506742]  [<c0199d7a>] ? do_munmap+0x1da/0x230
Oct 30 12:57:59 pastorius kernel: [ 6532.506747]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
Oct 30 12:57:59 pastorius kernel: [ 6532.506749]  =======================
Oct 30 12:57:59 pastorius kernel: [ 6532.506751] ---[ end trace 4ce4ed59a0f961ee ]---
Oct 30 12:57:59 pastorius kernel: [ 6532.605488] e1000e 0000:00:19.0: PCI INT A disabled
Oct 30 12:58:02 pastorius kernel: [ 6536.254959] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
Oct 30 12:58:02 pastorius kernel: [ 6536.254968] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Oct 30 12:58:02 pastorius kernel: [ 6536.257751] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Oct 30 12:58:02 pastorius kernel: [ 6536.257774] e1000e 0000:00:19.0: setting latency timer to 64
Oct 30 12:59:24 pastorius kernel: [ 6617.925014] e1000e 0000:00:19.0: PCI INT A disabled

```

If this doesn't have a simple solution I'm overlooking, then I'll report it as a bug: let me know if you have any luck or report this.

Cheers,

L.

---

### Post by likuidkewl on 2008-10-30
I have not had time to report this yet.  So feel free to go at it.
Out of curiousity have/did you install the ethtool package?  I don't think I was getting this error before that.  But I could be wrong, it could be one of the updates.

-Dan

---

