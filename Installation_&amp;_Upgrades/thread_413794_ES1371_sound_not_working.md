---
title: "ES1371 sound not working"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by sglow on 2007-04-19
I'm reposting this from the Feisty development list which is now closed:

----

I have recently installed Feisty Beta on a PC with an on-board Ensoniq ES1371 sound card. I'm not getting any sound at all.

The chipset is detected. lspci gives me:

00:0e.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)

The driver seems to be getting loaded properly. In lsmod I see:

...
snd_ens1371 27552 1
gameport 16520 1 snd_ens1371
snd_ac97_codec 98336 1 snd_ens1371
ac97_bus 3200 1 snd_ac97_codec
snd_pcm_oss 44544 0
snd_mixer_oss 17408 1 snd_pcm_oss
snd_pcm 79876 3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy 4740 0
snd_seq_oss 32896 0
snd_seq_midi 9600 0
snd_rawmidi 25472 2 snd_ens1371,snd_seq_midi
snd_seq_midi_event 8448 2 snd_seq_oss,snd_seq_midi
snd_seq 52592 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
snd_timer 23684 2 snd_pcm,snd_seq
snd_seq_device 9100 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
...

I see /dev/dsp. This is owned by root with group audio. Access mode is 660.

I'm in the audio group. Also tried changing mode to 666 and trying as root. Still no joy.

I've checked the alsamixer and turned every channel on and up.

Still no sound.

I've tried booting from the 6.10 install CD, and sound works there. No sound booting from the 7.04 install CD however.

Any thoughts?

Thanks,
Steve
Edit/Delete Message

---

### Post by sglow on 2007-04-19
Some more info:

The PC is a bit old, but not ancient. It's a Micron PC that I picked up maybe around 2000 or 2001. It's got an 866 MHz Pentium III processor, 256 M of ram. The sound card that I'm trying to get working is built into the motherboard. There are not other sound cards in the system.

I've looked through dmesg and logs. Nothing that looks interesting to me there.

The sound preferences tool may be interesting though:

I have a 'Default Mixer Tracks' selection at the bottom of this that I don't see on another computer running ubuntu (6.10). This gives me two mixer choices: 'Ensoniq AudioPCI (Alsa mixer)' and '0x43004e53 C?N,0x43004e53 C?N (OSS Mixer)'.

Regardless of which mixer I select, I see the same set of choices in the 'Sound playback' drop down box. The choices are:
Autodetect
ES1371 DAC1
ES1371 DAC2/ADC
ALSA
ESD
OSS

No matter which of these I select, I get the same result when I hit the test button. The testing pipeline dialog pops up, and the progress bar just sits in the first location. There is no motion on the progress bar and no sound. I can hit OK to get rid of the progress bar, but something is clearly hanging when the system tries to produce sound.

Not sure what that all means. Any suggestions welcome.

Thanks,
Steve

---

### Post by rillip on 2007-04-19
I recommend you go to the media section and check out the ultimate sound guide.  If that doesn't help, I'd post this there.

---

