---
title: "Hardy sound problem"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by mboisson on 2008-05-11
Hello,
I have a Gigabyte GA-MA78GM-S2H motherboard with the 780G chipset and the HD 3200 ATI IGP. I installed the server amd64 version of hardy and apt-got ubuntu-desktop.

I can get sound through the analog output, but the volume is ridiculously low. How can I change that ?

Also, I can not get sound playing through the optical S/PDIF output, neither through the HDMI. Anyone knows a solution ?


Thank you,

---

### Post by Yosh08 on 2008-05-12
Hello,

i had the same problem.. I have to say that i'm a complete beginner and i don't know much about Ubuntu (that's the reason why i'm here ;)).
So that's what i did: 

First, i downloaded the driversoftware from realtek's-website. I followed the intruction (readme-file) and installed the new driver. After that, I used the synaptec-packed-manager to install 'GNOME ALSA'(User interface for ALSA). In the audio-controls i selected 'ALC882 Digital' and in the last drop-down-list HDA Ati SB (Alsa-Mixer)'. Now i used the GNOME ALSA Panel to configure the sound devices, i had to unmute some (!). And that's it. I got digital signal.

I hope this helps anybody. Sorry for my bad English :)

Bye

---

### Post by mboisson on 2008-05-12
thank you, I will try that tonight when I get back at home.

---

### Post by Yosh08 on 2008-05-13
I had to install ubuntu again and i found out, that you don't have to install the drivers from realtek. Just install the GNOME ALSA Mixer and start it. Now tick 'IEC958' on.In the audio-options i used the digital-out for ALSA.

Bye

---

### Post by domness on 2008-05-13
Well I have the problem that every so often the sound just completely stops. If I restart the PC then it works fine. But when it stops working, any of the music players just won't play any music files..

Any ideas? It doesn't really annoy me, but just concerns me every so often. It doesn't happen all the time.

---

### Post by mboisson on 2008-05-13
I tried installing the realtek drivers (at first, I could not finish the installation because alsaconf was missing, I had to install first the latest alsa from the source code, because it seems that alsaconf is missing from the packages on the repositories).

However, I still have no sound from the HDMI output. I did not test the optical S/PDIF (I don't have speakers with optical input right now.) Did you suceed in getting audio from the HDMI ??

Thanks

---

### Post by Yosh08 on 2008-05-14
Hello,

did you check the box in the Gnome-Alsa-Tool? I don't have a HDMI-Device to test it. But in the Gnome-Alsa-Tool you can tick the 'IEC958 Box' on for every sounddevice. That was the only thing i had to do to start the optical-sound-output.

@Domness: Sorry, i have no idea :( I just changed my OS a few days ago, so Ubuntu is very new for me.

---

### Post by domness on 2008-05-15
@Yosh08 - No worries. I'll search around and see what I can find.

---

### Post by SebMKd on 2008-05-17
Hi Guys,

I've found this to be a partial solution: [_Thread Here_]("http://ubuntuforums.org/showthread.php?p=4948939")
I have now audio over HDMI if I play raw video files (Mov, Avi, MPEG), but no sound with ISO, VOB or even Youtube.

There is maybe a chance the developers at ALSA are working on a solution, because so far the they do not list the 780G chipset on their website (alsa-project.org) and a few bugs tracked for it.

However, if anyone make progress please post!

---

### Post by misterspider on 2008-05-29
Hi,
I too had the same problem, i followed this and it worked.

I just went System->Preferences->Sound.

Under Music and movies i chose 'ALC882 Digital'. I used Synaptic to install Gnome-alsamixer, and ticked the box IEC958, and just to be sure i un-muted everything.

Really happy now! Thanks guys!

---

