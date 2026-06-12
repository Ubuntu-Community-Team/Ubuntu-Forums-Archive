---
title: "Ubuntu 17.04 Intel 7th Gen NUC - no hdmi audio"
date: 2017-04-22
forum: Installation &amp; Upgrades
---

### Post by manicminer on 2017-04-22
Hi all,

I've got a shiny new Kaby Lake (7th Gen) intel NUC to be the new media centre - yay!

I've put 17.04 on there as I'd read this was the best bet for the brand new chips, however I've got a huge problem that is no audio over HDMI :(. It works fine when I plug headphones in, audio output works, it just doesn't come out over the HDMI cable (which works fine, same cable and TV port with the old media centre).

I found some instructions here:

[http://www.intel.com/content/www/us/en/support/boards-and-kits/000005499.html](http://www.intel.com/content/www/us/en/support/boards-and-kits/000005499.html)

Which suggested I needed the  oem-audio-hda-daily-dkms package, but those don't seem to exists for 17.04 yet.

Any guidance as to how to get HDMI Audio working would be greatly appreciated.

---

### Post by SuperFreak on 2017-04-22
Not sure if this helps but I had no sound with HDMI in Mint

I solved in this way:
sudo gedit /etc/pulse/default.pa
commented this line --> load-module module-switch-on-port-available
Saved
Switched my headphone jack from front-panel to back motherboard port and then reboot. Now it works fine.
[https://ubuntuforums.org/archive/ind...t-2321631.html](https://ubuntuforums.org/archive/ind...t-2321631.html)

---

### Post by manicminer on 2017-04-23
> **SuperFreak said:**
> Not sure if this helps but I had no sound with HDMI in Mint

I solved in this way:
sudo gedit /etc/pulse/default.pa
commented this line --> load-module module-switch-on-port-available
Saved
Switched my headphone jack from front-panel to back motherboard port and then reboot. Now it works fine.
[https://ubuntuforums.org/archive/ind...t-2321631.html](https://ubuntuforums.org/archive/ind...t-2321631.html)

Nope, no luck with that either :(

---

### Post by Maarten1112 on 2017-05-28
Same issue here, bought intel NUC7i7BNH, upgraded from ubuntu 16.04 to 17.04 and HDMI is causing problems. I did follow everything from [https://askubuntu.com/questions/834731/how-can-i-get-hdmi-sound-to-work-in-16-04](https://askubuntu.com/questions/834731/how-can-i-get-hdmi-sound-to-work-in-16-04).
1. Alsamixer, unmuted all. I have only sound through S/PDIF digital audio output. So Spotify works and system sounds work. But no VLC or Youtube.

When I start VLC or youtube, the sound is gone and I need to restart ubuntu to get sound again. Really annoying this. Please help!

---

### Post by Saunter on 2017-06-20
Ditto.  Just loaded Kubuntu 17.04 into my newly arrived NUC and no HDMI audio.  Headphones work fine.  Someone needs to solve this!

---

### Post by jmj23 on 2017-06-22
Same problem with my Asus gaming laptop with i7 7700 chip. HMDI output not appear in sound selector. I only can use jack output.

---

### Post by Saunter on 2017-06-22
After trying many ideas, I unplugged my monitor with internal speakers, and plugged in my HD bigscreen TV.  Suddenly the audio started working!  When I plugged my monitor back in, it worked too!  But on the next reboot, it quit working again.  Mystified!

---

### Post by Tadaen_Sylvermane on 2017-06-23
Had this problem awhile back. I returned the nuc and built a custom mini pc for my media centers. Never did figure it out. Still loiking for solution as well for future medua centers in my house. Nucs are awesome.

---

