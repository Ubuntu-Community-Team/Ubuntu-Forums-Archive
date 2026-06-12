---
title: "Backups before a fresh install? Help please"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by maddbaron on 2011-05-09
I've decided to do a full total fresh install of natty since i've had so many issues with 10.10, Can someone tell me how to backup all my terminal commands and my ppa source list as .txt files?

Also can i do a fresh install via ethernet cable or should I use the live cd to overwrite my current maverick Ubuntu?

Thanks in advance

---

### Post by akand074 on 2011-05-09
your terminal commands are stored in ~/.bash_history so just show hidden files in your home folder and backup that file, when you put it back in /home after a clean install and open up the terminal you should still be able to access your history. I prefer to re-add the software sources via ppa each time because you'll have to change each one manually to natty anyways but otherwise the file is located at /etc/apt/sources.list which you can just backup

---

### Post by maddbaron on 2011-05-10
> **akand074 said:**
> your terminal commands are stored in ~/.bash_history so just show hidden files in your home folder and backup that file, when you put it back in /home after a clean install and open up the terminal you should still be able to access your history. I prefer to re-add the software sources via ppa each time because you'll have to change each one manually to natty anyways but otherwise the file is located at /etc/apt/sources.list which you can just backup

Thank you, do you if I can do a full fresh reinstall through Ethernet cable or is it best to use a live cd?

---

### Post by akand074 on 2011-05-10
> **maddbaron said:**
> Thank you, do you if I can do a full fresh reinstall through Ethernet cable or is it best to use a live cd?

Best to use a live CD. Definitely.

---

### Post by maddbaron on 2011-05-12
yea thanks

> **akand074 said:**
> Best to use a live CD. Definitely.

---

