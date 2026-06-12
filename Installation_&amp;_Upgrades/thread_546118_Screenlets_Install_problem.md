---
title: "Screenlets Install problem"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by puke929 on 2007-09-08
Hi,

Ive just downloaded screenlets 0.0.10 and have it in a tar.bz2 folder on my desktop. could anyone give some advice in how to install it because i am no good with this terminal stuff and am finding it very taxing.

cheers, luke

---

### Post by puke929 on 2007-09-08
Please make it as simple as possible... dont prosume anything becouse im no good at much.. at the moment anyway.. all help would be awsome

---

### Post by puke929 on 2007-09-14
anyone?!?!

---

### Post by groggyboy on 2007-09-16
you've downloaded teh source code, which isn't too hard if you know what your doing.  however, it would be easier to install screenlets through a repository.  there is one here: [http://hendrik.kaju.pri.ee/ubuntu/]("http://hendrik.kaju.pri.ee/ubuntu/").

fire up synaptic package manager (System >> Administration >> Synaptic).  add the repository by going to Settings >> Repositories.  Select the second tab (Third Party Software) and click the Add... button.  Paste this in: ```
*deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty all*
``` and click Add Source.  Right click [this link]("http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg") and save to the Desktop.  Now click on the Authentication tab in Synaptic.  Import the key you just saved to your desktop (named F854AFD7.gpg).  Close the settings window.  Reload your repository, and then search for Screenlets.  Voila!

Hope that helps.

---

