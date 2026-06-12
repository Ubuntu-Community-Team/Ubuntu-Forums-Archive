---
title: "Installing lubuntu in an Acer Chromebook"
date: 2013-07-19
forum: Installation &amp; Upgrades
---

### Post by rawbertb on 2013-07-19
I recently purchased an Acer Chromebook.  While I was originally impressed, I have decided that it (Chrome OS) is very restrictive.  Is there a way that I can install lubuntu instead of the Chrome OS?

---

### Post by DeathByDenim on 2013-07-19
The answer is a cautious yes. It appears quite involved to get another OS on the Chromebook. See this guide by Ars Technica: [http://arstechnica.com/gadgets/2012/12/how-to-install-ubuntu-on-acers-199-c7-chromebook/](http://arstechnica.com/gadgets/2012/12/how-to-install-ubuntu-on-acers-199-c7-chromebook/)

That will get you Ubuntu (Well.. ChrUbuntu as they call it). After that it should be possible to install the LXDE desktop, so you'll have your Lubuntu.

Good luck!

---

### Post by oldrocker99 on 2013-08-02
This page: [http://chromeos-cr48.blogspot.com/2013/05/chrubuntu-one-script-to-rule-them-all_31.html](http://chromeos-cr48.blogspot.com/2013/05/chrubuntu-one-script-to-rule-them-all_31.html) has an updated script, which will (read the whole thing before starting!) install lubuntu-desktop, with no Unity at all, if that's what you want, or several other flavors of *buntu. I used it the other day, and it installed Lubuntu 13.04.

---

### Post by donovan1983 on 2013-08-04
Chromebooks aren't really meant to have another OS installed on them although for the determined there are ways. There is ChrUbuntu, as referenced in the post above, but I wasn't very happy with how well (or not) it worked when I tried it a few times. There's also crouton ([https://github.com/dnschneid/crouton/](https://github.com/dnschneid/crouton/)), which installs as a chroot within Chrome OS and looks to be simpler to install than ChrUbuntu. I haven't tried it, though.

Before you try either of those options, be sure to go to [chrome://imageburner](chrome://imageburner) on your Chromebook and have an 8GB or larger flash drive handy so you can easily restore Chrome OS if you need it. These things are near impossible to brick so you can tinker yet still go back to Chrome OS easily.

---

