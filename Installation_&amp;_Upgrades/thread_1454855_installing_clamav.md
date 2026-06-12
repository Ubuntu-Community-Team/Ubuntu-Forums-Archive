---
title: "installing clamav"
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by speedygarth on 2010-04-15
hi there i`m a newby to ubuntu how do i install and update the antivirus?  i downloaded it using ubuntu geek help but the console is saying the package is missing.
i also need help on editing my root password.

---

### Post by mikewhatever on 2010-04-15
Whatever ubuntu-geek help was used, you forgot to link to it, which makes it irrelevant for now.;) To install clam:

*sudo apt-get install clamav clamtk*

and to update:

*freshclam*

The root password in Ubuntu in blank, but for all intents and purposes, your user password is the one to use.

---

### Post by speedygarth on 2010-04-15
thanks for the help, could you advise also on setting the clam to update on its own without me typing in the command from time to time?

---

### Post by mikewhatever on 2010-04-15
Sure. From 'man freshclam':

```
(2) Run as a daemon and check 2 times per day for new database:

              freshclam -d -c 2

```

---

### Post by Jan Greeff on 2010-04-24
I have installed Clam av on my Ubuntu 9.10 via the terminal but how do I get it to work?

---

### Post by cybrsaylr on 2010-04-24
Just curious?
Do many people use clamav?

---

### Post by ottosykora on 2010-04-24
why not? I use it on all my linux installs, just to check this and that sometimes. I have also the windows version on my usb stick as portable version, to carry some small tool for such purposes with me.

---

### Post by claracc on 2010-04-24
> **Jan Greeff said:**
> I have installed Clam av on my Ubuntu 9.10 via the terminal but how do I get it to work?

Simply you run from a xterm: clamscan

In order to update the virus database you have to run: sudo freshclam

---

### Post by speedygarth on 2010-07-23
my clamav is no longer updating its giving this message " your time stamp is in the future"

---

