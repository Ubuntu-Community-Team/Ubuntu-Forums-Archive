---
title: "Upgrade from Hoary to Breezy did not go well"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by jmooney on 2005-10-16
First off, my system is triple-boot with SuSE handling the boot up via Grub.

Using Synaptic, I attempted to update from Hoary to Breezy.  Many packages didn't go it, postfix was broken, gnubiff stopped working, etc.  From the command prompt did apt-get update, apt-get upgrade, apt-get dist-upgrade and a whole bunch of packages went in that Synaptic did not install (same repository list for both, although I did select the "smart update" option in synaptic).

With the exception of gnubiff and postfix not working, and some missing features on gnome that I had grown to like with hoary, it looked like it was working OK.  I had to manually edit the GRUB menu.lst in the SuSE install to get it to point to the new kernel (Actually, I installed both the 386 and 686 varieties) but no big deal there.

Then, after installing some updates to Gnome (I'm guessing that was the cause), nvidia-glx got real flaky.  Generally, it just would not start and drop me back to the command prompt.  Now, if I type in "startx", it fires up just fine - nVidia boot logo, glxgears runs good, etc., but I can't get to the gnome "human" login screen.  As a result, I lose all of the funtionality associated with gdm (like the logoff menu).

If I go in a do a dpkg reconfigure on x.org and either fall back to the "nv" driver or disable glx, it works, but I don't have openGL.

I don't have alot of rogue packages installed, but I am using the legacy nvidia-glx driver (computer has a GeForce2 Ti card).


Any thoughts?

---

### Post by kvidell on 2005-10-16
Upgrading thusly destroyed one of my servers, as well.
I backed up the rc files from my homedirectories on it, and anything custom edited in /etc and did a fresh install.
It runs very, very well now. :-\
The only OS I ever trust to upgrade from one version to the next without a format is OSX. I've never had any luck with Windows or any Linux distribution upgrade I've ever tried.
- Kev

---

### Post by remmelt on 2005-10-16
Have you tried starting gdm instead of startx? 

sudo gdm

---

### Post by jmooney on 2005-10-16
[QUOTE=remmelt]Have you tried starting gdm instead of startx? 

sudo gdm[/QUOTE]

Yup, even sudo .../init.d/gdm   no dice

---

### Post by jmooney on 2005-10-16
Ok, this seems to have fixed the nvidia-glx-legacy issue:

First, following some advice elsewhere in this forum, I disabled "dri" and "GLcore" in the xorg.conf  (can do this with "sudo dpkg-reconfigure xserver-xorg
" just follow the prompts).

Enabled glx (while doing the reconfig)

then "sudo apt-get install ubuntu-desktop"

This dropped about 107M of new/replacement files on my computer.

After that, the nvidia driver seems to have worked.

Next up, I'll see if gnubiff will work I guess.

---

