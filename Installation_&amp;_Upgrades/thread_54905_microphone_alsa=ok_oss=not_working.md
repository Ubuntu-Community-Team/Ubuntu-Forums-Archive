---
title: "microphone alsa=ok oss=not working"
date: 2005-08-06
forum: Installation &amp; Upgrades
---

### Post by art2003 on 2005-08-06
Hello, my microphones (a usb one part of a quickcam messanger) and a standard micro plugged to the micro jack of an on-board sound card, don't work under OSS.
I go into gstream-properties and setting ALSA both output and input works (the cam micro). Setting OSS on input there is utter silence. 

 cat /proc/asound/cards
0 [SI7012         ]: ICH - SiS SI7012
                     SiS SI7012 with CMI9761 at 0xdc00, irq 18
1 [Bt878          ]: Bt87x - Brooktree Bt878
                     Brooktree Bt878 at 0xcfcff000, irq 17
2 [Audio          ]: USB-Audio - USB Audio
                     C-Media INC. USB Audio at usb-0000:00:03.1-2.1, full speed
3 [Camera         ]: USB-Audio - Camera
                     Camera at usb-0000:00:03.1-2.3, full speed

(the SiS on-board card with micro jack is number 0 and number 3 is the Quickcam messanger with built-in microphone.

 lsmod | grep snd
snd_usb_audio          65600  0
snd_usb_lib            12544  1 snd_usb_audio
snd_rawmidi            24928  1 snd_usb_lib
snd_seq_device          8524  1 snd_rawmidi
snd_bt87x              12996  0
usbcore               119224  6 quickcam,snd_usb_audio,snd_usb_lib,ehci_hcd,ohci_hcd
snd_intel8x0           32416  1
snd_ac97_codec         74208  1 snd_intel8x0
snd_pcm_oss            52516  0
snd_mixer_oss          19776  1 snd_pcm_oss
snd_pcm                94920  5 snd_usb_audio,snd_bt87x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25156  1 snd_pcm
snd                    55268  12 snd_usb_audio,snd_rawmidi,snd_seq_device,snd_bt87x,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10080  1 snd
snd_page_alloc          9796  3 snd_bt87x,snd_intel8x0,snd_pcm


 cat /etc/asound.conf
pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "duplex"

}

pcm.dmixer {
type dmix
ipc_key 1025
slave {

pcm "hw:2,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}

pcm.duplex {
     type asym
     playback.pcm "dmixer"
     capture.pcm "hw:3,0"
}

I want to run xtensoftphone which needs OSS and just can't get any micro sound through it.

---

