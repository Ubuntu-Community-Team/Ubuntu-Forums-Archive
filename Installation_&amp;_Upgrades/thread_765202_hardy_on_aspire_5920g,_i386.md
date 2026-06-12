---
title: "hardy on aspire 5920g, i386"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by f76 on 2008-04-24
If anyone is using a 5920g and planning to install hardy these are my experiences so far:

1. Installation:
I used the alternate cd of the i386 distro of 8.04 without any hitches, no need for the modprobe piix trick any more. Wireless is working off the bat. Probably i could have used the standard install CD.

2. Sound not working:
I default sound is not enabled. Double click on the sound icon to get into the volume control. Under preferences enable surround,center,lfi and side. Then in the main window unmute and raise the volumes.

3. Webcam and microphones - working

4. Card reader.
So far SD-cards seem to be working fine EDIT: also sony memory cards are working.

5a. HDMI video out - Had to restart with the cable in for hardy to detect it. Then i started nvidia-settings (from repos) and could setup the screen. EDIt:
U only need to restart x (ctrl+alt+backspace) and login again..
* I now have the screen setup as side by side twinview, whenever i restart x, the gfx card flips to the correct setting..
* I just run smplayer with the video content in the laptop screen, move it into the TV output area (on the right in my setup) and double click for fullscreen

5b. HDMI audio out? does it exist on this laptop?

---

### Post by gun_p on 2008-06-17
Thanks. the part of the sound was really helpful. I didn't have sound until I took the steps. It works on the 64-bit hardy.

---

### Post by Gatemaze on 2008-08-05
> **f76 said:**
> If anyone is using a 5920g and planning to install hardy these are my experiences so far:

2. Sound not working:
I default sound is not enabled. Double click on the sound icon to get into the volume control. Under preferences enable surround,center,lfi and side. Then in the main window unmute and raise the volumes.


Hmmm yes I figured that out, but the only one that seems to be making a difference to me is the surround one... anyone knows what the above ones control? Also, I wonder which one is the subwoofer?

Regarding the builtin mic, did you tested with reconding through ekiga? Cause my recording fails despite turning mic and front mic as well as their boosts to very high levels which results into hiss noises... so i presume the mic works... I might have to run more tests and see if they indeed work and which control actually controls the mic.

---

### Post by f76 on 2008-08-16
well, for me "front mic" and "front mic boost" control the built in mics

running "amixer controls" in term will give u a good overview of the different params

---

### Post by Gatemaze on 2008-08-17
cheers... i ll check it out

---

### Post by beyboo on 2008-08-17
I got a vanilla 5920. Experience is ditto (and awesome). Can proudly say Hardy worked out of the box. The sound trick had to be used. 

The only thing which dont work for me is the scroll buttons. The 2nd touch screen which control medial controls seem to have hijacked the up-down/left-right which is kinda funny. Elsewhere there is a thread to correct this on the 5920s but I have kinda ignored this. 

The Irda port does not work, but dont care as I dont have too many IRda devices around. 

The MicroSD card reader is awesome. Coupled with the latest version of F-Spot, the whole thing rocks. 

Be sure to check out two additional things on your  5920G 
[LIST=1]
[*]** VERY IMPORTANT : The sticky for "laptop harddrive Load_Cycle_Count issue" under hardware & laptops.**

[*] Install wi-fi radar for wireless experience.
[/LIST]

Cheers !!

---

### Post by Gatemaze on 2008-08-17
cheers for the hints, which sound trick are you referring to?


for the scroll buttons, touchpad "normal" behaviour and the shiny touch media keys check the following post
[http://ubuntuforums.org/showthread.php?t=517156&page=11](http://ubuntuforums.org/showthread.php?t=517156&page=11)
and then to get an external usb mouse again
[http://www.linuxquestions.org/questions/linux-hardware-18/external-usb-mouse-not-working-on-acer-5920g-662455/](http://www.linuxquestions.org/questions/linux-hardware-18/external-usb-mouse-not-working-on-acer-5920g-662455/)

---

### Post by beyboo on 2008-08-17
> **Gatemaze said:**
> cheers for the hints, which sound trick are you referring to?


for the scroll buttons, touchpad "normal" behaviour and the shiny touch media keys check the following post
[http://ubuntuforums.org/showthread.php?t=517156&page=11](http://ubuntuforums.org/showthread.php?t=517156&page=11)
and then to get an external usb mouse again
[http://www.linuxquestions.org/questions/linux-hardware-18/external-usb-mouse-not-working-on-acer-5920g-662455/](http://www.linuxquestions.org/questions/linux-hardware-18/external-usb-mouse-not-working-on-acer-5920g-662455/)

have to use the "surround" option to make the speakers have some life. that one.

---

### Post by Gatemaze on 2008-08-18
ah yes, i was ok with the surround.... regarding the load-cycles, does your 5920g suffer from it? what hdd model and specs have you got if i may ask? cheers.

---

### Post by f76 on 2008-08-21
seems a little to advanced to be neccesary... Im gambling and letting the HD settings be..

---

