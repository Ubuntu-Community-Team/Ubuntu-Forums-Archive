---
title: "ttf-mscorefonts-installer reinstall"
date: 2015-07-13
forum: Installation &amp; Upgrades
---

### Post by Camilia on 2015-07-13
Have ubuntu 15.04 OS. Recently did sudo apt-get install ubuntu-restricted-extras. Ran software updater. Then got message;

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed. ttf-mscorefonts-installer. 
This is a permanent failure that leaves these packages unusable on your system.  You may need to fix your Internet connection, then remove and reinstall the packages to fix this problem.

I don't quite understand the suggestions to fix this. How do I reinstall the package?

---

### Post by kerry_s on 2015-07-13
sudo apt-get install --reinstall ttf-mscorefonts-installer

---

### Post by coffeecat on 2015-07-13
You need a reliable connection to the internet when you install the mscorefonts installer as it has to download all the fonts themselves. You've probably ended up with the corefonts installer installed, but not the fonts. Check your internet connection, and once you are happy with this, run this in a terminal:

```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```

Watch the process. You will be prompted with a EULA to agree to in the terminal. You can't use the mouse for this. Use the tab key to highlight the OK, and then press enter. If you don't agree the EULA, you will end up with the same half-installed installer.

---

### Post by Camilia on 2015-07-13
> **coffeecat said:**
> 
```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```

Watch the process. You will be prompted with a EULA to agree to in the terminal. You can't use the mouse for this. Use the tab key to highlight the OK, and then press enter. If you don't agree the EULA, you will end up with the same half-installed installer.
I didn't click on the OK after initial instillation.  Just closed terminal after sudo command. Thus tried again and now this is what I get
kim@Brain:~$ sudo apt-get install --reinstall ttf-mscorefonts-installer
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
kim@Brain:~$ sudo dpkg --configure -a
kim@Brain:~$

---

### Post by ajgreeny on 2015-07-13
Use synaptic to reinstall as that way you will always see the EULA appear, which you may not when using terminal as it may pop-up beneath the terminal; in synaptic it always shows as far as I can remember.

---

### Post by coffeecat on 2015-07-13
> **Camilia said:**
> I didn't click on the OK after initial instillation.  Just closed terminal after sudo command. Thus tried again and now this is what I get
kim@Brain:~$ sudo apt-get install --reinstall ttf-mscorefonts-installer
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
kim@Brain:~$ sudo dpkg --configure -a
kim@Brain:~$

And now you must run the apt-get command I gave you, or use synaptic as ajgreeny suggests.

---

### Post by Camilia on 2015-07-13
> **ajgreeny said:**
> Use synaptic to reinstall as that way you will always see the EULA appear, which you may not when using terminal as it may pop-up beneath the terminal; in synaptic it always shows as far as I can remember.
I recently reinstalled ubuntu thus didn't not have the synaptic manager available. Couldn't remember how it was spelled thus couldn't find it. Now I got it installed. Reinstalled the fonts just as you said. Now easier to approve EULA.

---

### Post by bapoumba on 2015-07-14
Just for the ones who may be reading looking for a solution in the terminal, you need to hit <Tab> to highlight the OK (or Yes, I do not remember) box.

---

### Post by redguy41 on 2016-04-22
This happened to me on 16.04 LTS as well, thanks for the help.

---

