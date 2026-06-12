---
title: "Installing Codecs Does Not Work"
date: 2005-05-24
forum: Installation &amp; Upgrades
---

### Post by cinematography on 2005-05-24
I updated my sources.list file by copying and pasting the text here:  
[http://www.frankandjacq.com/ubuntuguide/5.04/index.html#extrarepositories](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#extrarepositories)

When I run the code on the pain page found here: 
[http://www.frankandjacq.com/ubuntuguide/5.04/index.html#codecs](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#codecs)

I get this response....

> root@ubuntu:/home/me # wget -c [http://frankandjacq.com/ubuntuguide/gstreamer0.8-lame_0.8.8-0.1_i386.deb](http://frankandjacq.com/ubuntuguide/gstreamer0.8-lame_0.8.8-0.1_i386.deb)
--19:34:42--  [http://frankandjacq.com/ubuntuguide/gstreamer0.8-lame_0.8.8-0.1_i386.deb](http://frankandjacq.com/ubuntuguide/gstreamer0.8-lame_0.8.8-0.1_i386.deb)
           => `gstreamer0.8-lame_0.8.8-0.1_i386.deb'
Resolving frankandjacq.com... 66.113.130.205
Connecting to frankandjacq.com[66.113.130.205]:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

root@ubuntu:/home/me # sudo apt-get install gstreamer0.8-plugins
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-artsd gstreamer0.8-caca
  gstreamer0.8-festival gstreamer0.8-jack gstreamer0.8-mad gstreamer0.8-mikmod
  gstreamer0.8-mpeg2dec gstreamer0.8-sid gstreamer0.8-swfdec jackd
  liba52-0.7.4 libjack0.80.0-0 libmikmod2 libmpeg2-4 libsidplay1-c102
  libsndfile1 libswfdec0.3
Suggested packages:
  qjackctl jack-tools meterbridge libjackasyn0 sidplay-base xsidplay
The following NEW packages will be installed:
  gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-artsd gstreamer0.8-caca
  gstreamer0.8-festival gstreamer0.8-jack gstreamer0.8-mad gstreamer0.8-mikmod
  gstreamer0.8-mpeg2dec gstreamer0.8-plugins gstreamer0.8-sid
  gstreamer0.8-swfdec jackd liba52-0.7.4 libjack0.80.0-0 libmikmod2 libmpeg2-4
  libsidplay1-c102 libsndfile1 libswfdec0.3
0 upgraded, 20 newly installed, 0 to remove and 1 not upgraded.
Need to get 1066kB of archives.
After unpacking 3211kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
root@ubuntu:/home/me #


Does anyone know what the problem could be? :(

---

### Post by cinematography on 2005-05-24
Nevermind. Problem solved. MrBass is a genius! :D

---

### Post by djpharoah on 2005-05-25
can you post the solution to the problem so that others might also have a chance to solve their probs

cheers

---

