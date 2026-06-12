---
title: "No sound anymore with Intel HDA"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Xenesis on 2008-10-09
I am having trouble with my sound. Everything was working perfectly until 8. October. After my regulary daily upgrade of my Intrepid Beta Installation my sound stopped working. Before, everything was allright. Now I can only here some very quiet cracking if I am trying to play anything via pulseaudio or alsa. OSS is however working!

Tested with:
gst-launch audiotestsrc ! alsasink (quiet cracks)
gst-launch audiotestsrc ! pulsesink (same)
gst-launch audiotestsrc ! osssink (WORKING)

All cards seem to be recognized by the system, pulseaudio manager pam shows the audio cards, but nothing goes through but that quiet cracking :(.

There is also some strange version number difference:
PAM says the following:
Linked to version: 0.9.10
Compiled with version: 0.9.8

Any idea whether this is the source of the problem? Or was just pam compiled with version 0.9.8, which shouldn't have a great impact.

---

### Post by psyke83 on 2008-10-09
The alsasink will remap to PulseAudio due to recent changes to the ALSA libraries, so your problem is PulseAudio.

From your post, it sounds as though the PC Speaker bug has possibly resurfaced on your machine. Open the PulseAudio Manager and check if the default sink is set to your sound card, and not the PC speaker or another device.

Also try this: Start playing audio in an application, open the PulseAudio Volume Control, then right-click on the playback entry and try moving the stream to another sink.

---

### Post by Xenesis on 2008-10-09
Thanks for your answer. However it unfortunately seems not to be useful for me.
I have only one sink in the Pulse Audio Manager and thats called alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0. Description says it is "ALSA PCM on front:0 (STAC92xx Analog) via DMA".
I think the right device is selected as I can hear some very quiet cracks if I play some audio. Also, the pulse audio manager's volume meter shows that the sound should be played on the device. However it seems the sound data is not reaching the sound card.

More informations about my sound system are at [http://www.alsa-project.org/db/?f=699210b3ddaeeceb9b8360bf71355d1abc87fcdf](http://www.alsa-project.org/db/?f=699210b3ddaeeceb9b8360bf71355d1abc87fcdf) created by alsa-info.sh.

Any help is very welcomed!

---

### Post by Xenesis on 2008-10-10
Hm, I found something interesting when I looked at pulseaudios logs:

```

D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0 "alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 1792 bytes.
[...skipping log...]

I: module-volume-restore.c: Restoring volume for <pulsecore/protocol-native.c$ALSA plug-in [gst-launch-0.10]>
I: module-alsa-sink.c: Trying resume...
I: module-alsa-sink.c: Resumed successfully...
I: module-alsa-sink.c: Starting playback.
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0 becomes busy.
I: resampler.c: Forcing resampler 'copy', because of fixed, identical sample rates.
D: resampler.c: Channel matrix:
D: resampler.c:        I00 
D: resampler.c:     +------
D: resampler.c: O00 | 1,000
D: resampler.c: O01 | 1,000
I: resampler.c: Using resampler 'copy'
I: resampler.c: Using float32le as working format.
I: sink-input.c: Created input 0 "ALSA Playback" on alsa_output.pci_8086_284b_sound_card_0_alsa_playback_0 with sample spec s32le 1ch 44100Hz and channel map mono

```

Most interesting is the last line, as it says that the sample spec for the ALSA output is s32le, however the devices is loaded with a sample spec for s16le. So is pulseaudio using the wrong format???

EDIT: Format seems not to matter, it fails even if I force s16le format. :(

---

### Post by wireless on 2008-10-11
Hi,
Im having same symptoms with intel HDA sound card. anyone have any idea about it?

---

### Post by tom17 on 2008-10-11
I too am having the same symptoms now.

It was working last night and then this morning I was trying to get sound working in VMWare Server 2. Everything was working at one point, albeit very quietly.

Came back to my PC after watching the F1 qualifying (GO LEWIS!) and now I have the same symptoms, to the word, as the original poster.

I did an upgrade *after* the symptoms started but this did not help.

Tom...

---

### Post by bpl07 on 2008-10-11
For a week or so now the login sound has started working for me but no sound will work after that until I kill and restart pulseaudio:

> killall pulseaudio ; sleep 2 ; pulseaudio --log-target=syslog &

If that works for you like it does for me, you can just remember to do that each time you startup and wait for the official fix.  Contribute to the bug report if you can.  The problem might have something to do with libcanberra using alsa while pulseaudio is trying to connect at login, but really I'm not sure, psyke83 can probably give more insight on that.  Check the pulseaudio thread for more details on current issues and how to contribute.

---

### Post by Jim March on 2008-10-11
This is "sorta good news" in that somebody is obviously paying attention to this ALSA driver, which is failing in weird ways for some of us.  Seems like they haven't got it sorted out yet, but hey, they're paying attention.

Meanwhile there's a "cure" available: yank ALSA completely and swap in OSS4 as documented at:

[http://ubuntuforums.org/showthread.php?t=913328](http://ubuntuforums.org/showthread.php?t=913328)

Read the whole thread...it works, it even has some cool aspects, but let's be honest it's not pretty...

---

### Post by tom17 on 2008-10-11
Umm, guys who are having this problem. Go run 

```
alsamixer -Dhw
```

(from the thread linked above) and double check that your PCM volume is not inexplicably set to 0 lol.

Mine was on 0. Doesn't explain why I hear the feint crackles, but it did fix my "problem"

I wonder what set the volume to 0...

Tom...

---

### Post by syko21 on 2008-10-12
Some others have had this problem because the module was unloaded. Try adding this

snd_hda_intel

line to your /etc/modules file.

EDIT: FIRST check if the module is already loaded by doing
```
lsmod | grep snd_hda_intel
```
if it returns anything at all then this IS NOT your problem

---

### Post by peddy on 2008-10-16
> **tom17 said:**
> Umm, guys who are having this problem. Go run 

```
alsamixer -Dhw
```

(from the thread linked above) and double check that your PCM volume is not inexplicably set to 0 lol.

Mine was on 0. Doesn't explain why I hear the feint crackles, but it did fix my "problem"

I wonder what set the volume to 0...

Tom...


cheers, that fixed it :)

---

### Post by milliman on 2008-10-17
It seems that the snd_hda_intel module is not loaded in the kernel.  When I tried to load it, this is what I received:
```
$ sudo modprobe snd_hda_intel
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.27-7-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```
dmesg gives this response:
```

[   20.511901] snd_ac97_codec: disagrees about version of symbol snd_pcm_hw_rule_add
[   20.511909] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
[   20.512291] snd_ac97_codec: disagrees about version of symbol ac97_bus_type
[   20.512294] snd_ac97_codec: Unknown symbol ac97_bus_type
[   20.549589] snd_intel8x0: Unknown symbol snd_ac97_pcm_close
[   20.549824] snd_intel8x0: Unknown symbol snd_ac97_resume
[   20.549908] snd_intel8x0: disagrees about version of symbol snd_pcm_new
[   20.549911] snd_intel8x0: Unknown symbol snd_pcm_new
[   20.550030] snd_intel8x0: disagrees about version of symbol snd_pcm_limit_hw_rates
[   20.550032] snd_intel8x0: Unknown symbol snd_pcm_limit_hw_rates
[   20.550333] snd_intel8x0: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   20.550336] snd_intel8x0: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   20.550590] snd_intel8x0: Unknown symbol snd_ac97_pcm_open
[   20.550849] snd_intel8x0: Unknown symbol snd_ac97_set_rate
[   20.550966] snd_intel8x0: Unknown symbol snd_ac97_update_bits
[   20.551091] snd_intel8x0: Unknown symbol snd_ac97_mixer
[   20.551257] snd_intel8x0: Unknown symbol snd_ac97_bus
[   20.551594] snd_intel8x0: Unknown symbol snd_ac97_pcm_double_rate_rules
[   20.551735] snd_intel8x0: Unknown symbol snd_ac97_update_power
[   20.551948] snd_intel8x0: Unknown symbol snd_ac97_suspend
[   20.552197] snd_intel8x0: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   20.552201] snd_intel8x0: Unknown symbol snd_pcm_lib_malloc_pages
[   20.552281] snd_intel8x0: disagrees about version of symbol snd_pcm_lib_ioctl
[   20.552283] snd_intel8x0: Unknown symbol snd_pcm_lib_ioctl
[   20.552375] snd_intel8x0: disagrees about version of symbol snd_pcm_lib_free_pages
[   20.552378] snd_intel8x0: Unknown symbol snd_pcm_lib_free_pages
[   20.552500] snd_intel8x0: disagrees about version of symbol snd_pcm_set_ops
[   20.552502] snd_intel8x0: Unknown symbol snd_pcm_set_ops
[   20.552602] snd_intel8x0: disagrees about version of symbol snd_pcm_hw_constraint_list
[   20.552604] snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_list
[   20.552946] snd_intel8x0: Unknown symbol snd_ac97_get_short_name
[   20.553026] snd_intel8x0: disagrees about version of symbol snd_pcm_suspend_all
[   20.553028] snd_intel8x0: Unknown symbol snd_pcm_suspend_all
[   20.553238] snd_intel8x0: Unknown symbol snd_ac97_pcm_assign
[   20.553320] snd_intel8x0: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   20.553322] snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_integer
[   20.553646] snd_intel8x0: disagrees about version of symbol snd_pcm_hw_constraint_msbits
[   20.553648] snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_msbits
[   20.553820] snd_intel8x0: disagrees about version of symbol snd_pcm_period_elapsed
[   20.553823] snd_intel8x0: Unknown symbol snd_pcm_period_elapsed
[   20.553938] snd_intel8x0: Unknown symbol snd_ac97_tune_hardware

```
Apparently there is a driver problem now and the module needs to be rebuilt.  I noticed that the kernel headers were updated before sound disappeared.

---

### Post by karlstad on 2008-10-22
> **milliman said:**
> It seems that the snd_hda_intel module is not loaded in the kernel.  When I tried to load it, this is what I received:
```
$ sudo modprobe snd_hda_intel
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.27-7-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```
dmesg gives this response:
```

[   20.511901] snd_ac97_codec: disagrees about version of symbol snd_pcm_hw_rule_add
[   20.511909] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
[   20.512291] snd_ac97_codec: disagrees about version of symbol ac97_bus_type
[   20.512294] snd_ac97_codec: Unknown symbol ac97_bus_type
[   20.549589] snd_intel8x0: Unknown symbol snd_ac97_pcm_close
[   20.549824] snd_intel8x0: Unknown symbol snd_ac97_resume
[   20.549908] snd_intel8x0: disagrees about version of symbol snd_pcm_new
[   20.549911] snd_intel8x0: Unknown symbol snd_pcm_new
[   20.550030] snd_intel8x0: disagrees about version of symbol snd_pcm_limit_hw_rates
[   20.550032] snd_intel8x0: Unknown symbol snd_pcm_limit_hw_rates
[   20.550333] snd_intel8x0: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   20.550336] snd_intel8x0: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   20.550590] snd_intel8x0: Unknown symbol snd_ac97_pcm_open
[   20.550849] snd_intel8x0: Unknown symbol snd_ac97_set_rate
[   20.550966] snd_intel8x0: Unknown symbol snd_ac97_update_bits
[   20.551091] snd_intel8x0: Unknown symbol snd_ac97_mixer
[   20.551257] snd_intel8x0: Unknown symbol snd_ac97_bus
[   20.551594] snd_intel8x0: Unknown symbol snd_ac97_pcm_double_rate_rules
[   20.551735] snd_intel8x0: Unknown symbol snd_ac97_update_power
[   20.551948] snd_intel8x0: Unknown symbol snd_ac97_suspend
[   20.552197] snd_intel8x0: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   20.552201] snd_intel8x0: Unknown symbol snd_pcm_lib_malloc_pages
[   20.552281] snd_intel8x0: disagrees about version of symbol snd_pcm_lib_ioctl
[   20.552283] snd_intel8x0: Unknown symbol snd_pcm_lib_ioctl
[   20.552375] snd_intel8x0: disagrees about version of symbol snd_pcm_lib_free_pages
[   20.552378] snd_intel8x0: Unknown symbol snd_pcm_lib_free_pages
[   20.552500] snd_intel8x0: disagrees about version of symbol snd_pcm_set_ops
[   20.552502] snd_intel8x0: Unknown symbol snd_pcm_set_ops
[   20.552602] snd_intel8x0: disagrees about version of symbol snd_pcm_hw_constraint_list
[   20.552604] snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_list
[   20.552946] snd_intel8x0: Unknown symbol snd_ac97_get_short_name
[   20.553026] snd_intel8x0: disagrees about version of symbol snd_pcm_suspend_all
[   20.553028] snd_intel8x0: Unknown symbol snd_pcm_suspend_all
[   20.553238] snd_intel8x0: Unknown symbol snd_ac97_pcm_assign
[   20.553320] snd_intel8x0: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   20.553322] snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_integer
[   20.553646] snd_intel8x0: disagrees about version of symbol snd_pcm_hw_constraint_msbits
[   20.553648] snd_intel8x0: Unknown symbol snd_pcm_hw_constraint_msbits
[   20.553820] snd_intel8x0: disagrees about version of symbol snd_pcm_period_elapsed
[   20.553823] snd_intel8x0: Unknown symbol snd_pcm_period_elapsed
[   20.553938] snd_intel8x0: Unknown symbol snd_ac97_tune_hardware

```
Apparently there is a driver problem now and the module needs to be rebuilt.  I noticed that the kernel headers were updated before sound disappeared.

Mhm! I got the exact same problem today after I installed the new kernel an booted my laptop. Any solutions?

---

### Post by zoomy942 on 2008-10-23
gah!  mine did this too.
this is the second time it has happened!@

---

### Post by marttali on 2008-10-23
easy solution is to install OSS.

---

### Post by zoomy942 on 2008-10-23
> **marttali said:**
> easy solution is to install OSS.



and how do i do this?

---

### Post by karlstad on 2008-10-23
Oh snap! I found out that I've downloaded and installed the latest ALSA development drivers. re-compiling these fixed my problems :D

For those of you who still doesn't get any sound, take a look at "Troubleshooting" here: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by Jove on 2008-10-23
Solution above which was simply to run "alsamixer -Dhw" in a terminal window and turn up the PCM volume fixed my mate Darren's sound issue... cheers!

---

### Post by jbg7474 on 2008-10-24
alsamixer -Dhw showed that my PCM volume was also at 0.  Not sure how that happened, but turning it up fixed the problem.

---

### Post by Moonlit Knight on 2008-10-24
Hi I have a hda intel soundard, and this is weird. Compiz is activated by default on my computer, and when I turn it off (metacity --replace). All sound applications crash, totem, banshee... 

I restarted alsa doing sudo /sbin/alsa force-reload and nothing

I activate again Compiz (compiz --replace) and sound starts again. 

My video card is an ati xpress 200, and I'm using the open source drivers. 

Thanks in advance

---

### Post by natros on 2008-10-25
I have no sound after suspend.

---

### Post by milliman on 2008-10-25
Some of you may want to look at other devices that may have replaced the standard ALSA package.  In my case and possibly Dell users, I had installed the Linuxant modem drivers for my Conexant based modem.  The Linuxant drivers package contains its own version of ALSA modified to work with Conexant modem chips.  Every time the kernel updates, it will break ALSA. If you try to manually add the snd-intel8x0 or snd-hda-intel modules, they will fail because of the Linuxant package.  

The solution is to go to the [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/) page and download the package:  [alsa-driver-linuxant_1.0.18git20081020-1_all.deb]("http://www.linuxant.com/alsa-driver/alsa-driver-linuxant_1.0.18git20081020-1_all.deb").  Use the deb installer to install the package and rebuild your kernel.  You can now manually load the driver using "modprobe" and test your sound.  

You will need to repeat this procedure every time your kernel changes, not just minor updates.  No need to blame ALSA or PulseAudio if this is your situation.  If you replace ALSA with OSS you will end up breaking your modem configuration.

---

### Post by jbg7474 on 2008-10-25
I discovered today (after fixing the PCM level issue yesterday) that my volume buttons on my D620 were controlling the PCM level, not the master level.  I suspect that the original reason why my PCM level was at 0 is because it has switched back and forth before unbeknownst to me, and I muted it when it was controlling the PCM level.

I have no idea how to map the buttons back to the master level control, but I'm thinking this will involve the new HAL method for configuring things, which I have yet to master.  Arrrgh.

---

### Post by psyke83 on 2008-10-25
> **jbg7474 said:**
> I discovered today (after fixing the PCM level issue yesterday) that my volume buttons on my D620 were controlling the PCM level, not the master level.  I suspect that the original reason why my PCM level was at 0 is because it has switched back and forth before unbeknownst to me, and I muted it when it was controlling the PCM level.

I have no idea how to map the buttons back to the master level control, but I'm thinking this will involve the new HAL method for configuring things, which I have yet to master.  Arrrgh.

It's probably much simpler than that. In System/Preferences/Sound, there is an option to choose the default mixer, which influences laptop hotkeys.

---

### Post by jbg7474 on 2008-10-25
Thanks, psyke.  I discovered that my Sound preferences had PCM selected as the track to control from the keyboard.  Changing it back to master fixed the problem.  Now did I do that by mistake or did something do it for me?  Hmmmm...

---

