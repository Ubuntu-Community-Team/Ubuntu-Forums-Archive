---
title: "Install problems on Gutsy?"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by BruceWayne on 2008-01-04
Ok i finally figured out how to install gutsy but now I cant install any programs from terminal. I try apt-get install vlc or beagle or just anything and it gives me this:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Any ideas? Thanks

---

### Post by chewearn on 2008-01-04
Did you use "sudo" in front of the commands?

E.g.
```
sudo aptitude install vlc
```

---

### Post by BruceWayne on 2008-01-04
yea i tryed sudo in front also and still didnt get programs to install.

---

### Post by jan quark on 2008-01-04
is another installation program running when you install via the terminal, 

when yes close all

Synaptic and Add/Remove windows and try again

---

### Post by christianxxx on 2008-01-04
I've had a similar problem, when after installing a piece of software I was suddenly not a member of the admin-group. A clue was that I couldn't even open the simplest little Administration tool, nor could I perform any sudo + command.

I would check your group belongings, could be broken. 

Also, have a look at [http://ubuntuforums.org/showthread.php?t=588616]("http://ubuntuforums.org/showthread.php?t=588616")

---

### Post by BruceWayne on 2008-01-04
here is the outcome for sudo aptitude install vlc


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "vlc"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done

---

### Post by zvacet on 2008-01-04
system>administration<software sources>under ubuntu software tick all and under updates tab also.Refresh.Now you can go to the synaptic and install VLC or by typing in terminal

```
sudo apt-get install vlc
```

---

