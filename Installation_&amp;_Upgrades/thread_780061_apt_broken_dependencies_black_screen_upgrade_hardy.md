---
title: "apt broken dependencies black screen upgrade hardy"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by bamboomy on 2008-05-03
Hi, sorry for the uncoherent title but this is what I would look for on google (which I did, but allas, no solution).

so far the introduction, now my problem:

as far as I can remember I upgraded from gutsy to hardy which booted perfectly into X and all with the nice bird and all, no problem there.

The first thing that went wrong was the use of my printer, the (usb )printer was recognized but after sending jobs to it nothing but silence followed while printing in windows is no problem.

I followed [this guide]("http://ubuntuforums.org/archive/index.php/t-374898.html").

which I followed in gutsy with as result a printer that took jobs (the first right test-page is still a memory I cherish). I rebooted hardy a couple of times without a problem. I turned my computer off for a reason I no longer remember and the next boot the update icon informed me about the fact that updates where available. I clicked on the icon but nothing showed up. I vaguely remember that maybe on another desktop the installer was started, to cut a long story short, I suppose I rebooted during an install.

The next boot gdm refused to start up. I had a black screen with a 'thinking' pointer so my X worked, after switching to one of the non-graphical consoles 'top' reported two gdm's running (which is one to much in my point of view). I tried killing one, setting gdmgreeter to gdmlogin in /etc/gdm/gdm.conf: no vail.

I fired up links to look for solutions and other people reported the same problem. I don't have the exact link anymore and on first sight I can't find the page google directed me to but I must have tried to install something only to see that apt was broken.

When I try apt-get install (something) apt wants me to run apt-get -f install which gives the 'error.txt' attached

I read on a forum about hardy that apt-get update, apt-get upgrade and apt-get dist-upgrade from within a chrooted environment with the gutsy cd-rom environment would fix the apt problem but I came as far as apt-get update with a error similar to 'error.txt'

somewhere else I read that dpkg --remove or apt-get remove would be able to solve things but they don't. I attached the attempt to install evolution and remove evolution-common to the post.

Apt asks me nicely to do "Try 'apt-get -f install' with no packages (or specify a solution)." but allas I can't come up with a decent one it seems.

I know that reïnstalling ubuntu would solve my problem but I can't accept that. I want to solve this problem otherwise.

Is this possible ?

kind regards,

S.

---

### Post by ddrichardson on 2008-05-04
You should [report this as a bug]("https://bugs.launchpad.net/evolution"), something similar happened with upgrades to Edgy.

Some found that a hack around was to ```
apt-get -f install
``` each of the packages in sequence then alternate between that and forced upgrades but I really would not recommend it.

---

