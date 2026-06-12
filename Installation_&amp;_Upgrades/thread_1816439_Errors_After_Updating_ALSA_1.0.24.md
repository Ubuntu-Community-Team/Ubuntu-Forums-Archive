---
title: "Errors After Updating ALSA 1.0.24"
date: 2011-08-01
forum: Installation &amp; Upgrades
---

### Post by GeoSmoot on 2011-08-01
I am running mythbuntu 11.04 with kernal 2.6.38-10-generic with a Hauppauge HVR-1600 as my tuner, video in, and ATSC device. I have an Nvidia GT430 as the video card and have been following Nvidia's list of everything that should be updated before trying to get HDMI output (I've already done the malloc kernal adjustment). I have done the latest update for the Nvidia driver and I have done the latest git update for v4l drivers. Something broke after updating ALSA from 1.0.23 to 1.0 24. Can anyone give me an idea of where to look to correct the problem? Here are the appropriate portions of /var/log/syslog before and after the update.
 
[code]
Excerpts of /var/log/syslog with ALSA 1.0.23:
Aug 1 19:43:12 VideoBox2 kernel: [ 29.160623] tda18271: RF tracking filter calibration complete
Aug 1 19:43:12 VideoBox2 kernel: [ 29.208685] tda829x 1-0042: type set to tda8295+18271
Aug 1 19:43:13 VideoBox2 kernel: [ 29.913204] cx18-0: Registered device video0 for encoder MPEG (64 x 32.00 kB)
Aug 1 19:43:13 VideoBox2 kernel: [ 29.913211] DVB: registering new adapter (cx18)
Aug 1 19:43:13 VideoBox2 kernel: [ 30.039206] tda18271 0-0060: creating new instance
Aug 1 19:43:13 VideoBox2 kernel: [ 30.043957] TDA18271HD/C2 detected @ 0-0060
Aug 1 19:43:13 VideoBox2 kernel: [ 30.292117] DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
Aug 1 19:43:13 VideoBox2 kernel: [ 30.292538] cx18-0: DVB Frontend registered
Aug 1 19:43:13 VideoBox2 kernel: [ 30.292545] cx18-0: Registered DVB adapter0 for TS (32 x 32.00 kB)
Aug 1 19:43:13 VideoBox2 kernel: [ 30.292635] cx18-0: Registered device video32 for encoder YUV (20 x 101.25 kB)
Aug 1 19:43:13 VideoBox2 kernel: [ 30.292780] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
Aug 1 19:43:13 VideoBox2 kernel: [ 30.292859] cx18-0: Registered device video24 for encoder PCM audio (256 x 4.00 kB)
Aug 1 19:43:13 VideoBox2 kernel: [ 30.292866] cx18-0: Initialized card: Hauppauge HVR-1600
Aug 1 19:43:13 VideoBox2 kernel: [ 30.293968] cx18: End initialization
Aug 1 19:43:13 VideoBox2 kernel: [ 30.309307] cx18-alsa: module loading...
Aug 1 19:43:13 VideoBox2 kernel: [ 30.460019] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
Aug 1 19:43:13 VideoBox2 kernel: [ 30.595661] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
Aug 1 19:43:13 VideoBox2 kernel: [ 30.602013] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
Aug 1 19:43:14 VideoBox2 kernel: [ 31.453896] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
Aug 1 19:43:14 VideoBox2 kernel: [ 31.474661] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
 
Excerpts of /var/log/syslog with ALSA 1.0.24:
Aug 1 19:53:34 VideoBox2 kernel: [ 29.691272] tda18271 0-0060: creating new instance
Aug 1 19:53:34 VideoBox2 kernel: [ 29.696039] TDA18271HD/C2 detected @ 0-0060
Aug 1 19:53:35 VideoBox2 kernel: [ 29.944200] DVB: registering adapter 0 frontend 0 (Samsung S5H1411 QAM/8VSB Frontend)...
Aug 1 19:53:35 VideoBox2 kernel: [ 29.944666] cx18-0: DVB Frontend registered
Aug 1 19:53:35 VideoBox2 kernel: [ 29.944673] cx18-0: Registered DVB adapter0 for TS (32 x 32.00 kB)
Aug 1 19:53:35 VideoBox2 kernel: [ 29.944762] cx18-0: Registered device video32 for encoder YUV (20 x 101.25 kB)
Aug 1 19:53:35 VideoBox2 kernel: [ 29.944905] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
Aug 1 19:53:35 VideoBox2 kernel: [ 29.944985] cx18-0: Registered device video24 for encoder PCM audio (256 x 4.00 kB)
Aug 1 19:53:35 VideoBox2 kernel: [ 29.944991] cx18-0: Initialized card: Hauppauge HVR-1600
Aug 1 19:53:35 VideoBox2 kernel: [ 29.945109] cx18: End initialization
Aug 1 19:53:35 VideoBox2 modprobe: FATAL: Error inserting cx18_alsa (/lib/modules/2.6.38-10-generic/kernel/drivers/media/video/cx18/cx18-alsa.ko): Invalid argument
Aug 1 19:53:35 VideoBox2 kernel: [ 30.071370] cx18_alsa: disagrees about version of symbol snd_pcm_new
Aug 1 19:53:35 VideoBox2 kernel: [ 30.071378] cx18_alsa: Unknown symbol snd_pcm_new (err -22)
Aug 1 19:53:35 VideoBox2 kernel: [ 30.072379] cx18_alsa: disagrees about version of symbol snd_pcm_lib_ioctl
Aug 1 19:53:35 VideoBox2 kernel: [ 30.072384] cx18_alsa: Unknown symbol snd_pcm_lib_ioctl (err -22)
Aug 1 19:53:35 VideoBox2 kernel: [ 30.072810] cx18_alsa: disagrees about version of symbol snd_pcm_set_ops
Aug 1 19:53:35 VideoBox2 kernel: [ 30.072814] cx18_alsa: Unknown symbol snd_pcm_set_ops (err -22)
Aug 1 19:53:35 VideoBox2 kernel: [ 30.073811] cx18_alsa: disagrees about version of symbol snd_pcm_hw_constraint_integer
Aug 1 19:53:35 VideoBox2 kernel: [ 30.073816] cx18_alsa: Unknown symbol snd_pcm_hw_constraint_integer (err -22)
Aug 1 19:53:35 VideoBox2 kernel: [ 30.074624] cx18_alsa: disagrees about version of symbol snd_pcm_period_elapsed
Aug 1 19:53:35 VideoBox2 kernel: [ 30.074629] cx18_alsa: Unknown symbol snd_pcm_period_elapsed (err -22)
Aug 1 19:53:35 VideoBox2 kernel: [ 30.180419] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
Aug 1 19:53:35 VideoBox2 kernel: [ 30.337778] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
Aug 1 19:53:35 VideoBox2 kernel: [ 30.344131] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
Aug 1 19:53:35 VideoBox2 kernel: [ 30.712407] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
Aug 1 19:53:36 VideoBox2 kernel: [ 30.749520] EXT4-fs (sdb1): re-mounted. Opts: commit=0
Aug 1 19:53:36 VideoBox2 kernel: [ 31.309050] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
Aug 1 19:53:36 VideoBox2 kernel: [ 31.329843] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
[code]

---

