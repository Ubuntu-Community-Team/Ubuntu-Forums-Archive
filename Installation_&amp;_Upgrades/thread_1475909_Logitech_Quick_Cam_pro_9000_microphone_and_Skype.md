---
title: "Logitech Quick Cam pro 9000 microphone and Skype"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by Hamletriveroftime on 2010-05-07
Hello,nice to meet you all. It has been a long time i dreamed to get ubuntu and now i have my ubuntu 10.04 installed. I am a very beginner and i have a problem i hope you could possibly help me to fix. I found similar posts in the forum but no one helped me out.
i have a webcam Logitech quick cam pro 9000 and i tried to use it with skype 2.1 beta 2 i installed this morning. Well i can see the video but the microphone (build in the webcam ) does not work at all and it worked fine with windows.  This is the lsusb command in the terminal :

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

So i think the webcam is connected well.
Thank you for your help and attention in advance.

---

### Post by wackston on 2010-06-26
I'm afraid I can only give you negative "help".  I have a pro 9000 and although the mike seemed to work nicely under 9.10 with skype its unusable with skype under 10.04.

At a guess is some kind of version dependency in the way the alsa beta hooks up to pulse audio or an old-fashioned oops in the relevant driver.

Since the mike seems to work fine with other tools via oulse its probably the former.  Most likely it will 'self-fix' if an when skype bring out an updated linux release...

---

### Post by wackston on 2010-06-26
I of course meant ...  the way *skype* hooks ... ;-)

---

### Post by dfehrer on 2011-05-05
I have an older Quickcam (e2500, I think it's a Connect) that I got working with Skype: both the video and the camera's mic.

I'm pretty new to Ubuntu, so sorry if what I'm posting here is obvious and you already tried it and it didn't work.  

In Skype I went to Options > Sound Devices. In my version, the "Microphone", "Speakers", and "Ringing" dropdowns just say, "PulseAudio server (local)", and there are no other options.  There's a little "i" box though that says I have to use my "Desktop Manager volume control or PulseAudio volume control" to adjust the settings.

Well, I opened the desktop volume control (speaker with soundwaves in the upper right) went to "Sound Preferences", and then the "Input" tab and turned up the "Input volume" and clicked the button for "QuickCam E2500 Series Analog Mono" (maybe yours says QuickCam 9000 something).  Then I went back to Skype and did a test call and it worked!  Kind of funny that it was that simple.  

Hope this works for you or helps some other noobs like myself.

---

