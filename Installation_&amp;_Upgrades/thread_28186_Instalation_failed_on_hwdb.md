---
title: "Instalation failed on hwdb"
date: 2005-04-19
forum: Installation &amp; Upgrades
---

### Post by flurdy on 2005-04-19
Hi,
I am trying to install ubuntu 5.04.
I already got mdk 10.1 installed and was installing ubuntu on a 40gb partition.

The initial install went okay, then the reboot for further installation options.
However a way into the installation it fails.

Its in the process of unpacking a lot of sw, when it pops up with a install failed message. It prompts me to use apt-get to remedy the problem.

When i scroll up I notice that the last package it was trying to set up was hwdb-client-0.6.0ubuntu2. Not sure if this is what failed, but presume so.

I have not been able to fix it tru apt-get, ( accidentally removed the whole ubuntu desktop, as it kept trying to download gnome-art but failing in upacking it as well).
(Hate text based menu tools)

What shall I do? Could the disc have errors? HD or CD ?
Could I get round it via apt-get if I knew where to look?

 ](*,)

---

### Post by TravisNewman on 2005-04-19
It very well could be a bad CD. Try editing your /etc/apt/sources.list and commenting out the line for the CD, then run apt-get update, and "apt-get install ubuntu-desktop" and se if that works.

---

### Post by flurdy on 2005-04-22
Cheers for the tip.

It was not neccessary in the end as I tried a different downloaded ISO, on a different network, on a different machine, burned on a different burner.

And it worked perfectly.

So now I got another drinks coaster...       :)

---

