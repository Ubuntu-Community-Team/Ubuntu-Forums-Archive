---
title: "Held Back Pakages from Upgrade"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andyrogers2008 on 2009-10-07
Would anyone be able to explain why these packages have been held back from an upgrade:-

The following packages have been kept back:
  desktop-switcher evolution-plugins grub-common grub-pc
  libaccess-bridge-java-jni linux-generic linux-headers-generic
  linux-image-generic

Also if I try to do dist-upgrade I get this:-

The following NEW packages will be installed
  cheese go-home-applet libaccess-bridge-java libclutk-0.2-0 libfakekey0
  liblauncher-0.1-0 libnetbook-launcher-0 libpst4 linux-headers-2.6.31-12
  linux-headers-2.6.31-12-generic linux-image-2.6.31-12-generic maximus
  netbook-launcher ubuntu-netbook-remix ubuntu-netbook-remix-default-settings
  webfav


Could anyone explain why netbook-remix would be installed etc?

Thanks

Andy

---

### Post by Roger E Critchlow Jr on 2009-10-07
The grub stuff comes because the latest grub2 packages are forcing removal of the old grub.  Search for grub in synaptic, remove the packages of the old generation of grub, update the packages of the new generation, and you should be good to go.

No good explanations for the rest.  

If the package mix seems too confusing, I'll just wait a few hours, reload, and see if it makes more sense.

-- rec --

---

### Post by ranch hand on 2009-10-07
While you are in synaptic, do your update from there.  The kernal stuff has been being updated for me there after apt-get held them back.

---

### Post by andyrogers2008 on 2009-10-07
I have removed desktop-switcher from my system now with apr-ger autoremove desktop-switcher which has stopped the netbook packages appearing on a dist-upgrade.

My next question is should network-remix packages including desktop-switcher be needed by my Karmic install on my normal laptop or are these additional packages which are not needed which are not installed by default.

Thanks


Andy

---

