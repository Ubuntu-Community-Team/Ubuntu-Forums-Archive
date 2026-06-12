---
title: "I am utterly screwed"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by Fabled One on 2011-05-03
Ever since I uninstalled pulseaudio (apparently the most important piece of software in history) my 10.10 installation is completely boned. 

I just want to reinstall. But I can't. When I try the alternate installer, it says it failed to create the partition for /home. 

I want to just wipe the hdd, but gparted does not work at all. I tried in on the live cd for 10.10, 11.04 and the live gparted, but it just wont run.

PLEASE someone tell me how to destroy the entire hard drive. Otherwise I'm gonna buy a new hdd. I can't believe this is so difficult.

I have been looking for about 2 weeks. PLEASE PLEASE PLEASE PLEASE just how do I delete everything.

---

### Post by tprice99 on 2011-05-03
If You could, can you please try these codes?

           killall pulseaudio

           sudo apt-get remove pulseaudio

Please advise if this works!

---

### Post by Rasa1111 on 2011-05-03
Why are you using Gparted?

Why not just use the installer and install over the whole HDD? 

That doesn't work either?
Or haven't you tried it? 

I've never not been able to wipe a HDD with a fresh install using the installer. 

Good luck.

---

### Post by tgalati4 on 2011-05-03
Uninstalling pulseaudio will definitely break things.  As a framework, it's thoroughly embedded now into the Ubuntu system.  Why did you need to remove it in the first place?

---

