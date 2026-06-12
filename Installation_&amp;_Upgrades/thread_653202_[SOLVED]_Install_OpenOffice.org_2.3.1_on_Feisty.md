---
title: "[SOLVED] Install OpenOffice.org 2.3.1 on Feisty"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by hydraconsole on 2007-12-29
Something went wrong with the 2.2 version of oOo in my feisty fawn. Synaptic keeps on saying that there's something wrong with the package or something. My brother (w/o me knowing it) deleted all instance of the 2.2 in synaptic and downloaded the 2.3.1. now he doesn't know how to install it. neither do i. shall we stick with 2.2 using synaptic or can someone up to the challenge of teaching us how to install 2.3.1.

thanks

---

### Post by Partyboi2 on 2007-12-30
It would probably be easier to re-install the 2.2 from feisty repo's, then trying to install 2.3

---

### Post by Seisen on 2007-12-30
If he downloaded the .deb file from the Openoffice website then you can double click on the .deb file or you can you install it this way too

```
sudo dpkg -i nameoffile
``` in the terminal.

---

### Post by hydraconsole on 2008-01-02
We finally got this thing installed.

We just followed the instructions in the setup guide:)

Installing .debs
The simplest way to install the OpenOffice.org package you've downloaded is use the
command dpkg -i (short for dpkg –install).
   1. First log on as root or from the GUI, open a root terminal.
   2. Type:
       dpkg -i -–force-overwrite openoffice.org*.deb \
        desktop-integration/openoffice.org-debian-menus*.deb
       and openoffice.org will be installed. If you already had an older version, dpkg will
       upgrade it rather than installing both versions at once.
   3. Install any language packs needed for OpenOffice.org.

---

