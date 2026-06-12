---
title: "No HMDI audio after upgrade to 14.04 [x-post from /mythbuntu]"
date: 2014-12-14
forum: Installation &amp; Upgrades
---

### Post by Denis_Papathanasio on 2014-12-14
I upgraded my mythbuntu machine to 14.04 via the update manager.

I experienced many of the same problems Paul Rubin described here: [http://orinanobworld.blogspot.com/2014/08/mythbuntu-upgrade-from-hell.html](http://orinanobworld.blogspot.com/2014/08/mythbuntu-upgrade-from-hell.html)

But even after resolving all the other issues, I cannot get digital sound via HDMI (analog does work, though).

Here's a snapshot of my alsa data: [http://www.alsa-project.org/db/?f=5853563c300e39bea5fbdde8d53e1c63511da36d](http://www.alsa-project.org/db/?f=5853563c300e39bea5fbdde8d53e1c63511da36d)

Any help would be appreciated!

---

### Post by SeijiSensei on 2014-12-15
Try installing **pavucontrol** and see if it enables you to switch among your audio outputs.

---

### Post by Denis_Papathanasio on 2014-12-15
Thanks for replying.

The "pavucontrol" package is already installed, and is the latest version, according to apt.

What's frustrating is that prior to upgrading, I could see "HDMI" as a choice separate from the "Built in Audio" options.

Now, only the "Built in Audio" options are there, and there's only one digital option -- Digital Stereo (IEC958) Output -- but that does *not* correspond to the hdmi cable and speakers.

---

### Post by Bucky Ball on 2014-12-15
Yep, had the same issue on an xfce4 14.04 LTS install I did for a friend awhile ago. No hdmi option in Pavucontrol. I never got to the bottom of, so will be watching this with interest. 

I will be having another go at it when I get back from xmas stuff, so will add any discoveries I make then (unless you get to the bottom of this first). ;)

Good luck.

---

### Post by Denis_Papathanasio on 2014-12-15
At this point, I'm thinking of just backing up my media and downgrading back to Mythbuntu 12.04.3.

It was running just fine.

I regret clicking the "upgrade to 14.04" button which had been popping up for weeks; I should have just continuied to ignore it...

---

### Post by SeijiSensei on 2014-12-17
Have you installed the proprietary driver for your video card if you have an ATI or NVIDIA adapter?  That's often required to get HDMI audio to function properly.

---

### Post by Denis_Papathanasio on 2014-12-17
Yes, I was using the proprietary driver (my video card is nvidia) before I upgraded.

The frustrating thing is that the hardware is exactly the same, and it was all functional under the previous version.

---

### Post by Denis_Papathanasio on 2014-12-31
This is now working; fixing it was a pain, but here are the steps, in case anyone else has the same problem.

First, I installed the alsa-daily ppa:

```

  sudo apt-add-repository ppa:ubuntu-audio-dev/alsa-daily
  sudo apt-get update
  sudo apt-get install oem-audio-hda-daily-dkms
```

Then, I used alsamixer which showed an alternative to the default IXP (analog) output.

There were four "S/PDIF" settings (S/PDIF, S/PDIF1, S/PDIF2, S/PDIF3) all of which were muted (set to "MM"), which I enabled (setting to "00") by typing "m" while scrolling through them.

Next, I ran this:

```

  aplay -L | more
```

which (finally) showed the NVidia HDMI card among the list of possibilities:

```

plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
```
  
Next, I tried each by trial and error:

```

  aplay -D plughw:CARD=NVidia,DEV=3 /usr/share/sounds/alsa/Front_Center.wav
  aplay -D plughw:CARD=NVidia,DEV=7 /usr/share/sounds/alsa/Front_Center.wav
  aplay -D plughw:CARD=NVidia,DEV=8 /usr/share/sounds/alsa/Front_Center.wav
  aplay -D plughw:CARD=NVidia,DEV=9 /usr/share/sounds/alsa/Front_Center.wav
```

For me, this combination was the only one that worked:

 ```
plughw:CARD=NVidia,DEV=7
``` 

So back in the MythFrontend application, I went to **Setup** -> **Audio** and in the **Audio output device** input field, I scrolled until I found ```
plughw:CARD=NVidia,DEV=7
```

Success!

What I still don't understand, though, is why pavucontrol shows just "Built-in Audio".

Before upgrading, the same exact hardware and proprietary nvidia driver (331) showed up as a distinct "HDMI Audio" option in pavucontrol.

I could just pick that, and not have to mess around with aplay or changing the preferred audio device in the MythFrontend app.

---

