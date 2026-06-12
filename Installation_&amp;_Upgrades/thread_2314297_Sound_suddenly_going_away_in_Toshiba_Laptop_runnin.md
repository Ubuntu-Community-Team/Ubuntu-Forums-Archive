---
title: "Sound suddenly going away in Toshiba Laptop running only 14.04 LTS"
date: 2016-02-20
forum: Installation &amp; Upgrades
---

### Post by sougata on 2016-02-20
Dear All, 

I am suddenly facing this peculiar issue with my sound. Mine one is Toshiba Satellite series laptop and running only Ubuntu 14.04 LTS. I just installed this new LTS version some weeks ago. Everything was running smoothly till last week when all of a sudden the sound is going away. The laptop speaker is not providing any sound at all but strangely i can listen using headphones. If i restart my laptop the sound comes back. It may stay for long or may go away suddenly again and this thing is not stopping at all. When i run the below command it shows me this, 

sougata@sougata-SATELLITE-L750:~$ sudo aplay -l
[sudo] password for sougata: 
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CX20585 Analog [CX20585 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I am going through different posts but couldn't find any specific solution to my problem. 

Need kind help from anyone who is expert in this matter, 

Regards, 

Sougata

---

### Post by justen_m on 2016-02-21
Is this sound problem related to your computer going to sleep? I've got a system that if it goes to sleep, there is no sound when it wakes. I have a workaround that fixes it... cut'n'paste... For me too, the pc speaker stops working, but headphones still work.

#!/bin/sh
# put this in a new file in /etc/pm/sleep.d/
# fixes the problem on hpz400 and hpxw8400 of no sound after resume from sleep


/usr/bin/amixer set Master mute
/usr/bin/amixer set Master unmute
/usr/bin/amixer set PCM unmute
/usr/bin/amixer set Speaker unmute
/usr/bin/amixer set Headphone unmute
/usr/bin/amixer set Master 2dB+

---

### Post by sougata on 2016-02-26
Hi [COLOR=#000000]justen_m, 

Sorry for my late reply to your response. I really appreciate you replying to my thread.
In my case its not happening only when laptop goes to sleep. It happening randomly. Like i start my laptop sound is coming out from laptop speakers and then suddenly goes way. Then i have to put on headphones. If i suspend my laptop for some time and start it again sound comes back. But doesn't stay for long... goes away again ... It has suddenly started since last 2 weeks.

Cheers, 

Sougata[/COLOR]

---

