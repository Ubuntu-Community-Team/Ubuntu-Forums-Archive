---
title: "new to ubuntu - Install packages"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by Rephiscorth on 2011-05-13
Hello I'm new to Ubuntu and ergo to the forums, so please forgive if I posted this in the wrong section.

Well I was trying to install the flash plugin to play videos on youtube.  

I tried the following commands

sudo apt-get install flashplugin-install
sudo apt-get install flashplugin-nonfree


but each of them says they can't be installed because they depend on something else:

flashplugin-nonfree depends on flashplugin-install.

flashplugin-isntall depends on nspluginwrapper   and  ia32-libs.


ia-32-libs depends on other 6 more stuffs. So I guess this is  a chain and those other 6 stuffs will depend on other stuffs.

So I was wondering if there is a way to install everything fast and easy,   instead of downloading one by one everything they say the package depends.


Thanks in Advance

---

### Post by Joe of loath on 2011-05-13
Ubuntu should download the dependencies automatically. Can you post the output of

```
sudo apt-get install flashplugin-install
```?

---

### Post by oldos2er on 2011-05-13
If you're using 64-bit Ubuntu, may I recommend you use FlashAid to install 64-bit flash? [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by spcwingo on 2011-05-13
Have you tried this method?

```
sudo add-apt-repository ppa:sevenmachines/flash && sudo apt-get update && sudo apt-get install flashplugin64-installer
```

---

### Post by Rephiscorth on 2011-05-14
I think I found it, it was cause my sources.list was kinda modified.

thanks to all :)

---

