---
title: "Yet another Flash problem after upgrading to 10.04"
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by jjcnn on 2010-07-17
I have seen loads and loads of people having audio problems in flash after upgrading to 10.04, and I am no exception. However, I have not seen anyone reporting problems as big as mine, and none of the suggested solutions have worked for me.

I'm running 32-bit Kubuntu 10.04 (upgraded yesterday), Firefox 3.6.6, Flash 10.1.53.64 (according to apt-get). Firefox is run with flashblock 1.5.13, but disabling it does not result in different behaviour.

When viewing a youtube video, I get to see the video, but without sound. Navigating away from the page causes firefox to freeze.

Sound works with Amarok, and I get system sounds as well. Pulseaudio does not seem to work (testing Pulseaudio at System Settings->Multimedia does not produce any sound), but I have never managed to get it to work on my machine in either of the 3 Ubuntu versions I've run. Not that I'm an expert on sound issues, mind.

Everything worked fine under Kubuntu 9.10. 

I'm pretty sure this is a flash problem. Disabling all other firefox plugins gives me the same behaviour, and I get exactly the same behaviours in Opera and Konqueror. In Chrome, the   only difference is that only the current tab freezes, not the entire   browser.

I have tried removing flashplugin-installer from my installation, and  then searching for other flash .so-files, but I have found none.  Conflicting flash versions does not seem to be the problem.

I have also tried to set up Pulseaudio, using 
[http://www.pulseaudio.org/wiki/PerfectSetup ]("http://www.pulseaudio.org/wiki/PerfectSetup")
but then all sound was disabled.

Does anyone have a good suggestion?

---

### Post by jjcnn on 2010-07-18
Fixed. My lack of understanding of the sound options in KDE was the problem.

The guide that finally made the penny drop for me was this one:

[http://www.shcherbyna.com/?p=866](http://www.shcherbyna.com/?p=866)

---

