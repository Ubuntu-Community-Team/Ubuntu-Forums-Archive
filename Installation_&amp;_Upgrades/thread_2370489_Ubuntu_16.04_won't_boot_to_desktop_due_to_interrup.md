---
title: "Ubuntu 16.04 won't boot to desktop due to interrupted update."
date: 2017-09-04
forum: Installation &amp; Upgrades
---

### Post by denerd on 2017-09-04
Hi. I was doing some update on my Ubuntu 16.04 HP desktop and it got interrupted due to power failure. I tried to boot again and after putting in my password, my system just won't boot to the desktop even after many tries. I tried recovery mode from the menu shown at start up, yet the system remains blank. Please i need help from the community. Thanks.

---

### Post by BenginM on 2017-09-04
Hiya , welcome tot he forums .. try running dpkg from recovery mode.

---

### Post by ajgreeny on 2017-09-04
At the login screen where you put in your username and password try Ctrl+Alt+F1 for a command line.
Login at that; your username will show but password will not show anything so type carefully and hit Enter.
From the command-line now try ```
sudo dpkg --configure -a
sudo apt-get install -f
``` and see if that fixes things or throws up more errors that may help.

---

### Post by denerd on 2017-09-04
Hi ajgreeny, thanks for the initial help. However, as i got to the command prompt, I see a prompt like this "denerd login:" and i have tried inputting all i know and yet i'm told incorrect login even after carefully putting in my password. How do I go about this please?

---

### Post by ajgreeny on 2017-09-04
I assume from that "denerd login:" prompt which you saw that you have a machine hostname of denerd, ie, denerd is the name you gave the computer when you installed the system; correct?  If your username is also denerd (as it is for this forum) the prompt you will have seen in a terminal when you opened it would have been denerd@denerd.

When you see that prompt "denerd login:" the system is asking for your username not your password which may be where you have been confused by using the same username and hostname.  Try your username first, hit enter, then your password when asked for it; this is where you will see nothing echoed to screen.

---

### Post by denerd on 2017-09-04
[SIZE=3]Oh! Thanks very much for the help. My system is back to good working condition. I highly appreciate. At least this adds some knowledge to my quest to be a Linux power user and I'm enjoying the whole new experience. God bless.&#8203; [/SIZE]:D:D

---

### Post by ajgreeny on 2017-09-04
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

