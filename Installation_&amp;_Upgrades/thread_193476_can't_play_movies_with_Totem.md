---
title: "can't play movies with Totem"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by rreyes3000 on 2006-06-10
I cannot play movies with totem. I get a "Totem could not play 'dvd:///media/cdrom0'" Message. The other message was that I do not have the needed plugins. 

Any suggestions?

---

### Post by FredB on 2006-06-10
[QUOTE=rreyes3000]I cannot play movies with totem. I get a "Totem could not play 'dvd:///media/cdrom0'" Message. The other message was that I do not have the needed plugins. 

Any suggestions?[/QUOTE]

I can only answer the second part. Launch Synaptic, and activate universe and multiverse repositories.

After having done that, search for gstreamer plugins bad and ugly. Install them both, and I think you'll get the codecs you need. Your ubuntu will also plays MP3 ;)

Hope it helps !

---

### Post by rreyes3000 on 2006-06-10
Man! I am not having any luck. I cant get wifi, usb ports, and watch movies. 

I did as suggested and I still get the same error. I have been losing so much sleep and spending money on linux just to make the switch over from windows. I am starting to have my doubts. 

Any other ideas?

---

### Post by ubuntu27 on 2006-06-10
[QUOTE=rreyes3000]I cannot play movies with totem. I get a "Totem could not play 'dvd:///media/cdrom0'" Message. The other message was that I do not have the needed plugins. 

Any suggestions?[/QUOTE]


Check this website for instructions on how to install Codecs: 

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

So, it seems to me that you need "libdvdcss2" to play your video (I am assuming you're trying to play a DVD).

Again, everything you need is here: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)  ;)

---

