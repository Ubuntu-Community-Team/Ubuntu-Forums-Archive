---
title: "Latest kernel upgrade, Ubuntu 7.10, breaks sound"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by TheSynAck on 2007-12-20
Upgraded Kernel in Ubuntu 7.10 from 2.6.20-16-generic to 2.6.22-14-generic and my sound device is not recognized.

A list of /dev/ shows the audio devices have not been populated or created.

Reverting back to the old kernel, sound works.

Installing 2.6.22-14-386 (new) provides working sound, but no-SMP/Multi-core support, and a machine that runs half its normal speed.

At this point, I can trade sound for multi-core, or multi-core for sound with the newest kernel.

I searched for related items by subject and using the forum search. Latest item listed appears to have been from April-May.

Unless anyone knows of an existing thread on this same issue, or has a quick-quick, I'll track down the kernel module that is not being loaded properly, or maybe missing.

If you want more specific, that can be provided. (Dumps of logs, lspci, lsmod, and more can be overwhelming, and exceed the maximum post limit on the forums.)

---

### Post by OldManRiver on 2007-12-20
> **TheSynAck said:**
> Upgraded Kernel in Ubuntu 7.10 from 2.6.20-16-generic to 2.6.22-14-generic and my sound device is not recognized.

A list of /dev/ shows the audio devices have not been populated or created.

Reverting back to the old kernel, sound works.

Installing 2.6.22-14-386 (new) provides working sound, but no-SMP/Multi-core support, and a machine that runs half its normal speed.

At this point, I can trade sound for multi-core, or multi-core for sound with the newest kernel.

I searched for related items by subject and using the forum search. Latest item listed appears to have been from April-May.

Unless anyone knows of an existing thread on this same issue, or has a quick-quick, I'll track down the kernel module that is not being loaded properly, or maybe missing.

If you want more specific, that can be provided. (Dumps of logs, lspci, lsmod, and more can be overwhelming, and exceed the maximum post limit on the forums.)

What is the chipset?

I had real sound problems with ALC655/AC97 (SIS) on my install and have a play-by-play log of it at:

[http://ubuntuforums.org/showthread.php?t=637969](http://ubuntuforums.org/showthread.php?t=637969)

The sound problem is problem #1.

The trick was extracting and running the realtek custom driver, up inside the original extract directory.  If you try the normal install, which needs to read this driver set, it will not find it.  If you have another driver set, check to see if you have the same extract problem and try what I did with the manual install at the end to the log for my problem #1.

OMR

---

### Post by TheSynAck on 2007-12-22
> **OldManRiver said:**
> What is the chipset?

I had real sound problems with ALC655/AC97 (SIS) on my install and have a play-by-play log of it at:

[http://ubuntuforums.org/showthread.php?t=637969](http://ubuntuforums.org/showthread.php?t=637969)

The sound problem is problem #1.

The trick was extracting and running the realtek custom driver, up inside the original extract directory.  If you try the normal install, which needs to read this driver set, it will not find it.  If you have another driver set, check to see if you have the same extract problem and try what I did with the manual install at the end to the log for my problem #1.

OMR

Thanks for the reply. :-)

I spent some time, and did track down the cause for this.

I have a "winmodem" on this laptop and bought the linuxant drivers for linux. They have worked fine from the 6.10 through to the 7.10 Ubuntu, but the latest kernel upgrade after Ubuntu 7.10 (working) to new Ubuntu 7.10 kernel (issues with hsfmodem from linuxant) is where problems have surfaced.

Narrowed it down. When the hsf modem drivers for Ubuntu 7.10 (hsfmodem-7.68.00.04full/hsfmodem_7.68.00.04full_k2.6.22_14_generic_ubuntu_i386.deb.zip 
"fd74a6161b5b4b00fdc0979f58c5b2f4" ) was installed, sound was broken and the modem was no longer recognized.

I've tried several variations of their drivers, including a source-build, but all result with the same thing.

Once their hsf* modules are loaded, the following two modules (required by my hardware for proper sound function) won't load:

snd_hda_intel
snd_hda_codec

When I attempt to load them by hand, I get the following from dmesg:
  
Dec 21 11:46:33 localhost kernel: [   18.532000] snd_hda_codec: disagrees about version of symbol snd_ctl_add
Dec 21 11:46:33 localhost kernel: [   18.532000] snd_hda_codec: Unknown symbol snd_ctl_add
Dec 21 11:46:33 localhost kernel: [   18.532000] snd_hda_codec: disagrees about version of symbol snd_pcm_kernel_ioctl
Dec 21 11:46:33 localhost kernel: [   18.532000] snd_hda_codec: Unknown symbol snd_pcm_kernel_ioctl
Dec 21 11:46:33 localhost kernel: [   18.532000] snd_hda_codec: disagrees about version of symbol snd_card_proc_new
Dec 21 11:46:33 localhost kernel: [   18.532000] snd_hda_codec: Unknown symbol snd_card_proc_new
Dec 21 11:46:33 localhost kernel: [   18.532000] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
Dec 21 11:46:33 localhost kernel: [   18.532000] snd_hda_codec: Unknown symbol snd_ctl_find_id
Dec 21 11:46:33 localhost kernel: [   18.532000] snd_hda_codec: disagrees about version of symbol snd_pcm_open_substream
Dec 21 11:46:33 localhost kernel: [   18.532000] snd_hda_codec: Unknown symbol snd_pcm_open_substream
Dec 21 11:46:33 localhost kernel: [   18.532000] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
Dec 21 11:46:33 localhost kernel: [   18.532000] snd_hda_codec: Unknown symbol snd_ctl_new1
Dec 21 11:46:33 localhost kernel: [   18.532000] snd_hda_codec: disagrees about version of symbol snd_component_add
Dec 21 11:46:33 localhost kernel: [   18.532000] snd_hda_codec: Unknown symbol snd_component_add
Dec 21 11:46:33 localhost kernel: [   18.532000] snd_hda_codec: Unknown symbol snd_ctl_elem_read
Dec 21 11:46:33 localhost kernel: [   18.532000] snd_hda_codec: Unknown symbol snd_ctl_elem_write
Dec 21 11:46:33 localhost kernel: [   18.532000] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_list
Dec 21 11:46:33 localhost kernel: [   18.532000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_list
Dec 21 11:46:33 localhost kernel: [   18.532000] snd_hda_codec: disagrees about version of symbol snd_device_new
Dec 21 11:46:33 localhost kernel: [   18.532000] snd_hda_codec: Unknown symbol snd_device_new
Dec 21 11:46:33 localhost kernel: [   18.532000] snd_hda_codec: disagrees about version of symbol snd_pcm_release_substream
Dec 21 11:46:33 localhost kernel: [   18.532000] snd_hda_codec: Unknown symbol snd_pcm_release_substream
Dec 21 11:46:33 localhost kernel: [   18.532000] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_step
Dec 21 11:46:33 localhost kernel: [   18.532000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_pcm_new
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: disagrees about version of symbol snd_card_register
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_card_register
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: disagrees about version of symbol snd_card_free
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_card_free
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_hda_bus_new
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_hda_build_pcms
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_hda_codec_new
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_hda_queue_unsol_event
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: disagrees about version of symbol snd_card_new
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_card_new
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_hda_calc_stream_format
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_hda_suspend
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: disagrees about version of symbol snd_device_new
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_device_new
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_hda_codec_remove_notify_all
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_card_disconnect
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_hda_resume
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_hda_build_controls
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
Dec 21 11:46:33 localhost kernel: [   18.540000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step

Bummer deal. I've reported this to the HSF mailing list for linuxant.

I don't think this will help anyone here, but I'll include the result of lspci anyway: 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
 
Waiting for a reply from their list. If I find a solution, I'll followup this thread with the fix that worked for me.

---

