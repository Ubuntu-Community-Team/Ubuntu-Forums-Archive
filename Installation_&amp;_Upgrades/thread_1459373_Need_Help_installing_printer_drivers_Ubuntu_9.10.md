---
title: "Need Help installing printer drivers Ubuntu 9.10"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by tehno 2 on 2010-04-21
Hello there,
I have printer Brother MFC5860 and could not have it work on Ubuntu, when contacting brother support, they forwarded me to several drivers; Cupswrapper and LPR each of them available in two formats rpm & deb. 
Can some tell me what are cups & LPR and how to install the right one.
My Ubuntu is 9.10, 64 bit installed inside windows vista "dual boot"
Thanks in advance to all

---

### Post by mikewhatever on 2010-04-21
You'll need the .deb files for Ubuntu, and just double click each to install. I am sure others will lay out 'The Linux Printing Theory' before you shortly, why ever you need that.

---

### Post by tehno 2 on 2010-04-21
> **mikewhatever said:**
> You'll need the .deb files for Ubuntu, and just double click each to install. I am sure others will lay out 'The Linux Printing Theory' before you shortly, why ever you need that.

Unfortunately, it did not work and when clicking on it an error pops up in red (Error: Wrong architecture 'i386')
although what I have is intel prcoessor.

---

### Post by partloer on 2010-04-21
The error message: Wrong architecture 'i386' is caused by the fact that your hardware is 64 bit and the software driver is built for 32 bit.

Find out if they make drivers for 64 bit.  If not there might be a way to still install them (I don't know how but someone else might be able to help out).

---

### Post by plucky on 2010-04-22
> Hello there,
I have printer Brother MFC5860 and could not have it work on Ubuntu, when contacting brother support, they forwarded me to several drivers; Cupswrapper and LPR each of them available in two formats rpm & deb.
Can some tell me what are cups & LPR and how to install the right one.
My Ubuntu is 9.10, 64 bit installed inside windows vista "dual boot"
Thanks in advance to all 



Your printer drivers are already packaged in **Synaptic Package Manager**

Open **Synaptic package manager** and search for **MFC-5860** and it will find ```
brother-cups-wrapper-bh7
brother-lpr-drivers-bh7
```

Select cups-wrapper driver which will also install the LPR drivers as you need both.

Then open **System > Administration > Printing** and add your printer.You should then be able to find the drivers for your printer.

Good Luck

---

### Post by tehno 2 on 2010-04-23
> **plucky said:**
> Your printer drivers are already packaged in **Synaptic Package Manager**

Open **Synaptic package manager** and search for **MFC-5860** and it will find ```
brother-cups-wrapper-bh7
brother-lpr-drivers-bh7
```

Select cups-wrapper driver which will also install the LPR drivers as you need both.

Then open **System > Administration > Printing** and add your printer.You should then be able to find the drivers for your printer.

Good Luck

Big & Great WOW, it worked great and wirelessly. You proved to be more knowledgeable:guitar: than Brother tech support.
Thank you very much.

---

### Post by tehno 2 on 2010-04-23
> **partloer said:**
> The error message: Wrong architecture 'i386' is caused by the fact that your hardware is 64 bit and the software driver is built for 32 bit.

Find out if they make drivers for 64 bit.  If not there might be a way to still install them (I don't know how but someone else might be able to help out).

Thanks for the information, the printer is working now

---

