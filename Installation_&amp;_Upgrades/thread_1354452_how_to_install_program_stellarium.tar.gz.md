---
title: "how to install program stellarium.tar.gz?"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by tonjaa on 2009-12-13
i try to install program stellarium-0.10.2.tar.gz i uncompress it i got this
[COLOR=Green]root@gooddog-desktop:/home/gooddog/Downloads/stellarium-0.10.2# ls
AUTHORS                   COPYING     nebulae      src
ChangeLog                 data        po           stars
cmake                     doc         README       stellarium.iss
CMakeLists.txt            Doxyfile    scripts      textures
cmake_uninstall.cmake.in  INSTALL     sip          util
config.h.cmake            landscapes  skycultures[/COLOR]

how to use correct  command to install it ? please tell me by step .

---

### Post by staf0048 on 2009-12-13
> **tonjaa said:**
> i try to install program stellarium-0.10.2.tar.gz i uncompress it i got this
[COLOR=Green]root@gooddog-desktop:/home/gooddog/Downloads/stellarium-0.10.2# ls
AUTHORS                   COPYING     nebulae      src
ChangeLog                 data        po           stars
cmake                     doc         README       stellarium.iss
CMakeLists.txt            Doxyfile    scripts      textures
cmake_uninstall.cmake.in  INSTALL     sip          util
config.h.cmake            landscapes  skycultures[/COLOR]

how to use correct  command to install it ? please tell me by step .

Typically to install something like this you'd use:

1.
```
./configure
```
2.
```
make
```
3.
```
make install
```

I'm not an expert though, so that might not work as I thought.  Can I ask why you're not just installing Stellarium from the repos?  The 0.10.2 version is available there (in the Karmic repos anyway).

---

### Post by aysiu on 2009-12-13
First, ditch the .tar.gz. It's not needed.

Then, just install Stellarium through Applications > Ubuntu Software Center (Ubuntu 9.10) or Applications > Add/Remove (Ubuntu 9.04 and earlier).

More details here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by tonjaa on 2009-12-14
;) thank you so much

---

### Post by Syd35 on 2010-01-12
I have tried the 'Ubuntu Software Centre", and 'Synaptic', and '.... tar.gz', all several times, and although the 'launcher' appears in Applications/Science, once I 'click on it' the screen returns to the boot Ubuntu window. This has happens with "Miro" when I try to open a downloaded video, but not audio, and with "OpenUniverse Space Simulator, and also with 'Earth 3d' software. Stellarium loaded OK on Ubuntu 9.04 with no problems.      

I do have 'Kstars' which I find brilliant, and works fine.
Any suggestions please?
Thanks if someone can help.

---

