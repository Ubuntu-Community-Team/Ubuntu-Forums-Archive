---
title: "Has anyone else got this problem?"
date: 2009-12-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by woodbj on 2009-12-16
A white background that cannot be changed. (see screenshot)

---

### Post by ranch hand on 2009-12-16
Nope, all four installs have a different color window background.

---

### Post by VMC on 2009-12-16
Does everything work. Just can't change background?

Any log files in disarray? When you right-click on the desktop, what happens?

---

### Post by woodbj on 2009-12-16
I can right click my background like normal and pick a new background but when I click close it flash the background for half a sec then goes back to that.. Also when I logout, restart, shutdown etc. I see the normal background until it continues to shutdown.

---

### Post by phillw on 2009-12-16
I had that happen when I tried this one out --> [http://ubuntuforums.org/showthread.php?t=1349674](http://ubuntuforums.org/showthread.php?t=1349674)

dunno if it is one of the libraries that did it. I had a go at reversing them, but just did a fresh install & everything was okay.

You haven't been accepting partial updates, have you ?

Phill.

---

### Post by woodbj on 2009-12-16
> **phillw said:**
> I had that happen when I tried this one out --> [http://ubuntuforums.org/showthread.php?t=1349674](http://ubuntuforums.org/showthread.php?t=1349674)

dunno if it is one of the libraries that did it. I had a go at reversing them, but just did a fresh install & everything was okay.

You haven't been accepting partial updates, have you ?

Phill.

Argh yes I have been using that ppa.. and I may have let one or two partial updates through :-P

---

### Post by cariboo on 2009-12-16
I have the same problem running Lucid in a vm, I've got the same ppa enabled. I haven't had time to track down what the problem is though. I did have one other problem, I tried to open nautilus, and it just check loading more of them. I finally had to power-off the vm

---

### Post by Atzu on 2009-12-16
I do... using virtualbox.. and when i try changing the wallpaper it tries opening File Manager or something and its very annoying... it was after updating

---

### Post by phillw on 2009-12-16
There were issues like that raised with the PPA, such as killing gksudo functions. I tried to back mine out, but just a did a fresh install & rsynced my /home area back over from my 9.10 onto the 10.04 test partition.

I've got a growing list of partital updates available - but am currently avoiding them until I can closely follow the sticky on partital upgrades.

Phill.

---

### Post by phillw on 2009-12-16
> **woodbj said:**
> I can right click my background like normal and pick a new background but when I click close it flash the background for half a sec then goes back to that.. Also when I logout, restart, shutdown etc. I see the normal background until it continues to shutdown.


Yup, that's what i was seeing.

Phill.

---

### Post by Darkshade on 2009-12-16
I had the same problem with that ppa. Ended disabling it and manually downgrading all the packages the hard way with aptitude since Synaptic wanted to wipe half my system when I tried to downgrade them. The problem, I believe, is that there is a newer version of nautilus in the lucid repos than the one in the ppa. Maybe wait a while and it'll get fixed, I personally couldn't since it's my main OS.

---

### Post by VMC on 2009-12-17
@woodbj.

If you tried the "[GTK Enhancements]("http://ubuntuforums.org/showthread.php?t=1349674")" then hopefully you can back out of it to fix your issues. I didn't apply for that testing, and I'm ok.

---

### Post by durand on 2009-12-17
Doh, I've got the same problem caused by that PPA. Downgrading will be fun :D (sigh..)

---

### Post by xir_ on 2009-12-17
i've got this too, has anyone submitted a bug report yet?

i had a look but couldn't find one.

---

### Post by Darkshade on 2009-12-17
Ok since many people seem to have that problem here's the way I downgraded:

**_READ FIRST OR CLOWNS WILL EAT YOU_: The reason I did this was because Synaptic wanted to wipe about 200 packages when I tried to downgrade them. Using aptitude everything went smooth. NOTE: This worked for me about 24 hours ago, if any of the packages in the list were updated during that time it will most likely not work. In that case go to Synaptic and check the available versions of the package that's causing you trouble, then replace the one in the command posted below with the current version and run it again. Abort the operation if aptitude wants to remove a package (or packages). Proceed at your own risk, it worked for me but may not work for you. The only guarantee I can give you is that there was no harm intended, just sharing my far-from-perfect solution.**


**1.**
```
gksudo software-properties-gtk
```
Enter your password, go to "Other Software", uncheck the ubuntu-desktop-ppa, close the application. This will disable the ppa.

**2.**
```
sudo aptitude update
```
Self-explanatory.

**3.**
```
sudo aptitude install fontconfig=2.6.0-1ubuntu12 fontconfig-config=2.6.0-1ubuntu12 gtk2-engines-pixbuf=2.19.1-1 libfontconfig1=2.6.0-1ubuntu12 libgail18=2.19.1-1 libgail-common=2.19.1-1 libgtk2.0-0=2.19.1-1 libgtk2.0-bin=2.19.1-1 libgtk2.0-common=2.19.1-1
```
This will downgrade the packages to the versions shipped with Lucid without removing anything else. When you're finished just reboot and everything should work fine again.

---

### Post by zika on 2009-12-17
> **Darkshade said:**
> Ok since many people seem to have that problem here's the way I downgraded:

**_READ FIRST OR CLOWNS WILL EAT YOU_: The reason I did this was because Synaptic wanted to wipe about 200 packages when I tried to downgrade them. Using aptitude everything went smooth. NOTE: This worked for me about 24 hours ago, if any of the packages in the list were updated during that time it will most likely not work. In that case go to Synaptic and check the available versions of the package that's causing you trouble, then replace the one in the command posted below with the current version and run it again. Abort the operation if aptitude wants to remove a package (or packages). Proceed at your own risk, it worked for me but may not work for you. The only guarantee I can give you is that there was no harm intended, just sharing my far-from-perfect solution.**


**1.**
```
gksudo software-properties-gtk
```
Enter your password, go to "Other Software", uncheck the ubuntu-desktop-ppa, close the application. This will disable the ppa.

**2.**
```
sudo aptitude update
```
Self-explanatory.

**3.**
```
sudo aptitude install fontconfig=2.6.0-1ubuntu12 fontconfig-config=2.6.0-1ubuntu12 gtk2-engines-pixbuf=2.19.1-1 libfontconfig1=2.6.0-1ubuntu12 libgail18=2.19.1-1 libgail-common=2.19.1-1 libgtk2.0-0=2.19.1-1 libgtk2.0-bin=2.19.1-1 libgtk2.0-common=2.19.1-1
```
This will downgrade the packages to the versions shipped with Lucid without removing anything else. When you're finished just reboot and everything should work fine again.Did anyone try a script called [ppa-purge](https://launchpad.net/ppa-purge/+packages) from xorg-edgers that does exactly that: removes effect of given ppa to Your system...? I think it works (also) for (most) ppa's (other then xorg-edgers) ...

---

### Post by woodbj on 2009-12-18
ppa-purged ubuntu-desktop, all is good now thanks

---

### Post by xir_ on 2009-12-18
as of this morning i no longer get gksudo errors inside of the virtual box, although the background is still broken.

---

