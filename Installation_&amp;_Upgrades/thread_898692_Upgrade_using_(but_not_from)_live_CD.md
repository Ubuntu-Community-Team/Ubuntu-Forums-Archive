---
title: "Upgrade using (but not from) live CD"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by LittleKoy on 2008-08-23
Hello :)
I'm using Intrepid, and I can't access to my account anymore but from console, and I was hoping that an upgrade could fix it. The problem is that neither wired or wireless seem to work using the console (ctrl+alt+f1 from login screen), while I can connect using the live cd.
So, is there a way to upgrade my Intrepid running a live cd?

---

### Post by Pumalite on 2008-08-23
Have you tried going into Recovery Mode?

---

### Post by LittleKoy on 2008-08-23
Y, I did, but no luck :( 
Using the live cd it connects to ethernet automatically, while into recovery mode it doesn't, it just shows a lot of strange output

---

### Post by Pumalite on 2008-08-23
Try to run:
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by LittleKoy on 2008-08-23
Sorry but I'm already using Intrepid, which is the last distro... Also, wouldn't a simple apt-get upgrade from a live session try (uselessly) to upgrade the live session itself, and not my real  installation?

---

