---
title: "m-audio delta 44 in Ubuntu 10.04 [pulse probs]"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by nlz on 2010-05-01
Here's how I got my M-Audio delta 44 working in Ubuntu 10.04:

1.
Disable on-boad audio card in BIOS

2.
open a terminal and type:
```
sudo gedit /etc/pulse/default.pa
```

3. Find 'module-udev-detect' and 'module detect' and put # in front of the sentences so that it looks like this:

```
### Automatically load driver modules depending on the hardware available
# .ifexists module-udev-detect.so
# load-module module-udev-detect
# .else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
# load-module module-detect
# .endif
```

4.
Paste the following text in the file:
```
# Load Delta 44:
load-module module-alsa-sink sink_name=delta_out device=hw:1 channels=10 channel_map=left,right,aux0,aux1,aux2,aux3,aux4,au x5,aux6,aux7
load-module module-alsa-source source_name=delta_in device=hw:1 channels=12 channel_map=left,right,aux0,aux1,aux2,aux3,aux4,au x5,aux6,aux7,aux8,aux9
```

5.
save & quit

(DON'T CHANGE /etc/pulse/system.pa or /usr/share/alsa/cards/ICE1712.conf 

6.
reboot

good luck!

PS This thread was composed with the help of the following links:
[http://www.linuxforums.org/forum/ubuntu-help/158290-m-audio-delta-44-sound-card-problems.html](http://www.linuxforums.org/forum/ubuntu-help/158290-m-audio-delta-44-sound-card-problems.html)
[http://ubuntuforums.org/showthread.php?t=1317065](http://ubuntuforums.org/showthread.php?t=1317065)

---

### Post by yagogak on 2010-05-08
Hi nlz, 

Same problem, but your solution didn't work for me.
The sound service failed to start

any other idea?

sys / pref /sound show  Digital Surround 4 IEC958 as parameter.

thanks in advance

---

### Post by rdmiller on 2010-05-24
I've been struggling with this too, but just found a solution that works for me by adding two lines to usr/share/alsa/cards/Ice1712.conf.

[Follow picrard's instructions]("http://www.linuxquestions.org/questions/ubuntu-63/no-sound-in-ubuntu-studio-with-m-audio-delta-44-a-781558/") in green.

Hope this works for everyone else...

Rob

---

### Post by homerj742 on 2010-06-21
> **rdmiller said:**
> I've been struggling with this too, but just found a solution that works for me by adding two lines to usr/share/alsa/cards/Ice1712.conf.

[Follow picrard's instructions]("http://www.linuxquestions.org/questions/ubuntu-63/no-sound-in-ubuntu-studio-with-m-audio-delta-44-a-781558/") in green.

Hope this works for everyone else...

Rob

This did the trick for me! Thank you!

---

### Post by fleaaccela on 2010-08-27
@ NLZ

TOTALLY works! awesome! thank you so much!!!!! :KS

---

