---
title: "Dell XPS 400"
date: 2006-08-06
forum: Installation &amp; Upgrades
---

### Post by mikimano on 2006-08-06
Hello,

I am trying to switch from Windows XP to Ubuntu. So far I like the ride however I have a few bumps. I was wondering if somebody can help.
Here are my problems:
1. i have an:
Intel 945P chipset with SigmaTel STA9220 Audio controller and Intel 82562GT 10/100 Ethernet Controller motherboard. XP was using Sound Blaster Audigy ADVANCED HD but that is software improvement as I know. I added "snd-hda-intel" to the /etc/modules file and rebooted. I still don't have sound and the microfon is not working either.

2. if i go to the device manager tells me processor unknown. i have an intel pentium D dual 3.2 GHz. Is there something specific i need to install.

3. i am running on firmware 2.6.15-26-386. Is there any firmware which would be better for me to install?

thanks for your help in advance.
Attila

---

### Post by mikimano on 2006-08-10
I found out myself in meantime the responses to it.

First of all Dell XPS 400 with Pentium dual core needs the multi processor kernel. Go to Synaptic Package Manager and select the 2.6.15-26-686 kernel. It is listed as kernel for Pentium processors and it is mentioned SMP which is support for multiprocessor.

Second: you can check if sound is installed from cat /dev/sndstat. It probably will, just as for me. Then you need to go to the voice manager (Applications-> Sound&Video-> Sound Recorder. Menu File -> Volume Control is one way to get there). In edit preferences select all tracks to be visible. Then go to each one and uncheck mute. In order to have the microfone working, you need to set capture to mic, instead of capture.

Attila

---

