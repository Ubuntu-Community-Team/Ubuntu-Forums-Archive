---
title: "System check came up with several fails/ Graphics card issues"
date: 2014-02-12
forum: Installation &amp; Upgrades
---

### Post by Kaitlyn_Milspaw on 2014-02-12
I'm super noob at Linux and I have a dell with an intel graphics card, and I'm running Ubuntu 13.10. I'm not sure what information is important, but these are my fails on my systems check, so if anybody could tell me how to fix them, please.
-audio_record_playback_external
-audio_record_playback_internal
-camera/display
-graphics/display
-graphics/driver_version Error:No driver loaded! Possibly in failsafe mode!
-keys/media_control
-optical/read_sr0
As for my graphics card issue, I think I'd find it in System Settings/Softwear & Updates/Additional Drivers, but nothing is there and no proprietary drivers are in use. If someone could point me in the direction to find my graphics card and see if it's up to date, that'd be great. If you need more info, I'll try my best to provide it. 
~Thank you.
      Edit: I'm having issues getting my League of Legends to play via PlayOnLinux. I've downloaded Wine and League, but when I go to log in, I keep getting Connection Error: Unable to connect to PVP.Net. I've checked forums for help. I found something that almost worked except I have a 64-bit and the help was for a 32-bit. I'm at a loss.
deb [http://ppa.launchpad.net/s-elser/winelol/ubuntu](http://ppa.launchpad.net/s-elser/winelol/ubuntu) precise main

---

### Post by bc.haynes on 2014-02-12
Lets see what graphics card you do have. Enter in Terminal:
```
lspci | grep VGA
```

---

### Post by Kaitlyn_Milspaw on 2014-02-12
Intel Coproration 2nd Generation Core Processor Family Integrated Graphics Controller
NVIDIA Corporation GF108M [GeForce GT 525M] (rev a1)

---

