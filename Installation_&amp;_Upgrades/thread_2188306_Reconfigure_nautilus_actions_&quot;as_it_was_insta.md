---
title: "Reconfigure nautilus actions &quot;as it was installed&quot;?"
date: 2013-11-16
forum: Installation &amp; Upgrades
---

### Post by c-info-x on 2013-11-16
Cheers,

i'm using Ubtunu 12.04 and i happend to unintentionally "apt-get purge" my nautilus from my installation. After re-installation of nautilus i realized that all the nice right-click menu actions were gone (e.g. sent to removeable drive etc.)
I now know that i need nautilus actions for this, which i already installed. I've also already checked [http://www.grumz.net/](http://www.grumz.net/) with all its preconfigured actions, but unfortunately a. the import-function does not work and b. actions like the above mentioned sending of files to an USB stick are missing.

I would loooooove to have back the actions that were preconfigured during the initial installation of Ubuntu on my machine. Is there any way to do this?

Thanks and best regards,
Sascha

---

### Post by Frogs Hair on 2013-11-16
Hello and Welcome
 
To re-enable the context menu if missing  open the Gnome Tweak Tool and select Desktop and enable Have File manager handle desktop. Nautilus actions at least on 13.10  is a septate program not installed by default. What Nautilus version was installed installed and what context menu options are missing?

---

### Post by c-info-x on 2013-11-17
> **Frogs Hair said:**
> Hello and Welcome
 
To re-enable the context menu if missing  open the Gnome Tweak Tool and select Desktop and enable Have File manager handle desktop. Nautilus actions at least on 13.10  is a septate program not installed by default. What Nautilus version was installed installed and what context menu options are missing?

Hello Frogs Hair,

thanks for the answer! I've checkd the Tweak Tool, but the option you mentioned was already activated. De/Re-activating it did not change anything...

What i mostly missed was the "send-to" menu. I've now learned that this is yet another package which is not installed by default when installing nautilus on your own (yet it seems to be installed with the initial installation).
so i used

```
sudo apt-get install nautilus-sendto
```
and now i finally have back the deeply missed option to shove music files on my playing device with one click again :-)

Thanks anyway, if i hadn't had to express my problem here, i would not have stumbled upon the package which i was missing and finally solved this issue for good

Cheers!

---

