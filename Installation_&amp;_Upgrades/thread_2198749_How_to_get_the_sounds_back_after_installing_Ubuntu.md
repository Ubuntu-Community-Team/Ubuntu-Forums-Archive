---
title: "How to get the sounds back after installing Ubuntu 13.10 Saucy Salamander"
date: 2014-01-10
forum: Installation &amp; Upgrades
---

### Post by still_learning_to_ on 2014-01-10
...on Fujitsu Siemens Amilo La 1703?

I'm a total beginner so I could really use some guidance. I've tried following some threads online but until now I've only managed to make my sound icon disappear from the top panel. It didn't show any options when I checked it before, not even the 'dummy output' some of the sound retrieval instructions mentioned. 
It's been a few weeks since this problem came to be, 

This is what I tried first: [http://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/](http://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/)
Maybe after that the sound icon vanished, not sure.

I checked at the terminal with the commandment "sudo aplay -l" and got the answer:

**** List of PLAYBACK Hardware Devices **** card 0: VT82xx [HDA VIA VT82xx], device 0: VT1708 Analog [VT1708 Analog]   Subdevices: 1/1   Subdevice #0: subdevice #0 card 0: VT82xx [HDA VIA VT82xx], device 6: Si3054 Modem [Si3054 Modem]   Subdevices: 1/1   Subdevice #0: subdevice #0

I checked if my Via High Definition sound card was supported by alsa
"
7. Is my sound card supported by the Ubuntu sound system?

Ubuntu  uses the Advanced Linux Sound Architecture (ALSA) for managing sound  output. There is a listing of all of the sound cards supported by ALSA  at [http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)  . You should look for the information that was listed by the command in  the previous step. If it happens that your sound card is not supported  by ALSA, you have two options: obtain a new sound card that is supported  by ALSA, or contact the ALSA developers and request support for your  sound card. 
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-VIA](http://www.alsa-project.org/main/index.php/Matrix:Vendor-VIA)


I got an answer in terminal that recognized some via soundcards when I checked them according to some other guided tour.

I also run alsamixer and changed AUTO-MUTE MODE from ENABLE to DISABLE. Didn't help.

I did a lot of other things I can't recall now, but I'll try and find out more about them.

So, where could I even begin again?

Thank you, I so appreciate your advice!

---

