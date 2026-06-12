---
title: "Netflix-Desktop"
date: 2016-12-01
forum: MINT
---

### Post by bl1ndm0nk on 2016-12-01
Howdy all, I recently upgraded 17.3 to 18 and trying slowly restore what  I had before, also encounter same problem as you guys and Google search  brought me here. reading and I was able to force installation of **netflix-desktop** package by modifying source file. Since I'm newbie, something might be redundant so please forgive me.
After adding ppa  i believe you will end up having **ehoover-compholio-xenial.list** file in folder **/etc/apt/sources.list.d/  **open it as root via text editor of your choice

sudo apt-add-repository ppa:ehoover/compholio

sudo gedit /etc/apt/sources.list.d/ehoover-compholio-xenial.list

change **xenial** to [B]trusty
[/B]
deb [http://ppa.launchpad.net/ehoover/compholio/ubuntu](http://ppa.launchpad.net/ehoover/compholio/ubuntu) **trusty** main
deb-src [http://ppa.launchpad.net/ehoover/compholio/ubuntu](http://ppa.launchpad.net/ehoover/compholio/ubuntu) **trusty** main

save

sudo apt-get update
sudo apt-get install netflix-desktop

install msfonts, agree to whatever

sudo apt-get install msttcorefonts

run Netflix Desktop app from Sound & Video 
you will have to install Mono, Wine, Gecko, something with silverlight etc.

after that I've l get netflix running. 
sources:
netflix-desktop app                 [https://www.linux.com/learn/how-install-netflix-streaming-client-linux](https://www.linux.com/learn/how-install-netflix-streaming-client-linux)
adapted  this guy explanation how to force super-boot-manager install onto mint  17  [https://www.youtube.com/watch?v=03d4blnHlp8](https://www.youtube.com/watch?v=03d4blnHlp8)  in Russian language.

hope that helps, good luck.

---

### Post by QIII on 2016-12-01
Moved to MINT  from [https://ubuntuforums.org/showthread.php?t=2337041](https://ubuntuforums.org/showthread.php?t=2337041)

---

