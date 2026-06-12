---
title: "[SOLVED] Cant install codecs ??!!"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by brugui00 on 2007-11-29
just installed ubuntu, but maybe it didn't install correctly.

When i try to open a video file, any video file, i get a message saying that I am missing certain codecs and that I need to search for the correct ones. I click on search and it gives me a list of the missing codecs, but I dont have the "install" option available. I double click on the codec I want, and it says to "confirm", i confirm and it tells me that "the list of applications is not available" and to "reload". I then click refresh and it downloads more package information (4 to be prezise), but then it goes back to the initial window, with the list of codecs available, but all is still the same.

can anybody help? 

thanks

---

### Post by atlfalcons866 on 2007-11-29
what ubuntu version are you using?

---

### Post by brugui00 on 2007-11-29
ubuntu 7.10

---

### Post by bjarneh on 2007-11-29
note the names of these packages and just try to install them with aptitude, maybe something has gone haywire with the synaptic stuff, for example if the codec-package was called supercodecs

open a shell: 
programs--> accessories--> terminal

sudo aptitude install supercodecs

something like that...

---

### Post by atlfalcons866 on 2007-11-29
what video format is it?

---

### Post by atlfalcons866 on 2007-11-29
if they are files like .mov .flv w/e you will need to install the restricted codecs

> sudo apt-get install gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly


---

### Post by brugui00 on 2007-11-29
I'm trying to install:

GStreamer extra plugins
GStreamer ffmpeg video plugin
Gstreamer plugins for aac, xvid, mpeg2, faad

how do I find out their code name??

---

### Post by atlfalcons866 on 2007-11-29
for the ffmpeg one do this at terminal 

> gstreamer0.10-ffmpeg

for aac and xvid and other restricted codecs do

> sudo apt-get install gstreamer0.10-plugins-bad-multiverse

---

### Post by brugui00 on 2007-11-29
```
:~$ sudo apt-get install gstreamer0.10-plugins-bad-multiverse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gstreamer0.10-plugins-bad-multiverse
```


could this problem be because i did the installation wrong? its my first time installing ubuntu, but i think i did everything right!

---

### Post by atlfalcons866 on 2007-11-29
works on mine

i made an error on the ffmpeg one its

> sudo apt-get install gstreamer0.10-ffmpeg

---

### Post by brugui00 on 2007-11-29
ok! it worked, thank you very much

---

### Post by atlfalcons866 on 2007-11-29
alright

---

