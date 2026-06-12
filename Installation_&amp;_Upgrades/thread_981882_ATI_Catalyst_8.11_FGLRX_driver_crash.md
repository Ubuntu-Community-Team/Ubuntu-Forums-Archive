---
title: "ATI Catalyst 8.11 FGLRX driver crash"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by frogotronic on 2008-11-14
Hello,

Running a fully patched 8.04.1 LTS (Hardy Heron) system.  Radeon Mobile x2300 card on an HP 6910p laptop.

Previously running ATI Catalyst FGLRX 8.10 driver.  Manually installed ( [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page) ).

Worked beautifully, Suspend & Hibernate, dual screen - you name it.

Tried to upgrade to 8.11 and crashed.  Bulletproof X kicked in (nice feature) and booted me into a 800x600 VESA X server.  Tried uninstall & reinstall.

Finally removed 8.11 and went back to 8.10.

Anyone else have this issue with 8.11?  Is 8.11 incompatible with 8.04.1?

Thanks
- CH 

:confused:

---

### Post by Mr_Freez3 on 2008-11-14
CH,

You are not alone.  The exact same thing happened to me, and I also had to go back to the ATI Catalyst FGLRX 8.10 driver.

I have a destop PC running a fully patched 8.04.1 LTS (Hardy Heron) 32-bit system, AMD Sempron 2500+, Radeon 9600XT video graphics card.

Guessing there is something flawed in the 8.11 driver, or there is a missing step in METHOD 2 of the manual install instructions.

It's good to know someone else had the problem also. :lolflag:

**After reading the release notes concerning the 8.11 driver, I'm content to stay with 8.10 because there's really nothing new relevant to my video card anyway.

---

### Post by frogotronic on 2008-11-14
Thanks, good to know.  I'll file a bug with ATI and post the bug number back here.

- CH

_____________________________________________________________

Bugzilla Bug Posted:  [http://ati.cchtml.com/show_bug.cgi?id=1357](http://ati.cchtml.com/show_bug.cgi?id=1357)

---

### Post by enryfox on 2008-11-14
Hi, 

same problem to me: 8.10 works perfectly (using right now), tried update to 8.11 manual method but fglrx driver hangs while loading DRM module. 

I have a IBM laptop with mobility fireGl v3200 ( ~mobility radeon x600)

I've reverted back to 8.10 and will skip 8.11 version (i actually have no reason to update).

Let us what ATI folks say!

cheers

---

### Post by frogotronic on 2008-11-14
This bug is also reported in launchpad.

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/297799/](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/297799/)

---

### Post by Cruxic on 2008-11-15
8.552 is working for me on intrepid.  As suggested in the launchpad thread I installed the packages provided by *intrepid-proposed* (checkbox in Synaptic->Repositories->Updates)

I seem to be having an unrelated issue where my DVI connection wont work (only analog).  It was working with hardy but not intrepid so I was hoping this update would fix it.  No dice.

---

### Post by Skripka on 2008-11-15
> **enryfox said:**
> 
Let us what ATI folks say!

cheers


Breaking News Flash:  New AMD/ATi drivers are beta quality:shock:

---

### Post by Prankie1 on 2008-11-15
> **enryfox said:**
> Hi, 

same problem to me: 8.10 works perfectly (using right now), tried update to 8.11 manual method but fglrx driver hangs while loading DRM module. 

I have a IBM laptop with mobility fireGl v3200 ( ~mobility radeon x600)

I've reverted back to 8.10 and will skip 8.11 version (i actually have no reason to update).

Let us what ATI folks say!

cheers

Hi, how do you revert to a earlier version of ATI catalyst driver?

---

### Post by enryfox on 2008-11-15
> **Prankie1 said:**
> Hi, how do you revert to a earlier version of ATI catalyst driver?

I start Xorg with radeon driver (just edit xorg.conf and reboot), then simply remove all fglrx packages with synaptic, delete the /etc/ATI directory and delete everything under /var/lib/dkmg/fglrx; finally i simply re-do the procedure using previous ATI driver package...

bye

---

### Post by frogotronic on 2008-11-15
> **Cruxic said:**
> 8.552 is working for me on intrepid.  As suggested in the launchpad thread I installed the packages provided by *intrepid-proposed* (checkbox in Synaptic->Repositories->Updates)

I seem to be having an unrelated issue where my DVI connection wont work (only analog).  It was working with hardy but not intrepid so I was hoping this update would fix it.  No dice.

So...just to clarify:  I can download the 8.552 debs from the intrepid repos and install them on hardy?  That won't work by the package installer as it causes all sorts of dependency problems.

Just to re-iterate...I'm using Hardy, not Intrepid.

- CH

---

### Post by patrickballeux on 2008-11-15
I updated this morning to proposed 8.11 in Intrepid (amd64) and my laptop booted in low res.  Reverting to 8.10.

Here is the logs from dmesg:

[   60.798385] BUG: scheduling while atomic: Xorg/7059/0x10000001
[   60.798389] Modules linked in: af_packet binfmt_misc rfkill_input rfcomm sco bridge stp bnep l2cap ipv6 vboxdrv ppdev powernow_k8 cpufreq_ondemand cpufreq_powersave cpufreq_stats freq_table cpufreq_conservative cpufreq_userspace sbs container sbshc pci_slot vloopback visor usbserial sbp2 parport_pc lp parport joydev arc4 ecb crypto_blkcipher dcdbas b43 uvcvideo rfkill compat_ioctl32 videodev mac80211 serio_raw pcspkr v4l1_compat psmouse evdev snd_hda_intel cfg80211 led_class snd_pcm_oss input_polldev snd_mixer_oss snd_pcm btusb snd_seq_dummy bluetooth snd_seq_oss wl(P) ieee80211_crypt fglrx(P) video snd_seq_midi output snd_rawmidi snd_seq_midi_event snd_seq sdhci_pci sdhci snd_timer snd_seq_device mmc_core snd wmi soundcore button ac k8temp battery shpchp pci_hotplug i2c_piix4 snd_page_alloc i2c_core ext3 jbd mbcache sr_mod cdrom pata_acpi sd_mod crc_t10dif pata_atiixp sg ohci1394 ieee1394 b44 mii ehci_hcd ohci_hcd ata_generic ahci usbcore libata scsi_mod dock ssb thermal processor fan fbcon tileblit font bitblit softcursor fuse
[   60.798475] Pid: 7059, comm: Xorg Tainted: P      D   2.6.27-8-generic #1
[   60.798477] 
[   60.798478] Call Trace:
[   60.798479]  <#DB[1]>  [<ffffffff8024416d>] __schedule_bug+0x6d/0x80
[   60.798491]  [<ffffffff80500798>] thread_return+0x19b/0x3c3
[   60.798495]  [<ffffffff802e2050>] ? __slab_free+0x10/0x120
[   60.798500]  [<ffffffff8045c71f>] ? __kfree_skb+0x3f/0xa0
[   60.798504]  [<ffffffff80245d90>] __cond_resched+0x20/0x50
[   60.798506]  [<ffffffff80500ac5>] _cond_resched+0x35/0x50
[   60.798510]  [<ffffffff8030021d>] dput+0x13d/0x190
[   60.798514]  [<ffffffff804ddee5>] unix_release_sock+0x175/0x260
[   60.798517]  [<ffffffff8045895a>] ? release_sock+0xba/0xd0
[   60.798520]  [<ffffffff804ddff6>] unix_release+0x26/0x30
[   60.798523]  [<ffffffff80455d69>] sock_release+0x29/0xa0
[   60.798525]  [<ffffffff80455e0b>] sock_close+0x2b/0x50
[   60.798529]  [<ffffffff802eaf99>] __fput+0xc9/0x1b0
[   60.798531]  [<ffffffff802eb0a5>] fput+0x25/0x30
[   60.798535]  [<ffffffff802e743b>] filp_close+0x5b/0x90
[   60.798538]  [<ffffffff802512d2>] put_files_struct+0x82/0xe0
[   60.798541]  [<ffffffff80251384>] exit_files+0x54/0x70
[   60.798544]  [<ffffffff802532b5>] do_exit+0x2b5/0x410
[   60.798548]  [<ffffffff805032c0>] oops_begin+0x0/0xb0
[   60.798551]  [<ffffffff80214d23>] die+0x63/0xa0
[   60.798554]  [<ffffffff8050396e>] do_trap+0x14e/0x170
[   60.798557]  [<ffffffff8050581a>] ? atomic_notifier_call_chain+0x1a/0x20
[   60.798561]  [<ffffffff80503a14>] do_int3+0x84/0xc0
[   60.798564]  [<ffffffff80502e86>] int3+0xb6/0xf0
[   60.798651]  [<ffffffffa02c2fd0>] ? mc_heap_add_inv_fb_heap+0x180/0x190 [fglrx]
[   60.798654]  <<EOE>>  [<ffffffffa02c069a>] ? mc_heap_init+0x21a/0x710 [fglrx]
[   60.798750]  [<ffffffffa02c0c3c>] ? mc_heap_cleanup+0xac/0x420 [fglrx]
[   60.798794]  [<ffffffffa02a3e2e>] ? KCL_STR_Memset+0xe/0x10 [fglrx]
[   60.798841]  [<ffffffffa02b11ba>] ? firegl_init_pcie+0xfa/0x370 [fglrx]
[   60.798886]  [<ffffffffa02b10c0>] ? firegl_init_pcie+0x0/0x370 [fglrx]
[   60.798931]  [<ffffffffa02acacd>] ? firegl_ioctl+0x1ed/0x260 [fglrx]
[   60.798936]  [<ffffffff80267050>] ? autoremove_wake_function+0x0/0x40
[   60.798980]  [<ffffffffa02a16a6>] ? ip_firegl_ioctl+0x16/0x20 [fglrx]
[   60.798983]  [<ffffffff802f85c5>] ? vfs_ioctl+0x85/0xb0
[   60.798986]  [<ffffffff802f8873>] ? do_vfs_ioctl+0x283/0x2f0
[   60.798988]  [<ffffffff802f8981>] ? sys_ioctl+0xa1/0xb0
[   60.798993]  [<ffffffff8021285a>] ? system_call_fastpath+0x16/0x1b
[   60.798995] 
[   60.801983] [fglrx:firegl_release] *ERROR* device busy: 1 0
[   60.801985] [fglrx] release failed with code -EBUSY

Seems that the new driver is broken...

---

### Post by enryfox on 2008-11-16
> **cement_head said:**
> So...just to clarify:  I can download the 8.552 debs from the intrepid repos and install them on hardy?  That won't work by the package installer as it causes all sorts of dependency problems.

Just to re-iterate...I'm using Hardy, not Intrepid.

- CH

It looks like 8.11 driver has serious problems... i'm using hardy too (intrepid has still some youth problems) and i will stick to 8.10; if you do not have specific issue requiring driver update (i have none) keep using 8.10. By mid December 8.12 will be out and we will try that release instead. 

I myself should remind me more often the old saying "don't fix it if it ain't broken"

bye

---

### Post by frogotronic on 2008-11-16
yep, sounds like a plan, 8.10 is working well so I wait and see if 8.12 are any better.

Thanks all,
- CH   :popcorn:

---

### Post by zwaardmeester on 2008-11-18
Mario Limonciello  wrote on 2008-11-14
> Please use 8-11 from intrepid-proposed if you want to use 8-11

This appears to work for me on intrepid.

---

