---
title: "Installing XChat"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by rruelas on 2007-01-24
I'm pretty new to Ubuntu (I switched from Fedora Core recently, since it was giving me problems) and i've been trying to install XChat on this. I've tried typing "sudo apt-get install xchat" but it gave me no results. I can't seem to find a version of XChat that fails to satisfy the dependencies.
To make it short, i'm looking for how to install XChat.

I'd greatly appreciate it if anyone could help me. Thanks in advance.

---

### Post by wpshooter on 2007-01-24
Why don't you go to Synaptic and do a NAME search for xchat and see what comes up and then install it from there.  Synaptic will do all of that stuff for you.  If it can be installed from Synaptic, Update Manager, or add/remove programs, there's a good likelyhood that you don't need it installed.

---

### Post by bruenig on 2007-01-24
> **wpshooter said:**
> Why don't you go to Synaptic and do a NAME search for xchat and see what comes up and then install it from there.  Synaptic will do all of that stuff for you.  If it can be installed from Synaptic, Update Manager, or add/remove programs, there's a good likelyhood that you don't need it installed.
Not sure about that analysis.

But anyways, xchat is in the universe repository which isn't enabled by default. If you haven't yet messed with your sources.list, the following command should enable all the repositories, update, and then install xchat.
```
sudo sed -e 's/# deb/deb/g' -e 's/edgy universe/edgy universe multiverse/g' -e 's/edgy-security universe/edgy-security universe multiverse/g' -i.backup /etc/apt/sources.list && sudo apt-get update && sudo apt-get install xchat
```
Copy and paste all of that at once on one line.

---

