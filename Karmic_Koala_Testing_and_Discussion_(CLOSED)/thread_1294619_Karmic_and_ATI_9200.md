---
title: "Karmic and ATI 9200"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by poohter on 2009-10-18
Currently upgraded from jaunty to karmic with ati 9200. On jaunty 3d effects worked fine after upgrade they do not work. After fooling around I think I have now completly removed all ati drivers free and non free and now have no video, just a black screen that flickers. can someone tell me the entry to reinstall the open source driver for the ati 9200 in karmic?

I can get to text only login in, but I seem to have no video drivers to start x server

---

### Post by the111dan on 2009-10-22
try typing 

sudo apt-get install xserver-xorg-video-radeon (or something like that)

in command line

this should help you install the open ati drivers

---

