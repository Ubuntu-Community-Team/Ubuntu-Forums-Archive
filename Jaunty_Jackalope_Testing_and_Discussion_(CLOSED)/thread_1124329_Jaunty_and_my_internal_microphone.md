---
title: "Jaunty and my internal microphone"
date: 2009-04-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cfogelberg on 2009-04-13
Hi all,

I'm at my wits end when it comes to microphones and sound on Ubuntu. My installation is desktop-ready only for the deaf and mute. But enough rant :)

I first installed 64 bit Intrepid on my Dell XPS M1330, but decided quite quickly that some of the things in Jaunty (Amarok 2, longer before the support runs out etc) made it worth trying the beta. Now I have the 64 bit Jaunty beta installed.

When using Intrepid I had to add "options snd-hda-intel model=3stack" to /etc/modprobe.d/alsa-base.conf to make the volume audible. In Jaunty the volume is pretty good by default, and when I add that line in Jaunty it makes it too quiet.

Unfortunately the internal microphone is almost completely inaudible, and it has been that way for almost everything I have tried. I didn't get round to trying the mic with Intrepid, so I can't compare.

I have tried it in Sound Recorder, skype, skype-static-oss and skype-static. In all four of those configurations the internal mic is the same inaudible whisper.

Capture, Capture 1 and Capture 2 are all maxed out in the Volume Control applet, and I have unchecked the tick box which lets Skype play with the mixer levels.

Skype is set to use "HDA Intel (hw:intel,0)" for sound in, out and ringing. The volume level of the voice on echo123 is a little bit quiet given the volume is all on max, overall I'd say it's at a comfortable level.

Sound recorder shows the same properties as Skype (inaudibly quiet), and the level bar in the bottom right corner of its window never really gets above about 20% full.

Yesterday, VLC was working fine and could record voice at a reasonable level using the internal mic. Today though it's at the same inaudible level as the rest of it. Unless it was installing all of those versions of skype (yesterday I'd only tried skype) or adding then removing that line from alsa-base though then the only thing which could have broken it would be the "sudo apt-get update" and "sudo apt-get upgrade" I did earlier today. And that's kinda confusing.

Suffice to say I've read a lot, none of it has helped, and I'm extremely confused. All help appreciated!

One final factor which may be completely unrelated. Physically, the XPS M1330 has slightly strange input/output jacks:
* There are two sound-out ports, a left and a right. When I plug in to the left and call echo123 on Skype or use the test sound options in System|Preferences|Sound I can hear it fine. When I use the right hand socket I hear nothing. That's annoying, but not a biggie.
* I also have a microphone in, and I don't think that works at all, OR it works in exactly the same way - when I plug in a headset and do the sound tests the sound is the same inaudibly low volume.

Like I said, I'm confused. Any help, even just a way to up the gain on the mic and sound out a little, would be much appreciated!

Thanks,
Christo

---

### Post by cfogelberg on 2009-04-13
Further note:

Somehow between yesterday and today, Front (the slider in the Volume Control) was turned down from 100% to about 80%. When I put it back up to 100% the maximum volume is now the slightly-too-loud I would expect from the runty speakers on my laptop. The microphone is also fractionally louder (but still much quieter, and too quiet to use).

---

### Post by Hakkatuka on 2009-04-13
The following work-around works for me in Skype on Dell XPS m1330.

[https://lists.ubuntu.com/archives/kernel-bugs/2008-December/045858.html](https://lists.ubuntu.com/archives/kernel-bugs/2008-December/045858.html)

---

### Post by nwadams on 2009-04-13
ok, here's how to set up your volume settings for the xps m1330.

master: well that's obvious hopefully.
pcm: controls external speakers (and is similar to master)(controls overall volume too)
front: left headphone jack
surround: right headphone jack

you may have to go edit preferences to enable some of these switches
i have capture 1-3 enabled as well as digital, digital imput source and all three imput sources.

i maxed all the captures as well as digital.

on the options tab i set the digital imput source to digital mic 1
all the other imput sources are set to mic. Seemed to work fine for me then.

---

### Post by cfogelberg on 2009-04-13
> **Hakkatuka said:**
> The following work-around works for me in Skype on Dell XPS m1330.

[https://lists.ubuntu.com/archives/kernel-bugs/2008-December/045858.html](https://lists.ubuntu.com/archives/kernel-bugs/2008-December/045858.html)

Grrrrrrrr. It doesn't work.

I did the first two steps of the fix, and it didn't work. paman showed:
  Default sink: alsaboost_sink
  Default source: alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0

As recommended, I added "set-default-source alsaboost_source" to the bottom of default.pa and rebooted. However this also hasn't fixed the problem - the volume in Skype is as quiet as it always was, and paman now reports that the source and the sink are both alsaboost.

Gnome sound recorder also behaves identically. Prior to making this change VLC had also started recording sound at the normal level, but now it's back at the barely audible level.

I have tried moving the +50db slider around but that appears to have no effect. It's hard to tell though because the sound level is already so low.

In the gnome volume control applet I've noticed that Capture 1 and Capture 2 volume levels had reset to the minimum. Capture was still at the maximum. I set them all back to max, but again no effect. Does ANYTHING affect the volume of the recording?!

Another thing which doesn't affect the volume of the recording is as follows. Beneath each slider on the Recording tab of the Gnome volume control applet are two toggles - a little speaker (Mute/unmute X) and a little microphone (Toggle audio recording from X). After reboot all of the "Toggle audio recording from X" toggles are set to "no" and have a little x through them. Setting any or all of them to on has no effect.

For the record, I know that this isn't a hardware problem as it all works *perfectly* in Vista, which I dual boot. I only keep that partition around because I like iTunes so much (yes, I appreciate the irony). I hope I don't have to keep it around for Skype as well...!

Christo

---

### Post by nwadams on 2009-04-13
did u max digital and change the digital mic source to digital mic 1?

EDIT: if that doesn't work, i'm not sure what to do. I'm currently using hardy and thats what worked for me. I've live tested jaunty and it seemed to work fine out of the box...

---

### Post by cfogelberg on 2009-04-13
> **nwadams said:**
> ok, here's how to set up your volume settings for the xps m1330.

master: well that's obvious hopefully.
pcm: controls external speakers (and is similar to master)(controls overall volume too)
front: left headphone jack
surround: right headphone jack

you may have to go edit preferences to enable some of these switches
i have capture 1-3 enabled as well as digital, digital imput source and all three imput sources.

i maxed all the captures as well as digital.

on the options tab i set the digital imput source to digital mic 1
all the other imput sources are set to mic. Seemed to work fine for me then.

Hi nwadams,

Thank you for clarifying what maps to which jacks. Unfortunately even when I have the Surround maximised the right hand jack still doesn't make any sound.

What's the difference between pcm and "front and surround" - it seems that both control external speakers. Or by external speakers do you mean through HDMI?

I don't have a Digital preference option, and I only have capture 1 and captuer 2, no capture 3.

I have Digital Input Souce, which is set to Digital Mic 1, and only one other Input Source, which is set to mic.

Unfortunately that still does not work. I take it you are using the Jaunty beta as well?

Thanks,
Christo

---

### Post by nwadams on 2009-04-13
pcm is internal speakers. I've never used hdmi so i've no idea what controls it. 
But PCM acts like a second master so you can change your control and button volume to that so you don't ahve the retarded master that drops effective volume by 25% every time you touch the button. (sound coming out)

check to make sure the surround is not muted. 

Go to edit preferences and check the boxes for front, lfe, digital, capture 3, and anything else that seems interesting. 

I've beta tested a live cd of Jaunty but i'm currently using hardy, so my help is sort of skewed. But in jaunty i remember testing everything and it seemed to work properly right away...

---

### Post by cfogelberg on 2009-04-13
> **nwadams said:**
> did u max digital and change the digital mic source to digital mic 1?

EDIT: if that doesn't work, i'm not sure what to do. I'm currently using hardy and thats what worked for me. I've live tested jaunty and it seemed to work fine out of the box...

Hi nwadams,

Digital Mic Source is set to Digital Mic 1. I don't seem to have a Digital slider that I can max though? My options in preferences are:
* Master
* Headphone
* PCM
* Front
* Surround
* Center ###########################
* LFE ###########################
* PC Beep
* Capture
* Capture 1
* Capture 2
* +50db Mic
* Mux ###########################
* Mux 1 ###########################
* Mux 2 ###########################
* IEC958 ###########################
* IEC958 Default PCM  ###########################
* Analog Loopback ###########################
* Swap Center/LFE  ###########################
* IEC958 Playback Source  ###########################
* Digital Input Source
* Input Source
* Input Source
* Input Source

The ones with "###########################" after them are the ones I haven't played with or ticked the preferences box for, they seem completely irrelevant to audio recording.

Thanks again,
Christo

---

### Post by nwadams on 2009-04-13
ok, i guess it would be the 50 db mic that would be the digital. what are your imput sources set to??

i'm gonna boot to my live cd and play wiht things so i might be 15 mins before i get a chance to reply again.

---

### Post by cfogelberg on 2009-04-13
> **nwadams said:**
> pcm is internal speakers. I've never used hdmi so i've no idea what controls it. 
But PCM acts like a second master so you can change your control and button volume to that so you don't ahve the retarded master that drops effective volume by 25% every time you touch the button. (sound coming out)

check to make sure the surround is not muted.

Heh, now I feel stupid. Well that fixed that problem.

> **nwadams said:**
> Go to edit preferences and check the boxes for front, lfe, digital, capture 3, and anything else that seems interesting. 

I've beta tested a live cd of Jaunty but i'm currently using hardy, so my help is sort of skewed. But in jaunty i remember testing everything and it seemed to work properly right away...

Update on this:
* I don't have a Digital option in the list of preferences. Should I? This has been mentioned in a few places and I'm a little confused/worried I don't have it?
* LFE was muted for some reason.
* I don't have a Capture 3 option in the list of preferences. I only have Capture, Capture 1 and Capture 2.

I want to change my earlier statement to. I said that every time I rebotted the Capture options always "remuted" themselves, i.e. toggled off the microphone toggle below the slider "Toggle audio recording from X". It actually seems to happen every time I re-open the volume control, but not if I just change from the Recording tab to another tab and don't close the Gnome volume control.

Christo

---

### Post by cfogelberg on 2009-04-13
> **nwadams said:**
> ok, i guess it would be the 50 db mic that would be the digital. what are your imput sources set to??

i'm gonna boot to my live cd and play wiht things so i might be 15 mins before i get a chance to reply again.

Hi,

Thanks for all your help on this!

I don't think the "+50db mic" is the Digital, because that was what I added by editing /etc/asound.conf and /etc/pulse/default.pa (described in bug report that an above post linked to, I guess the point of doing this was to give me something I could add gain to the mic with).

EDIT: Above post linked to: [https://lists.ubuntu.com/archives/kernel-bugs/2008-December/045858.html](https://lists.ubuntu.com/archives/kernel-bugs/2008-December/045858.html)
I have followed the steps in this exactly as described, except that paman showed alsaboost_sink automatically became the default sink. Thus I only needed to add "set-default-source alsaboost_source" to the end of /etc/pulse/default.pa

My input sources are:
Digital Input Source: Digital Mic 1
Input Source: Mic
Input Source: Mic
Input Source: Mic

I don't know why it switched from having just one Input Source to 3, it must have taken a close-and-reopen of the volume control applet to get it to show the others when I ticked all of the Input Source check boxes in the preferences.

Christo

---

### Post by nwadams on 2009-04-13
ya, i'm not sure what the alsaboost is supposed to do. But i have that interesting low volume thing that you have with the mic on my live cd, trying to fix it.

EDIT: if you have a headphone volume thing, get rid of it, it doesn't do anything.

---

### Post by nwadams on 2009-04-13
sorry to double post BUT I FIXED IT. 

ok. So you know about the pulseaudio gnome 2.26 volume controller that was supposed to go into jaunty but got cut. Well install it

```
sudo apt-get install gnome-volume-control-pulse
```

then log out/log back in and it will show up as another volume icon. Open it and go to settings and just change the input volume on the input tab.

Then if you want you can get rid of the old icon by removing it from the panel. You will probably want to play with stuff to make the remote change the volume correctly and stuff like that but all should be good. There's probably lots of little tweaking to be done to make it perfect but it does fix the mic problem.

I hope that helps.

---

### Post by cfogelberg on 2009-04-13
> **nwadams said:**
> sorry to double post BUT I FIXED IT. 

ok. So you know about the pulseaudio gnome 2.26 volume controller that was supposed to go into jaunty but got cut. Well install it

```
sudo apt-get install gnome-volume-control-pulse
```

then log out/log back in and it will show up as another volume icon. Open it and go to settings and just change the input volume on the input tab.

Then if you want you can get rid of the old icon by removing it from the panel. You will probably want to play with stuff to make the remote change the volume correctly and stuff like that but all should be good. There's probably lots of little tweaking to be done to make it perfect but it does fix the mic problem.

I hope that helps.

Aaaargh! That makes it work even less for me!

Initially, the Input volume level is at about 50%. At that level the level indicator in Sound Recorder doesn't even move now, and it's completely inaudible when I call echo123 (I used to be able to hear it making noise).

The same thing happens now though if I max the Input volume out, or put it down to zero, or anywhere in between - the recorded sound is completely inaudible.

On the other hand the output is fine (e.g. I can hear echo123 talking to me quite clearly).

I think it's still working though because Skype doesn't complain about an input problem or that there is no sound - it just merrily lets me record silence on echo123.

I wondered if it could be because an important update was available, but sudo apt-get update and upgrade showed nothing: some gtk stuff and other odds and ends, also base-fileds, but nothing else.

I also wondered if there is some subtle difference in the steps we have taken, or if my earlier changes are screwing things up. The relevant part of my changelog is:

> 	SKYPE AND INTERNAL MIC
20090411 - sudo apt-get install skype (21mb) - sound doesn't work yet
20090412 - Skype|Options|Sound Devices. Select “HDA Intel (hw:Intel,0)” for Sound In, Sound Out, and Ringing.
20090412 - Volume Control (right click on volume icon in taskbar) - Preferences, add Digital Input Source, Capture 1, Capture 2 tabs, turn up volume to max)
	(also added third-from-bottom Input Source (adds option to choose between internal/front mic), and PC Beep volume level (for configurability))
	This makes internal mic work but is too quiet
	Exeternal mic doesn't work/is even quieter
	Audio is loud enough when using vlc though?! ---> PulseAudio problem?
	Maybe use skype-static-oss: [http://forum.skype.com/index.php?showtopic=119961](http://forum.skype.com/index.php?showtopic=119961)
20090413 - Added "options snd-hda-intel model=3stack" to /etc/modprobe.d/alsa-base.conf BEFORE "options snd-cmipci mpu_port=0x330 fm_port=0x388", i.e. so it's the third last non-commented line in the file
	Removed this, it basically made it inaudible.
20090413 - sudo apt-get install skype-static-oss, then skype-static, then back to skype (6mb more over skype, this was freed when skype plain was put back on)
	Still too quiet
20090413 - Tried alsaboost fix described here: [https://lists.ubuntu.com/archives/kernel-bugs/2008-December/045858.html](https://lists.ubuntu.com/archives/kernel-bugs/2008-December/045858.html) and here: [https://bugs.launchpad.net/bugs/275998](https://bugs.launchpad.net/bugs/275998) (i.e. created file /etc/asound.conf with text at link; modified /etc/pulse/default.pa)
20090413 - sudo apt-get install paman (Pulse Audio visual administrator, 2mb)
20090413 - Above alsaboost modifications didn't work and paman revealed that default source was: "alsa_input.pci_8086_284b_sound_card_0_alsa_capture_0", so added "set-default-source alsaboost_source" to end of /etc/pulse/default.pa
	Still too quiet.
20090413 - sudo apt-get install gnome-volume-control-pulse
	Back to being completely inaudible again.

---

### Post by nwadams on 2009-04-13
hmm, interesting. To be completely honest I did not test with skype, i tested with the basic gnome sound recorder. So if you do a quick test with the basic sound recorder we might be able to determine whether its a skype problem or a pulseaudio/alsa problem still. 

My configuration is a jaunty netbook remix default live usb with gnome-volume-control-pulse installed (only live disk i had)

Are you still using alsaboost?

EDIT: how did you set up skype to work for audio output. Mine wont' do that at all :|

---

### Post by cfogelberg on 2009-04-13
> **nwadams said:**
> hmm, interesting. To be completely honest I did not test with skype, i tested with the basic gnome sound recorder. So if you do a quick test with the basic sound recorder we might be able to determine whether its a skype problem or a pulseaudio/alsa problem still. 

My configuration is a jaunty netbook remix default live usb with gnome-volume-control-pulse installed (only live disk i had)

Are you still using alsaboost?

EDIT: how did you set up skype to work for audio output. Mine wont' do that at all :|

Yeah, I tested with both Skype and sound recorder and neither worked.

My Jaunty install is the desktop 64 bit beta. Alsaboost is still installed but that didn't seem to have any effect on it beforehand (good or bad). Still, maybe it's playing with it now.

I'm not familiar with what the netbook remix live usb is, specifically the "usb" part of it?

It's getting late-ish for me and I'm going to head to bed, but what I'll do tomorrow is:
* test the live CD (both desktop and the netbook remix)
* disable alsaboost and hope for the best

My hope is that either disabling alsaboost will solve the problem, or that at least I can get the same sort of results as you've been getting.

To get skype working I changed it's sound in, sound out, ring tone from Default (or whatever the default setting is) to "(intel hw,0)". I think "(intel hw,0)" is what the text is, I'm using a WinXP laptop right now and don't remember exactly. Anyway, it was the first entry in the drop down box. These settings worked with all of the skypes (i.e. skype, skype-static etc). The GUI is a bit finicky and sometimes doesn't display properly, but random clicking around usually makes it show itself :)

Best,
Christo

---

### Post by nwadams on 2009-04-13
just use jaunty desktop live cd, dont' worry about netbook remix. Thanks, ill keep looking and will update my post if i figure anything brilliant out

EDIT: did you upgrade to jaunty or do a clean install? Implementation of Pulseaudio in Hardy/Intrepid was less than spectacular so it might have botched it enough to create a mess in jaunty(which fixed it)

---

### Post by cfogelberg on 2009-04-14
> **nwadams said:**
> just use jaunty desktop live cd, dont' worry about netbook remix. Thanks, ill keep looking and will update my post if i figure anything brilliant out

EDIT: did you upgrade to jaunty or do a clean install? Implementation of Pulseaudio in Hardy/Intrepid was less than spectacular so it might have botched it enough to create a mess in jaunty(which fixed it)

I did a clean install of the 64bit desktop Jaunty beta on a newly formatted ext3 drive, so I can't blame Intrepid :(

My beta CD was downloaded and burnt on 9/4/9, but I don't think the supplied image has changed from the beta's release.

I tried installing gnome-volume-control-pulse on the Live CD but I couldn't. [EDIT: See next post.]
* Initially, it didn't show up as something I could install using "sudo apt-get install gnome-volume-control-pulse".
* I tried doing "sudo apt-get update" and "sudo apt-get upgrade", but I kept running out of disk space with the live CD.
* Even after "sudo apt-get remove openoffice-*", "sudo apt-get remove evolution*" and "sudo apt-get remove compiz*" I still didn't have enough space to update and upgrade!

So I didn't try that any further. However, reversing the alsaboost stuff has produced hopeful results, but far from perfect... After reversing the alsaboost changes:

* When every single slider is maxed out (Old panel: PCM, Front, Master, LFE; Pulse panel: Input, Output; etc) the recording is now at a good volume, maybe even slightly too loud. A little bit crackly, but not too bad.

* Unfortunately, at this volume other sounds play back way too loud. For example, when logging in to Ubuntu the default login noise crackles over the speakers.

For the record I have also checked the volume levels using alsamixer and aumixer, and those are also all maxed out.

The whole problem is exacerbated by the odd calibration of the volume sliders, and AFAICT this odd calibration applies to any slider in any of the volume control applets I'm trying to use. On each of these sliders it seems like the effective range of it is compressed into the top half, and the bottom 50% of each slider doesn't do anything. By the time I've put the volume down to half way it'll be the quietest whisper. At 45% it's completely inaudible. This makes fine tuning the volume very difficult!

If I could recalibrate these then maybe I'd be able to kludge it and tweak it all together into some sort of shambling mess, but one that worked?

Christo

---

### Post by cfogelberg on 2009-04-14
> **cfogelberg said:**
> I tried installing gnome-volume-control-pulse on the Live CD but I couldn't.

Heh, a flash of idiocy. I had forgotten to enable the other repositories on the Live CD. I've just tried that now and it works on the Live CD as it does on the hard disk installation (although the volume sliders are still horribly mis-calibrated and the noise level is scratchy at any volume level you can actually hear it at).

Can the sliders be fixed? :/

Christo

---

### Post by nwadams on 2009-04-14
I'm not sure about the volume sliders calibration issue. You can try, if you do get them let me know how you did it.

As for the slider volume. I found that the recording volume was independent of speaker volume...I'll conduct further tests today...

---

### Post by bigbrovar on 2009-04-15
it would really be unacceptable if we have to suffer internal mic problems on jaunty just as we did on hardy and ibex. it would really be unfortunate if we want to be accepted by the average joe simple things like sound recording for making skype calls should just work, since the hardware is already supported.

---

### Post by nwadams on 2009-04-15
yes it would be nice. And it should be done. The problem is that we are in the middle of transitioning between the older audio models (alsa, OSS) and pulseaudio. Many apps like skype, vlc. do not yet support pulseaudio natively, and either need plugins or need some workaround method for them. Yes, some distro's have done it better than us but with the immense number of different hardware its hard to support everything out of the box. the gnome-volume-control-pulse shoudl ahve been used though because thats all I had to do to make my mic work

---

### Post by cfogelberg on 2009-04-15
> **nwadams said:**
> yes it would be nice. And it should be done. The problem is that we are in the middle of transitioning between the older audio models (alsa, OSS) and pulseaudio. Many apps like skype, vlc. do not yet support pulseaudio natively, and either need plugins or need some workaround method for them. Yes, some distro's have done it better than us but with the immense number of different hardware its hard to support everything out of the box. the gnome-volume-control-pulse shoudl ahve been used though because thats all I had to do to make my mic work

And hopefully the transition from old to new finishes soon! Maybe I should have waited 6 months for Koala...? :(

Anyway, why did they partially pull Pulse from GNOME? It seems to have left things in a very confusing muddle!!

Christo

---

### Post by nwadams on 2009-04-15
> **cfogelberg said:**
> And hopefully the transition from old to new finishes soon! Maybe I should have waited 6 months for Koala...? :(

Anyway, why did they partially pull Pulse from GNOME? It seems to have left things in a very confusing muddle!!

Christo

That in my opinion is the problem. Everything is all frozen right now unless there's a catastrophic crash or something so I expect the fix will get put in post-release. 

What i'm gonna do is purge all my pulseaudio files when i upgrade and see if that helps. Because the supposedely fixed some stuff. But we still have this little problem. ya, it will definatly get fixed post release

---

### Post by bigbrovar on 2009-04-16
Sad to see that going to 2 years after pulse audio was announced its still havent taking use to the promiseland, on the contrary it has become the biggest PITA for linux users. i cant help but wonder what the retionale for shipping this piece of crap and making is the default sound system. it just beat me.. really.. i was hoping that things would have improved on jaunty only to find out that its still same ol same ol .. am almost tempted to say with Pulse Audio Linux doesn't really need a Virus

---

### Post by cfogelberg on 2009-04-16
OK, to summarise the final solution:
* Install PULSE audio control (sudo apt-get install gnome-volume-control-pulse)
* Set the Input slider in this to maximum (it is installed as gnome-volume-control-settings)
* Change the Device in gnome-sound-properties to "Playback: HDA Intel - STAC92xx Analog (PulseAudio..."
* Change the Audio Conferencing:Sound capture drop down in gnome-volume-control settings to "PulseAudio Sound Server"
* In Skype - Options:Sound Devices leave Ringing and Sound Out on "HDA Intel (hw:intel,0)". Set Sound In to "pulse".

With this, Skype test calls now work and I can record using Sound Recorder fine, plus all the audio everywhere seems to work.

Huge thanks to nwadams for his help with this!!
Christo

---

### Post by Hakkatuka on 2009-04-16
> With this, Skype test calls now work and I can record using Sound Recorder fine, plus all the audio everywhere seems to work.

Have you tried actually calling someone on Skype? When I did there was a delay on the other end of the call, and it kept accumulating.

---

### Post by cfogelberg on 2009-04-19
> **Hakkatuka said:**
> Have you tried actually calling someone on Skype? When I did there was a delay on the other end of the call, and it kept accumulating.

So far so good - I made a few phone calls using Skype Out with it last night, it seemed to work OK. Fingers crossed... :)

That said, the volume is still a *lot* quieter than on Vista. On Vista I have the volume set at about 25%, on Linux I need it at about 80-90%. What's Window's secret?

xto

---

### Post by nwadams on 2009-04-19
thats interesting that the volume is still quieter. 
open alsamixer (run in terminal) and make sure all the playback sliders are at max. your PCM or front might be still lower.

---

### Post by cfogelberg on 2009-04-20
> **nwadams said:**
> thats interesting that the volume is still quieter. 
open alsamixer (run in terminal) and make sure all the playback sliders are at max. your PCM or front might be still lower.

On Playback only pcbeep is at 0, and on the Capture tab only Mux, Mux 1 and Mux 2 are at 0. In others words pretty much all at max, and still quieter than Vista.

---

