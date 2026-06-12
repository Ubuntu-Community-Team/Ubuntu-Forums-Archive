---
title: "kubuntu install"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by smitty423 on 2007-01-22
[FONT="Georgia"][SIZE="3"][COLOR="Red"][/COLOR][/SIZE][/FONT] getting ready to the install of kubuntu going to boot to to the other partition is there anything about kubuntu that i need to know that may be different than Ubuntu on this different os? im a newbie when it comes to this any help would be great full. ):P

---

### Post by temba on 2007-01-22
Hi there,

I'm running kubuntu 6.10.

However, as far as I know, you don't need to install kubuntu as it is *just* ubuntu running KDE instead of GNOME.

Check synaptic to find the KDE packages and install them, then I reckon you just need to change your preferred environment to KDE and voila you have kubuntu.

Please, anyone, correct me if I'm wrong.

cheers

---

### Post by Pobega on 2007-01-22
> sudo aptitude remove ubuntu-desktop
sudo aptitude install kubuntu-desktop
Or if you just want KDE;> sudo aptitude install kde-core

If you decide to go for the full Kubuntu installation, you might have to know that most applications will end up requiring you to install GTK libs, so you probably benefit from just keeping Ubuntu and install kde-core (Or full KDE).

---

