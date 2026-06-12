---
title: "Plymouth disconnected on mountall - drops to command line"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by GBrogan on 2010-10-10
just upgraded from 10.4 - no love on bootup with 10.10 - any ideas?

---

### Post by dino99 on 2010-10-10
copy/paste each line into console, one by one, then "enter":

sudo apt-get update
sudo apt-get install -f

sudo dpkg --configure -a
sudo dpkg-reconfigure jockey
sudo dpkg-reconfigure plymouth
sudo dpkg-reconfigure gdm

---

### Post by GBrogan on 2010-10-10
thanks dino - nothing on jockey, though. I was able to get a low res boot - i'm thinking there's something going on with my nvidia in x - getting ready to check it out.

---

### Post by dino99 on 2010-10-10
remove xorg.conf

sudo rm -f /etc/X11/xorg.conf

then reboot and check driver activation (system admin addiotional driver), nvidia-current might be activated

---

### Post by tjapko on 2010-10-21
I have tried all of the commands mentioned without any effect. There is no xorg.conf that I can remove and I don't have nvidia on this machine.

I upgraded my msi Wind Notebook from Lucid to Maverick (twice, I have a backup of Lucid) and get mountall: Plymouth command failed and mountall: Disconnected from Plymouth. ( That's why I am here).

A fresh install prints similar messages but gives me a GUI after some hesitation.

Am I in the wrong place?

---

### Post by jimbo99 on 2010-10-21
> **dino99 said:**
> copy/paste each line into console, one by one, then "enter":

sudo apt-get update
sudo apt-get install -f

sudo dpkg --configure -a
sudo dpkg-reconfigure jockey
sudo dpkg-reconfigure plymouth
sudo dpkg-reconfigure gdm

If he is at the command line he can't copy and paste those commands.  And, generally at this point you can't even type at the login prompt in order to log on.

The only solution I have to both above is to ssh into it, if you installed ssh to begin with.

---

