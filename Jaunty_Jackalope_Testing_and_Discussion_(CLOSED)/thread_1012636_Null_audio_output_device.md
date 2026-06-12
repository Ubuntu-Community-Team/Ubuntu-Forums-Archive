---
title: "Null audio output device"
date: 2008-12-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starks on 2008-12-16
Why is my Intel audio only working sporadically as of late?

I don't understand why I now find myself reinstalling the kernel on a daily basis.

---

### Post by Starks on 2008-12-18
Anyone else experiencing this?

---

### Post by iason86 on 2008-12-18
i have another issue with the audio. when i first installed ubuntu i had no problem but today i can't hear sounds from youtube or any other falsh and also cant talk on skype! does any1 have an idea? is there a application to control the sounds?

---

### Post by DPic on 2009-02-25
After an upgrade and reboot i am now getting the same error. If i click on the volume applet and open volume control, the only devices are "Playback: Null Output (PulseAudio Mixer)" and "Capture: Monitor of Null Output (PulseAudio Mixer)"

---

### Post by mc4100 on 2009-02-25
> **DPic said:**
> After an upgrade and reboot i am now getting the same error. If i click on the volume applet and open volume control, the only devices are "Playback: Null Output (PulseAudio Mixer)" and "Capture: Monitor of Null Output (PulseAudio Mixer)"

Seeing the same thing: this works around the problem (at least for me)
```
killall pulseaudio; sudo pulseaudio --system
```


Edit: I'm testing 0.9.15, and I think Luke's PPA (~themuso) was just updated. I assume everyone else is in the same boat?

---

### Post by taavikko on 2009-02-25
> **DPic said:**
> After an upgrade and reboot i am now getting the same error. If i click on the volume applet and open volume control, the only devices are "Playback: Null Output (PulseAudio Mixer)" and "Capture: Monitor of Null Output (PulseAudio Mixer)"

Having same problem, related to [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/330814](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/330814) ?

Err... Have only these two present:
HDA Intel (alsa mixer)
Analog Devices (oss mixer)

PA dies randomly

Haven't tried making PA system service rather than per-user
If that would fix this issue...

---

### Post by Sand &amp; Mercury on 2009-02-25
After today's updates I am also no longer getting any sound.

---

### Post by zenarcher on 2009-02-25
Same here.  After today's updates, I have no sound and also get the null message with PulseAudio.

Cheers,
zenarcher

---

### Post by yelo3 on 2009-02-25
I see this when starting pulseaudio:
```
E: alsa-util.c: Error opening PCM device hw:0: Nessun file o directory
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0 tsched=0"): initialization failed.
E: alsa-util.c: Error opening PCM device hw:0: Nessun file o directory
E: module.c: Failed to load  module "module-alsa-source" (argument: "device_id=0 source_name=alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0 tsched=0"): initialization failed.
```

---

### Post by frasch on 2009-02-25
Hi,
add your username to group audio. Sound will work afterwards

Frank

---

### Post by fut21 on 2009-02-25
> **frasch said:**
> Hi,
add your username to group audio. Sound will work afterwards

Frank

How?

---

### Post by frasch on 2009-02-25
Hi,
```
sudo adduser <username> <groupnname> 
```
example:
```
sudo adduser tom audio
```
or use systemsettings on gnome btw. kuser on kde

Frank

---

### Post by plun on 2009-02-25
> **frasch said:**
> Hi,
add your username to group audio. Sound will work afterwards

Frank

Thanks,  works just fine but I must also create a audio group

(Menu System > administration > Users & groups)

---

### Post by Sand &amp; Mercury on 2009-02-25
> **frasch said:**
> Hi,
```
sudo adduser <username> <groupnname> 
```
example:
```
sudo adduser tom audio
```
or use systemsettings on gnome btw. kuser on kde

Frank
Worked like a charm. Thanks for the tip!

---

### Post by fut21 on 2009-02-25
> **Sand & Mercury said:**
> Worked like a charm. Thanks for the tip!

Same here:-)

---

### Post by DPic on 2009-02-25
> **frasch said:**
> Hi,
```
sudo adduser <username> <groupnname> 
```
example:
```
sudo adduser tom audio
```
or use systemsettings on gnome btw. kuser on kde

Frank

Okay so that gives me back all my audio devices, and this time i heard the start up sound after logging in (not just the sound to prompt entering my username and password), but i still have no sound after that. Any ideas?

---

### Post by TrueTom on 2009-02-25
sudo killall pulseaudio

---

