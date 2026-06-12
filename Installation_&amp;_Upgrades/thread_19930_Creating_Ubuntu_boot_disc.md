---
title: "Creating Ubuntu boot disc"
date: 2005-03-14
forum: Installation &amp; Upgrades
---

### Post by ExemplarUbuntu on 2005-03-14
I have been asked to create a minimal Ubuntu installation that will boot from a Compact Flash card plugged into an IDE socket.

I have the card mounted and I am able to access it from Ubuntu which is running from a hard disc.

I've used grub to install the mbr as follows:

root (hd1,0)
setup (hd1)

and this succeeds. However, every attempt to get the pc to boot from the CF card results in the error:

Invalid or damaged bootable partition

grub never even starts.

I've searched as much as I can for grub related issues but I think there is a missing step that is preventing the disc from booting.

Any suggestions ?

---

### Post by ExemplarUbuntu on 2005-03-16
Does anyone know if GRUB will boot from a CF card in an IDE slot ?

---

### Post by ExemplarUbuntu on 2005-04-01
bttt

---

### Post by feneks on 2005-04-02
Have you seen these pages?

[http://silent.gumph.org/content/4/1/011-linux-on-cf.html](http://silent.gumph.org/content/4/1/011-linux-on-cf.html)
[http://www.linuxjournal.com/comment/reply/7383](http://www.linuxjournal.com/comment/reply/7383)

---

### Post by cgirda on 2005-11-22
I was able to fit ubuntu 5.10 onto a 256MB CF card. After all the
cleanups my FS size is "157MB".  Try "SERVER" installation which
automatically does most of the minimal installation. If not let me know
the point of failure.
        Make sure your mother board is seeing your CF card via adapter.
Don't get confused with OS installation seeing the CF. Get into the BIOS
and see if your mother board is seeing the CF card.

---

### Post by rklauco on 2006-06-27
Did anyone consider using Linux-live scripts?
Slax distro is based on them.
I managed to install server version of Ubuntu and get IceWM and Mozilla up and running in 880MB.
After the script I get 230 MB iso and using scripts I can put them on CD or on the USB flash drive.
Did not yet tried the USB version, but I will this evening and I will post the results.

---

