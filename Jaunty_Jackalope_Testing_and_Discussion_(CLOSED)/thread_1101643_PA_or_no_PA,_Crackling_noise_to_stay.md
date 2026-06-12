---
title: "PA or no PA, Crackling noise to stay"
date: 2009-03-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Flag on 2009-03-20
As info, as ????, or maybe someone can do something with it.
The machine is an Acer Aspire 7520 with ALC 268 Analog.
The harddisk has three partitions: OS1, OS2 and Home.
OS1 = 8.04, OS2 = 9.04, both up to date, 9.04 freshly installed and updated upto today.

On the 8.04 PA has not been disabled, all works well, also Skype. There was no need to add, change or remove anything in eg " pulse-daemon " or " alsa-base " Sound in preferences is set at " autodetect " minus Capture which is set at " ALC analog " Skype settings are all " hw:NVIDIA,0 "
Though different settings have been tried and are OK, both in prefs. and Skype.

Trying since alpha 2.
On the 9.04 with PA enabled, I had to add to " alsa-base.conf " the line snd-hda-intel model=auto, tried model=acer as well, to get the built in mic working, but that did not work.
Fiddled with different settings both in Skype's options menu as in preferences -> sound. No avail, test calls come back with an incredible crackling and static noise.
I have no intention to remove PA once 9.04 is final, though I need Skype and most probably I won't need all possibilities PA offers. 
Just to try out I removed PA today and installed esound, adjusted all sound settings in preferences -> sound and Skype options.
After reboot tried Skype again, not much improvement though I can hear my own voice now through a lot of crackling, static noise.

The bottomline of this story is, Why in 8.04 with PA all is well and why not in 9.04 ? I have the feeling at this moment it has more to do with the soundcard not appreciated by 9.04, rather then to seek it in PA.

Does anyone have simular experiences, if so, was it solved ?

Thanks

---

