---
title: "6 SoundCards Regognized???"
date: 2005-04-07
forum: Installation &amp; Upgrades
---

### Post by jandante on 2005-04-07
Hi,

I've recently installed Ubuntu as i saw it growing on the DistroWatch rankings. (OK i just go for popular distro's). And I must say I really like this one. Almost everything works just like that. Except for sound...

I have two soundcards, reason of that is one card that's embedded in the mother board, and another one that I bought to install a 5.1 surround system.

When I start up the Gnome-Volume-Control the program recognizes 6 sound devices...
I wanted to take a screenshot but apparently that is impossible while navigating in a menu. So here is the text version. In the Gnome-Volume-Control I click "File, Change Device" that gives me following options:
0:C-Media Electronics CMI91739 (OSS-mixer)
1:C-Media PCI (OSS-mixer)
2:USB Mixer (OSS-mixer)
3:SIS SI7012 (ALSA-mixer)
4:C-Media PCI CMI8738-MC6 (ALSA mixer)
5:USB Device 0x46d:0x8b4 (ALSA-mixer)

I can play music in XMMS via eSoundPlugin. But in RhytmBox I get the following error: > OSS-apparaat  "/dev/dsp" is already in use
I get the same error in Totem.

So when playing sound in XMMS I can mute by going in Gnome-Volume-Control to C-Media Electronics CMI9739 (OSS-mixer), although I thought that supposed to be SIS SI7012 (ALSA-mixer). Cause that is where my boxes are attached to (the on-board soundcard). I tried the newer souncard but that doesn't work no mather what device selected. I assume the new card is: C-Media PCI CMI8738-MC6 (Alsa mixer).

Could anyone point me out where I'm making a mistake. And what are those USB devices doing there? Or is this a bug where i'm not responsible for.

Thanks already,

Dante

---

### Post by IceAxe18 on 2005-04-08
In my opinion I think that you should remove that sound card from your computer & see if you can get things working with just the onboard sound.

Im not sure if your mother board is semi current, because mine is semi current & my on board sound is able to do 5.1 surround.

---

### Post by jandante on 2005-04-08
I don't know exactly what semi current means but my onboard sound card doesn't support 5.1 surround. So now I'm listening to music with two pathetic little boxes... And my pretty expensive 5.1 system is just laying around. I want de C-Media sound card to work. Wich previously worked in GentooLinux. Only I could easily make changes myself in gentoo, I'm affraid changing something in Ubuntu might f*** up the system.

thanks

---

### Post by jandante on 2005-04-08
Maybe following info gives a more clear description of my hardware concerning Soundcards:

dante@angelina:~$ lspci | grep -i audio
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:0a.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)


with sis being the onboard sound card (DON'T NEED THAT ONE CAN I DISABLE IT?)
and C-Media Electronics being my "new" sound card. I know the alsadriver for my new card is "cmipci". But which config files to change...

Please help me

---

### Post by ubuntu_fan on 2005-04-08
[QUOTE=jandante]Maybe following info gives a more clear description of my hardware concerning Soundcards:

dante@angelina:~$ lspci | grep -i audio
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:0a.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)


with sis being the onboard sound card (DON'T NEED THAT ONE CAN I DISABLE IT?)
and C-Media Electronics being my "new" sound card. I know the alsadriver for my new card is "cmipci". But which config files to change...

Please help me[/QUOTE]

Usually you can disable the onboard soundcard in the machine's BIOS...

That might just be the trick.

a.

---

### Post by jandante on 2005-04-08
Ok that was an easy one. The onboard sound controller is now disabled. Also I figured out what the USB mixer was: my webcam with microphone. I removed it from the computer because video wasn't working and I actually never needed it anyway.
So here we are now:

Gnome-Volume-Control is giving me two devices, actually one device but once as OSS-mixer and once as ALSA-mixer:

0:C-Media PCI (OSS-mixer)
1:C-Media PCI CMI8738-MC6 (ALSA mixer)

I hear system sounds!
I can play music in XMMS via eSound Output Plugin 1.2.10 (libesdout.so)!
I can play movies in MPlayer also via the eSound Output Plugin (while playing music in XMMS!!!!)
BUT
I CAN'T play music in RhythmBox (still same error :  "OSS-apparaat "/dev/dsp" is already in use", while it isn't in use according to me)
I did an apt-get to install totem-xine (I can play movies but can't hear anything)

While playing something I try changing the volume in Gnome-Volume-Control. Both devices (ALSA and OSS mixer) respond.

And to get everything clear. Am I right when i try to visualise Sound in Ubuntu in layers with the following layer diagram:


[CENTER]APPLICATION[/CENTER] 

[CENTER]-----------------------------------------------------------------------------

ALSA or OSS or ESOUND or ... (SOUND SERVERS????)

-----------------------------------------------------------------------------

GStreamer Framework[/CENTER]


Thanks for your help

---

### Post by jandante on 2005-04-11
I got one step further. I'm updating just for people experiencing same problem and also -more important- for a new question.

I've been able to play music in RhytmBox by killing the ESD proces:

dante@angelina:~$ /usr/sbin/lsof | grep dsp
esd        7167      dante    5w      CHR       14,3               8042 /dev/dsp
dante@angelina:~$ kill 7167

But now ESD is killed and I can use XMMS only when I change the output plugin back to OSS. And with OSS there's appareantly no simoultaneous (sorry for my bad english...) play possible. I like RhytmBox more then XMMS but to give up simoultaneous play...

And please someone take a look at the layer I made in my previous post. I really like to know if I'm making any sense there.

Greetings

---

### Post by jorgepeixoto on 2005-10-16
It is strange what you say about rhytmbox. I use rhytmbox with esd normally here. But it seems that your rhytmbox is trying to bypass esd. Maybe your rhytmbox is misconfigured. I use Breezy btw. 

Also I have heard that the automatix script does some audio tweaks that could help you. Google for it. 

I hope that helps, that is all I know.

---

### Post by jorgepeixoto on 2005-10-16
Maybe your problem is related with bug 16282.

---

