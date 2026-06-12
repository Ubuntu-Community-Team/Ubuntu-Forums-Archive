---
title: "blank screen from xubuntu wubi install"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by agrayray on 2011-06-14
I am trying to install xubuntu 10.04 on an emachine 1024 GB RAM machine and getting a blank screen when xubuntu is trying to install after the eject CD and reboot part.

I also get a blank screen after the xubuntu startup image using the live cd under a normal startup.

If however, from the live cd, I select 'nomodeset' from F6 options, XUbuntu starts fine.

It appears there is a process that is trying to set the screen mode/resolution and this is causing the blank screen as if I do a nomodeset, the display is 1024X768; 85hz and works fine..and the xubuntu startup image is much bigger than the default startup mode.  I am more than fine with a 1024X768 display as basically I am trying to setup a file and printer sharing server; in fact I prefer 1024x768 so I can easily see the screen when I remote desktop into this machine as it will be headless(monitor less) server.

Does anyone know how I can complete the wubi install and not get a blank screen for this computer..?

Thanks in advance!

---

### Post by Rubi1200 on 2011-06-15
You also need to use nomodeset after the first reboot of the Wubi install.

See here for more:
[http://ubuntuforums.org/showpost.php?p=10089820&postcount=8](http://ubuntuforums.org/showpost.php?p=10089820&postcount=8)

---

### Post by agrayray on 2011-06-15
Thanks that did it...I somehow missed the text writeup at the bottom the page..anyway thanks for the link..adding into the boot command worked like a charm!!!

---

### Post by Rubi1200 on 2011-06-16
No problem, you are more than welcome :-)

Please mark this Solved using the Thread Tools near the top of the page.

---

