---
title: "troubles with Flash 10"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2010-09-09
with ubuntu 8.04.4 I could not get flash 10 installed correctly , and I version upgraded (online) to ubuntu 10.04

however, although maybe a clean install would have worked ok, after the upgrade, I still could not get flash 10 installed and working.

I removed ubuntu restricted extras.

and then, following 

[http://www.linuxquestions.org/questions/linux-newbie-8/ive-installed-flash-player-on-ubuntu-but-vids-on-youtube-wont-play-or-load-at-all-764068/](http://www.linuxquestions.org/questions/linux-newbie-8/ive-installed-flash-player-on-ubuntu-but-vids-on-youtube-wont-play-or-load-at-all-764068/)

in particular, from  'lidex':
Try entering these commands - one at a time - into terminal:
Code:
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-installer
Restart browser.


flash 10 (and BBC iplayer) worked ok, in ubuntu 10.04 that is. 
I then re installed ubuntu restricted extras.

still ok.
Thanks lidex!

---

