---
title: "no sound"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by shamimkhaliq on 2009-03-31
when i first installed ubuntu 8.04 long term support i had sound. then i updated and lost sound. now i've upgraded to ubuntu 9.04 jaunty jackalope beta and still don't have sound. i've been searching posts and reading stickies and faqs for a week, following suggestions to no avail. this post is my last ditch effort before formatting and reinstalling the old long-term support version hoping sound comes back. if that doesn't work, i'll try another linux version (i was thinking MEPIS because someone told me it was stable, i hope meaning alsa-competent, but not newbie-friendly so i hope i don't have to try it).

anyway, here's various outputs that might indicate where the problem is: lspci, lsmod, lspci -v, dmesg, aplay -l, lspnp -v, esd,  killall esd, lsof /dev/snd/*, lsof /dev/dsp

i have permissions for the sound card. i checked using System->Administration->Users and Groups


i've opened volume control>preferences>ticked all the boxes>closed box>Volume Control Playback tab>Made sure none of the playback tracks is muted>"Switches" tab>Unticked "External Amplifier"


shamim@shamim-desktop:~$ lspci
02:0d.0 Multimedia audio controller: Ensoniq 5880B [AudioPCI] (rev 02)


shamim@shamim-desktop:~$ lsmod
Module                  Size  Used by
video                  25360  0 
output                 11008  1 video
snd_ens1371            30496  3 
gameport               19340  1 snd_ens1371
snd_ac97_codec        112292  1 snd_ens1371
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  2 snd_ens1371,snd_seq_midi
psmouse                61972  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
pcspkr                 10496  0 
serio_raw              13316  0 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  16 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  1 snd_pcm


shamim@shamim-desktop:~$ lspci -v

02:0d.0 Multimedia audio controller: Ensoniq 5880B [AudioPCI] (rev 02)
	Subsystem: Ensoniq Device 2000
	Flags: bus master, slow devsel, latency 32, IRQ 21
	I/O ports at de80 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: ENS1371
	Kernel modules: snd-ens1371


dmsg

[    2.381393] Driver 'sd' needs updating - please use bus_type methods
[    2.381413] Driver 'sr' needs updating - please use bus_type methods

[   12.711142] intel_rng: Firmware space is locked read-only. If you can't or
[   12.711146] intel_rng: don't want to disable this in firmware setup, and if
[   12.711148] intel_rng: you are certain that your system has a functional
[   12.711151] intel_rng: RNG, try using the 'no_fwh_detect' option.

[   13.473666] input: PC Speaker as /devices/platform/pcspkr/input/input4

[   13.860856] ENS1371 0000:02:0d.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21


shamim@shamim-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
shamim@shamim-desktop:~$ lspnp -v

00:03 PNP0800 AT speaker
    state = active
	io 0x61-0x61


00:0b INT0800 (unknown)
    state = active
	mem 0xfff00000-0xffffffff
	mem 0xffb00000-0xffbfffff



shamim@shamim-desktop:~$ esd
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
shamim@shamim-desktop:~$ killall esd
esd: no process killed

shamim@shamim-desktop:~$ lsof /dev/snd/*
COMMAND    PID   USER   FD   TYPE DEVICE SIZE NODE NAME
mixer_app 3577 shamim   21u   CHR  116,8      4753 /dev/snd/controlC0
shamim@shamim-desktop:~$ lsof /dev/dsp

cat /proc/asound/cards
 0 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                      Ensoniq AudioPCI ENS1371 at 0xde80, irq 21

lsmod | grep snd
snd_ens1371            30112  3 
gameport               19340  1 snd_ens1371
snd_ac97_codec        112548  1 snd_ens1371
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            45984  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            39296  0 
snd_seq_midi           14240  0 
snd_rawmidi            29472  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57584  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29320  2 snd_pcm,snd_seq
snd_seq_device         15372  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    66724  18 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         17032  1 snd_pcm

---

### Post by timcredible on 2009-03-31
sometimes the master volume gets reset to 0.  not sure where that is in xubuntu, but try opening whatever volume control app you have and move all the slider bars to max and see if you  have sound again.

---

### Post by shamimkhaliq on 2009-03-31
> **timcredible said:**
> sometimes the master volume gets reset to 0.  not sure where that is in xubuntu, but try opening whatever volume control app you have and move all the slider bars to max and see if you  have sound again. nope, nothing's muted, volume controls all set near max

---

### Post by shamimkhaliq on 2009-04-01
ok, so sound is bad in linux. are there any operating systems that are less bad? like perhaps an operating system that an alsa programmer worked on that presets everything to working ranges?

---

### Post by sanjeevpunj on 2009-04-01
Your Motherboard's sound device (Ensoniq AudioPCI) must be having some supported drivers.You can read some info at [http://ubuntuforums.org/showthread.php?t=135068](http://ubuntuforums.org/showthread.php?t=135068)
 related to this problem.

---

### Post by shamimkhaliq on 2009-04-01
> **sanjeevpunj said:**
> Your Motherboard's sound device (Ensoniq AudioPCI) must be having some supported drivers.You can read some info at [http://ubuntuforums.org/showthread.php?t=135068](http://ubuntuforums.org/showthread.php?t=135068)
 related to this problem.

thank you so much for pointing me the right way. the truth is out there :-)

---

### Post by shamimkhaliq on 2009-04-01
nope, that didn't work. i tried: before log in with gdm, ctl+alt+f1 (=console login) > sudo modprobe -r snd_ens1371
> sudo modprobe snd_ens1371 > exit > login with gdm. still no sound (bar a system beep on shut down)

cat /proc/asound/cards
 0 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                      Ensoniq AudioPCI ENS1371 at 0xde80, irq 21

so my 1371 is CARD 0, the default card

any other ideas?

---

### Post by j1mc on 2009-04-01
Sorry for the difficulties on this; I know sound is a bit of a mess on Linux sometimes, but it should still work.  I'm not a "sound master," but it does look like you've tried working through the Ubuntu Sount Troubleshooting guide.  (If not, though, you may want to take a look.)

Have you tried filing a bug on this?  Filing a bug will help to get the attention of the developers to get things together to fix your issue.

---

### Post by shamimkhaliq on 2009-04-01
> **j1mc said:**
> Sorry for the difficulties on this; I know sound is a bit of a mess on Linux sometimes, but it should still work.  I'm not a "sound master," but it does look like you've tried working through the Ubuntu Sount Troubleshooting guide.  (If not, though, you may want to take a look.)

Have you tried filing a bug on this?  Filing a bug will help to get the attention of the developers to get things together to fix your issue.


yup been through that guide and numerous others umpteen times.

i'm sure the developers are working really hard on the issue. internet searches lead me to believe there's been many a symposium, paper, blog and of course threads on this issue. 

but it's nice of you to reply, and so sympathetically too.

what i don't understand is why when i first installed ubuntu from an old cd i downloaded last year, everything was working fine. then i updated and lost functions. and now i try a clean reinstall from the old cd, i still don't have those functions i used to have? does what is installed depend on the internet connection data? should i try reinstalling again unplugging internet? 

i've tried some other linux distributions, but ubuntu beats all the ones i've tried for newbie-friendliness. i haven't figured out how to install most of the disks i have.

---

### Post by TBerk on 2009-04-01
You are not alone in having Sound Trouble.

I am running an Audigy2 card, (Sigma Tel STAC9721,23 chipset?);  it works fine in WinXP and *used to* work in 8.10 Intrepid. As in, I had sound in 8.10, but I got rid of that OS version during a repartition and install of 9.04.

I am in two camps at once; search, search, search for a 'been there, fixed that' solution & 'wait until *they* fix it in Justy. er Jaunty.

The current cuss words appear to be ALSA, OSS, and PulseAudio.

btw- my current flavor is Ubuntu Studio, I just noticed this thread was in Xubuntu. I don't think the difference is relative.


TBerk

---

### Post by shamimkhaliq on 2009-04-02
> **TBerk said:**
> ...btw- my current flavor is Ubuntu Studio, I just noticed this thread was in Xubuntu. I don't think the difference is relative.
TBerk

just installed ubuntu studio; easy install. no sound, but at least i get to follow the same help files from scratch rather than with a garbled up system cos of all the solutions i've tried. why do human beings look in the same place over and over again when they've lost something?


Done check sound device detected: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
Done ALSA update: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
Done PulseAudio update: [http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965) or should i do a downgrade [http://ubuntuforums.org/showthread.php?t=866965?](http://ubuntuforums.org/showthread.php?t=866965?)
Done change to pulseaudio: [http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)
fixing gnome-alsamixer: [http://www.debianhelp.org/node/7984](http://www.debianhelp.org/node/7984)
done debugging sound problems: [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

### Post by knarf on 2009-04-02
Have you tried muting and subsequently unmuting the PCM channel and Master? On my Thinkpad T23 (with a Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)) this always works - it quite often starts with no sound even though the channel 'looks' unmuted in alsamixer. Muting followed by unmuting brings the sound to live. Apparently the mixer starts in an undefined state.

---

### Post by TBerk on 2009-04-02
I had purposely left PCM alone but I;ll work that angle now.... one min...

- Click on speaker icon in upper Right hand corner.
- Click on **VOLUME CONTROL**.
- note currently set to:

Device: Audigy 2 [Unknown] [Alsa mixer]
Current channels selected; 
Master, Front, Surround, Center, LFE, Line In, CD Microphone.

- Click on **PREFERENCES** 
Add the following Channels;
PCM, PCM Center, PCM Front, PCM LFE, PCM Surround
- Click **CLOSE**

- Select MUTE for all PCM channels and close, reopen and un-select MUTE for any and all channels, close app again. 
(Note that upon re-open the MUTE button didn't show MUTE status, yet sliders were all the way in the DOWN or OFF position. Re-slid upwards as well as toggled MUTE ON & OFF again manually before closing app.)

Open Audacity Music App, play Roxanne mp3 file; NO SOUND.

(Just this morning I had booted into the WinXP partition and sounds there worked as expected.)


TBerk
Follow up; I rebooted into CMOS setup and verified that my settings for built in Audio was set to DISABLED.

---

### Post by shamimkhaliq on 2009-04-02
muting and unmuting the PCM channel and Master using alsamixer didn't work for me.

last time i went the pulseaudio way, [http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html), which didn't work.

this time should i go alsa for all applications, [http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/](http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/) ?

but then [http://ubuntuforums.org/showthread.php?t=929641](http://ubuntuforums.org/showthread.php?t=929641) says oss works and pulseaudio and alsa don't. where's a webpage that explains how to set that up?

answered part of my own question below. still want to try oss but don't know how to.

   1. Totem and Rhythmbox - these applications can play audio simultaneously, as they both use the GStreamer framework - and the GStreamer framework has native PulseAudio support.
   2. Totem and Neverball - if you try to use these applications together, only one will successfully play audio, and the other will fail. Totem will successfully use PulseAudio (through GStreamer). Neverball uses the SDL libraries for sound, however, and the ALSA driver for SDL is installed in Ubuntu by default. This will cause a conflict.
   3. Totem and Adobe Flash - again, it is not possible to use both of these applications simultaneously, as Totem uses PulseAudio (through GStreamer), but Flash only has ALSA support and thus cannot use PulseAudio by default. This will also cause a conflict.

---

### Post by TBerk on 2009-04-08
This worked for me, I'm using an Audigy2 (Creative Labs, Soundblaster). 

I had poked and prodded, wiped and reinstalled, downloaded updates. THIS is the final thing that enabled me to play 'Roxanne' on my speakers.

TBerk



> 

**Alsa doesn't work on Debian (snd_emu10k1) **
[http://www.linuxquestions.org/questions/linux-hardware-18/alsa-doesnt-work-on-debian-sndemu10k1-716321/?highlight=audigy](http://www.linuxquestions.org/questions/linux-hardware-18/alsa-doesnt-work-on-debian-sndemu10k1-716321/?highlight=audigy)


**wet-willy**

I have SB Audigy 2ZS, I was troubleshooting another member's 'no sound' issue with the same card and suggested playing with mixer settings, like mute things you don't use etc. The next day I found I had no sound also, didn't know that when I was troubleshooting buddies issues.
Anyway, he was talking about the Audigy output jack channel in his mixer, he had Gnome and I was in Mandriva with KDE and noticed I did not have that channel in kmix. Through kmix settings I enabled it, but still no sound like him, then I muted it and VOILA!, I had sound. But disabling the Audigy output jack again rendered Mandriva soundless. It had to be enabled but muted if not used...I guess.


---

### Post by TBerk on 2009-04-08
Just prior to my previous post I had added alsaplayer* (alsaplayer-common 0.99.80-3ubuntu, etc) this may have been the missing link.

"PCM Player designed for ALSA" in the details is what caught my eye. 


TBerk

---

### Post by shamimkhaliq on 2009-04-08
> **TBerk said:**
> Just prior to my previous post I had added alsaplayer* (alsaplayer-common 0.99.80-3ubuntu, etc) this may have been the missing link.

"PCM Player designed for ALSA" in the details is what caught my eye. 


TBerk
installed alsaplayer. installed kmix (i was using aumix and i can't find output jack channel there). trying to enable output jack channel then muting it, still no output jack channel visible. currently playing around muting, unmuting what is there. no luck.

---

### Post by TBerk on 2009-04-09
> **shamimkhaliq said:**
> installed alsaplayer. installed kmix (i was using aumix and i can't find output jack channel there). trying to enable output jack channel then muting it, still no output jack channel visible. currently playing around muting, unmuting what is there. no luck.

installing output jack channel 
>terminal>sudo synaptic>search: output jack>install: alsaplayer-jack
>terminal kmix> unmute everything (still no output jack showing)
terminal>alsaplayer>play cd> no sound


Hang tight a little bit.  I did a Synaptic Package Manager update to my Justy w/ Studio added on top and today (Wed 08Apr09) and it failed to reboot successfully.

I'm posting from a LiveCD session at the moment.

When I get Justy back up and running off the HD I'll take better step by step notes as to what got Sound Working.

------------- (re)INSTALLING OS from CD  -----------...

OK, rebooted from the HD after a Reinstall from CD. [Note, I have my /home on a separate partition, this may make a difference...] I haven't yet ran any updates re; Synaptic. 

I initially had **no sound** on boot.

Now I do, here is the toggle that enabled it for me:

- Open Sound App up in the Upper Right Hand Corner.
- Click Volume Control.
- Click PREFERENCES.
- Under "Select tracks to be Visible" I have:

BASS
TREBLE

PCM 
PCM CENTER
PCM FRONT
PCM LFE
PCM SURROUND

AUDIGY ANALOG/DIGITAL OUTPUT JACK

SIGMATEL 4-SPEAKER STEREO
SIGMATEL SURROUND PHASE INVERSION PLAYBACK

It seems it is the *Output Jack* that is key here, (but remember; right before I had success I had added some PCM related updates to ALSA as well.)

OK,  

- Click CLOSE.
- Click SWITCHES tab; upper left.
- Click on the 'Output Jack'.
- Click CLOSE, try some sound files.

In my case I am running a Creative Labs Sound Blaster Audigy2 (SB0240), it is a multi channel board and I have a second set of (currently un-amplified) speakers in a second output port- they are getting signal as well.

My next step is two fold; 1) verify Digital Output and function and/or Multi-Channel Output (Front/Center/LFE/Surround) & 2) detail what version of files/apps/updates is the actual winning combination.


TBerk

---

### Post by TBerk on 2009-04-09
Oh, btw- in 

- System
- Preferences
- Sound

The top three selections are set to Audigy 2 ... blah, blah, blah... p16v (ALSA)

Well, all of them are really but of course Capture is set to a capture version, etc. 

Next up for me is to explore the Multichannel versions of these same drivers...


TBerk

---

### Post by shamimkhaliq on 2009-04-09
thank you so much tberk for your detailed description. i am convinced that in Output Jack lies my solution. however, i am having trouble getting it to show up in my volume control. i continue to fiddle, hoping to one day control this important feature. i have, due to your informative posts, been able to set other sound preferences to suitable values, so sound should show up when i fix this problem.

---

### Post by TBerk on 2009-04-09
```
sudo apt-get install gnome-alsamixer
```

```
gnome-alsamixer
```

You should have a box there to select to activate the 'jack'.


Report back....


TBerk

---

### Post by kansasnoob on 2009-04-09
Regarding the OP's first post, if you do decide to "jump ship" my top 3 below Ubuntu are Linux Mint, Fedora, and then Mepis!

But that's largely because Simply Mepis is purely KDE and I like Gnome!

Mint's come up with many flavors that are looking really good ...... largely based on Ubuntu!

I'm still sure that Ubuntu will get the pulse audio thing right!

Super dumb question??????????? Is it possible that you unplugged something and then plugged it in the wrong port? I've done it! that's why I ask.

---

### Post by nystire on 2009-04-10
Just a minor point: For those who have problems with SDL based programs not working with PulseAudio, try installing 'libsdl1.2debian-pulseaudio'. This allows SDL programs to directly use PulseAudio.

---

### Post by shamimkhaliq on 2009-04-10
> **TBerk said:**
> ```
sudo apt-get install gnome-alsamixer
```

```
gnome-alsamixer
```

You should have a box there to select to activate the 'jack'.


Report back....


TBerk

hmmm, no jack in alsamixer. i am starting to travel backwards in my head. perhaps it is the sound card? but no, this sound card worked in xubuntu before, it will work again!

gnome-alsamixer does think it's pointing to tritech instead of Ensoniq. can i call my computer dumb or will that hurt its feelings? perhaps i need a healing crystal to hang over it ;-)

---

### Post by shamimkhaliq on 2009-04-10
> **nystire said:**
> Just a minor point: For those who have problems with SDL based programs not working with PulseAudio, try installing 'libsdl1.2debian-pulseaudio'. This allows SDL programs to directly use PulseAudio.

done (this removed some alsa package by the way)

---

### Post by shamimkhaliq on 2009-04-10
> **kansasnoob said:**
> Regarding the OP's first post, if you do decide to "jump ship" my top 3 below Ubuntu are Linux Mint, Fedora, and then Mepis!

But that's largely because Simply Mepis is purely KDE and I like Gnome!

Mint's come up with many flavors that are looking really good ...... largely based on Ubuntu!

I'm still sure that Ubuntu will get the pulse audio thing right!

Super dumb question??????????? Is it possible that you unplugged something and then plugged it in the wrong port? I've done it! that's why I ask.

newbie installation problems, couldn't install slackware, mepis, knoppix, gentoo for one reason or another (ranging from could not find the install button to did not know the username and password) so back with ubuntu. if i get frustrated with subtitles on streaming video (i wish i could hear a canned laughter track on "the wire") i shall try again.

i NEVER unplug cables. too many, too everywhere. replugging is a headache i avoid at all costs. reminds me to buy some sticky labels so i can write "plug a" "socket a" on things.

i'd try big eyes on a geek friend, but i fear he hates linux and cannot bear the scorn in his Macintosh loving eyes.

---

### Post by Awareness on 2009-04-10
just read the whole thread.. I have no solution... but i share the same agony... not your exact same problem but sound issues... Its so frustrating... ive tried lot of things already... i worked it out so it worked half of the time... but it didnt work in wine for example :(

Anyway, i had to reinstall ubuntu coz i had a severe video problems... spent so many time trying to fix it and it was easy to reinstall... and im back at the beginning with my sound problem... i bought a usb sound card to try another card... but its the same...

Again, nothing to offer but sympathy :(

I wish i weren't the most ubuntu nerdy i know... so i could ask for some help

Good luck (also for me)

---

### Post by redenex on 2009-04-10
> **Awareness said:**
> just read the whole thread.. I have no solution... but i share the same agony... not your exact same problem but sound issues... Its so frustrating... ive tried lot of things already... i worked it out so it worked half of the time... but it didnt work in wine for example :(

Anyway, i had to reinstall ubuntu coz i had a severe video problems... spent so many time trying to fix it and it was easy to reinstall... and im back at the beginning with my sound problem... i bought a usb sound card to try another card... but its the same...

Again, nothing to offer but sympathy :(

I wish i weren't the most ubuntu nerdy i know... so i could ask for some help

Good luck (also for me)

AMEN to that! :-({|=

---

### Post by TBerk on 2009-04-11
> 

I'd try big eyes on a geek friend, but...


Hey, Hey!, they're working already...

Lets see what the coleslaw that is my Bookmark file turns up:

Related to Digital/Analog JACK toggle:
[http://ubuntuforums.org/archive/index.php/t-26158.html](http://ubuntuforums.org/archive/index.php/t-26158.html)

Ubuntu Forum- Debugging Sound Problems
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

**ALSA w/ Pulsaudio** Excerpt:
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)> 
Audigy
If your Creative Audigy card is not giving you any sound, make sure the analog/digital check box in your sound mixer is unchecked. Updates seem to reset this switch regularly so keep this in mind.


**How it works, SOUND**
[http://ubuntuforums.org/showthread.php?p=5931543](http://ubuntuforums.org/showthread.php?p=5931543)

**Simple guide to Sound Solutions for Hardy,Intrepid and Jaunty Jackalope Users**
[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)

Kill off Pulse Audio (I thought this might have helped, and am including it, but it was a dead end for me)
[http://ubuntuforums.org/showthread.php?t=937275&highlight=audigy2](http://ubuntuforums.org/showthread.php?t=937275&highlight=audigy2)

**Comprehensive Sound Problem Solutions Guide v0.5e**
(This thread began in 2006, but it has some good base knowledge, command line stuff to harvest.)
[http://ubuntuforums.org/showthread.php?t=205449&highlight=audigy2](http://ubuntuforums.org/showthread.php?t=205449&highlight=audigy2)


OK, there's some homework to read up on. Get ta crack'n.


TBerk

---

### Post by TBerk on 2009-04-11
> **TBerk said:**
> ```
sudo apt-get install gnome-alsamixer
```

```
gnome-alsamixer
```

You should have a box there to select to activate the 'jack'.

**APPEND**

If you don't have the box to click on, enable it via:

```

- Edit
- Sound Card Properties
- slide down to Audigy Analog/Digital Output Jack and click on it.

```

Report back....


TBerk

---

### Post by American on 2009-04-11
I have a Dell M1210 on 8.10 which has been working flawlessly (well wifi comes and goes at boot sometimes) until a few days ago when, I believe, some updates killed my sound too.

No sound in Gnome... but I have sound in KDE. I've tried several of the alsa updates...nada.

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Dell Device 01d7
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I'm pretty Linux savvy but this on is kicking my buttocks too...

Obviously the sound card works as I have sound with KDE....just not in Gnome which is my preferred gui.

---

### Post by American on 2009-04-11
Ok... well I rebooted back in to Gnome after I made the post above, which I have done a few times trying to troubleshoot this problem, and presto I have sound. No idea why, didn't do a thing in between making the post above.

Crazy...maybe I just embarrassed my laptop and it fell in to line. Maybe it was the holy water I sprinkled on it. Who knows...

Maybe KDE somehow corrected some bad settings and then when I rebooted in to Gnome is was set correctly??? That's all I can figure. Try booting to KDE then back to Gnome.

---

### Post by AlecJ on 2009-04-11
You might try this guide?
[http://www.mythtv.org/wiki/Sound_Troubleshooting](http://www.mythtv.org/wiki/Sound_Troubleshooting)
see where it takes you.

---

### Post by freddie3782 on 2009-04-11
adding my self to the list.
Updated my computer last night.
Now.
No sound.
So many users with out sound. 
Can't the programers do something about this.
I mean the sound sucked compared to windows vista.
But it was sound non the less.
.Now.
NOTHING.
:guitar:

---

### Post by amano on 2009-04-11
Please Intel users: Read crimson's last post and try his deb file.

Does the deb file solve your problems? Please report back in THAT thread: [http://ubuntuforums.org/showthread.php?t=1084919&page=9](http://ubuntuforums.org/showthread.php?t=1084919&page=9)

---

### Post by TBerk on 2009-04-13
Well, going back over the original poster's information I see that here sound card is listed in Ubuntu as an **Ensoniq 5880 B** .

I'm using an Audigy2, (Sigmatel 9721. 32 chipset).  So my exact directions don't seem to be directly relevant.

Still, all hope is not lost, lets see what we can dig up. Someone, somewhere might well have solved this already.


TBerk

PS-  As AlecJ recommended, perhaps a "How to Troubleshoot Sound" link might help.  The following one is systematic and should generate info for yourself and/or the developers to tackle the problem.

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

