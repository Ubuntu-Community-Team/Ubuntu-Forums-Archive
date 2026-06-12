---
title: "Upgrading from 18.04.4"
date: 2020-06-30
forum: Installation &amp; Upgrades
---

### Post by jgw on 2020-06-30
I think the time is coming to upgrade.  I may have a problem on one machine.  I decided, a your or so ago, to install kbuntu over ubuntu for some reason I can't remember.  its been running ok since then (with some small livable problems) but I am wondering what this will do when I try and update.  I would appreciate anybody's thoughts on this one as to how I should handle this.

Thank you................

---

### Post by Impavidus on 2020-07-01
If it's Ubuntu 18.04, it will upgrade to Ubuntu 20.04. If it's Kubuntu 18.04, it will upgrade to Kubuntu 20.04. If it's a mix, it will upgrade to a mix. It shouldn't matter. But release upgrading isn't the most reliable process, so be prepared for a fresh install if things go wrong. The upgrade will be released in about a month.

---

### Post by jgw on 2020-07-15
thank you for the response. 

Is there a way for me to get rid of the kubuntu part before I upgrade!  That, hopefully, might lessen the load and possible mistakes?

---

### Post by MoebusNet on 2020-07-15
@jgw - I think Impavius is right. I believe that your best course will be to 1) back up all of the data you wish to keep (always a good idea anyway) and 2) perform a clean installation of your desired Ubuntu desktop (Ubuntu, Kubuntu, Xubuntu, etc.) then 3) restore your data from your backup. This is what I do whenever I move to a new Long-Term version of Ubuntu. It saves a lot of hair-pulling chasing things that aren't quite right.

---

### Post by ActionParsnip on 2020-07-16
If you remove the KDE and plasma stuff it should remove the KDE bits but there is no problem using a mix of KDE and Gnome apps

---

### Post by Impavidus on 2020-07-16
Have you installed the Kubuntu parts by installing the kubuntu-desktop metapackage? In that case, remove the metapackage, then use autoremove. In an ideal world, that will remove all Kubuntu bits and get you back to a clean Ubuntu 18.04 system. Of course, we don't live in an ideal world.

---

### Post by dino99 on 2020-07-16
With synaptic: search for the installed 'kubuntu' 'kde' 'plasma' packages, then select them for complete removal; you will then get a possible list of sub dependencies to purge too.
As said earlier, use autoremove to clean the system; but the best solution is a fresh install anyway.

---

