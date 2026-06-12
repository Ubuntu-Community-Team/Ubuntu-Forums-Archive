---
title: "Upgrade to Ubuntu 22.04 - advice requested"
date: 2023-02-24
forum: Installation &amp; Upgrades
---

### Post by williepabon on 2023-02-24
Hi:
Now, for quite a while, every time I receive a s/w update I get the  message to upgrade the OS 22.04.1 (I have 20.04). I want to do it, but I  have a few concerns, as follows:

**Firefox:**
    Firefox is my default browser for years. I've read that the version  that comes with 22.04 is the snap version. My concern here is about what  happens  to: (1) my installed extensions, (2) data associated to all saved  bookmarks, (3) data associated with my saved passwords, (4) data associated  with the gnome shell extensions I installed, (5) configuration associated with Sync. If there is any impact to the aforementioned, I would  prefer, and be advised on how keep the DEB package of Firefox to avoid  any disruptions to my data.

**GNOME**
    Ubuntu 22.04 comes with version 42.  My OS now has 3.36.9. I have  installed a few shell extensions (using the Firefox connector) and added  new themes to my desktop. What will happen to those when gnome 42 runs?

Following is info about my machine:


[COLOR=#4E9A06]**williepabon@williepabon-Macmini**[/COLOR]:[COLOR=#3465A4]**~**[/COLOR]$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.5 LTS
Release:    20.04
Codename:    focal
[COLOR=#4E9A06]**williepabon@williepabon-Macmini**[/COLOR]:[COLOR=#3465A4]**~**[/COLOR]$ uname -a
Linux williepabon-Macmini 5.4.0-139-generic #156-Ubuntu SMP Fri Jan 20 17:27:18 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux

Thanks in advance for any help.
wp

---

### Post by tea for one on 2023-02-24
I always install a new LTS from scratch rather than an in-situ upgrade.

It's essential to backup your data.
You can use a Firefox deb with [https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)
The article also contains info about gnome-shell-extension-manager, which avoids the need to download extensions via the browser.

You will probably have to upgrade all the extensions and themes to be compatible with gnome 42.

Have a look at this theme and the facility to change accent colours
[https://www.gnome-look.org/p/1214931](https://www.gnome-look.org/p/1214931)
You will still need gnome-tweaks to change themes/icons.

Ubuntu 22.04 has a selection of light and dark Yaru themes installed automatically.

Anyway, why not experiment with a live session of 22.04 before deciding?

---

### Post by williepabon on 2023-03-05
[**[COLOR=#000000]tea for one[/COLOR]**]("https://ubuntuforums.org/member.php?u=585392")[B][COLOR=#000000]:

[/COLOR][/B]Thank you for the prompt answer and advice. Read the included article on the Firefox deb package alternative for the snap package, which I may consider (has some complications,, though). But first, I will follow your advice on backing up the essential data on my machine ( will make a copy of my /Home folder and the Firefox profile folder). If you think there are other folders that I should back up before proceeding with the upgrade, please, let me know. Thanks.
wp

---

