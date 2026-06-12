---
title: "fresh 10.10 install; right speaker = fail"
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by morissette on 2011-03-15
I have already updated to the dev alsa modules, so yeah not sure what else you need, so i'll give you a bit of info:

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)

speakers are cheap logitech usb come w/ wireless keyboard & mouse

root@freedom:~# lsusb 
Bus 002 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 002: ID 1130:1620 Tenx Technology, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 059f:0642 LaCie, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and theres a model number for ya :D

dmesg has:

root@freedom:~# dmesg | grep -i alsa
[   13.393994] ALSA hda_intel.c:2565: chipset global capabilities = 0x4401
[   13.428017] ALSA hda_intel.c:914: codec_mask = 0x1
[   13.432350] ALSA hda_intel.c:1357: codec #0 probed OK
[   13.813963] ALSA endpoint.c:448: 2:1:1: add audio endpoint 0x1
[   13.819971] ALSA mixer.c:1186: [2] FU [PCM Playback Switch] ch = 1, val = 0/1/1
[   13.819977] ALSA mixer.c:813: 2:0: cannot get min/max values for control 2 (id 2)
[   13.820078] ALSA mixer.c:1186: [2] FU [PCM Playback Volume] ch = 2, val = 0/1/1
[   14.072026] ALSA patch_realtek.c:1456: SKU: Nid=0x1d sku_cfg=0x4004c601
[   14.072029] ALSA patch_realtek.c:1458: SKU: port_connectivity=0x1
[   14.072032] ALSA patch_realtek.c:1459: SKU: enable_pcbeep=0x0
[   14.072034] ALSA patch_realtek.c:1460: SKU: check_sum=0x00000004
[   14.072037] ALSA patch_realtek.c:1461: SKU: customization=0x000000c6
[   14.072039] ALSA patch_realtek.c:1462: SKU: external_amp=0x0
[   14.072042] ALSA patch_realtek.c:1463: SKU: platform_type=0x0
[   14.072044] ALSA patch_realtek.c:1464: SKU: swap=0x0
[   14.072046] ALSA patch_realtek.c:1465: SKU: override=0x1
[   14.072050] ALSA hda_codec.c:4634: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0)
[   14.072054] ALSA hda_codec.c:4638:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   14.072057] ALSA hda_codec.c:4642:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   14.072060] ALSA hda_codec.c:4643:    mono: mono_out=0x0
[   14.072062] ALSA hda_codec.c:4646:    dig-out=0x1e/0x0
[   14.072064] ALSA hda_codec.c:4647:    inputs:
[   14.072067] ALSA hda_codec.c:4651:  Rear Mic=0x18
[   14.072069] ALSA hda_codec.c:4651:  Front Mic=0x19
[   14.072072] ALSA hda_codec.c:4651:  Line=0x1a
[   14.072074] ALSA hda_codec.c:4653: 
[   14.308020] ALSA patch_realtek.c:1513: realtek: No valid SSID, checking pincfg 0x4004c601 for NID 0x1d
[   14.308024] ALSA patch_realtek.c:1529: realtek: Enabling init ASM_ID=0xc601 CODEC_ID=10ec0887
[   14.608026] ALSA hda_codec.c:2165: Cannot find slave Front Playback Volume, skipped
[   14.608030] ALSA hda_codec.c:2165: Cannot find slave Surround Playback Volume, skipped
[   14.608034] ALSA hda_codec.c:2165: Cannot find slave Center Playback Volume, skipped
[   14.608037] ALSA hda_codec.c:2165: Cannot find slave LFE Playback Volume, skipped
[   14.608040] ALSA hda_codec.c:2165: Cannot find slave Side Playback Volume, skipped
[   14.608043] ALSA hda_codec.c:2165: Cannot find slave Headphone Playback Volume, skipped
[   14.608045] ALSA hda_codec.c:2165: Cannot find slave Speaker Playback Volume, skipped
[   14.608048] ALSA hda_codec.c:2165: Cannot find slave Mono Playback Volume, skipped
[   14.608051] ALSA hda_codec.c:2165: Cannot find slave Line-Out Playback Volume, skipped
[   14.608059] ALSA hda_codec.c:2165: Cannot find slave Front Playback Switch, skipped
[   14.608062] ALSA hda_codec.c:2165: Cannot find slave Surround Playback Switch, skipped
[   14.608064] ALSA hda_codec.c:2165: Cannot find slave Center Playback Switch, skipped
[   14.608067] ALSA hda_codec.c:2165: Cannot find slave LFE Playback Switch, skipped
[   14.608070] ALSA hda_codec.c:2165: Cannot find slave Side Playback Switch, skipped
[   14.608074] ALSA hda_codec.c:2165: Cannot find slave Speaker Playback Switch, skipped
[   14.608077] ALSA hda_codec.c:2165: Cannot find slave Mono Playback Switch, skipped
[   14.608081] ALSA hda_codec.c:2165: Cannot find slave Line-Out Playback Switch, skipped
[   34.577860] ALSA pcm.c:227: setting usb interface 1:1
[   34.618867] ALSA pcm.c:227: setting usb interface 1:1
[   34.639869] ALSA pcm.c:227: setting usb interface 1:1
[   34.663258] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.663402] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.663610] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.663925] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.664074] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.664204] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.664395] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.664709] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.664841] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.664972] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.665161] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.665472] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.665604] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.665731] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.665919] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.666227] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.666359] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.666486] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.666677] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.666984] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.667366] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   34.667377] ALSA hda_codec.c:1228: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[   34.688022] ALSA hda_codec.c:1228: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   34.712084] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   34.712096] ALSA hda_codec.c:1228: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x4011
[   34.712101] ALSA hda_codec.c:1228: hda_codec_setup_stream: NID=0x2, stream=0x5, channel=0, format=0x4011
[   34.712399] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x8
[   34.712543] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x8
[   34.712749] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x8
[   34.713060] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x8
[   34.713391] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   34.713398] ALSA hda_codec.c:1228: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   34.736064] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   34.736073] ALSA hda_codec.c:1228: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   34.736095] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x8
[   34.736121] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x8
[   34.736829] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.736832] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x6
[   34.736848] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.737141] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.737398] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.737726] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.738164] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.738425] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.738677] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.738991] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x2
[   34.769126] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   34.769136] ALSA hda_codec.c:1228: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
[   34.776089] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   34.776100] ALSA hda_codec.c:1228: hda_codec_setup_stream: NID=0x6, stream=0x8, channel=0, format=0x4011
[   34.776414] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x8
[   34.776557] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x8
[   34.776764] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x8
[   34.777077] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x8
[   34.777414] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   34.777422] ALSA hda_codec.c:1228: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   34.777435] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   34.777441] ALSA hda_codec.c:1228: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   34.777451] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x8
[   34.777460] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x8
[   34.778014] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x6
[   34.778045] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x6
[   34.789221] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   34.789228] ALSA hda_codec.c:1228: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   34.789241] ALSA hda_intel.c:1682: azx_pcm_prepare: bufsize=0x3700, format=0x4011
[   34.789247] ALSA hda_codec.c:1228: hda_codec_setup_stream: NID=0x8, stream=0x1, channel=0, format=0x4011
[   34.789255] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x8
[   34.789266] ALSA hda_codec.c:1291: hda_codec_cleanup_stream: NID=0x8
[15111.172765] ALSA pcm.c:227: setting usb interface 1:1
[15125.774092] ALSA pcm.c:227: setting usb interface 1:1
[15132.717717] ALSA pcm.c:227: setting usb interface 1:1
[15141.648527] ALSA pcm.c:227: setting usb interface 1:1
[15150.717390] ALSA pcm.c:227: setting usb interface 1:1
[15174.218469] ALSA pcm.c:227: setting usb interface 1:1
[15185.452475] ALSA pcm.c:227: setting usb interface 1:1

---

