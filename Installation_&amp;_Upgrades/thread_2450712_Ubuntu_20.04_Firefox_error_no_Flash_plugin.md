---
title: "Ubuntu 20.04 Firefox error no Flash plugin"
date: 2020-09-19
forum: Installation &amp; Upgrades
---

### Post by jimhce on 2020-09-19
Hi,

Adobe Flash is going to be ended this year, which open source flash should I install to play it on firefox? I followed the link [http://ubuntuhandbook.org/index.php/2019/04/install-flash-player-plugin-ubuntu-19-04/](http://ubuntuhandbook.org/index.php/2019/04/install-flash-player-plugin-ubuntu-19-04/) and [https://support.mozilla.org/en-US/kb/install-flash-plugin-view-videos-animations-games](https://support.mozilla.org/en-US/kb/install-flash-plugin-view-videos-animations-games), none of works for apt installation

Thank you.

---

### Post by Impavidus on 2020-09-19
Just don't use flash.

---

### Post by ajgreeny on 2020-09-19
Do you actually go to sites that work only with flash?  I don't  think I have had it installed now for a very long time and never see any notifications that flash is needed.

I'm  not on my Xubuntu machine at present so can not look in detail but there is, or was a package called flashplugin-installer that would get the most recent version of flash for you. Perhaps that no longer is available; I have not bothered to look for it now for a couple of years.

Just run your system without flash and you may find that its totally superfluous.

---

### Post by SeijiSensei on 2020-09-19
The flashplugin-installer package is listed as available for 20.04, though I've not needed Flash for anything for years now.

```
sudo apt flashplugin-installer
```

You need to enable the multiverse repository in /etc/apt/sources.list.

---

### Post by jimhce on 2020-09-20
> **SeijiSensei said:**
> The flashplugin-installer package is listed as available for 20.04, though I've not needed Flash for anything for years now.

```
sudo apt flashplugin-installer
```

You need to enable the multiverse repository in /etc/apt/sources.list.

Thanks for all helps, as I said my previous email, it did not work:

$ cat /etc/apt/sources.list

deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) focal-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) focal multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) focal-updates multiverse

$ sudo apt update

$ sudo apt install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-installer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'flashplugin-installer' has no installation candidate

---

### Post by Impavidus on 2020-09-20
I see only source repositories (lines starting with deb-src) in your sources.list. flashplugin-installer is not in the source repositories (which are meant to download source code), but in the regular (lines starting with deb) multiverse repository. Most people keep the source repositories disabled.

Having said that, flashplugin-installer just installs the Flash player from Adobe. When Adobe stops support of Flash, flashplugin-installer will no longer get updates. My guess is that Mozilla will push an update to Firefox to block old Flash players, and so will Microsoft for all supported browsers. So just stop using Flash. Very few websites still use it and they should stop before the end of the year, or they'll get no more visitors.

There have been some attempts at open source Flash players, but they've always been lacking in features, making them hardly useable.

---

### Post by grahammechanical on 2020-09-20
According to this help page

[https://help.ubuntu.com/stable/ubuntu-help/net-install-flash.html.en](https://help.ubuntu.com/stable/ubuntu-help/net-install-flash.html.en)

We should activate the Canonical Partners repository to install adobe-flashplugin. The page also points out that the Google Chrome web browser comes with flash bundled in it and does not need a plug-in. Although what will happen at the end of the year I cannot say. Here is what Google says

[https://support.google.com/chrome/a/answer/7084871?hl=en](https://support.google.com/chrome/a/answer/7084871?hl=en)

[https://www.chromium.org/flash-roadmap](https://www.chromium.org/flash-roadmap)

Regards

---

### Post by jimhce on 2020-09-21
> **grahammechanical said:**
> According to this help page

[https://help.ubuntu.com/stable/ubuntu-help/net-install-flash.html.en](https://help.ubuntu.com/stable/ubuntu-help/net-install-flash.html.en)

We should activate the Canonical Partners repository to install adobe-flashplugin. The page also points out that the Google Chrome web browser comes with flash bundled in it and does not need a plug-in. Although what will happen at the end of the year I cannot say. Here is what Google says

[https://support.google.com/chrome/a/answer/7084871?hl=en](https://support.google.com/chrome/a/answer/7084871?hl=en)

[https://www.chromium.org/flash-roadmap](https://www.chromium.org/flash-roadmap)

Regards

Installed Google Chrome did the trick.

Thanks all helps, greatly appreciated it.

---

### Post by mastablasta on 2020-09-22
so all short/small flash games (there are many over internet) will no longer work or is there a substitute?

---

### Post by Dennis N on 2020-09-22
> so all short/small flash games (there are many over internet) will no longer work or is there a substitute? 
If you have .swf files, you can use **Adobe Flash Player Projector** which is independent of any browser. See screen shot where it is running a flash game called Incredipede on Ubuntu 18.04. The player is downloadable from Adobe's web site.

---

