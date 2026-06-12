---
title: "No Sound - RealTek ACL658 AC'97 Output through s/pdif optical out"
date: 2006-03-21
forum: Installation &amp; Upgrades
---

### Post by elalamm on 2006-03-21
Hello Guys,

I just did an install of Ubuntu... went flawlessly... Breezy 5.10

I think I love this distro... but I have one main problem before I can completely switch over from XP... 

I have no sound...

I use a gigabyte motherboard and use the onboard sound Realtek AC'97 ACL658 I believe... but I use the optical output which goes into my receiver that plays my music...

I don't know if my sound is not working because of my setup or if its because its not configured properly...

I checked alsamixer and made sure that everything was unmuted... still no resolution...

I started totem as root to ensure it wasn't a permission problem... still no resolution...

I am using ESD... but also tried using ALSA in system -preferences - multimedia center... still no resolution...

I am really not sure where to go with this... I did some reading... but not sure what it could be...

Any help would be greatly appreciated... 

Thanks Everyone...

---

### Post by tuxinvader on 2006-03-21
In my experience spdif is always a pain! 

The most common cause of not having any sound is the IEC958 playback control. It should be unmuted, but the volume should be right down to 0. 

On all my systems that use spdif, once I have it working I back up asound.state file, it's in /var/lib/alsa/asound.state on Ubuntu. That way if anything changes the settings (ogle does for example) I can copy the backup back.

---

