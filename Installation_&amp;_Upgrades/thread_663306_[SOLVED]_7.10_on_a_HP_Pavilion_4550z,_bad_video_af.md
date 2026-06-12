---
title: "[SOLVED] 7.10 on a HP Pavilion 4550z, bad video after clean install (includes photo)"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by diablo75 on 2008-01-10
I am trying to install Xubuntu 7.10 on a HP Pavilion 4550z (old celeron machine, about 450 Mhz CPU).
A thorough memory test was done before install.

The first attempt at installing would cause the video driver to look slightly haywire when the gui finally loaded. The splash screen displays perfectly, though.
The second attempt was to instead try Safe-graphics mode, which worked fine. But the install process locked shortly into the process and would never make it any further.
The third attempt was the text based install on an alternate install CD, which worked. But now, the video looks like it did in the first install attempt: freggin' terrible. Just a bunch of digital noise on the right hand of the screen like that NIN cd that came out a couple years ago.

Any ideas? Perhaps some boot option that could be added during install?

Here's what it looks like:

[IMG]http://www.davestechsupport.com/download/badvideo.jpg[/IMG]

[**_Here_**]("http://www.davestechsupport.com/download/badvideo.avi") is a short video of it.

What should I try next?

---

### Post by Partyboi2 on 2008-01-10
Try getting to a terminal (Ctrl+Alt+F1-F6)
then 
```
sudo dpkg-reconfigure xserver-xorg
```choose "Vesa" driver from the list
and answer the questions that are asked. If unsure just use the default, which is the one it displays when asking the question.
Then
```
startx
```This will reconfigure the xserver and should get you to your Desktop where you can see things normally.
You will then need to look at what driver is required for for video card and try and get that working.
What video card are you using?

---

### Post by diablo75 on 2008-01-12
That worked!  Thank you very much!

---

