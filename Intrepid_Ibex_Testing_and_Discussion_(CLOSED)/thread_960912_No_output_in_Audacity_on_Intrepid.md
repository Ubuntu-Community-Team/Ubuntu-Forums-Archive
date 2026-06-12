---
title: "No output in Audacity on Intrepid"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rowanq on 2008-10-27
Has anyone running Intrepid notice a loss of audio output in Audacity under Intrepid?
 I seemed to lose it as of yesterday. The only thing that I can think of was that I installed Ardour (which also has problems for me).
I've tried re-installing and deleting my config files, and double checked my output device, but nothing seems out of place.
 Any thoughts?

---

### Post by BwackNinja on 2008-10-27
Try running it in a terminal - it may give you errors about no mmap support, which would be it trying to run in pulseaudio like all alsa apps are configured to do in intrepid. If so, then try "pasuspender audacity."

---

### Post by au_vagabond on 2008-10-27
Make sure the output is correct. I am fairly sure that audacity uses jack as a default, so make sure you have changed it back to alsa/whatever.

---

### Post by marmuta on 2008-10-28
Audacity is a pain to setup currently. Check this bug and its duplicates:
[https://bugs.launchpad.net/ltsp-cluster/+bug/178895](https://bugs.launchpad.net/ltsp-cluster/+bug/178895)

Running "padsp audacity" and selecting /dev/dsp for playback and recording used to work for me in hardy but it now locks up on playback in Intrepid.

This is how I get playback&recording: 
- run "pasuspender audacity" as BwackNinja wrote.
- in preferences->Audio I/O select the main alsa device (hw:0,0) for playback 
- select /dev/dsp for recording
- disable Preferences->Audio I/O->Play other tracks while recording new one

Everything else at best gives errors in audacity but mostly freezes it or silences audio for the rest of the system until the next reboot.

---

### Post by rowanq on 2008-10-28
Thanks Guys!
  Sorry about the delay, currently traveling.
 So I ran it through terminal, but got no error output. I then ran it as 'pasuspender audacity' in terminal and changed the output to alsa device (hw:0,0) as suggested by au_vagabond and marmuta.
 I've got audio output back, though the master volume control in Audacity no longer works. I consider that only a minor annoyance for the moment.

 Thanks for helping me get this back on line guys!

---

### Post by au_vagabond on 2008-10-29
yay! Have fun audio editing :P

---

