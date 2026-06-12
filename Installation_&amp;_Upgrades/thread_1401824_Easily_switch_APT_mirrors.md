---
title: "Easily switch APT mirrors?"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by npmeyer on 2010-02-08
I have a work laptop that runs Ubuntu 9.10 (Karmic) i386.  My company maintains a mirror of the APT repositories on their internal network and provides a sources.list file for accessing them.  However, when I take the laptop home, I want to use the standard United States APT mirrors since I can't get to my employers' unless I'm on their network.

Are there any tools out there that will help me quickly switch APT mirrors, or even do so automatically based on my network connection?  Or should I script this myself?

---

### Post by mbsullivan on 2010-06-22
You can easily select the fastest repo through Synaptic. See [here]("http://www.ubuntugeek.com/how-to-select-fastest-mirror-in-ubuntu.html").

Doing it from the command line seems like [it's possible]("http://www.go2linux.org/find_the_fastest_debian_mirror-apt-spy_and_netselect-apt") (see also [here]("http://ubuntuforums.org/showthread.php?t=392642")), but I haven't found a way that's in the Ubuntu repos.

Mike

---

