---
title: "Downloading updates while installing Ubuntu 14.04"
date: 2016-05-04
forum: Installation &amp; Upgrades
---

### Post by ChristmasPi on 2016-05-04
When installing Ubuntu 14.04, there are two options that I can choose and I have listed them below.

1.  Download updates while installing.  Ubuntu uses third party software to play Flash, MP3 and other media and to work with some graphics and wi-fi hardware.  Some of this software is proprietary.  The software is subject to license terms included with its documentation.  

2.  Install this third party software.  Fluendo MP3 plugin includes MPEG Layer-3 audio decoding technology licensed from Fraunhofer IIS and Technicolor SA

I'm not sure if I need them or not.  Should I be selecting these or not when installing Ubuntu?

Thank you

---

### Post by Bucky Ball on 2016-05-04
*Thread moved to **Installation & Upgrades**.*

Best to click neither to be on the safest side. Neither is necessary. Ticking one or both can sometimes cause issues. You can update once you've installed and then install any drivers you need.

Main aim is to end up with a stable install at the end of the process. Installing third-party drivers during install may destabilise the system in unpredictable ways.

Once you know you've installed successfully, you can do an update via the Software Updater or via a terminal. Once you know that is all good and stable, you can start to experiment with any required drivers, unless you've been forced to do that prior. 

One question, curiousity only: Why 14.04 LTS? Nothing wrong with it. Great, stable, solid. But 16.04 LTS was released about two or three weeks ago and is support for a couple more years than 14.04 LTS. You are waiting for the bugs to be fixed with 16.04?

---

### Post by ChristmasPi on 2016-05-04
> **Bucky Ball said:**
> 

One question, curiousity only: Why 14.04 LTS? Nothing wrong with it. Great, stable, solid. But 16.04 LTS was released about two or three weeks ago and is support for a couple more years than 14.04 LTS. You are waiting for the bugs to be fixed with 16.04?

There's only one reason that I went with 14.04 and that is because I use Remastersys.  I know it works perfectly on 14.04 and use this to make liveCDs that I can then use elsewhere.  From what I understand, Remastersys doesn't work with 16.04 and unfortunately, I don't see any other reliable alternative.

I know Remastersys has been forked but I always worry about getting a virus or malicious code from third party software that isn't released by Canonical.

You may be asking why then am I using Remastersys since that isn't made by Canonical but I started using quite some time back when I was a bit more naive and since, knock on wood, everything has worked out until now, I have kept using it.

---

### Post by Bucky Ball on 2016-05-04
I was just curious and not concerned whether you use Canonical software only or not. Back to your question(s). Have I answered them? If so, please mark the thread as solved. Thanks. This will not close the thread to further discussion if anyone else chimes in with thoughts but it will help others.

---

### Post by ajgreeny on 2016-05-04
I also agree with Bucky Ball; I have been using Ubuntu since 2005 and in all that time I have never installed third party packages nor updates as I install the system.

I much prefer to know what is being installed so always wait till after the OS is in place and then add whatever I need and fully update the system. This has one more advantage; that the OS installs much faster as it is not downloading lots of packages from the repositories as it installs, everything comes from the DVD or USB you're using.

---

### Post by howefield on 2016-05-05
> **ChristmasPi said:**
> I'm not sure if I need them or not.  Should I be selecting these or not when installing Ubuntu?

I always select the Download Updates option but not the third party software option.

As I understand it, the third party software option installs the package ubuntu-restricted-addons and (if applicable) wireless drivers for the Broadcom chipset.

On this 15.10 machine ubuntu-restricted-addons consists of...
```

hugh@wily-laptop:~$ apt show ubuntu-restricted-addons
Package: ubuntu-restricted-addons
Priority: optional
Section: multiverse/metapackages
Installed-Size: 28.7 kB
Maintainer: Evan Dandrea <ev@ubuntu.com>
Version: 22
Recommends: gstreamer0.10-plugins-ugly, gstreamer1.0-plugins-ugly, flashplugin-installer, gstreamer0.10-plugins-bad, gstreamer1.0-plugins-bad, gstreamer1.0-libav, gstreamer0.10-fluendo-mp3, gstreamer1.0-fluendo-mp3, chromium-codecs-ffmpeg-extra, oxideqt-codecs-extra
Download-Size: 2,956 B
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu
APT-Sources: [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) wily/multiverse amd64 Packages
Description: Commonly used restricted packages for Ubuntu
 This package depends on some commonly used packages in the Ubuntu universe
 and multiverse repositories.
 .
 You should not install this package directly, but instead install the
 ubuntu-restricted-extras package.

hugh@wily-laptop:~$
```  

This package is used by the installer and shouldn't be installed after the fact, but rather the ubuntu-restricted-extras should be used if required. 

Using 

```
apt-cache show ubuntu-restricted-extras
```

will show you what the package includes.

---

