---
title: "Sound Problem"
date: 2009-05-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Clifweb on 2009-05-15
Hi, Totem Movie player and Rhythmbox Music Player the audio works but using the vlc or a flash inside a web site the SB Live/Analog/Digital Output Jack: is changed resulting in a noise instead of the actual volume. I don't have digital speakers normal analog. y is this changing when I play audio from different source and how can I force it to always use analog output

I tried a video in youtube no audio come up. 
System > Preferences > Sound and clicked on test it worked.

My card Create Sound Blaster live 5.1

---

### Post by Clifweb on 2009-05-27
Is their a way to prevent my sound card from switching to digital output?

---

### Post by psyke83 on 2009-05-27
> **Clifweb said:**
> Is their a way to prevent my sound card from switching to digital output?

Install the package pavucontrol (PulseAudio Volume Control), run it, and click the Configuration tab.

---

### Post by Clifweb on 2009-05-27
That stoped I think the vlc and firefox to switch to digital output.

I switched VLC to use AlSA output since Defualt was giving me no output.

PulseAudio Volume Control: Configuration tab I selected Output Analog 5.1 + Input Analog Mono.

FireFox no sound and UBuntu themes no sound as well.

IN sound preferenves all output are using ALSA Playback

---

### Post by jocko on 2009-05-27
> **Clifweb said:**
> IN sound preferenves all output are using ALSA Playback
Set everything to use pulseaudio instead, then make sure pulseaudio is set to use the analog output.

---

### Post by ranch hand on 2009-05-27
I have had more luck getting that straight is using the alsa mixer.  I am using Ubuntu (Gnome) and find that if I have that set everything works fine.

Alsa-gnome may need installed.

---

### Post by Clifweb on 2009-05-28
10x Now everything is working perfectley. All should be using ALSA.

---

### Post by MilesRdz on 2009-05-29
I still have an issue with this. I get a bunch of static no matter what program I use (Realtek HD audio).

---

### Post by taavikko on 2009-05-29
> **MilesRdz said:**
> I still have an issue with this. I get a bunch of static no matter what program I use (Realtek HD audio).

Realtek HD-audio isn't piece of hardware, mearly a common naming for windows
like AC'97 

Please post the output of "aplay -l ; aplay /usr/share/sounds/question.wav"
That gives the chipset in use, and tries to play file question.wav through alsa.

---

### Post by ranch hand on 2009-06-14
I had problems with low volume in A1-32 with my audigy1 5.1 card.

A2-64 is fine.

---

