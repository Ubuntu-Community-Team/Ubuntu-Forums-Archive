---
title: "unable to install anything"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by mailbox on 2010-07-06
So I made the mistake of thinking I could install a new version of Flash from Adobe's website. Now, I have this:

*sudo apt-get install flashplugin-installer* returns:```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/19.6kB of archives.
After this operation, 188kB of additional disk space will be used.
Preconfiguring packages ...
dpkg: regarding .../flashplugin-installer_10.1.53.64ubuntu0.9.10.1_amd64.deb containing flashplugin-installer:
 adobe-flashplugin conflicts with flashplugin-installer
  flashplugin-installer (version 10.1.53.64ubuntu0.9.10.1) is to be installed.
dpkg: error processing /var/cache/apt/archives/flashplugin-installer_10.1.53.64ubuntu0.9.10.1_amd64.deb (--unpack):
 conflicting packages - not installing flashplugin-installer
Errors were encountered while processing:
 /var/cache/apt/archives/flashplugin-installer_10.1.53.64ubuntu0.9.10.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
If I try to remove adobe-flashplugin, it tells me it's not installed.
*sudo dpkg --configure -a* returns:```
dpkg: dependency problems prevent configuration of image2mpeg:
 image2mpeg depends on libmagick++9c2a (>= 6.1.8); however:
  Package libmagick++9c2a is not installed.
dpkg: error processing image2mpeg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 image2mpeg
```
Same story with image2mpeg; if I try to remove it, i'm told it doesn't exist.

Any ideas?

---

### Post by mailbox on 2010-07-08
anyone?

---

### Post by mailbox on 2010-07-10
please, someone, i really need help with this!

---

### Post by oldos2er on 2010-07-10
Are you using 9.10?

Try ```
sudo apt-get clean && sudo apt-get update && sudo apt-get install adobe-flashplugin
```

---

### Post by mailbox on 2010-07-10
Yes, I'm running 9.04.
Everything ran fine up until the last command, which returned *E: Couldn't find package adobe-flashplugin*

---

### Post by Steve603z on 2010-07-10
to install flash try
[apt:adobe-flashplugin?channel=$distro-partner](apt:adobe-flashplugin?channel=$distro-partner)
then see what happens, it MIGHT be a repository issue

---

### Post by Steve603z on 2010-07-10
also here is a direct .deb file from adobe

[http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10.1_for_Linux_(.deb)]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10.1_for_Linux_%28.deb%29")[URL="http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10.1_for_Linux_%28.deb"]
[/URL]

---

### Post by oldos2er on 2010-07-10
> **mailbox said:**
> Yes, I'm running 9.04.
Everything ran fine up until the last command, which returned *E: Couldn't find package adobe-flashplugin*

Then replace adobe-flashplugin with flashplugin-installer, or try the other suggestions.

---

### Post by mailbox on 2010-07-10
steve: installing the .deb from Adobe's website is what caused this problem in the first place.
your first link comes back with "channel unknown."

oldos: same result with flashplugin-installer as in my first post.

---

### Post by mailbox on 2010-07-18
anyone else have any ideas?

---

### Post by oldos2er on 2010-07-18
Do you have the multiverse repository enabled?

---

### Post by mailbox on 2010-08-08
> **oldos2er said:**
> Do you have the multiverse repository enabled?

Yes, I do. I disabled it, then tried all the steps I had done earlier, but I got the same results.

---

