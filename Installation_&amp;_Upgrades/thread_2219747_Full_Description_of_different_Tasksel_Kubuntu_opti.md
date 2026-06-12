---
title: "Full Description of different Tasksel Kubuntu options?"
date: 2014-04-25
forum: Installation &amp; Upgrades
---

### Post by cmt29 on 2014-04-25
Hello.

I've noticed that there are a few different options for Kubuntu 14.04 when you run the tasksel command. Does anyone know where I can find a fuller description of what the different options install please?

E.g. what's the difference between kubuntu-full and kubuntu-desktop?

tasksel --list doesn't give much info.

Thanks.

---

### Post by cmt29 on 2014-04-25
Answer from [http://askubuntu.com/questions/455178/full-description-of-different-tasksel-kubuntu-options](http://askubuntu.com/questions/455178/full-description-of-different-tasksel-kubuntu-options)

[COLOR=#333333][FONT=UbuntuRegular]**MetaPackages**[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)[/FONT][/COLOR]
[INDENT]One of the handy features of apt (the packaging system used by Ubuntu) is the use of metapackages. These packages do not contain actual software, they simply depend on other packages to be installed...
[/INDENT][COLOR=#333333][FONT=UbuntuRegular]**kubuntu-desktop**[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][http://packages.ubuntu.com/trusty/kubuntu-desktop](http://packages.ubuntu.com/trusty/kubuntu-desktop)[/FONT][/COLOR]
apt-cache show kubuntu-desktop

Description: Kubuntu Plasma Desktop/Netbook system
 This package depends on all of the packages in the Kubuntu desktop system.
 Installing this package will include the default Kubuntu Plasma Desktop or
 Netbook installation.
[COLOR=#333333][FONT=UbuntuRegular]**kubuntu-full**[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][http://packages.ubuntu.com/trusty/kubuntu-full](http://packages.ubuntu.com/trusty/kubuntu-full)[/FONT][/COLOR]
apt-cache show kubuntu-full

Description: Full Kubuntu Plasma Desktop/Netbook system
 This package depends on all of the packages in the Kubuntu DVD for a very
 complete system.  Installing this package will include much more than the
 default Kubuntu Plasma Desktop or Netbook installation.

---

