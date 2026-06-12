---
title: "upgrading: only wants to remove packages"
date: 2009-04-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Tiftof on 2009-04-14
Hi,

I want to try jaunty on my desktop after successful upgrading on my laptop. But upgrading using update-manager or do-release-upgrade on my desktop only wants to remove packages... What could be the problem? I'm using the Belnet mirrors

```
Remove: apturl avant-window-navigator-trunk awn-extras-applets-trunk 
  awn-manager-trunk bicyclerepair bzr bzrtools command-not-found 
  compizconfig-settings-manager deskbar-applet dia dia-common 
  eclipse-pydev fontypython foomatic-db-hpijs gimp gnochm gnome-orca 
  hpijs-ppds hplip-gui ipython java-gcj-compat-dev jockey-common 
  jockey-gtk kdebase-runtime kdebase-runtime-bin-kde4 kdelibs-bin 
  kdelibs5 khelpcenter4 kile konsole libdeskbar-tracker 
  libokularcore1 lilo meld music-applet nautilus-dropbox 
  nautilus-share nvidia-common okular onboard 
  openoffice.org-emailmerge pylint python-apport python-awn-trunk 
  python-beagle python-chardet python-clientcookie python-clientform 
  python-crypto python-egenix-mxdatetime python-egenix-mxtools 
  python-fstab python-gnome2-desktop python-gnome2-extras 
  python-imdbpy python-kaa-base python-kaa-metadata 
  python-launchpad-bugs python-logilab-astng python-logilab-common 
  python-lxml python-mechanize python-numpy python-paramiko 
  python-pexpect python-pkg-resources python-problem-report 
  python-pyatspi python-qt4 python-qt4-common python-rdflib 
  python-reportlab python-setuptools python-sqlite 
  python-uniconvertor python-uno python-virtkey python-wxgtk2.6 
  python-wxgtk2.8 python-wxversion python-xapian python-xkit 
  rhythmbox screen-resolution-extra subdownloader system-cleaner 
  system-cleaner-gtk totem totem-plugins ubufox umbrello usb-creator 
  xbmc xbmc-common xbmc-skin-amped xbmc-skin-backrow 
  xbmc-skin-basics-vision xbmc-skin-basics101 xbmc-skin-ceomr 
  xbmc-skin-clearity xbmc-skin-containment xbmc-skin-mc360 
  xbmc-skin-mediastream xbmc-skin-mint xbmc-skin-pdm xbmc-skin-pm3 
  xbmc-skin-pm3-hd xbmc-skin-vision xbmc-skin-xtv xbmc-web-pm3 
  xscreensaver 


Install: libvolume-id1 ubuntu-minimal vim-common vim-tiny 


```

---

### Post by dino99 on 2009-04-14
hi,
don't worry !!! nothing bad

Have you done: sudo apt-get clean , ...autoclean , ...autoremove first ?
then sudo apt-get install -f before to upgrade to Jaunty ?

You should not use update-manager or dist-upgrade till Jaunty was release (it's a beta at time); prefer to modify the sources.list instead: replace intrepid with jaunty only on the basic(s) ubuntu repo(s), don't allow 'proposed' or personal added repo (tweaks)

the process only want to remove outdated version files. If you don't allow it, then the update process can't be done !!!

So, let's go.

---

### Post by Tiftof on 2009-04-14
But there are no packages to be upgraded. Only these are going to be installed: libvolume-id1 ubuntu-minimal vim-common vim-tiny... that can't be the whole upgrade to jaunty :p

---

### Post by Claus7 on 2009-04-14
Hello,

first of all from which version do you want to upgrade to? You do know that the right procedure is from version to version... I say to you this because I see that you are a Feisty Fawn user.

Have you installed any program that has done something to your dependencies? For example python? When you open synaptic do you get any messages for broken packages?

In case you do not face some of the above, do you get any messages about removing packages when you want to install a new package without having to update? Try to update only one package or install a new one just for testing reasons and see what you get. I updated from dapper to hardy and I do not remember telling me than only three packages will be installed.

Regards!

---

### Post by Tiftof on 2009-04-14
My info was outdated: I am using Intrepid.

When I just change my sources.list to jaunty everywhere, still no updates appear (using Belnet mirror and ftp.ubuntu.com). 

I don't think I installed a package which messed up dependencies...

Synaptic doesn't give me any errors. Installing new packages still works as asual.

---

### Post by Claus7 on 2009-04-14
Hello,

I do not know the exact procedure. Have you tried this and see what it produces?
[http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)

It sais what it wants in order to upgrade.

Regards!

---

### Post by Tiftof on 2009-04-14
I'm using that procedure. Both methods (update-manager and do-release-upgrade) have the same problem.

---

### Post by Tiftof on 2009-04-14
it seems that the ubuntu-desktop package wasn't installed, but installing didn't change anything: I still can't upgrade

---

### Post by dino99 on 2009-04-14
what are the log saying ?
.xsessions
system/administration/view journal
at last dmesg 
var/crash

look at errors and warnings

i suppose you can surf on the net without trouble, else check your connection, wrights ...

---

### Post by Tiftof on 2009-04-16
I looked through those logs but didn't see anything special... What errors should I be looking for?

---

