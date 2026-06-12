---
title: "Not showing up in applications"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by Hullon on 2007-07-05
After I've used apt-get to install both rTorrent and Beagle, neither show up under Applications, how should I start them? Are they even installed? I've installed other programs that have showed up.

---

### Post by bigken on 2007-07-05
have you rebooted the pc ?

---

### Post by Hullon on 2007-07-05
Actually I hadn't, It fixed Beagle, still no sign of rTorrent though...

---

### Post by bigken on 2007-07-05
have you look in internet ?

if its not there try this in a terminal 

sudo aptitude install rtorrent

---

### Post by Hullon on 2007-07-05
Didn't upgrade or install anything, so I guess it's actually installed but just hiding somewhere...

---

### Post by bigken on 2007-07-05
just run  **sudo aptitude install rtorrent **in a terminal

---

### Post by Hullon on 2007-07-05
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  compiz 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done


As I said, no upgrades or installs.

---

### Post by bigken on 2007-07-05
press alt and F2 then type rtorrent or rTorrent

---

### Post by Hullon on 2007-07-05
According to the known applications list it's not known, when I try to do it with rtorrent nothing happens and when I try rTorrent it claims the file could not be opened.

---

### Post by Hullon on 2007-07-05
I tried using sudo aptitude remove rtorrent and it removed 1 package called rtorrent, I'll try reinstalling it now.

---

### Post by Hullon on 2007-07-05
Same thing.

---

### Post by bigken on 2007-07-05
look [here]("http://ubuntuforums.org/showthread.php?t=331823&highlight=rtorrent") it might help

---

### Post by Hullon on 2007-07-05
That didn't work very well either so I'll just go ahead and settle for KTorrent, thanks for the effort.

---

