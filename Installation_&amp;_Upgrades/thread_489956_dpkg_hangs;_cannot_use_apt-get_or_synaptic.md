---
title: "dpkg hangs; cannot use apt-get or synaptic"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by maluze on 2007-07-01
I dunno what went wrong, but over the course of today, I was using synaptic to install libghc6-gtk-dev, so I could play the chess game in 3D. I thought synpatic was done, so I force closed it. Well, I tried to use apt-get later in the day, and found that i got this message: "E: dpkg failed to complete; use dpkg --command -a" (or something along those lines). Well, after running the said command, my computer runs it, then gets to this line, where it says "building GHCi Library blah blah blah", and then slows my PC way down. 

I tried to use dpkg --remove -a, that didnt work, and dpkg --purge -a, that didnt work either (it says that the package is missing), and in both instances it continues on to display the "building GHCi" line

what can I do?

---

### Post by oldmanstan on 2007-07-02
that typically happens when the package you were installing wanted some sort of input from the user (the little terminal dropdown thing on the synaptic progress window) and when it doesn't get the input but doesn't finish installing the package it dies...

are you sure you're waiting long enough to let it finish it's thing? (dpkg that is...)

---

### Post by maluze on 2007-07-02
yes, as a matter of fact i did. I let it run for a few hours. while it was running, system monitor indicated a huge jump in memory usage right as it went to the last line (buildingg..).  I left it on and went to the play ball, came back, found it was totally unresponsive, probably becuase it took up all the memory, and no progress whatsoever in the terminal window :(

---

### Post by maluze on 2007-07-02
* bump*

anyone? this is getting to be a pain in the a**. Everytime i use synaptic, after the installation is done, it will say "setting up...", and then "building GHCi..." Please, somebody help me.. :(

---

### Post by maluze on 2007-07-03
*bump* ..please, this issue needs to be resolved very soon... any suggestions as to what to do?

---

### Post by rillip on 2007-07-03
Mm, you should be able to remove the package with dpkg.  You'll have to man up the command, I imagine it's something like dpkg -dselect (packagename)  Hopefully it wouldn't try to make you configure the package you are trying to remove.  Not really sure what else to do on that one.

---

