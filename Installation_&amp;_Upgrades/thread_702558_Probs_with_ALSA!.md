---
title: "Probs with ALSA!"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by alexmoerch on 2008-02-20
Hi there..
Im new to Ubuntu (7.10 Studio), but have used a little week on getting in to the stuff.. It works just great, though I haven't had any luck on installing my soundcard (EMU 1212m).
I have now tried following two different guides, but no luck. The last one, the most simple one I tried on my fully updated system:

$ sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source

$sudo dpkg-reconfigure alsa-source

$sudo module-assistant a-i   alsa-source

It seems to work out great, until it closes down the module-assistent and says the following:

You should now stop all applications using sound devices 
and reload all ALSA sound modules.

And then I write the following to check:

$ aplay -l
aplay: device_list:204: no soundcards found...

Please help, dont know what to do :confused:

Regards Alex

---

### Post by alexmoerch on 2008-02-22
Bump :guitar:

No ideas, anyone?

---

