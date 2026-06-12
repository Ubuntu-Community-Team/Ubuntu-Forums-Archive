---
title: "Karmic installation boots to flashing terminal"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jic2000 on 2009-10-06
Well, I installed the Karmic beta, and everything seemed fine - then installed fglrx through the restricted hardware manager program, rebooted, and my installation was broken. It boots with no errors to a terminal asking me to log in, but the text is flashing several times a second, and only responds to keypresses when the text is visible, making it pretty much impossible to type my password accurately and get into the terminal. Is there anything I can do to fix this, or anything I can do in a fresh installation to get fglrx working without this problem?

My system is a Fujitsu Lifebook A6230, with 4GB of RAM, a 2.13 GHz Core 2 Duo processor, and an ATI Radeon Mobility HD 3470 graphics card.

---

### Post by rufuse on 2009-10-10
Bump. I have the same issue on samsung q210.

---

### Post by paul.dorman on 2009-10-22
I get this also. I also see ntpd repeatedly stopping and starting. Without installing linux-headers-`uname -r` you don't get past the flashing terminal if using nVidia drivers.

Only a week to go! Let's hope they've got some miracle workers at Canonical!

---

### Post by XsCode on 2009-10-22
i had this on my nvidia 8400m GT and fixed it... see here.. [http://ubuntuforums.org/showthread.php?t=1295120](http://ubuntuforums.org/showthread.php?t=1295120)

---

