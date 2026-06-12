---
title: "Bye bye PulseAudio (for now?)"
date: 2009-02-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by eyelessfade on 2009-02-20
So after I upgraded to 9.04 most went to hell!. Not that I complain its still alpha after all, but I found out something. Since before 8.10 I haven't been able to play 720p h264 flicks on my laptop, I had a vague memory that I could do it before but I wasn't sure. Maybe it was due to a number of factors, fglrx comes to mind. Anyway just before Xmas last year I changed to the free ati drivers, now I could atleast watch 480p. Horay!

My laptop is not a fast one it has a screen of 1680x1050, but only a celeron 1700MHz.

Last week I figured to disable pulse due to the problems I even had on 320x240 videos. Guess what? Now I even can play 720p without framedrop! How is it possibly that pulse draw this much resources?

---

### Post by TenPlus1 on 2009-02-20
I always remove Pulse after an Ubuntu install and stick work good 'ol Alsa...

---

### Post by KhaaL on 2009-02-20
I'm also very intrested to see if pulse hogs that much resources. Did you have any of its network broadcasting features enabled?

---

### Post by eyelessfade on 2009-02-20
Might have, but I can check tomorrow

---

### Post by RIchard James13 on 2009-02-20
Thanks for the tip "sudo apt-get remove pulseaudio". Now I can have multiple programs access sound.

---

### Post by Linuxidiot on 2009-02-20
Wouldnt sudo apt-get remove pulseaudio , remove ubuntu desktop as well?

---

### Post by Starks on 2009-02-20
The metapackage ubuntu-desktop is not critical. Uninstalling it will not (normally) uninstall the packages it installs.

---

### Post by ugkbunb on 2009-02-20
ubuntu-desktop is just a metapackage that relies on all the other packages being installed... as I understand you can remove it without any harm to your system i.e. it won't remove all the packages that install when you install ubuntu-desktop

---

### Post by nystire on 2009-02-21
However, uninstalling it will also prevent your installation from pulling in many of the newer packages due to the fact that ubuntu-desktop is used as a base package for them.

---

### Post by Starks on 2009-02-21
> **nystire said:**
> However, uninstalling it will also prevent your installation from pulling in many of the newer packages due to the fact that ubuntu-desktop is used as a base package for them.

Individual updates wouldn't be affected and neither would a final release of Jaunty unless the devs decided to do something unprecedented and add a new package outside of a point release.

---

### Post by RIchard James13 on 2009-02-21
I don't have ubuntu-desktop as I'm using Kubuntu.

---

### Post by nystire on 2009-02-21
The devs adding new packages wouldn't be too unprecedented. It happened in the past when some libraries were put into a separate package to save on the size of individual downloaded packages.

---

