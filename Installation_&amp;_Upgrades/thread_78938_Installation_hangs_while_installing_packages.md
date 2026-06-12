---
title: "Installation hangs while installing packages"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by Polo78 on 2005-10-19
Hi people,

this is the first time I try Ubuntu and I'm not a Linux expert either, so please be patient. ;) 

I'm trying to install Ubuntu 5.10 in a VMware virtual machine. The installation goes fine until it enters the second phase (after reboot) and it begins installing additional packages. The installation hangs at 95% after displaying the message "Installed language-pack-gnome-it-base". The installation process doesn't go any further but the hard disk still shows intense activity.
After a closer look it turns out that /var/log/base-config-pkgsel.log keeps growing and growing while the installation process is frozen. Tail messages in this log file are:

Should I go ahead and install the packages anyway?
Per continuare, inserisci "Sì"; per abbandonare, inserisci "No": Input non riconosciuto. Inserisci "Sì" o "No".

It sounds like a locale problem: the question is in italian (my locale), but probably the answer is in another language and it is not recognized, hence the infinite loop.

Is there a way to work around this problem without having to fall back to english language?

---

