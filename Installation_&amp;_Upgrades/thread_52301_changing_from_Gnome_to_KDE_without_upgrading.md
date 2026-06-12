---
title: "changing from Gnome to KDE without upgrading"
date: 2005-07-27
forum: Installation &amp; Upgrades
---

### Post by blossom on 2005-07-27
I'm new to Ubuntu and quite new to Linux in general. I would like to change from Gnome to KDE without upgrading Warty to Hoary.
How can I do that?
As I have only few experience with commands yet, I would be glad for a simple description. 
Thanks!

---

### Post by GavinX on 2005-07-27
[QUOTE=blossom]I'm new to Ubuntu and quite new to Linux in general. I would like to change from Gnome to KDE without upgrading Warty to Hoary.
How can I do that?
As I have only few experience with commands yet, I would be glad for a simple description. 
Thanks![/QUOTE]
Are you hoping to get KDE 3.4? If so, your best bet is to simply upgrade to Hoary and install all the KDE related stuff. Other than that, you may have to to some pinning of your sources. As you said, you are not very experienced with commands yet, so pinning may not be for you as it is a fairly difficult task. If you're interested in learning about pinning you can follow this link [http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)

---

### Post by blossom on 2005-07-27
[QUOTE=GavinX]Are you hoping to get KDE 3.4? If so, your best bet is to simply upgrade to Hoary and install all the KDE related stuff. Other than that, you may have to to some pinning of your sources. As you said, you are not very experienced with commands yet, so pinning may not be for you as it is a fairly difficult task. If you're interested in learning about pinning you can follow this link [http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)[/QUOTE]

Thank you for the link, it actually seems rather difficult for me at the moment.
I do not need KDE 3.4, any older version would do it.
If upgrading is the only solution, I consider to do so.  How can I make an upgrade to Hoary? Do I have to install everything new from CD, or is there another way?

---

### Post by GavinX on 2005-07-28
[QUOTE=blossom]How can I make an upgrade to Hoary? Do I have to install everything new from CD, or is there another way?[/QUOTE]
What kind of internet connection are you using? If you're using 56k modem, it may be out of the question unless you are prepared to allow it to run for about 20 hours or so to get your system updated.

However, if you're using broadband, DSL or wireless LAN, then you're in business. You can update the entire system in a matter of a few (maybe 2 or 3 hours depending on your connection speed). 

All you need to do is to follow the VERY SIMPLE instructions given in this link [http://ubuntuguide.org/4.10/index.html#upgradewartytohoary](http://ubuntuguide.org/4.10/index.html#upgradewartytohoary)

I am not certain if KDE is in the Warty repositories and if you want KDE you might as well take the latest. Why settle for a 1986 Thunderbird when you can have a 2006 Thunderbird for the same price? So your best bet is to simply upgrade. It's a very simple process and you will be glad that you did.

Hope this helps.

---

### Post by blossom on 2005-07-29
I could do the upgrade and it worked out well so far. Unfortunately, after 
apt-get install kubuntu-desktop
my desktop still looks like gnome.
I have set gdm to kdm, and after restarting the computer, I get the KDE-Display. But after login I get the gnome-desktop.
What changes do I have to make?

---

