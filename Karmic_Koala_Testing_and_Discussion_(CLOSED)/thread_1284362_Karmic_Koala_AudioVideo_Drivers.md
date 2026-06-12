---
title: "Karmic Koala Audio/Video Drivers"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Pauly BC on 2009-10-06
Can you please streamline/improve the audio and video 'driver' implementation in Karmic? I installed Jaunty on my desktop but due to pervasive hardware conflicts and unpleasant replies to my forum-posting requests for help I dumped Ubuntu off my system. I have an ASUS P5K mobo with built-in Realtek Audio 883 and an ATI Radeon 3850 video card. When you install Jaunty from the live CD, it loads in about 6 different audio 'drivers' including PulseAudio, ALSA all of which offer audio through the ATI HDMI or Realtek 5.1. When I go into the hardware drivers and activate the proprietary driver for the ATI card Catalyst, it somehow messes up the audio system so all I get is static. I have been unable to resolve the issue.

My recommendation/hope for Karmic is threefold:
1. Streamline/simplify/reduce the number of options for 'standard baseline' audio drivers. I know Linux is modular and customizable, but one driver that works will do the trick.
2. If possible improve the integration of Catalist into the system.
3. Provide some sort of driver conflict diagnostic utility. Windows has always had such a feature to let you detect IRQ conflicts or driver activation problems, but in Ubuntu you seem to need a lot of experience in order to diagnose and resolve those conflicts.

Here's the catch: If I can't resolve the conflict and make the audio work I'm not going to keep Ubuntu, and if I don't keep Ubuntu I'm not going to learn to resolve the conflict.

Thanks
Pauly

---

### Post by ikt on 2009-10-06
> I have an ASUS P5K mobo with built-in Realtek Audio 883 and an ATI Radeon 3850 video card. When you install Jaunty from the live CD, it loads in about 6 different audio 'drivers' including PulseAudio, ALSA all of which offer audio through the ATI HDMI or Realtek 5.1. When I go into the hardware drivers and activate the proprietary driver for the ATI card Catalyst, it somehow messes up the audio system so all I get is static. I have been unable to resolve the issue.

Submit a bug against ubuntu? 

There's also several irc channels for reporting bugs and finding out who would be responsible for this type of bug.

---

### Post by emarkay on 2009-10-06
Sorry that some here and elsewhere are just plain idjets, I will offer what I can, and here, things have improved here fantastically regarding those aforementioned "jets"...

I have a similar config with Realtek AC97 and HD2600XT on my Karmic test machine.

I have audio, in 5.1 surround. I JUST tested it 5 minutes ago for the first time - on the other test PC that is now in Windows for some Flight Simming, so I won't be back to Ubunto Karmic there till tomorrow.

Can you attach screenshots and maybe annotate what specific things you don't like - I haven't even looked at the Audio sections and I bet I will feel similar - it was already confusing enough with the plethora of OS Audio settings, codecs and drivers.

As for Catalyst, the ATI/AMD "FGLRX Closed source" comes from them directly.  Plus, it's moot in Karmic since even Catalyst 9.9 will NOT run in the new Linux Kernel, as I understand.  Use the "Restricted Driver" (which is ACTUALLY Catalyst 9.10 -SSSSSH it's almost a secret!  :) )


I don't think the IRQ use is anything like Windows, but I have not researched it.  Mostly for driver issues I just try them till I find a working one.  When you say conflicts - be more specific - what sort of errors are you getting?  Again screenshots are easy in Ubuntu and posting them here is also easy.

No one can force you to use something you don't like, but seriously, give Ubuntu some time - it really does grow on ya' and there's nothing like not having to worry about Malware and "paid upgrades"!

MRK

---

### Post by Pauly BC on 2009-10-08
Sorry I did not get into Linux today to get more info. The error is that the audio output is always only static when it should be sounds or music. Even the drum tap at the login screen comes out as PSHSHSHSHST.

The solution may be as simple as a sudo command to erase one or two lines out of some config file. I just want it to work and don't see why it offers so many utilities and options.

---

### Post by Pauly BC on 2009-10-09
When I go through to Sound Preferences, for Sound Playback I have the following in the drop-down menu:
Autodetect
HDA Intel ALC883 Digital (ALSA)
HDA Intel ALC883 Analog (ALSA)
HDA ATI HDMI ATI HDMI (ALSA)
HDA Intel ALC883 Analog (OSS)
HDA Intel ALC883 Analog (OSS)
HDA Intel ALC883 Analog (OSS)
ALSA - Advanced Linux Sound Architecture
ESD - Enlightenment Sound Daemon
OSS - Open Sound System
PulseAudio Sound Server

I don't know how each of those options to use. Right now Autodetect, HDA Intel ALC883 Analog (OSS) [1 and 2 but not 3], ALSA - Advanced Linux Sound Architecture, ESD - Enlightenment Sound Daemon, and Pulse work from the test screen. The others do not work, probably because my monitor does not have speakers and my 5.1 is actually hooked up as 3.1 for now.

When I activate Catalyst, none of the audio options make nice sounds, some of them make static when sounds should be played.

So in this case my request for the next release of Ubuntu is to streamline the sound management package to have fewer options, to make sure those options work 'out of the box' and to make sure they do not conflict with Catalyst and help me debug them if they do.

Does Catalyst load in some utility I could use to disable the on-board audio in the video card?

Thanks,
Paul

---

### Post by Pauly BC on 2009-10-14
Hmmm.

Five days and no reply. I can only hope this means other people hope drivers will be streamlined in Karmic.

---

