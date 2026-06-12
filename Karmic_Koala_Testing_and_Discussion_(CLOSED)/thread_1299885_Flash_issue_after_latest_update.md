---
title: "Flash issue after latest update"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Kev1n on 2009-10-24
Hi, I am unable to use flash anymore, in the update manager there is a flash option there, but every time i try to install it is gives me an error

Opening Synaptics Package Manager gives me this:
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
and then closes itself.

Update: a new partial upgrade for my Karmic Koala has appeared but won't let me upgrade because my flash plugin is in  "a bad state" it then tells me to manually remove or uninstall that but I cannot open synaptics package manager and 'sudo apt-get remove adobe-flashplugin' gives me similar errors.

could someone please help?
Thankyou,
Kevin

---

### Post by Kev1n on 2009-10-24
I also just read the sticky about Partial Upgrades o.O 
didn't know :\

---

### Post by buzzmandt on 2009-10-24
what happens if you? > sudo apt-get dist-upgrade

---

### Post by philinux on 2009-10-24
See post 6 if this is the same problem. Seemed to affect 32 bit users.
[http://ubuntuforums.org/showthread.php?p=8152201#post8152201](http://ubuntuforums.org/showthread.php?p=8152201#post8152201)

---

### Post by picopir8 on 2009-10-24
I believe that error is seen whenever a package is removed from the repo for some reason or another, ie a big bug was found and they dont want people to download it until they can get a fix up.  I have seen such errors periodically when running pre-release builds.  It will most likely be resolved in a day or two. If it has already been a day or two then try

sudo apt-get clean
sudo apt-get autoclean

then try again

---

