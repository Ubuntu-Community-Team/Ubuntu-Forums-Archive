---
title: "Upgrading Ubuntu 10.04 to Xubuntu 12.04"
date: 2012-03-22
forum: Installation &amp; Upgrades
---

### Post by jolindbe on 2012-03-22
I'm considering to change from Ubuntu to Xubuntu since I can't stand Unity, and Xubuntu seems a lot faster (I'm currently running Ubuntu 10.04 LTS, but I've tried Unity on other machines, and it is just not my cup of cake).

Am I asking for trouble if I'd like to do this upgrade? Would it be smarter to wipe the hdd? I've got a lot of specialised programmes installed that takes a while to reinstall.

If I go through with this, would it be better to do
1. Ubuntu 10.04 -> Ubuntu 12.04 -> Xubuntu 12.04
or
2. Ubuntu 10.04 -> Xubuntu 10.04 -> Xubuntu 12.04
?

In any case, I will wait for the release in April, I will not run alpha versions... I'm just preparing my mind for this upgrade.

---

### Post by snowpine on 2012-03-22
Personally I would convert Ubuntu to Xubuntu first, so that I could avoid Unity entirely:

[http://www.psychocats.net/ubuntu/purexfcelucid](http://www.psychocats.net/ubuntu/purexfcelucid)

Then upgrade:

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

(watch this space for Lucid upgrade notes to appear next month)

---

### Post by ccrs8 on 2012-03-22
Well, wiping the hard drive is always "safer" (which is why Mint doesn't even support upgrades), but upgrading may be worth a try since you have so many specialized programs set up.  Especially since you are on the LTS version upgrading to the next LTS version, it will definitely be a supported and well-tested path.

If you don't wipe your drive but instead do the upgrade, just stick with Ubuntu and and upgrade to 12.04 before fiddling with XFCE (Xubuntu).  Once you are on Ubuntu 12.04, you can simply install the xubuntu-desktop package and never have to play with Unity again.  After installing that package, when you boot up you will be given the options as to what desktop environment you want to log in to.  You can chose Xubuntu session at that point.  Gnome/Unity and XFCE can coexist without problems.

If you wipe the hard drive, obviously use the Xubuntu 12.04 media for installation.  The only difference that I know of between installing xubuntu-desktop on a "ubuntu" computer and installing xubuntu on a clean drive is the bootup splash screen and maybe the default login screen.  The former will be decorated like Ubuntu while the latter will have the Xubuntu decoration and branding.

---

### Post by 2F4U on 2012-03-22
> 1. Ubuntu 10.04 -> Ubuntu 12.04 -> Xubuntu 12.04

That would mean to upgrade from Ubuntu 10.04 to Ubuntu 12.04 (you will then get Unity) and install xubuntu-desktop on top on Ubuntu 12.04, so that you then have both Unity and XFCE desktops and can select which one to choose. If you intend to have a choice of both desktop environments, thats probably not a bad idea. But it is likely that Unity interferes with XFCE, at least thats the experience of some users here on the forum.

If you've decided to switch to XFCE, I would do a fresh installation of Xubuntu, and since upgrades are always kind of a risk, I would wait until Xubuntu 12.04 is out and do the install then.

---

### Post by rewyllys on 2012-03-22
> **jolindbe said:**
> . . . . In any case, I will wait for the release in April, I will not run alpha versions... I'm just preparing my mind for this upgrade.
I'd suggest that you consider setting up your /home directory on a separate partition.  

Doing so will make it easier for you to change versions of Linux or to upgrade to a newer release of your chosen version, because with a separate partition for /home, you can re-format your root ("/") directory prior to installing the new release or new version, and thus do a clean install.

For reasons for preferring to do a clean install, I recommend reading Tamlynmac's comments at the following URL:

[http://ubuntuforums.org/showthread.php?t=1939761&page=2](http://ubuntuforums.org/showthread.php?t=1939761&page=2)

---

### Post by sudodus on 2012-03-22
> **snowpine said:**
> Personally I would convert Ubuntu to Xubuntu first, so that I could avoid Unity entirely:

[http://www.psychocats.net/ubuntu/purexfcelucid](http://www.psychocats.net/ubuntu/purexfcelucid)

Then upgrade:

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

(watch this space for Lucid upgrade notes to appear next month)
+1

But I would wait with the upgrade to 12.04 until June or July, so that it will be stable. And of course, I would backup my system before doing such big things with my system.

By the way 'not would, but will': I'm running Ubuntu 10.04 too, so I'm in the same situation as you. Right now I'm testing the beta version on another partition with 'all four desktops', KDE, LXDE, Unity and XFCE (in alphabetical order). And LXDE makes my desktop from 2008 fly :KS

---

### Post by jolindbe on 2012-03-23
Thanks for all the useful input, it is very much appreciated.

So it seems that there is no consensus on whether an upgrade is preferable to a clean install... well, I have to think over how difficult my special programmes were to install. And as you say, it is maybe best to wait a few months after the release. The upgrade is not really pressing, my system works fine at the moment, so maybe there is no reason to fix what is not broken.

---

