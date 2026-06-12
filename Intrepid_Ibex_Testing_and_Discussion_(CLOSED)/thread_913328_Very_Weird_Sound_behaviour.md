---
title: "Very Weird Sound behaviour"
date: 2008-09-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ubername on 2008-09-07
Please see this:
[http://ubuntuforums.org/showthread.php?t=911294](http://ubuntuforums.org/showthread.php?t=911294)

It is so odd: sound works fine from the speakers, but when I plug the headphones in, it gradually diminishes until it is silent on the 'phones(@ 10 seconds), and then unplugging the 'phones leaves it silent on the speakers. Reboot resets the position; sound fine until 'phones plugged in. Any help much appreciated!

TIA

---

### Post by ubername on 2008-09-09
further Info: If I unplug the headphones before the sound is completely gone, the speakers are completely gone (i.e. no sound). Then when the 'phones are plugged back in the sound is gone (I suspect it keeps on tailing off after the 'phones are removed, but it's just a guess)

---

### Post by whitethorn on 2008-09-09
Have you had a look in your alsamixer what happens when you plug in your earphones?  I had a problem similar to that, Ubuntu goes mute when I plug in / unplug my earphones, I just turn the volume back up a bit and it's fixed.  So look and see if it mutes.

---

### Post by ubername on 2008-09-09
> **whitethorn said:**
> Have you had a look in your alsamixer what happens when you plug in your earphones?  I had a problem similar to that, Ubuntu goes mute when I plug in / unplug my earphones, I just turn the volume back up a bit and it's fixed.  So look and see if it mutes.
Thanks for the response!

I put alsamixer in one window (interesting - shows only the 'master'  channel with pulseaudio being the card and the chip).

I put gnome-sound-properties up in another window (which shows a number of channels, e.g. master, PCM, front, etc.) and tested the sound - outcome: continuous bleep. 

The I plugged the headphones in (while the bleep was playing)  and heard the sound fade away, without anything changing on alsamixer.

Seems my pulseaudio setup is not right? Or am I jumping ahead too much?

---

### Post by ubername on 2008-09-09
As a test, I put my playback properties in gnome-sound-properties to ALSA rather than Autodetect. Same thing happened, so it seems not to be PulseAudio

---

### Post by ubername on 2008-09-11
Whilst the behaviour mentioned above continues, I have another problem which may be related:

I can't get my keyboard volume control to work. I have a logitech cordless desktop MX300 keyboard which used to work fine - controlling whichever channel was selected in gnome-sound-properties but it doesn't work now.

---

### Post by ubername on 2008-09-12
Just installed the latest updates (including linux 2.6.27-3)  , and my keyboard now controls the sound again, but the problem with the headphones 'stealing' the sound remains.

---

### Post by ubername on 2008-09-15
Just installed the latest updates, which included alsa-base and linux sound base. Slight difference - When I plug the headphones in the sound still fades, but if I take them out before it is completely gone, then it will still play at the lower volume through the speakers.

---

### Post by ubername on 2008-09-15
If I run 
sudo alsa reload

I get

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 6696(pulseaudio) 6864(mixer_applet2). 
Unloading ALSA sound driver modules: snd-hda-intel snd-usb-audio snd-pcm-oss snd-mixer-oss snd-seq-dummy snd-pcm snd-seq-oss snd-usb-lib snd-hwdep snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-intel snd-usb-audio snd-pcm snd-usb-lib snd-hwdep snd-rawmidi snd-timer snd-seq-device snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-intel snd-usb-audio snd-pcm-oss snd-mixer-oss snd-seq-dummy snd-pcm snd-seq-oss snd-usb-lib snd-hwdep snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

but the sound remains at the quiet level after unplugging the headphones. Is this to be expected?

---

### Post by kostkon on 2008-09-15
You could try to install the *PulseAudio Device Chooser* application (*padevchooser* package) to check which device *PulseAudio* sees as the default, through the *PulseAudio Volume Control* utility. Also, you will be able to move the audio between devices. Especially, this will be useful if you are talking about USB headphones (recognised as an audio device by the system) and not mini-jack ones.

---

### Post by ubername on 2008-09-16
> **kostkon said:**
> You could try to install the *PulseAudio Device Chooser* application (*padevchooser* package) to check which device *PulseAudio* sees as the default, through the *PulseAudio Volume Control* utility. Also, you will be able to move the audio between devices. Especially, this will be useful if you are talking about USB headphones (recognised as an audio device by the system) and not mini-jack ones.

Thanks, this has given me a lot more avenues to explore.

I found in ~/home/.pulse/volume-restore.table, which by virtue of its name made me think it might be significant to my problem.

pulsecore/protocol-native.c$PulseAudio Volume Meter


alsa_output.pci_8086_284b_alsa_playback_0.monitor
pulsecore/protocol-native.c$Totem Movie Player
2 65536 65536
alsa_output.pci_8086_284b_alsa_playback_0

pulsecore/protocol-native.c$Adobe Flash
2 65536 65536
alsa_output.pci_8086_284b_alsa_playback_0

pulsecore/protocol-native.c$VLC media player
2 65536 65536
alsa_output.pci_8086_284b_alsa_playback_0

pulsecore/protocol-native.c$gnome-sound-properties
1 65536
alsa_output.pci_8086_284b_alsa_playback_0
alsa_input.usb_device_46d_8c5_DE62BEC2_if2_alsa_capture_0

does this look OK?

Also FWIW PulseAudio Manager (sink) says ALSA PCM on front:0 (STAC92xx analog)via DMA

but my gnome-sound-propertieshas default mixer tracks is set to 'master' which enables the keyboard volume control, and if I change it to 'front' it makes no difference. (headphones don't work).

I am clearly way out of my depth here. Any help gratefully received. 

I would like to know

- how pulseaudio and ALSA work together
- which files I need to post to enable proper analysis of the situation (I don't want to clog up the forum with screen shots)

If anyone can help it would be much appreciated.

---

### Post by ubername on 2008-09-16
If it helps:

I click on the 'test' button in gnome-sound-properties while I have PulseAdio manager open. Then I click on the 'Devices' tab in PulseAudio Manager and click the device for 'sinks'. Then I click on the 'properties' button and select 'show volume meter'. Then I launch 'Sounds' and click on (any) test button and the pulse-audio volume shows a signal but no sounds are played via the speakers or headphones. (I do get the occasional click when plugging the phones in and out)

---

### Post by ubername on 2008-09-20
Perhaps I am setting off down some wrong paths with the PulseAudio Volume Control. I don't know enough about it, but certainly the PulseAudio Volume control has a cross in the speaker icon, when using the speakers, even though they make sound. When I plug the 'phones in the sound fades (as above) but the Pulse Audio manager doesn't change and it doesn't list the 'phones as a new output device.

I have reinstalled ubuntu8.04 on a separate partition and have no problems with sound via the speakers or the 'phones. Thanks for the help so far - can anyone get me to make ibex work with the 'phones?

---

### Post by psyke83 on 2008-09-20
> **ubername said:**
> Perhaps I am setting off down some wrong paths with the PulseAudio Volume Control. I don't know enough about it, but certainly the PulseAudio Volume control has a cross in the speaker icon, when using the speakers, even though they make sound. When I plug the 'phones in the sound fades (as above) but the Pulse Audio manager doesn't change and it doesn't list the 'phones as a new output device.

I have reinstalled ubuntu8.04 on a separate partition and have no problems with sound via the speakers or the 'phones. Thanks for the help so far - can anyone get me to make ibex work with the 'phones?

Try to keep in mind that PulseAudio is in fact an ALSA client (therefore, ALSA mixer settings will impact PulseAudio's output). From a previous comment you said that alsamixer shows your soundcard as "PulseAudio" with just the "Master" mixer - that's fine.

To get access to the mixer settings on your real card, invoke alsamixer like this:
```
$ alsamixer -Dhw
```

If you have more than one sound card, you may need to modify it to -Dhw0 or -Dhw1, etc.

You also need to install "padevchooser" to get access to the PulseAudio Volume Control applet - check the mixer settings there as well.

---

### Post by ubername on 2008-09-20
> **psyke83 said:**
> Try to keep in mind that PulseAudio is in fact an ALSA client (therefore, ALSA mixer settings will impact PulseAudio's output). From a previous comment you said that alsamixer shows your soundcard as "PulseAudio" with just the "Master" mixer - that's fine.

To get access to the mixer settings on your real card, invoke alsamixer like this:
```
$ alsamixer -Dhw
```

If you have more than one sound card, you may need to modify it to -Dhw0 or -Dhw1, etc.

You also need to install "padevchooser" to get access to the PulseAudio Volume Control applet - check the mixer settings there as well.

Thanks.

When I try PulseAudio Volume control I get 'Connection failed: Connection refused', having followed this: [http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)

---

### Post by plun on 2008-09-20
> **ubername said:**
> Thanks.

When I try PulseAudio Volume control I get 'Connection failed: Connection refused', having followed this: [http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)

I filed this about esd_auth which where blocking PA-GUIs 

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/272402](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/272402)

Something is complete messed up...

---

### Post by ubername on 2008-09-22
In my latest set of updates I found that a number of pulseaudiio packages are now 'not authenticated'. Is there a problem?

---

### Post by ubername on 2008-09-29
I have just gone to kernel 2.6.26-1-rt  because of this:

[http://ubuntuforums.org/showthread.php?p=5876977&posted=1#post5876977](http://ubuntuforums.org/showthread.php?p=5876977&posted=1#post5876977)

and same behaviour with headphones.  Any clues as to how to diagnose? (other than those suggested up-thread))

---

### Post by ubername on 2008-10-02
bump

---

### Post by Jim March on 2008-10-05
New info: the problems are **_NOT PULSEAUDIO RELATED_**.  I did the following:

sudo apt-get remove pulse*

...and removed *everything* related to PulseAudio with extreme prejudice, then reconfigured for ESD in the System>Preferences>Sound menus.

Audio still works quite well EXCEPT that the headphone-sound-fade glitch is still there.  So the blame here isn't on PulseAudio, it's below that somewhere.

**[COLOR="Red"]EVERYBODY DO THIS:[/COLOR]**

At a terminal window do:

```
alsamixer -Dhw
```

If it doesn't pop up, do:

```
sudo apt-get install alsamixer
```

...and try the "alsamixer -Dhw" command again.

At the mixer screen that comes up, note your make and model of sound card.  My card is listed as "HDA Intel", chip is listed as "SigmaTel STAC9228".

Is that what everybody else has?  Or are we seeing this glitch with multiple sound card/chip types?  It's VERY important we sort that question out STAT.  Too many people are reporting their problems but NOT what hardware they have, that's freakin' critical here folks.

---

### Post by Jim March on 2008-10-05
Update: the command:

sudo alsa force-reload

...will "fix" the sound until you plug headphones in again and break it...

---

### Post by Jim March on 2008-10-05
Same issue here.  Driving me freakin' insane.

This is an all-Intel based recent model laptop, Dell Inspiron 1525, seems to be a basic HDA Intel sound setup with a SigmaTel "STAC9228" mixer.

I've tried ripping PulseAudio COMPLETELY out (sudo apt-get remove pulse*) and that hasn't helped.  Sound DOES still work OK mind you, so we need to stop looking at PulseAudio as the issue - it ain't.  

I've also learned that the terminal command:

sudo alsa force-reload

...will cause the sound to return out of the laptop speakers, until I plug headphones in again of course.

My hardware is an HDA Intel card, SigmaTel 9228 chipset as confirmed by this command at the terminal:

alsamixer -Dhw

Everybody else with this issue needs to do that, so we can sort out what hardware is affected.  I'm guessing it's limited to the SigmaTel 9228 chipset, possibly only when it's used by Intel...

---

### Post by Jim March on 2008-10-05
Whoops, I had the same thread open in two windows, my bad...sigh...

---

### Post by Jim March on 2008-10-05
[SIZE="7"]SUCCESS!  PROBLEM SOLVED!  Except...[/SIZE]

...I had to rip out not just PulseAudio, but also ALSA (gulp).

The good news: I replaced it with OSS4, using the really VERY good instructions at:

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Note that there's even Intrepid-specific notes, plus 64-bit specific stuff!

I would strongly recommend ripping PulseAudio out first the same way I did before following these instructions.

This pins the problem down to the ALSA subsystem somehow, and likely the snd_hda_intel driver.

So far I've tested OSS4 with Totem, Rythmbox, VLC Player 9.3 and Adobe's 10rc2 flash player by way of Firefox.  Kewl.  **Literally zero issues, once I used System>Preferences>Sound to configure all sound output to "OSS4 - HD Audio Play Front"** after following the instructions at the above link.

I've tested this in Gnome ONLY so far!  There are however KDE-specific notes, and I see no reason why this won't work in XUbuntu as well.

Understand: this is a pretty damn radical solution and some apps may choke unless reconfigured.  But it DOES work and should get us over the hump to full release assuming that this IS fixed in ALSA/Pulse by release date (no guarantees of course).

---

### Post by lucazade on 2008-10-05
The OSS4 control panel is impressive!
I've installed it some minutes ago with no issues and it seems to work out of the box.. interesting :)

---

### Post by bur[n]er on 2008-10-07
I must say, I'm hesitant to replace PulseAudio and Alsa with OSS.  Anyone figure out a way to fix this with pulse? 

My card is a "Sigmatel STAC9227" in a Dell Dimension e520 desktop.  Any help would be appreciated!  Here's hoping it's fixed before Intrepid's release.

---

### Post by psyke83 on 2008-10-07
Yes, it appears it is possible to get sound working correctly for your laptop and headphones if you enable a specific quirk (ironically, I found the solution on the openSUSE forums when googling the keywords of this post).

Starting here: [http://forums.opensuse.org/hardware/389637-sound-slowly-fades-out-when-connecting-phones-speakers.html](http://forums.opensuse.org/hardware/389637-sound-slowly-fades-out-when-connecting-phones-speakers.html)
Directs you to this post: [http://forums.opensuse.org/archives/sls-archives/archives-suse-linux/archives-hardware-support/archives-notebooks/382722-dell-vostro1400-hda-intel-no-sound.html#post1798954](http://forums.opensuse.org/archives/sls-archives/archives-suse-linux/archives-hardware-support/archives-notebooks/382722-dell-vostro1400-hda-intel-no-sound.html#post1798954)

In other words, edit /etc/modprobe.d/alsa-base, and append to the end of this file:

```
options snd-hda-intel model=dell-3stack
```

The setting should take effect after a restart.

I feel really sorry for the poor sod who installed OSSv4... ;)

---

### Post by psyke83 on 2008-10-07
> **'bur[n]er said:**
> I must say, I'm hesitant to replace PulseAudio and Alsa with OSS.  Anyone figure out a way to fix this with pulse? 

My card is a "Sigmatel STAC9227" in a Dell Dimension e520 desktop.  Any help would be appreciated!  Here's hoping it's fixed before Intrepid's release.

Of course, see my post above (though you may need to specify a different driver quirk).

I am >99% certain that it won't be fixed, unless you file a bug confirming the necessity of said quirk, and give your specific system specs. Only then can this quirk be made default for your hardware.

---

### Post by bur[n]er on 2008-10-07
Thanks for the tip Psycke.  I'll find out when I reboot if it worked.

To those that used the "sudo alsa force-reload" trick.  You also have to run "pulseaudio" again after alsa is reloaded and then relaunch any sound apps.

/me fires up launchpad.net to file a bug

---

### Post by bur[n]er on 2008-10-07
Bug report posted:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/279478](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/279478)

---

### Post by Jim March on 2008-10-07
As the "poor sod" in question running OSS4, hey, it's working!  The only problem so far is that sound fails in Bos Wars (game).  Shrug.

The volume controls in OSS4 are needlessly complex but my Dell 1525 keyboard "volume up/down" keys still work just as they did in Alsa/Pulse.  Kewl.  The level and detail of controls available are just amazing...and it appears to be easier to boost the sound on some of the dimmer youtube/flash videos as well.

Radical solution?  Hell yeah, but I plan on re-installing when Intrepid officially releases anyways.  I'll then try the standard combination, if it still farts I'll try tweaking that, if no joy it'll be back to OSS4.

Which is a damned viable solution, guys...

---

### Post by psyke83 on 2008-10-07
> **Jim March said:**
> As the "poor sod" in question running OSS4, hey, it's working!  The only problem so far is that sound fails in Bos Wars (game).  Shrug.

The volume controls in OSS4 are needlessly complex but my Dell 1525 keyboard "volume up/down" keys still work just as they did in Alsa/Pulse.  Kewl.  The level and detail of controls available are just amazing...and it appears to be easier to boost the sound on some of the dimmer youtube/flash videos as well.

Radical solution?  Hell yeah, but I plan on re-installing when Intrepid officially releases anyways.  I'll then try the standard combination, if it still farts I'll try tweaking that, if no joy it'll be back to OSS4.

Which is a damned viable solution, guys...

:)

Just keep in mind that PulseAudio is not OSSv4 compatible, and you may need to manually rebuild drivers with each kernel update.

---

### Post by Jim March on 2008-10-07
M'kay, but the jump from 2.6.27-4 to 2.6.27-5 happened while I was on OSS4 and it was smooth as silk...

---

### Post by psyke83 on 2008-10-07
> **Jim March said:**
> M'kay, but the jump from 2.6.27-4 to 2.6.27-5 happened while I was on OSS4 and it was smooth as silk...

That's good to hear - obviously OSSv4 has progressed since I last used it. Is PulseAudio working?

---

### Post by Jim March on 2008-10-07
Nope.  I pulled it first, then ALSA to put in OSS4, and never even tried to put PulseAudio back.

???

Do I need it?  It certainly appears not...

---

### Post by ubername on 2008-10-07
> **'bur[n]er said:**
> I must say, I'm hesitant to replace PulseAudio and Alsa with OSS.  Anyone figure out a way to fix this with pulse? 

My card is a "Sigmatel STAC9227" in a Dell Dimension e520 desktop.  Any help would be appreciated!  Here's hoping it's fixed before Intrepid's release.

Exact same set-up, I've got rid of pulse following advice upthread. now on the 2.6.25-7 kernel. I will report more later.

---

### Post by psyke83 on 2008-10-07
> **Jim March said:**
> Nope.  I pulled it first, then ALSA to put in OSS4, and never even tried to put PulseAudio back.

???

Do I need it?  It certainly appears not...

That's correct, you don't need PulseAudio - but you're missing out on extra functionality. Also keep in mind that if you file any bugs relating to audio problems, you must disclose that you're not using ALSA. You're also likely to receive the stock answer: "please remove OSSv4 and re-install ALSA to test this issue".

We should always try to keep third-party software to a minimum, especially during the development cycle.

---

### Post by Jim March on 2008-10-07
Yeah, that's *absolutely* understood: no complaining about audio without also documenting everything DONE to audio, and the mainstream Ubuntu devs aren't likely to support OSS4.  I'm OK with that - OSS4 was a last-ditch radical experiment that much to my surprise, works well enough for my needs.

I did the tweak simply to make Intrepid functional for me - I need that headphone jack (for reasons involving roommates and a severe difference in tunes tastes...).  I went to Intrepid both to test it, and because I need some of the newer functionality regarding cellmodems, dual head video and more.

---

### Post by ubername on 2008-10-08
> **Jim March said:**
> [SIZE="7"]SUCCESS!  PROBLEM SOLVED!  Except...[/SIZE]

...I had to rip out not just PulseAudio, but also ALSA (gulp).

The good news: I replaced it with OSS4, using the really VERY good instructions at:

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Note that there's even Intrepid-specific notes, plus 64-bit specific stuff!

I would strongly recommend ripping PulseAudio out first the same way I did before following these instructions.

This pins the problem down to the ALSA subsystem somehow, and likely the snd_hda_intel driver.

So far I've tested OSS4 with Totem, Rythmbox, VLC Player 9.3 and Adobe's 10rc2 flash player by way of Firefox.  Kewl.  **Literally zero issues, once I used System>Preferences>Sound to configure all sound output to "OSS4 - HD Audio Play Front"** after following the instructions at the above link.

I've tested this in Gnome ONLY so far!  There are however KDE-specific notes, and I see no reason why this won't work in XUbuntu as well.

Understand: this is a pretty damn radical solution and some apps may choke unless reconfigured.  But it DOES work and should get us over the hump to full release assuming that this IS fixed in ALSA/Pulse by release date (no guarantees of course).

Close to giving this post a big thanks, but - plugging the headphones in does not transfer the sound to the 'phones (they work in Vista) and I have lost the ability to control sound from my keyboard (but I can do it from ossxmix)

---

### Post by ubername on 2008-10-10
Things are looking up - I have messed with ossxmix gui and discovered I can have the sound from either the headphones alone (green jack set to 'input' (?) ) or both the headphones and the speakers (green jack set to 'front'). What I miss now is the keyboard control. (It's a logitech wireless keyboard MX3000)

Any help?

TIA

---

### Post by ubername on 2008-10-14
> **psyke83 said:**
> Of course, see my post above (though you may need to specify a different driver quirk).

I am >99% certain that it won't be fixed, unless you file a bug confirming the necessity of said quirk, and give your specific system specs. Only then can this quirk be made default for your hardware.

Any clues how to specify the different driver quirk for a STAC9227?

TIA

---

### Post by psyke83 on 2008-10-14
> **ubername said:**
> Any clues how to specify the different driver quirk for a STAC9227?

TIA

From: [http://www.kernel.org/doc/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.kernel.org/doc/Documentation/sound/alsa/ALSA-Configuration.txt)

```
	STAC9227/9228/9229/927x
	  ref		Reference board
	  3stack	D965 3stack
	  5stack	D965 5stack + SPDIF
	  dell-3stack	Dell Dimension E520
	  dell-bios	Fixes with Dell BIOS setup
```

Be sure to read through that document properly.

---

### Post by ubername on 2008-10-15
> **psyke83 said:**
> From: [http://www.kernel.org/doc/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.kernel.org/doc/Documentation/sound/alsa/ALSA-Configuration.txt)

```
	STAC9227/9228/9229/927x
	  ref		Reference board
	  3stack	D965 3stack
	  5stack	D965 5stack + SPDIF
	  dell-3stack	Dell Dimension E520
	  dell-bios	Fixes with Dell BIOS setup
```

Be sure to read through that document properly.

Um... Ii got a bit put off by the first lines of the document 'To enable ALSA support you need at least to build the kernel with primary sound card support (CONFIG_SOUND).'

I haven't built the kernel ever and think it might be just a tiny bit dangerous for me to do it with my level of understanding. ("What are you doing in the  Development & Programming  > Intrepid Ibex Testing and Discussion  > forum then?" I hear you rightly complain)

However, on the off chance I cut and pasted from the recommended article  and guessed that

'STAC9227/9228/9229/927x
	  ref		Reference board
	  3stack	D965 3stack
	  5stack	D965 5stack + SPDIF
	  dell-3stack	Dell Dimension E520
	  dell-bios	Fixes with Dell BIOS setup'

meant that I should add

options snd-hda-intel model=dell-3stack as mentioned upthread (which I had already tried, but I have installed upgrades since then so give it another go)

to the end of alsa-base.

Alas, no joy after restart.

Any more clues? (and thanks for the help)

---

### Post by psyke83 on 2008-10-15
> **ubername said:**
> Um... Ii got a bit put off by the first lines of the document 'To enable ALSA support you need at least to build the kernel with primary sound card support (CONFIG_SOUND).'

I haven't built the kernel ever and think it might be just a tiny bit dangerous for me to do it with my level of understanding. ("What are you doing in the  Development & Programming  > Intrepid Ibex Testing and Discussion  > forum then?" I hear you rightly complain)

However, on the off chance I cut and pasted from the recommended article  and guessed that

'STAC9227/9228/9229/927x
	  ref		Reference board
	  3stack	D965 3stack
	  5stack	D965 5stack + SPDIF
	  dell-3stack	Dell Dimension E520
	  dell-bios	Fixes with Dell BIOS setup'

meant that I should add

options snd-hda-intel model=dell-3stack as mentioned upthread (which I had already tried, but I have installed upgrades since then so give it another go)

to the end of alsa-base.

Alas, no joy after restart.

Any more clues? (and thanks for the help)

Try *all* of those quirks, one at a time.

---

### Post by ubername on 2008-10-15
> **psyke83 said:**
> Try *all* of those quirks, one at a time.

Sorry for being pedantic, but I wasn't sure I understood your suggestion. I tried adding  e.g.

options snd-hda-intel model=3stack 

to the end of alsa-base, after removing 

options snd-hda-intel model=dell-3stack

then tried each of:
options snd-hda-intel model=3stack
options snd-hda-intel model=5stack
options snd-hda-intel model=dell-bios

after removing the previous command.

All failed to fix the problem. Thanks for the help.

---

### Post by psyke83 on 2008-10-15
> **ubername said:**
> Sorry for being pedantic, but I wasn't sure I understood your suggestion. I tried adding  e.g.

options snd-hda-intel model=3stack 

to the end of alsa-base, after removing 

options snd-hda-intel model=dell-3stack

then tried each of:
options snd-hda-intel model=3stack
options snd-hda-intel model=5stack
options snd-hda-intel model=dell-bios

after removing the previous command.

All failed to fix the problem. Thanks for the help.

You followed the process correctly, though I hope you performed a full reboot between changes (the "sudo alsa reload" process may not always work correctly).

What's the model of your PC/laptop? I didn't see you mention it in earlier posts.

Also try "model=auto" to see if it helps.

---

### Post by ubername on 2008-10-15
> **psyke83 said:**
> You followed the process correctly, though I hope you performed a full reboot between changes (the "sudo alsa reload" process may not always work correctly).

What's the model of your PC/laptop? I didn't see you mention it in earlier posts.

Also try "model=auto" to see if it helps.

Dell E520 desktop, intel hda STAC9227,

I have been doing complete reboots between changing settings, which is why I take so long to respond (something to do with the RAID bios controlling my primary hard drive, but that's for another place/time!) And unfortunately model=auto doesn't work either,

Thanks for the ongoing support.

---

### Post by psyke83 on 2008-10-15
> **ubername said:**
> Dell E520 desktop, intel hda STAC9227,

I have been doing complete reboots between changing settings, which is why I take so long to respond (something to do with the RAID bios controlling my primary hard drive, but that's for another place/time!) And unfortunately model=auto doesn't work either,

Thanks for the ongoing support.

Hmm, "model=dell-3stack" should have solved the issue for you. Are you sure there isn't another line in alsa-base that's overriding your selection?

Try dell-3stack again, and ensure the ALSA *and* PulseAudio volume levels are okay.

For ALSA:
```
$ alsamixer -Dhw
```

For PulseAudio:
```
$ pavucontrol
```

Also make sure you've updated your BIOS.

---

### Post by ubername on 2008-10-15
> **psyke83 said:**
> Hmm, "model=dell-3stack" should have solved the issue for you. Are you sure there isn't another line in alsa-base that's overriding your selection?

Try dell-3stack again, and ensure the ALSA *and* PulseAudio volume levels are okay.

For ALSA:
```
$ alsamixer -Dhw
```

For PulseAudio:
```
$ pavucontrol
```

Also make sure you've updated your BIOS.

Not sure what you mean about updating my BIOS?

---

### Post by psyke83 on 2008-10-15
> **ubername said:**
> Not sure what you mean about updating my BIOS?

If you're dual-booting: [http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R157196&SystemID=DIM_PNT_P4_E520&servicetag=&os=WW1&osl=en&deviceid=308&devlib=0&typecnt=0&vercnt=8&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=209822](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R157196&SystemID=DIM_PNT_P4_E520&servicetag=&os=WW1&osl=en&deviceid=308&devlib=0&typecnt=0&vercnt=8&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=209822)

Otherwise: [http://linux.dell.com/wiki/index.php/Tech/libsmbios](http://linux.dell.com/wiki/index.php/Tech/libsmbios)

N.B. Take care when updating your BIOS. I can't be held responsible for charred metal ;).

---

### Post by ubername on 2008-10-16
> **psyke83 said:**
> If you're dual-booting: [http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R157196&SystemID=DIM_PNT_P4_E520&servicetag=&os=WW1&osl=en&deviceid=308&devlib=0&typecnt=0&vercnt=8&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=209822](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R157196&SystemID=DIM_PNT_P4_E520&servicetag=&os=WW1&osl=en&deviceid=308&devlib=0&typecnt=0&vercnt=8&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=209822)

Otherwise: [http://linux.dell.com/wiki/index.php/Tech/libsmbios](http://linux.dell.com/wiki/index.php/Tech/libsmbios)

N.B. Take care when updating your BIOS. I can't be held responsible for charred metal ;).

Checked my BIOS. I'm on 2.4.0 which is the one available from the Dell download site (intrigued by the idea of getting it one way if dual booting and another way if not. I am dual booting but I would have thought the BIOS was completely unaware, and independent,  of that. But that's not what this thread is for!)

Here is my alsa-base: Does anything seem to be over-riding my dell-3stack command?

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
# Test to keep the headphones from fading
options snd-hda-intel model=dell-3stack

And Thanks for all the help.

---

### Post by ubername on 2008-10-17
bump

---

### Post by psyke83 on 2008-10-17
Unfortunately not; the dell-3stack quirk should have fixed your issue. You should really escalate this issue and file a bug (OSSv4 is not a good alternative, honestly).

Make sure that you didn't add a different quirk to another of the files in /etc/modprobe.d/, e.g. /etc/modprobe.d/options.

---

### Post by ubername on 2008-10-18
> **psyke83 said:**
> Unfortunately not; the dell-3stack quirk should have fixed your issue. You should really escalate this issue and file a bug (OSSv4 is not a good alternative, honestly).

Make sure that you didn't add a different quirk to another of the files in /etc/modprobe.d/, e.g. /etc/modprobe.d/options.

Thanks

There is already one, I have discovered.
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/279478](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/279478)

I have added a 'me too'.

Thanks for you time in trying to sort this.

---

### Post by ubername on 2008-10-26
Output from sudo alsa force-reload

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
Terminating processes: 6210 6429lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-usb-audio snd-pcm-oss snd-mixer-oss snd-pcm snd-usb-lib snd-hwdep snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-usb-audio snd-pcm-oss snd-mixer-oss snd-pcm snd-usb-lib snd-hwdep snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.


output from  pulseaudio


W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
W: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
W: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0

Doesn't look good. The odd thing is a couple of minutes ago I had it fixed (after installing latest updates) i.re. I was quite happily listenng to the headphones. I then LOOKED AT (not changed anything intentionally) various pulseaudio volume controls / device choosers. Saw nothing I understood so tried some sounds again. There it was - broken. Now when I reboot I'm back to square one- sound works from speakers until 'phones are plugged in then it fades.

p.s. any one know how to switch smilies off? in the post above 'colon' followed by 'open bracket 'is represented as :(, but I don't want it to be.

---

### Post by ubername on 2008-10-27
After installing new upgrades etc. I now seem to be working. The headphones don't fade, the sound automatically switches between speeakers and 'phones when I plug in the 'phones, and the keyboard volume control works. 

Two slight quibbles: 
The volume control applet doesn't show 'mute' (i.e. a red cross on it) when it is muted, so I have a hunch it is not looking at the right thing, 
Quite a bit of static sounds from the phones when no sound is playing.

But overall, things seem sorted.

---

