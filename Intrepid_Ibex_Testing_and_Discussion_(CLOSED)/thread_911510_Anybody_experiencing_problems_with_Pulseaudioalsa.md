---
title: "Anybody experiencing problems with Pulseaudio/alsa?"
date: 2008-09-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by cantas on 2008-09-05
Hello,
since an upgrade that occurred a couple of days ago, I have no audio with Pulseaudio or Alsa. I have to use OSS in order to listen to any music or sound.
I have an nVidia MCP67 High Definition Audio (snd_hda_intel) and all the modules are up and running.

Stefano

---

### Post by taavikko on 2008-09-06
You'll may need to give an extra option to that card.
```
sudo modprobe snd-hda-intel model=acer
```

if above works, put it in /etc/modprobe.d/alsa-base
```
echo 'options snd-hda-intel model=acer' | sudo tee -a /etc/modprobe.d/alsa-base
```

---

### Post by cantas on 2008-09-06
It was working perfectly though. And my notebook is not an acer, but a compaq.

---

### Post by taavikko on 2008-09-07
> **cantas said:**
> It was working perfectly though. And my notebook is not an acer, but a compaq.

Did the above work?

Model=XX it doesn't matter if you have compaq notebook.
it's hardware related, not vendor


Like on acer 1 subnotebook, sound to work after sudpend, you have to 
use model=toshiba :lolflag:

---

### Post by cantas on 2008-09-07
problem solved, it was because i had installed a newer version of pulseaudio from a PPA that screwed things up in my system. I had to completely wipe out all the configuration files and install the default pulseaudio server. Now it is working.


Thanks
Stefano

---

