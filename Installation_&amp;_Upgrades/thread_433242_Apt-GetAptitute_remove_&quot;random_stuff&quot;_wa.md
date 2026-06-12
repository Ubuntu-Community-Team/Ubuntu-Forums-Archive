---
title: "Apt-Get/Aptitute remove &quot;random stuff&quot; wants to remove ubuntu-desktop"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by turbotom on 2007-05-04
Hey everyone,
I have a strange problem. I upgraded from edgy to feisty and had a problem with the hotkey-setuphotkey-setup package not installing. Whenever I tried to remove it, apt-get/aptitude etc. wanted to also remove the ubuntu-desktop package. I thought that it was a bit of a strange dependency, but I wasn't too concerned.
Now, I just tried to remove xvncviewer to install xvnc4viewer and it wanted to remove ubuntu-desktop again!
So, something strange is going on...

I'm not super skilled with ubuntu or linux, so if you have some clue as to what the deal is, let me know!
Thanks a bunch.

---

### Post by aidanr on 2007-05-04
ubuntu-desktop is a metapackage, it is safe to remove with the caveat that you may have issues dist-upgrading if you don't have it

---

### Post by chocbar31 on 2007-05-04
aidanr, you took the words right outta my mouth...darnitt. Gotta be faster these days. lol

Just do a:

sudo apt-get install ubuntu-desktop

Once you have finished the un-install of the other application, if you feel freaked by that message.

---

### Post by turbotom on 2007-05-04
Thanks for the quick response!

I was worried that it might do bad things. ;)

Now onto other problems.

---

### Post by Backharlow on 2007-10-19
There's more to this. Maybe I'm doing something wrong here but for example.. I removed Compiz, and its extra toys, which in turn removed ubuntu-desktop. But, then when I reinstalled ubuntu-desktop it forced me to reinstall Compiz along with everything else that is tethered to ubuntu-desktop, all of which I had removed over the lifetime of the distro. Yuck. As you can see below, re-apt-getting ubuntu-desktop forces me to sync a bunch of other applications that I didn't want in the first place, but happen to ship with ubuntu-desktop.
```
$ sudo apt-get install ubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnome-compiz-manager0 libberylsettings0 libemeraldengine0
  libberyldecoration0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  brltty-x11 compiz compiz-core compiz-gnome compiz-gtk compiz-plugins
  desktop-effects gnome-orca libbrlapi1 libgail-gnome-module libgnome-speech3
  python-orca-brlapi totem-mozilla
Suggested packages:
  python-gnome-orca-dbg python-pyorbit-dbg python-gtk2-dbg python-gnome2-dbg
  python-glade2-dbg python-orca-brlapi-dbg
The following NEW packages will be installed:
  brltty-x11 compiz compiz-core compiz-gnome compiz-gtk compiz-plugins
  desktop-effects gnome-orca libbrlapi1 libgail-gnome-module libgnome-speech3
  python-orca-brlapi totem-mozilla ubuntu-desktop
0 upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
Need to get 1222kB of archives.
After unpacking 8823kB of additional disk space will be used.
Do you want to continue [Y/n]?
```

---

