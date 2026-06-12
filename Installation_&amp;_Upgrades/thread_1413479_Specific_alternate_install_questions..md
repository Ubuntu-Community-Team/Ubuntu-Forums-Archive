---
title: "Specific alternate install questions."
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by Linuxperiment on 2010-02-22
EDIT: Ok I've just been revising the scripts and stuff so I can figure out what exactly I need.

Basically what I'm trying to figure out now is how to get a "working" version of Ubuntu using an alternate install. I plan to install a base system and have the synaptic package manager and wireless working so I can install all my application from there instead of just doing a command line. This is the "code" I have so far:

```
sudo apt-get update

sudo apt-get install gnome-core gdm synaptic xorg acpi-support gnome-volume-manager 
gnome-power-manager powernowd compiz gnome-screensaver xscreensaver menu gnome-utils 
gnome-system-tools libgnomevfs2-extra smbfs gnome-app-install app-install-data-commercial
update-manager update-notifier jockey-gtk nautilus-sendto nautilus-share nautilus-cd-burner
ubuntu-restricted-extras

sudo apt-get install network-manager-gnome
```

---

### Post by darkod on 2010-02-22
Do you mean a minimal install? The alternate install cd is installing the same (more or less) version of ubuntu as the standard desktop livecd. The only difference s that using the alternate install cd the installer is text based, not GUI.
Most of the packages you mention would already be installed with the alternate install too, I think.

---

### Post by Linuxperiment on 2010-02-22
> **darkod said:**
> Do you mean a minimal install? The alternate install cd is installing the same (more or less) version of ubuntu as the standard desktop livecd. The only difference s that using the alternate install cd the installer is text based, not GUI.
Most of the packages you mention would already be installed with the alternate install too, I think.

Oh I had no idea. I was hoping that the alternate install would let me choose the packages that I wanted instead of the typical included applications. I guess it is supposed to be the minimal install not the alternate one. Anyways, are any of those scripts "acceptable"?

---

### Post by darkod on 2010-02-22
dist-upgrade is for upgrading from version to the next as far as I know. So you don't need it because I guess you will use the latest version during install anyway.
As for the rest, the command to install is sudo apt-get install packagename and you can use it for as many packages as you want separated by space.
But it looks better to install just synaptic first and then use that for further software install.
Also, if you do use the minimum install don't forget you also need ubuntu-desktop to have desktop GUI if you want it. I'm not sure synaptic is worth anything without desktop GUI because it's a GUI tool.
Otherwise, the commands look just fine and consider the above. I don't know the packages in that detail and can't tell you much more.

---

### Post by Linuxperiment on 2010-02-22
> **darkod said:**
> dist-upgrade is for upgrading from version to the next as far as I know. So you don't need it because I guess you will use the latest version during install anyway.
As for the rest, the command to install is sudo apt-get install packagename and you can use it for as many packages as you want separated by space.
But it looks better to install just synaptic first and then use that for further software install.
Also, if you do use the minimum install don't forget you also need ubuntu-desktop to have desktop GUI if you want it. I'm not sure synaptic is worth anything without desktop GUI because it's a GUI tool.
Otherwise, the commands look just fine and consider the above. I don't know the packages in that detail and can't tell you much more.

So does the alternate install already come with the desktop GUI or do I have to do it myself? How much different is the alternate and minimal install if I use cli?

---

### Post by wojox on 2010-02-22
You can see all the packages and what they pull in for dependencies here: [http://packages.ubuntu.com/karmic/](http://packages.ubuntu.com/karmic/)

---

### Post by Linuxperiment on 2010-02-22
> **wojox said:**
> You can see all the packages and what they pull in for dependencies here: [http://packages.ubuntu.com/karmic/](http://packages.ubuntu.com/karmic/)

Alright I'll take a look at that then figure out what packages I need. I have a feeling the code I put up is way too much stuff to type.

---

### Post by adam814 on 2010-02-22
You're right, by default the alternate install CD just installs the normal desktop version.  It does however have a menu option to do a "command line install" which is a very minimal system.  I did this some time back with Debian and added only the packages I needed.

I'm not sure what packages you will and won't need though, with that one I used LXDE instead of GNOME and I didn't need wireless.

---

### Post by Linuxperiment on 2010-02-22
Oh okay thanks for the clarification. Anyways my code has been revised. I'm pretty sure that will include everything other than applications like OpenOffice, Internet, etc.

Can anyone comment on my code if I'm doing it in the right order or anything like that?

---

