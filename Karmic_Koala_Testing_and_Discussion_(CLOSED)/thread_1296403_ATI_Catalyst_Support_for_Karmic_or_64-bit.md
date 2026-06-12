---
title: "ATI Catalyst Support for Karmic or 64-bit"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Pauly BC on 2009-10-20
Does ATI Catalyst operate properly on 64-bit Ubuntu 9.04 or 9.10? I have had a lot of struggles with that driver and I noticed the AMD/ATI website does not offer a distinction between 32 or 64 bit.

The problems I have had related to some sort of driver conflict. When I use the default Ubuntu driver I cannot use the 3D features, graphics are heavily interlaced and the screen refresh rate is very slow. It basically does not use the video accelerators. When I try to activate the fglrx driver through the Ubuntu utility, it downloads the files, works through installation, then reports 'an error occured during installation' with no further details, then backs out the installation. When I download Catalyst from ATI I can install it, but it 'borks' the sound so every file plays as static rather than music, resolves the refresh rate and interlacing, but still does not activate 3D features.

Is this a 64-bit version problem? Any advice on which version of Catalyst to run in Jaunty or Karmic? Has anyone else experienced these problems and found an appropriate resolution?

Thanks
p

---

### Post by sloggerkhan on 2009-10-20
If you are using hdmi for sound it might be related to that? What card are you using?

I can't speak too much to your issue because I don't have similar hardware, but phoronix.com might be a good source for ati fglrx issues if nobody here can step up.

---

### Post by Pauly BC on 2009-10-20
Hi Slogger,

I'm not using the HDMI for sound, rather I am using the on-board Realtek 883 5.1 sound. It works great for me in Windows and it's fine in Linux so long as I don't load Catalyst.

---

### Post by P4man on 2009-10-20
the driver you download contains both the 32 and 64 bit version (hence no distinction)

What videocard do you have? Ive seen reports of people having fairly new ATI cards that had trouble with the restricted driver from the hardware driver manager, but the one on the ATI site seems to work fine.

As for the sound.. I guess the ATI driver also enables HDMI sound and perhaps that is now configured as default. Try changing in your pulseaudio settings.

---

### Post by Mark Phelps on 2009-10-20
You didn't way what video card/chip you're using, but since it's apparently an HP box, it could very well be some low-end chip like X300.  Only the newer high-end Hd3x, 4x, and 5x cards have ATI drivers that will work in 9.04 or 9.10.

If you have one of the legacy cards and are forcing the install of the ATI driver, that could explain why other things are getting hosed in the process.

If you have one of the newer cards, the suggestion to check the Phoronix forums is the best approach as they typically are the first to find and fix ATI driver related issues.

---

### Post by P4man on 2009-10-20
> **Mark Phelps said:**
>  but since it's apparently an HP box, 

I reread his posts 3x trying to see where he stated that.. 
think you misread his sig; Vista HP refers to Home Premium I bet.
And since the rest of his sig seems to indicate fairly new stuff, I doubt he has an X300, but who knows.

---

### Post by Mark Phelps on 2009-10-21
> **P4man said:**
> I reread his posts 3x trying to see where he stated that.. 
think you misread his sig; Vista HP refers to Home Premium I bet.
And since the rest of his sig seems to indicate fairly new stuff, I doubt he has an X300, but who knows.

Ok ... you're right. I misinterpreted the "HP" reference to mean that he was running an HP OEM version of Vista.

Still, the Phoronix forums are an excellent place to go to learn about the details of ATI drivers.

---

### Post by Pauly BC on 2009-10-21
Thank you for the feedback, here are some clarifications:

The PC is made from components and I am running Windows Vista Home Premium on another partition. To be precise I have successfully trio-booted XP, Vista and Linux.

The video card is a ATI Radeon 3850.

How do you edit the PulseAudio settings to restore default sound to the 5.1 rather than HDMI?

---

### Post by P4man on 2009-10-21
Install pavucontrol, run it from apps>sound and and video>pulse audio volume control, then go to the Output Devices.

---

### Post by Longinus00 on 2009-10-22
> **Pauly BC said:**
> Thank you for the feedback, here are some clarifications:

The PC is made from components and I am running Windows Vista Home Premium on another partition. To be precise I have successfully trio-booted XP, Vista and Linux.

The video card is a ATI Radeon 3850.

How do you edit the PulseAudio settings to restore default sound to the 5.1 rather than HDMI?

Can you not adjust it by opening system>preferences>sound and then going to the output tab?

---

### Post by P4man on 2009-10-22
> **Longinus00 said:**
> Can you not adjust it by opening system>preferences>sound and then going to the output tab?

In karmic you can. In jaunty I believe you can change it by changing the default mixer in sound preferences though that doesnt always seem to work

---

### Post by Pauly BC on 2009-10-22
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

I don't know how each of those options should be used so I go with what works. Right now Autodetect, HDA Intel ALC883 Analog (OSS) [1 and 2 but not 3], ALSA - Advanced Linux Sound Architecture, ESD - Enlightenment Sound Daemon, and Pulse work from the test screen. The others do not work, probably because my monitor does not have speakers and my 5.1 is actually hooked up as 3.1 for now.

When I activate Catalyst, none of the audio options make nice sounds, some of them make static when sounds should be played.

Does Catalyst load in some utility I could use to disable the on-board audio in the video card? Is there a way to sudo chop it so it only activates the video driver and not the HDMI sound driver?

Heh heh sudo chop.

Thanks,
Paul

---

### Post by Pauly BC on 2009-10-23
bump

---

### Post by P4man on 2009-10-24
you could see if there is a module for it that you can blacklist. run lsmod to see which ones are loaded and try to remove then with rmmod -r ?

---

