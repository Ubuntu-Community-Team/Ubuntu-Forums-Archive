---
title: "Jaunty Jackalope not detecting audio jack"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Ukato7 on 2009-03-30
Hello, I am currently running Ubuntu 9.04 on my Vaio FZ190.  I can get pretty much everything working and the updates keep making everything better.  However, I can't seem to get the system to detect my audio jack because it will just play through the speakers even when something is plugged into the jack.  I have a feeling that the jack may be on a separate board other the the mother board and the system, for whatever reason, is just ignoring that connected circuit.  
I won't say I am a master programmer, but I program in C++, so I was just wondering if anyone had any suggestions to the problem or if someone could tell me where the system code files are that control hardware detection.  I'd at least like to look at the code and see if I can fix it.  Of course that probably entails a lot more than what I'm capable of as of right now.  I would probably need to know how the system assigns hardware addresses and figure out how to get Ubuntu to look at a specific circuit in order to use it.  I really don't know.

Any helpful comments would be appreciated.

Cory

---

### Post by Astrak on 2009-04-17
I had to add the following line to /etc/modprobe.d/snd-hda-intel.conf in order to make the headphone plug to work:

```
options snd-hda-intel model=vaio
```

If the file does not exist create it with just the line above in it.

Best Regards.

---

### Post by danwood76 on 2009-04-17
You can normally check a 'switch' in the volumes control panel to enable this behaviour, sometimes you have to enable the switch by click the preferences.

To get that up right click the volume control in the task bar and click 'Open volume control' you may need to add the volume applet to the bar also.

---

