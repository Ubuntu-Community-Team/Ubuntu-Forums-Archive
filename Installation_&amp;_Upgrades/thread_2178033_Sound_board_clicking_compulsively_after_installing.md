---
title: "Sound board clicking compulsively after installing Ubuntu 12.04"
date: 2013-10-01
forum: Installation &amp; Upgrades
---

### Post by lads on 2013-10-01
Hello everyone,

I have just installed Ubuntu 12.04 on a Packard Bell EasyNote MV85-100 that was previously running WinXP. Pretty swift and no errors during install, but as soon as Ubuntu loads the sound board goes bonkers and starts issuing a compulsive clicking sound (not that different from an old Spectrum cassette loading); this is on max volume, after 5 minutes my head was cracking. I have tried to mute the sound, connect headphones and microphone, but nothing shuts the clicking off. In the Sound Settings menu there are two devices listed: the board and the headphones, with the later blinking to the rhythm of the clicking.

Any hints on how to tame this soundboard are welcome. Even just muting the sound would be an improvement. Thanks.

---

### Post by lads on 2013-10-03
Hello again. I went to ordeal of turning this laptop on again and tried a few more things. I ran the updates and got about 100 packages anew; I requested a search for proprietary drivers and got a driver for the DVD. I restarted it but the compulsive beeping remains.

Any help appreciated

---

### Post by michiel-reenaers on 2013-10-03
Ok this is what I would suggest: 
Find out what kernel module or a list of the soundcards playing on your system. 
aplay -l should give you the soundcards
lsmod | less should give you a list of kernel modules.

if you work with the kernel module
you can blacklist the specific module
f.e lsmod | less
output: 
snd_ens1370      21536   0
gameport         16776   1 snd_ens1370
snd_ak4531_codec 9856    1 snd_ens1370
snd_pcm          80388   5 snd_ens1370,snd_intel8x0,snd_ac97_codec

now blacklist the module

in /etc/modprobe.d/blacklist
add

# disable my sound card
blacklist snd_ens1370
 
Now i haven't tried this out myself, 
as I never had any sound problems and I'm currently in school and i'm forced to use windows. 
So let me know if it worked.

---

### Post by lads on 2013-10-03
Hi Michiel thank you for the reply.

Here's the output of the commands you suggested:

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC260 Digital [ALC260 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ lsmod | grep snd
snd_hda_codec_realtek    65004  1 
snd_hda_intel          38819  3 
snd_hda_codec         118613  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                85934  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    57014  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm

```

Blacklisting *snd_hda_intel* indeed deactivates the soundboard and the beep goes away. This is a relevant progress but I wont mark this thread as solved; a laptop without sound is quite limited.

To the admins: you might want to move this thread to the hardware section.

---

### Post by lads on 2013-10-05
Hello again,

Today I tried booting with Debian (7.0.0) and things went smoothly, no beeping or clicking. Wheezy is distributed with kernel version 3.2, whereas Ubuntu 12.04.3 uses kernel 3.8. So either I find a way to install 12.04 with the 3.2 kernel or I'll just go with Debian and then install Unity (if that's possible already).

I'll report further developments here.

---

### Post by lads on 2013-10-07
After installing the package with kernel 3.2 and successfully setting it as the default boot option with GRUB the clicking is gone.

---

### Post by Keith_Beef on 2013-10-22
I also get this odd clicking noise as the computer switches spontaneously between the on-board speakers and the headphone jack. I posted about it [in another thread]("http://ubuntuforums.org/showthread.php?t=2182556&highlight=clicking+sound") but have had no replies yet.
```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ lsmod | grep snd
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32719  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
```

As I mentioned in my other post, this is the first time I've encountered this problem on any hardware, and this little Vaio has been running Ubuntu for years&#8230; it's really strange that it should appear now after the upgrade to 12.04.

---

### Post by lads on 2013-10-22
Hi Keith. This is definitely something weird with the release 3.8 of the kernel. Installing back kernel 3.2 should also solve the issue for you. Good luck.

---

