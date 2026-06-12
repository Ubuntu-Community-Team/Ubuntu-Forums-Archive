---
title: "Upgrading within alpha releases and held back packages"
date: 2009-03-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by yodermk on 2009-03-23
I installed Jaunty at Alpha4 and have been running 'apt-get upgrade' regularly.  Someone at work told me that it's good to do a dist-upgrade to upgrade between alphas, but I've never seen any other references to that.  Is anything special needed to apply some changes beyond an apt-get upgrade?

Also I've been getting this for quite a while:
```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  blender brasero compiz compiz-core compiz-gnome compiz-plugins eog espeak espeak-data evolution evolution-common
  evolution-exchange evolution-indicator evolution-plugins exiv2 gedit gedit-common gimp gimp-data gnome-themes grub
  gstreamer0.10-plugins-bad gwenview jockey-common jockey-gtk jockey-kde kpackagekit libbrasero-media0 libcompizconfig0
  libespeak1 libgimp2.0 libgpgme11 libkexiv2-7 libsearchclient0 libstreamanalyzer0 libstreams0 libstrigihtmlgui0
  libstrigiqtdbusclient0 linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic
  openoffice.org-base-core openoffice.org-calc openoffice.org-core openoffice.org-draw openoffice.org-gnome
  openoffice.org-gtk openoffice.org-impress openoffice.org-kde openoffice.org-math openoffice.org-writer python
  python-beagle python-dev python-kde4 python-launchpad-integration python-minimal python-uniconvertor python-uno rhythmbox
  strigi-client strigi-daemon totem totem-common totem-gstreamer totem-mozilla totem-plugins ubuntu-desktop update-manager
  update-manager-core vim-common vim-gnome vim-gui-common vim-runtime vim-tiny virtualbox-ose xchat xchat-common
  xubuntu-default-settings xubuntu-desktop xulrunner-1.9 xulrunner-1.9-gnome-support
0 upgraded, 0 newly installed, 0 to remove and 83 not upgraded.

```

What is keeping these packages back? I want to get the new kernel, hoping that it has ATI DRI/DRM. (I'm tired of super-slow 2D and no Xv!)

Thanks

---

### Post by ubu-for on 2009-03-23
Did you already try to update with the Gnome GUI (System/System Administration/Update Manager)?

---

### Post by andrewabc on 2009-03-23
There is no need to specifically dist-upgrade between alphas/betas/rc/final.
Although sometimes an update can come out which will cause partial upgrade or dist upgrade. Make sure to do research before doing so because it could break your computer.

That is a lot of updates held back.

I'd probably wait until Thursday/Friday this week and download beta live cd. Backup important files, and then try to upgrade and see if it works. If it doesn't then format/install fresh beta.

---

### Post by taavikko on 2009-03-23
dist-upgrade is used for installing new upgrades and their new dependencies.

```
:~$ alias
alias ls='ls --color=auto'
alias upgrade='sudo apt-get update && sudo apt-get dist-upgrade'
```

And that's the one I use for entire devel-cycle.

---

### Post by jerrylamos on 2009-03-23
update alone hasn't been doing it for me.  I frequently get "partial" notifications.  When I get those then I do:

sudo apt-get update && sudo apt-get dist-upgrade 

No clue why upgrade should be needed within the alpha series of jaunty, but for me, it is.  I've got four test pc's (year old, older, older yet, pretty old) sometimes one will get "partial" from upgrade and another won't.  The sudo apt-get ... usually bails out the situation.

By the way, they are all at least dual boot in case one of the jaunty updates doesn't work.

Jerry

---

### Post by yodermk on 2009-03-24
> **taavikko said:**
> dist-upgrade is used for installing new upgrades and their new dependencies.

Sweet, that explains it. thanks. I guess I was thinking apt-get was like yum and automatically pulled any new dependencies.

Anyway, I did that this afternoon and now my slow video problems are fixed! Happy now!

---

