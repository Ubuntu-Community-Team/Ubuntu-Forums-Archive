---
title: "Skype+pulseaudio - anyone?"
date: 2009-04-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Stetzen on 2009-04-09
I'm experiencing an unpleasant bug with skype if it works through pulseaudio. Skype process uses my CPU at 100% if sound is playing and sound disappears after some time. I haven't seen this with 8.10, and it is annoying... Has anyone make skype to work with jaunty?

---

### Post by boteeka on 2009-04-09
I experience the same, and unfortunately I didn't found a solution to it either.
It would be very kind if some Ubuntu Guru would be so nice and gave us some explanation (if there is one).

---

### Post by olskar on 2009-04-09
This might work [http://www.pulseaudio.org/wiki/PerfectSetup#Skype](http://www.pulseaudio.org/wiki/PerfectSetup#Skype)

---

### Post by FuturePilot on 2009-04-09
I have the same problem. Though I'm not sure if it's PulseAudio that's at fault here. I had no problems with it in Intrepid. The process that's taking up the all the CPU usage is actually Skype. Seems to be some other people with this problem too. [http://forum.skype.com/index.php?showtopic=306381]("http://forum.skype.com/index.php?showtopic=306381")

---

### Post by hexion on 2009-04-09
For me the solution was to install skype-static-oss from the medibunto repositories:

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

Remove skype and install skype-static-oss.

---

### Post by Stetzen on 2009-04-09
I've tried to use oss skype via padsp, an the quality of my speech which other person heard was terrible. Actually, it looks like pasdp microphone is broken in jaunty, because I had similar problem with gizmo5 as well.

---

### Post by Stetzen on 2009-04-10
> **olskar said:**
> This might work [http://www.pulseaudio.org/wiki/PerfectSetup#Skype](http://www.pulseaudio.org/wiki/PerfectSetup#Skype)

Thank you very much! I've solved the problem. I've created ~/.asoundrc file which looks like this:

```
# Part I directly from ALSA Dmix Wiki

pcm.paul { # paul is my name, you can use your name, just make sure you use it below too
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:0,0"     
        period_time 0
        period_size 1024
        buffer_size 8192
       #format "S32_LE"
       #periods 128
        rate 44100
    }
}

pcm.dsp0 {
    type plug
    slave.pcm "paul"
}

# This following device can fool some applications into using pulseaudio
pcm.dsp1 {
    type plug
    slave.pcm "pulse"
}

ctl.mixer0 {
    type hw
    card 0
}


pcm.pulse { type pulse }
ctl.pulse { type pulse }
pcm.!default {
    type pulse
}

ctl.!default {
    type pulse
} 

```

Unfortunately, I cannot fully understand, what all this stuff means, but it works!

---

### Post by hanzomon4 on 2009-04-10
Never had any problems with it... but I just tested it and yeah... cpu is up to 97%

---

### Post by Polygon on 2009-04-10
i dont get 100% cpu with skype and pulse, i just tried it last night

---

