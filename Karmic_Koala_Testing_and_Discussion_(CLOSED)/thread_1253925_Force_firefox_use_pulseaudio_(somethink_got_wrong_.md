---
title: "Force firefox use pulseaudio (somethink got wrong last update)"
date: 2009-08-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by gcsoares on 2009-08-30
Hi, I have two sound devices (I only use one of then), the problem is that firefox since some days ago don't appear in the sound preferences anymore, so I can't chose where it will output it's sound, and thanks to murphy's law, the firefox sound is going only to my motherboard sound card (so, firefox's sound is working, but not in my headset).

A better explanation of my problem: [http://img194.imageshack.us/img194/5789/soundbug.png](http://img194.imageshack.us/img194/5789/soundbug.png)

I'm using a dist-upgraded karmic koala 64bits, I already:
-reinstaled firefox, flash and pulseaudio
-deleted (with gdm closed) ~/.pulse*, */.adobe and ~/.audio*
-created a new firefox profile
-upgraded everything
-searched for conf-files with the words "pulse" or "alsa" to try to change it, but found nothing usefull.

I don't know what to do now...

tks for the attention, Guilherme.


______________

EDIT: PS: I have some problems with "some custom menus that used to have a icon, now has no icons", but I didn't tried to fix it yet...

---

### Post by psyke83 on 2009-08-30
Install and run pavucontrol (PulseAudio Volume Control). On the Playback tab you can control the stream that an application will use (in this case, Firefox).

Are you using the 64-bit release by any chance? It's possible that the 32-bit PulseAudio ALSA libraries aren't working correctly, so sound isn't passing to the server.

Also keep this in mind: Java may not work correctly with PulseAudio, so it will override PulseAudio and output directly to the default ALSA device. This isn't the problem you're experiencing, though.

---

### Post by gcsoares on 2009-08-30
pavucontrol didn't helped, but I tested now with a HTML5 video ([http://www.mozilla.com/en-US/firefox/video/?video=awesomebar](http://www.mozilla.com/en-US/firefox/video/?video=awesomebar)) and the sound worked fine, it look like a flash-related problem...    I'm reading your topic about pulseaudio now too...

---

### Post by jfernyhough on 2009-08-30
Did you install Flash from the repos? If so, try using the 64-bit version from the Adobe Labs instead (seeing as the repo one uses a 32-bit version and a wrapper to get it to work).

---

### Post by gcsoares on 2009-08-30
PERFECT!!!

If someone have the same problem (flash in Karmic Koala 9.10 64bits mute) execute this commands (the firefox will be closed, so save it in a ".txt" before):
Go to: [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html) And download the .tag.gz in the end of the page (I won't link here, get the updated version). "Unzip" it and than:
```
sudo killall -9 firefox
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/

```

I followed [http://www.myscienceisbetter.info/install-native-64bit-flash-player-10-on-linux.html](http://www.myscienceisbetter.info/install-native-64bit-flash-player-10-on-linux.html) to see where I have to put the files.

Thanks guys, you helped a lot. :)

PS: A 64bits flash in the repos would be useful, with a different name, like "flash-instaler64-alphaversion" so you could chose. Someone can send the idea to the "MOTUs"?
PSS: It is crashing a bit in games, but I'm used to it (I love testing alpha software, hawhawhaw).

---

