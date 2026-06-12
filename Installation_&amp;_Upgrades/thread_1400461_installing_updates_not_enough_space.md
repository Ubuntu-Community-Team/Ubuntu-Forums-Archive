---
title: "installing updates not enough space"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by Glenn Owen on 2010-02-06
Hi, I have installed Ubuntu and all is working Ok except when I try to add the suggested updates it is telling me I do not have enough free space. When I set it up I gave Ubuntu a 10GB partition but it does not seem to have worked. How can I add the suggested updates.
thanks Glenn

---

### Post by mikewhatever on 2010-02-07
Well, you need to free some space or change the size of Ubuntu partition.

Try the following to get rid of cached debs and unused dependencies:

sudo apt-get clean
sudo apt-get autoremove

then post the output of:

df -h

---

### Post by Glenn Owen on 2010-02-07
where do I type the commands you mentioned

---

### Post by drs305 on 2010-02-07
> **Glenn Owen said:**
> where do I type the commands you mentioned

Open a terminal: Applications, Accessories, Terminal. It's best to paste commands you get on the forums to avoid typos. CTRL-C to copy outside a terminal (just like Windows), but inside a terminal you have to include "SHIFT", so CTRL-SHIFT-V to paste into a terminal. Even easier - a middle mouse click should paste it!

---

### Post by Glenn Owen on 2010-02-07
thanks

---

### Post by Glenn Owen on 2010-02-07
when I open the terminal and type sudo apt-get clean I get the following result

sudo: unable to resolve host 
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

any help would be great thanks

---

### Post by mikewhatever on 2010-02-08
Close all open windows other then Terminal, and try again.

---

