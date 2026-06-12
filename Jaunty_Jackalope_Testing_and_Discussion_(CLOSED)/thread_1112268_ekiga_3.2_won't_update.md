---
title: "ekiga 3.2 won't update ?"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by xens on 2009-03-31
Hello, I've noticed that Ekiga won't update, the 3.2 is available and I'm stucked with 3.02.


xens@xens-laptop:~$ sudo apt-get dist-upgrade
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Calcul de la mise à jour... Fait
Les paquets suivants ont été conservés*:
  ekiga
0 mis à jour, 0 nouvellement installés, 0 à enlever et 1 non mis à jour.
xens@xens-laptop:~$

---

### Post by taavikko on 2009-03-31
Please use "LANG=C command" on CLI when copy&paste

Not all of us speak French :(

It might be that Ekiga's dependencies aren't yet been build, so wait a day or two, so it should be upgraded by then.

---

### Post by xens on 2009-03-31
thanks for the command I didn't know it!

xens@xens-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  ekiga
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
W: Duplicate sources.list entry [http://www.e-oss.net](http://www.e-oss.net) ./ Packages (/var/lib/apt/lists/www.e-oss.net_ubuntu_gutsy_._Packages)
W: You may want to run apt-get update to correct these problems
xens@xens-laptop:~$

---

### Post by mc4100 on 2009-03-31
I saw it was held back a while ago, so I update it manually in synaptic, which worked fine. It had to replace libopal, or something, with a newer version -- but I can't be sure.

---

### Post by xens on 2009-03-31
mc4100

thanks for the tips! Updated manually from synaptic and it works! this update fixed the sound problem I had in the previous release, I'll test it now :]

---

### Post by alphacrucis2 on 2009-03-31
> **xens said:**
> mc4100

thanks for the tips! Updated manually from synaptic and it works! this update fixed the sound problem I had in the previous release, I'll test it now :]

I notice in update manager on Jaunty, after a recent update it has now listed ekiga as a "grayed out" package under the Distribution updates heading. I guess that means the package is available but can't be installed due to dependencies?

---

### Post by Ramptu on 2009-03-31
I also noticed that. Ekiga and gstreamer0.10 plugins-bad will not allow me to check the box to intall updates. If we hang tight will it eventually clear itself up?

---

### Post by dirtylobster on 2009-03-31
I installed it from the CLI with 'sudo aptitude dist-upgrade'

---

### Post by seppl82 on 2009-04-01
What are your expierences with the latest version of ekiga?

My Expierence is that i can't connect to my german provider 1&1 since the update.

I've got the error message 403 Forbidden (No RFC 1918 IP allowed).

The Previous Version worked out of the box.

---

### Post by rdoolen on 2009-04-01
I can't register my Gizmo acount. I don't even get an error; just nothing. This works fine in Ekiga 2 on another computer.

---

### Post by seppl82 on 2009-04-02
Which Protokoll Gizmo is using?

---

### Post by rdoolen on 2009-04-02
It started working yesterday. I am not sure why.

I am using my Gizmo number at proxy01.sipphone.com

---

### Post by xens on 2009-04-02
I use ekiga with the ekiga sip proxy (user@ekiga.net), it works fine.

---

