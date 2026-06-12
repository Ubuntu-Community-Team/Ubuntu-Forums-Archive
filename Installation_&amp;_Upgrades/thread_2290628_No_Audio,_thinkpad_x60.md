---
title: "No Audio, thinkpad x60"
date: 2015-08-13
forum: Installation &amp; Upgrades
---

### Post by madtyper on 2015-08-13
I can not get sound to work on my Thinkpad x60 laptop. I added some lines to a couple files (below), disabled at the suggestion of forum posts the machines modem (from Bios) and finally gave up a while (though not before skimming a 3 page document on make files to (maybe, I feel like) get it working. I'm at a loss.

I've been searching now forever and the most I've been able to find is a page that says it should work out the box for my model ( [http://www.linlap.com/ibm-lenovo_thinkpad_x60](http://www.linlap.com/ibm-lenovo_thinkpad_x60) ).

Any help would be greatly appreciated. I don't know..

_The lines I added were_

options snd-hda-intel model=thinkpad  

to alsa-base.conf

and

cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask /sys/devices/platform/thinkpad_acpi/hotkey_mask

to  /etc/rc.local script.

---

### Post by tgalati4 on 2015-08-13
Open a terminal and post the output of:

```
aplay -l
```

Sound should work out of the box.  Sometimes the audio jack gets damaged and that will kill sound for both the headset and the speakers.  Try jiggling a headset connector and see if any sound comes out.

Have you owned this computer since it was new?  If not, then there is a good chance that the sound chip is burned out.

Does this machine dual-boot in Windows?  If so, does the sound work in Windows?

---

### Post by madtyper on 2015-08-14
thanks.

> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD1981 Analog [AD1981 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by tgalati4 on 2015-08-14
What is the output of:

```
lsmod | grep snd
```

It might look similar to:

> tgalati4@Mint17 ~ $ lsmod | grep snd
snd_hda_codec_realtek    61438  1 
snd_hda_intel          52355  3 
snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
snd                    69238  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
soundcore              12680  1 snd


Then:

```
alsamixer
```

Set the Master, Headphone, Speaker, PCM to 100%.  Then play something.

---

### Post by madtyper on 2015-08-15
hi. sorry, i didn't realize i skipped over part of your response from before: i jiggled the headphone jack, still no sound. i was unable to get sound working in windows either, though it was windows 7; the machine came with windows xp.

this is the printout of the last command you gave (also, i did put all the alsa volume levels to max):

> snd_hda_codec_analog    16384  1 
snd_hda_codec_generic    65536  1 snd_hda_codec_analog
snd_hda_intel          32768  3 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         122880  4 snd_hda_codec_generic,snd_hda_intel,snd_hda_controller,snd_hda_codec_analog
snd_hwdep              16384  1 snd_hda_codec
snd_pcm                94208  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            28672  1 snd_seq_midi
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28672  2 snd_pcm,snd_seq
snd                    69632  17 snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_hda_codec_analog
soundcore              16384  2 snd,snd_hda_codec


---

### Post by tgalati4 on 2015-08-15
Have you owned the machine since it was new?  Did sound ever work?  Did you ever personally hear any sounds come out of this laptop?  I still think you have a bad sound chip.  The output stage is probably burned out, but the chip is still recognized and the correct linux modules are being loaded.  The fact that Windows 7 can't play any sound is instructive.  You can probably find Lenovo drivers for Windows on their website, although Win7 comes with most drivers for older, generic hardware.  Intel HDA sound is a pretty standard architecture that has been around for several years.

---

### Post by madtyper on 2015-08-15
Thanks for your help. That stinks.. I really don't want to install XP just to test the sound. Btw, there aren't win7 drivers for this model on the Lenovo site, though you're probably right- why wouldn't there be some kind of basic driver file for the chip? 

Is there any other troubleshooting step I could take before installing XP? I need the machine and just spent all this money and time putting in a SSD and Lubuntu.

---

