---
title: "blank screen during install"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by joebloggsman on 2007-09-10
I am not seeing any real answers on the subject.  My install starts of fine.  I then hear a beeping noise and the screen goes blank.  What am I missing?  I have modified my xorg.conf many different ways and no results.  My machine uses ATI Mobility FireGL V5000 for video.  I will post more info if needed.  Is this a xorg.conf file problem or something else?  I did not have this problem with the older ubuntu 5.x.  Please help.  Thanks.

---

### Post by merlinus on 2007-09-10
Video card problems.  Try the text-based Alternate install cd.

---

### Post by joebloggsman on 2007-09-12
Thanks.  It was looking good until 85% into the install (britty-x11) the machine appears to suspend the install.  Not sure what this means?  Sounds video card related.  I have installed the command line version now.  Can anyone help me install the GUI version please?

---

### Post by Pumalite on 2007-09-12
You mean you installed the server and you want a GUI?. If so, then:
sudo apt-get install ubuntu-desktop

---

### Post by joebloggsman on 2007-09-13
Okay, I tried to install the ubuntu desktop via command-line.  Setup frooze up.  I restarted.  Started looking like this might work.  Get a failed to start X server message.  Hit <enter> to see at the bottom of a long message: Fatal server error: caught signal 11. Server aborting.  Come on.  Does my video card suck that bad?  Why can't this or any other distro work.  This sucks.

---

### Post by Pumalite on 2007-09-13
Unfortunately ATI does not support Linux like Nvidia does.
Have you tried the Alternate CD?

---

