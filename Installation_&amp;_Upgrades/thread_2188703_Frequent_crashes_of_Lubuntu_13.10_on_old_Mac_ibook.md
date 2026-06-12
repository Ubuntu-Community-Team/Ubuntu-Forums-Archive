---
title: "Frequent crashes of Lubuntu 13.10 on old Mac ibook G4"
date: 2013-11-18
forum: Installation &amp; Upgrades
---

### Post by rdh61 on 2013-11-18
Hi,

I have "successfully" installed Lubuntu 13.10 on an old Mac ibook G4, but I am getting very frequent crashes. These have happened so far while working with Software Updater, Synaptic and Firefox (but I haven't opened any other applications so far). The screen freezes, then goes black, blinks back to normal a couple of times, then goes terminally black. Then I have to reboot. I suspect it is a graphics issue. Any ideas what yaboot or other parameters might solve this?

Many thanks.

---

### Post by elizabeth on 2013-11-21
I have the same problem today on my PowerBook G4 upon installing 13.10. I looked through the kern.log which gave me my clue:

I thought it was a zram issue, but apparently I spoke too soon... seems to be a radeon GPU lockup problem. Digging in a bit more.

> Nov 20 21:06:26 r2g4 kernel: [  698.459504] radeon 0000:00:10.0: GPU lockup CP stall for more than 10000msec
Nov 20 21:06:26 r2g4 kernel: [  698.459524] radeon 0000:00:10.0: GPU lockup (waiting for 0x0000000000000cda)
Nov 20 21:06:26 r2g4 kernel: [  698.459536] radeon 0000:00:10.0: failed to get a new IB (-35)
Nov 20 21:06:26 r2g4 kernel: [  698.459545] [drm:radeon_cs_ib_chunk] *ERROR* Failed to get ib !
Nov 20 21:06:26 r2g4 kernel: [  698.460659] radeon 0000:00:10.0: Saved 987 dwords of commands on ring 0.
Nov 20 21:06:26 r2g4 kernel: [  698.460669] radeon 0000:00:10.0: GPU reset succeeded, trying to resume
Nov 20 21:06:26 r2g4 kernel: [  698.460727] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
Nov 20 21:06:26 r2g4 kernel: [  698.460747] radeon 0000:00:10.0: WB disabled
Nov 20 21:06:26 r2g4 kernel: [  698.460759] radeon 0000:00:10.0: fence driver on ring 0 use gpu addr 0x0000000000000000 and cpu addr 0xf15bb000
Nov 20 21:06:26 r2g4 kernel: [  698.460829] [drm] radeon: ring at 0x0000000000001000
Nov 20 21:06:26 r2g4 kernel: [  698.602534] [drm:r100_ring_test] *ERROR* radeon: ring test failed (scratch(0x15E8)=0xCAFEDEAD)
Nov 20 21:06:26 r2g4 kernel: [  698.602544] [drm:r100_cp_init] *ERROR* radeon: cp isn't working (-22).
Nov 20 21:06:26 r2g4 kernel: [  698.602553] radeon 0000:00:10.0: failed initializing CP (-22).
Nov 20 21:06:26 r2g4 kernel: [  698.801425] Modules linked in: btusb(F) joydev(F) parport_pc(F) ppdev(F) lp(F) parport(F) rfcomm(F) bnep(F) bluetooth(F) arc4(F) rtc_generic(F) b43(F) mac_hid(F) appletouch(F) bcma(F) mac80211(F) pcmcia(F) uio_pdrv_genirq(F) uio(F) cfg80211(F) yenta_socket(F) apm_emu(F) apm_emulation(F) pcmcia_rsrc(F) snd_powermac(F) snd_pcm(F) pcmcia_core(F) snd_page_alloc(F) snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) soundcore(F) hid_apple(F) hid_generic(F) usbhid(F) hid(F) radeon(F) sungem(F) sungem_phy(F) firewire_ohci(F) firewire_core(F) crc_itu_t(F) ttm(F) drm_kms_helper(F) drm(F) ssb(F) uninorth_agp(F)
Nov 20 21:06:26 r2g4 kernel: [  698.806605] NIP [f1a803c8] radeon_pm_resume+0xb4/0x2ac [radeon]
Nov 20 21:06:26 r2g4 kernel: [  698.806889] LR [f1a80398] radeon_pm_resume+0x84/0x2ac [radeon]
Nov 20 21:06:26 r2g4 kernel: [  698.807272] [c5ccfc10] [f1a80398] radeon_pm_resume+0x84/0x2ac [radeon] (unreliable)
Nov 20 21:06:26 r2g4 kernel: [  698.807611] [c5ccfc30] [f1a1f280] radeon_gpu_reset+0x22c/0x260 [radeon]
Nov 20 21:06:26 r2g4 kernel: [  698.807915] [c5ccfca0] [f1a5018c] radeon_cs_ioctl+0x138/0x94c [radeon]
Nov 20 21:07:58 r2g4 kernel: [    3.306958] [drm] radeon kernel modesetting enabled.
Nov 20 21:07:58 r2g4 kernel: [    3.307065] fb: conflicting fb hw usage radeondrmfb vs OFfb ATY,Jasper - removing generic driver
Nov 20 21:07:58 r2g4 kernel: [    3.308336] fb: conflicting fb hw usage radeondrmfb vs OFfb ATY,Jasper - removing generic driver
Nov 20 21:07:58 r2g4 kernel: [    3.308488] radeon 0000:00:10.0: enabling device (0006 -> 0007)
Nov 20 21:07:58 r2g4 kernel: [    3.309820] radeon 0000:00:10.0: Invalid ROM contents
Nov 20 21:07:58 r2g4 kernel: [    3.309836] radeon 0000:00:10.0: Invalid ROM contents
Nov 20 21:07:58 r2g4 kernel: [    3.309844] [drm:radeon_get_bios] *ERROR* Unable to locate a BIOS ROM
Nov 20 21:07:58 r2g4 kernel: [    3.309900] radeon 0000:00:10.0: putting AGP V2 device into 4x mode
Nov 20 21:07:58 r2g4 kernel: [    3.309961] radeon 0000:00:10.0: GTT: 256M 0x00000000 - 0x0FFFFFFF
Nov 20 21:07:58 r2g4 kernel: [    3.309974] radeon 0000:00:10.0: VRAM: 128M 0x00000000B8000000 - 0x00000000BFFFFFFF (128M used)
Nov 20 21:07:58 r2g4 kernel: [    3.314898] [drm] radeon: 128M of VRAM memory ready
Nov 20 21:07:58 r2g4 kernel: [    3.314903] [drm] radeon: 256M of GTT memory ready.
Nov 20 21:07:58 r2g4 kernel: [    3.314978] [drm] radeon: 1 quad pipes, 1 Z pipes initialized.
Nov 20 21:07:58 r2g4 kernel: [    3.315527] radeon 0000:00:10.0: WB disabled
Nov 20 21:07:58 r2g4 kernel: [    3.315538] radeon 0000:00:10.0: fence driver on ring 0 use gpu addr 0x0000000000000000 and cpu addr 0xf157e000
Nov 20 21:07:58 r2g4 kernel: [    3.315592] [drm] radeon: irq initialized.
Nov 20 21:07:58 r2g4 kernel: [    3.316349] [drm] radeon: ring at 0x0000000000001000
Nov 20 21:07:58 r2g4 kernel: [    3.708235] [drm] radeon legacy LVDS backlight initialized
Nov 20 21:07:58 r2g4 kernel: [    4.994450] radeon 0000:00:10.0: fb0: radeondrmfb frame buffer device
Nov 20 21:07:58 r2g4 kernel: [    4.994455] radeon 0000:00:10.0: registered panic notifier
Nov 20 21:07:58 r2g4 kernel: [    4.995137] [drm] Initialized radeon 2.34.0 20080528 for 0000:00:10.0 on minor 0

---

### Post by rdh61 on 2013-11-21
> **elizabeth said:**
> seems to be a radeon GPU lockup problem. Digging in a bit more.

Thank you for your reply Elizabeth. Please do post back if you come up with a solution.

---

### Post by elizabeth on 2013-11-21
OK, I think I got it :)

Changed the append line in /etc/yaboot.conf:

        append="video=radeonfb:1024x786-32@60"

Then run: sudo yabin

And reboot. No crashes yet.

Got my clue via [https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/PPC#No_desktop_with_Radeon_video_chips_on_LiveCD](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/PPC#No_desktop_with_Radeon_video_chips_on_LiveCD)

---

### Post by rdh61 on 2013-11-22
Many thanks Elizabeth, it's worked for me so far!

(I think you mean "ybin")

---

