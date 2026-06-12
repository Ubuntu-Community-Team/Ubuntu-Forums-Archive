---
title: "Can you upgrade from Hoary ISO?"
date: 2005-03-31
forum: Installation &amp; Upgrades
---

### Post by Psquared on 2005-03-31
I don't seem to be able to upgrade from Warty to Hoary using dist-upgrade (please see other posts) so I was wondering if I could download the Hoary PR ISO and do an upgrade that way? In other words, when I boot up the ISO will it give me the option to upgrade an existing installation of Warty? I want to save my data.

If not, what is an easy way to save my data (emails and documents) and do a clean install of Hoary?

Thanks.

---

### Post by arctic on 2005-03-31
i don't know if it works with another iso, but it should (i updated via network)
i wonder what didn't work on your box... have you changed your mirrors from warty to hoary? if yes, then run an

apt-get update
apt-get dist-upgrade

and drink some coffee while your box does all the stuff. ;)

---

### Post by az on 2005-03-31
Burn the iso.

Add the cd to your sources

apt-cdrom add

apt-get update
apt-get dist-upgrade

you will need to change your other sources to point to hoary, too (like, if you have universe enabled....)

---

### Post by Psquared on 2005-03-31
[QUOTE=arctic]i don't know if it works with another iso, but it should (i updated via network)
i wonder what didn't work on your box... have you changed your mirrors from warty to hoary? if yes, then run an

apt-get update
apt-get dist-upgrade

and drink some coffee while your box does all the stuff. ;)[/QUOTE]


I have tried the dist-upgrade three times. Twice with apt-get and once with synaptic. (Yes, I changed my sources from warty to hoary and ran apt-get update) All three times it failed to upgrade to Hoary. I get the same error each time. I even tried to go back to a basic Warty install (uninstall the stuff I added) but it won't work. Each time I tried I cleaned my cache to start over thinking I may have gotten a bad file. I think I have made so many changes that it chokes the upgrade.

Anyway, it sounds like downloading the ISO won't help and I will just have to do a new install. I've got to figure out how to save my data - especially emails.

---

### Post by Psquared on 2005-03-31
[QUOTE=azz]Burn the iso.

Add the cd to your sources

apt-cdrom add

apt-get update
apt-get dist-upgrade

you will need to change your other sources to point to hoary, too (like, if you have universe enabled....)[/QUOTE]

Thanks for the advice. This sounds like it employs the same procedure as doing it online and that has failed for me three times.

I am really stumped by this. I am not a complete novice as I had Fedora Core 2 for six months. I found it too bloated so I switched to Ubuntu. I like Warty, but I would really like to give Gnome 2.10 a try.

---

