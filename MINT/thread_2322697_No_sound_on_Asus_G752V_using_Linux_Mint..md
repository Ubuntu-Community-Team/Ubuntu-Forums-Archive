---
title: "No sound on Asus G752V using Linux Mint."
date: 2016-04-29
forum: MINT
---

### Post by jaco_van_niekerk2 on 2016-04-29
Hi there

I hope someone can help me.  I can get no sound output from my new laptop.  It's a dual boot machine and the sounds works find under Windows 10.  I have tried reinstalling alsa-base and pulseaudio and tinkering with the /etc/modprobe.d/alsa-base.conf file.  Alsamixer only shows 3 S/PDIF outputs and F6 only shows "HDA NVidia".  Some output inclues:

**$ cat /proc/asound/cards**
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xdc080000 irq 17

**$ aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**$ lsmod | grep snd**
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_hda_codec_hdmi     53248  1 
snd_hda_intel          36864  3 snd_hda_codec_hdmi
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         143360  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_controller
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_timer              32768  2 snd_pcm,snd_seq
snd                    86016  13 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  2 snd,snd_hda_codec

**$ lspci | grep Audio**
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
01:00.1 Audio device: NVIDIA Corporation GM204 High Definition Audio Controller (rev a1)

Any help will be much appreciated.  
Thank you kindly.

---

### Post by QIII on 2016-04-29
*Moved to **MINT***

---

### Post by jaco_van_niekerk2 on 2016-04-30
UPDATE:  System logs shows this message:

 snd_hda_intel 0000:00:1f.3: failed to add i915_bpo component master (-19)

I am investigating further... any help?

---

### Post by jaco_van_niekerk2 on 2016-05-02
I got it working following the instructions here:

[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

However, no matter what I do, I cannot get any sound from my headphones? Does anyone one where I can tinker?  Under sound properties I now get:
1.  Digitial Output (S/PDIF)
2.  Speakers
3. Analog Output

Option 1 does nothing, while 2 and 3 does about the same thing, which is to play through the internal speakers.  If I plug in the headphones, absolutely nothing happens.

PLEASE, Anybody.... I don't know what to do now.

---

