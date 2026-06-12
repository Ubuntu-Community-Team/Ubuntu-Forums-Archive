---
title: "Failed upgrade"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by gryall on 2010-10-13
This morning I tried to upgrade my netbook to 10.10 . During the instalation bit of the upgrade (about half way through it) it stalled and stoped doing anything. I could still move the cursor, but couldn't open anything. I had the console view open on the updater, but unfortunately can't tell you what package it got stuck on because it didn't all fit on the screen of my netbook (a problem I have had with a few programmes since installing netbook remix). I left it for half an hour to see if anything happened, it didn't, so I turned the netbook off and on again.

On turning it back on it got as far as giving me a cursor, showing the time on the bar across the login screen and showing me the name of my netbook. It did not give me a log in screen. Clicking the name of the netbook replaced the name with "10.10" . 

What can I do now, is there a way I can complete the interrupted install from ubuntu live or revert back to 10.4 and try again? Is there a way of booting into a console and running the update from there? 

Thanks in advance, your help would really be appreciated.

---

### Post by gryall on 2010-10-13
I also just noticed the following error in the top right corner at the not quite log in screen:

"Install problem!
The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer admintistraor"

---

### Post by baisa on 2010-10-13
I have exaclty the same problem.

---

### Post by gryall on 2010-10-13
I have fixed it.

At the log in screen I used Alt-Fsomething , to go text based and then loggged in. I tried to run 'sudo apt-get update' ,but that gave me an error. I then ran the command the error message suggested.

---

### Post by baisa on 2010-10-15
Unfortunatelly it doesn't work for me. Googling answer is that Ubuntu 10.10 update just doesn't work with ATI video cards.

---

