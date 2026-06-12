---
title: "Anyone successfully install granola on ubuntu 11.10 ?"
date: 2011-12-02
forum: Installation &amp; Upgrades
---

### Post by AzharHafiz.com on 2011-12-02
I receive this error

```
Selecting previously deselected package granola.
(Reading database ... 183125 files and directories currently installed.) Unpacking granola (from .../granola_4.0.3-0oneiric1_i386.deb) ... Processing triggers for ureadahead ... Processing triggers for man-db ... Setting up granola (4.0.3-0oneiric1) ... Removing any system startup links for /etc/init.d/ondemand ... * Starting Granola granola [fail]

sudo apt-get install granola-gui
Reading package lists... Done Building dependency tree
Reading state information... Done E: Unable to locate package granola-gui

on the website it says it's compatible with 11.10 http://grano.la/support/linux_install.php?download&os=linux#repoconfig

```

can't start

anyone solved the problem?

---

### Post by Frogs Hair on 2011-12-02
I installed the 64 bit .deb package with the Gdebi package installer without issues . I then used the granola man page , but I got run time errors when trying the commands , so it has been removed . The version I installed was a CLI application .

---

### Post by jadaka on 2011-12-02
At the very bottom of the page you linked: 
> Ubuntu Unity has broken support for granola-gui.     In synaptic, it looks like the granola-gui package isn't even in the miserware repo for 11.10. I've tried setting the repo back to the Natty version and installing granola & granola-gui from there, but there were some dependency issues that were beyond me. The 11.10 version of granola worked ok without the gui on two machines for me though.

(Admittedly, I only used it for a week before switching back to what I'd used while waiting for a 11.10 version of granola - cpufrequtils + indicator-cpufreq on the desktop, jupiter on the laptop.)

---

### Post by AzharHafiz.com on 2011-12-02
> **jadaka said:**
> At the very bottom of the page you linked: 
In synaptic, it looks like the granola-gui package isn't even in the miserware repo for 11.10. I've tried setting the repo back to the Natty version and installing granola & granola-gui from there, but there were some dependency issues that were beyond me. The 11.10 version of granola worked ok without the gui on two machines for me though.

(Admittedly, I only used it for a week before switching back to what I'd used while waiting for a 11.10 version of granola - cpufrequtils + indicator-cpufreq on the desktop, jupiter on the laptop.)

i guess i'll just wait for 11.10 ?

---

