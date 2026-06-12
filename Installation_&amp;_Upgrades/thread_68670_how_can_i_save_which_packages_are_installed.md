---
title: "how can i save which packages are installed?"
date: 2005-09-23
forum: Installation &amp; Upgrades
---

### Post by kerinin on 2005-09-23
i'm going to reinstall ubuntu (it's a little wonky since i dist-upgraded to breezy), but i don't particularly want to spend an hour trying to remember which packages i've installed and reinstalling them.  is there some way that i can make a record of which packages are installed on my system, then tell apt to install everything on the list when the new system is installed?

i think i remember seeing a tool for doing this in a list of apt derivatives, but i can't find it anymore.

thanks!

---

### Post by kerinin on 2005-09-23
ok, found this:

[http://www.linuxquestions.org/questions/history/357683](http://www.linuxquestions.org/questions/history/357683)

---

### Post by phex on 2005-09-24
For Ubuntu there is also another mechanism. The packages you donwload are stored in /var/cache/apt/archives. Now you have 2 methodes. 1) You can backup it and simple use the dpkg -i command. but i would not recommend it because the depenent packages will not be installed. So you have to use dpkg for each dependant deb package. 2) you must transform this archives directory to a repository so you can use it with synaptic. I am not quite sure where i read about it how it can be done. but i think it was somewhere here in the forum. just search for it in the forum or do some googeling. good luck. ;)

---

### Post by phex on 2005-09-24
here is the link:
[http://www.linuxquestions.org/questions/history/360103](http://www.linuxquestions.org/questions/history/360103)

---

### Post by kerinin on 2005-09-26
thanks, that seems like a much cleaner solution

---

