---
title: "Solved skype working with pulseaudio 0.9.15 on 64-bit"
date: 2009-04-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by vlovich on 2009-04-20
Those of you who used themuso's ppa will have noticed that skype & wine will not work with the updated libraries.

/usr/bin/skype relocation error: /usr/bin/skype: symbol snd_pcm_hw_params_get_channels_min, version ALSA_0.9.0rc4 not defined in file libasound.so.2 with link time reference

This hack allows skype to startup & use alsa.  What I did was to grab the i386 packages from [https://edge.launchpad.net/~pgquiles/+archive/ppa]("https://edge.launchpad.net/~pgquiles/+archive/ppa") 

[https://edge.launchpad.net/~pgquiles/+archive/ppa/+files/libasound2_1.0.19-0ubuntu0~pgquiles2_i386.deb]("https://edge.launchpad.net/~pgquiles/+archive/ppa/+files/libasound2_1.0.19-0ubuntu0~pgquiles2_i386.deb")

[https://edge.launchpad.net/~pgquiles/+archive/ppa/+files/libasound2-plugins_1.0.19-0ubuntu0~pgquiles1_i386.deb]("https://edge.launchpad.net/~pgquiles/+archive/ppa/+files/libasound2-plugins_1.0.19-0ubuntu0~pgquiles1_i386.deb")

& install those (I think the i386 ones from themuso's ppa would also work).  I couldn't figure out how to get the alsa-lib modules to load (even mounting /usr/lib32/alsa-lib on /usr/lib/alsa-lib didn't work, so it's an issue with the linking within alsa).

```

wget https://edge.launchpad.net/~pgquiles/+archive/ppa/+files/libasound2-plugins_1.0.19-0ubuntu0~pgquiles1_i386.deb
wget https://edge.launchpad.net/~pgquiles/+archive/ppa/+files/libasound2_1.0.19-0ubuntu0~pgquiles2_i386.deb
dpkg -x libasound2_1.0.19-0ubuntu0~pgquiles2_i386.deb asound_tmp/
dpkg -x libasound2-plugins_1.0.19-0ubuntu0~pgquiles1_i386.deb asound_tmp/
sudo mkdir /usr/lib32/asound.bkp
sudo mv /usr/lib32/libasound* /usr/lib32/alsa-lib /usr/lib32/asound.bkp
sudo cp -r asound_tmp/usr/lib/* /usr/lib32/
sudo ldconfig

```

Startup skype.  Change from pulse to your alsa card.  Same restrictions as before when running alsa & pulse side-by-side (only 1 can use it at a time).

**UPDATE:**
Pulseaudio microphone works (useful when combined with workaround to boost microphone volume when using skype that is only available with pulse)

If someone can figure out how to get skype to load the 32-bit pcm_pulse & ctl_pulse modules, this would fix all issues until a proper package is put out with the correct symbols.

---

