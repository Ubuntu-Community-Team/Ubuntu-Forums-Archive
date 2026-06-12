---
title: "Gutsy killed my kdetv sound ?"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by ppera on 2007-10-23
After upgrading to gutsy from feisty, the sound in kdetv went away... The thing is that from other apps (like mplayer) I _do_ get sound from the tv card, it's just kdetv that is mute (red X on the speaker no matter what). To get even more puzzling, the version of kdetv in feisty and gutsy seems to be the same, so there should be no difference... except I have no TV sound now :( Any ideas ?

Leadtek Winfast 2000 XP Pro (the conexant version) here

PS. I have checked the mixer of course, everything seems to be OK, kdetv even crackles when starting (muting the line in shows this actually comes from the card, as there is no crackle is line in is muted).

---

### Post by azbarcea on 2007-10-29
I have the same issue! some backtrace:

Creating vbi proxy client, rev.
$Id: proxy-client.c,v 1.12 2006/05/31 03:54:28 mschimek Exp $
proxy_msg: connect: error 2, No such file or directory
kdetv: WARNING: VBIDecoder: vbi_capture_proxy_new error: Connection via socket failed, server not running.
Try to open V4L2 0.20 VBI device, libzvbi interface rev.
  $Id: io-v4l2.c,v 1.33 2006/05/22 09:00:47 mschimek Exp $
Opened /dev/vbi0
libzvbi:capture_v4l2k_new: Try to open V4L2 2.6 VBI device, libzvbi interface rev.
  $Id: io-v4l2k.c,v 1.42 2006/09/24 03:10:04 mschimek Exp $.
libzvbi:capture_v4l2k_new: Opened /dev/vbi0.
libzvbi:capture_v4l2k_new: /dev/vbi0 (AverTV Studio 303 (M126)) is a v4l2 vbi device,
driver cx8800, version 0x00000006.
libzvbi:capture_v4l2k_new: Using streaming interface.
libzvbi:v4l2_get_videostd: Current scanning system is 525.
libzvbi:v4l2_update_services: Querying current vbi parameters...
libzvbi:v4l2_update_services: ...success.
libzvbi:print_vfmt: VBI capture parameters supported: format 59455247 [GREY], 35468950 Hz, 2048 bpl, offs 244, F1 6...22, F2 318...334, flags 00000000.
libzvbi:print_vfmt: VBI capture parameters granted: format 59455247 [GREY], 35468950 Hz, 2048 bpl, offs 244, F1 6...22, F2 318...334, flags 00000000.
libzvbi:vbi3_raw_decoder_add_services: No services to add.
libzvbi:v4l2_update_services: Nyquist check passed.
libzvbi:v4l2_update_services: Request decoding of services 0x60000c7f, strict level -1.
libzvbi:_vbi_sampling_par_permit_service: Service 0x00000001 (Teletext System B 625 Level 1.5) requires videostd_set 0x1, have 0x2.
libzvbi:_vbi_sampling_par_permit_service: Service 0x00000003 (Teletext System B, 625) requires videostd_set 0x1, have 0x2.
libzvbi:_vbi_sampling_par_permit_service: Service 0x00000001 (Teletext System B 625 Level 1.5) requires videostd_set 0x1, have 0x2.
libzvbi:_vbi_sampling_par_permit_service: Service 0x00000003 (Teletext System B, 625) requires videostd_set 0x1, have 0x2.
libzvbi:_vbi_sampling_par_permit_service: Service 0x00000004 (Video Program System) requires videostd_set 0x1, have 0x2.
libzvbi:_vbi_sampling_par_permit_service: Service 0x00000400 (Wide Screen Signalling 625) requires videostd_set 0x1, have 0x2.
libzvbi:_vbi_sampling_par_permit_service: Service 0x00000008 (Closed Caption 625, field 1) requires videostd_set 0x1, have 0x2.
libzvbi:_vbi_sampling_par_permit_service: Service 0x00000010 (Closed Caption 625, field 2) requires videostd_set 0x1, have 0x2.
libzvbi:v4l2_update_services: Will capture services 0x00000060, added 0x60 commit=1.
libzvbi:v4l2_stream_alloc: Requesting 16 streaming i/o buffers.
libzvbi:v4l2_stream_alloc: Mapping 16 streaming i/o buffers.
libzvbi:capture_v4l2k_new: Successfully opened /dev/vbi0 (AverTV Studio 303 (M126)).
libzvbi:v4l2_stream: Failed to enable streaming, errno 22.
kdetv: WARNING: VbiDecoder: VBI capture error: Invalid argument
kdetv: WARNING: MainWindow::setupInfraRed(): Lirc not available
kdetv: WARNING: VolumeController::doSetVolume: SourceManager failed, trying AudioManager
kdetv: WARNING: VolumeController::doSetVolume: SourceManager failed, trying AudioManager
kdetv: WARNING: V4L2Dev::enqueueBuffer(): buffer already queued: 0
V4L2Grabber::~V4L2Grabber(): wait().
V4L2Grabber::~V4L2Grabber(): deleted.
kdetv: WARNING: VolumeController::doSetVolume: SourceManager failed, trying AudioManager

---

### Post by azbarcea on 2007-11-03
**Problem solved**:

1. I checked whether my tunner tv card outputs sound, and I was surprised to figure out that it doesn't.

2. I uninstalled kdetv 
```

sudo apt-get remove kdetv
sudo apt-get autoremove

```

3. I installed tvtime
```

sudo apt-get install -y tvtime

```

4. check the driver message
```

dmesg | grep cx88

```

and the output whas:
> 
[   40.693427] CORE cx88[0]: subsystem: 1461:000b, board: AverTV Studio 303 (M126) [card=6,autodetected]
[   40.841941] input: cx88 IR (AverTV Studio 303 (M12 as /class/input/input2
[   40.841978] cx88[0]/0: found at 0000:05:06.0, rev: 5, irq: 16, latency: 32, mmio: 0xd3000000
[   40.962958] tuner 2-0043: chip found @ 0x86 (cx88[0])
[   41.090092] tuner 2-0060: chip found @ 0xc0 (cx88[0])
[   41.487883] cx88[0]/0: registered device video1 [v4l2]
[   41.487930] cx88[0]/0: registered device vbi0
[   41.487958] cx88[0]/0: registered device radio0


that means that the video output is device video1. 

5. configure tvtime
```

tvtime-configure -d /dev/video1
tvtime-scanner

```

it is a good way to go "tvtime-configure -h" and see what other things u could configure
 
6. Launche tvtime and configure channels and so on, editing the 
```

kate ~/.tvtime/.stations.xml
tvtime

```

---

### Post by freedom on 2007-12-07
I was hoping that someone have the solution to this KDETV issue... :(
TVTIME works well but kdetv are mute... :confused:

---

