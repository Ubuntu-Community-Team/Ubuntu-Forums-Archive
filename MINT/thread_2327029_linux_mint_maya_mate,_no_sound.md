---
title: "linux mint maya mate, no sound"
date: 2016-06-07
forum: MINT
---

### Post by jim140 on 2016-06-07
Hi, first post here.

I&#7743; using Linux mint maya mate with a geoforce 210 card.  I've read miles of suggestions.  But something just happened and the sound is working now. 

Here is what I did.   Went into terminal and put --aplay -D plughw:0,1 /usr/share/sounds/speech-dispatcher/test.wav.   I didn't get any sound but when I went into Preferences/ Sound and tested the speakers under  Hardware, Built in audio, analog stereo output.  I got sound from the speakers.  

However, I had to unplug the hdmi video and use the 15 pin pc video out and the headphone out jack on the computer case.  

The video plays with VLC and is good quality.  The sound is good quality as well.

But, when I shut down and restart I have to do the terminal aplay thing again.  How can I make that permanent?  And can I shorten the command to just aplay -D plughw:0,1????

Thanks

---

### Post by howefield on 2016-06-07
Thread moved to the "*MINT*" sub forum.

---

### Post by SuperFreak on 2016-07-10
> **jim140 said:**
> Hi, first post here.

I&#7743; using Linux mint maya mate with a geoforce 210 card.  I've read miles of suggestions.  But something just happened and the sound is working now. 

Here is what I did.   Went into terminal and put --aplay -D plughw:0,1 /usr/share/sounds/speech-dispatcher/test.wav.   I didn't get any sound but when I went into Preferences/ Sound and tested the speakers under  Hardware, Built in audio, analog stereo output.  I got sound from the speakers.  

However, I had to unplug the hdmi video and use the 15 pin pc video out and the headphone out jack on the computer case.  

The video plays with VLC and is good quality.  The sound is good quality as well.

But, when I shut down and restart I have to do the terminal aplay thing again.  How can I make that permanent?  And can I shorten the command to just aplay -D plughw:0,1????

Thanks

Can't guarantee this will work but this is how I solved the same problem for my installations of 16.04 and Sarah 18 Cinnamon Mint:

I solved in this way:
sudo gedit /etc/pulse/default.pa
commented this line --> load-module module-switch-on-port-available
Saved

---

