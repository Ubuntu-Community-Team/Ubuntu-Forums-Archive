---
title: "error processing pulseaudio (--configure)"
date: 2009-03-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dan_kent on 2009-03-17
I recently did a dist upgrade on my jaunty laptop. Unfortunately it decided to crash half way through. A apt-get -f install and confiure -a fixed ost of the problems but i'm still left with the following;

dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing pulseaudio (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 pulseaudio
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas how I go about fixing this?

---

