---
title: "Install this third-party software -- what exactly will be installed?"
date: 2014-07-13
forum: Installation &amp; Upgrades
---

### Post by Untarnished_Truth on 2014-07-13
What exactly does Ubuntu/Kubuntu 14.04 install when I tick the "Install this third-party software" checkbox in the installation process?  Some ubuntuforums/askubuntu users say it will install ubuntu-restricted-extras, some say ubuntu-restricted-addons, some say that there's more than just these that will be installed.  This is confusing.  It would be great to know the exact, correct answer.  Thanks!

---

### Post by bapoumba on 2014-07-13
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Here are the packages depending on ubuntu-restricted-extras : [http://packages.ubuntu.com/trusty/ubuntu-restricted-extras](http://packages.ubuntu.com/trusty/ubuntu-restricted-extras)

If you click on the first one (ubuntu-restricted-addons), you'll see the codecs and plugins that will be installed.

Basically, these are packages that cannot be shipped by ubuntu by default due to their license but are required to read dvd/fonts/audio files that use proprietary encodings or licenses.

---

### Post by grahammechanical on 2014-07-13
The option to install third party software during the installation of Ubuntu does more than install ubuntu-restricted-extras and at the same time it does less than what installing ubuntu-restricted-extras will do.

For a start, we will get a proprietary video driver installed instead of using the default open source video driver. Also if a WiFi adapter does not have a driver in the kernel we may also get an available proprietary driver for it.

When we install ubuntu-restricted-extras it will install an installer to download and install Microsoft core TTF fonts. For this to proceed we need to accept the Microsoft End User License Agreement (EUAL). A dialog box will appear behind the Software Centre window. Unless we tick to accept this the installation of the fonts cannot proceed. But we are not asked to accept a Microsoft EULA during the installation of Ubuntu. So, we do not get Microsoft TTF core fonts installed during the installation of Ubuntu.

This is what the Preparing to install Ubuntu dialog says, according to the Ubuntu web site.

> Ubuntu uses third-party software to play Flash, MP3 and other media, and to work with some graphics and wifi hardware. Some of this software is proprietary. The software is subject to license terms included with its documentation ... Install this third party software ... Fluendo MP3 plugin includes MPEG Layer-3 audio decoding technology licensed from Franhofer IIS and Technicolor SA.

Regards.

---

