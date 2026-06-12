---
title: "OpenOffice 3.0 debs for Hardy"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by frogotronic on 2008-11-07
Are there any *working* repositories for debs for oo3 for Hardy Heron?

---

### Post by wilbur.harvey on 2008-11-07
Yes, there are

# OpenOffice 3.0
# deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
# deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

But I wouldn't use them. For some reason the app is very slow when you use them, the same as some of the pre-releases from Open Office.

I just downloaded the .deb release from the openoffice page and installed that. It works fine.

Just do a "sudo dpkg -i *.deb" in the directory with all the debs from the distribution, then go to the desktop integration directory and install that deb and you should be good to go.

---

### Post by frogotronic on 2008-11-07
> **wilbur.harvey said:**
> Yes, there are

# OpenOffice 3.0
# deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
# deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

But I wouldn't use them. For some reason the app is very slow when you use them, the same as some of the pre-releases from Open Office.

I just downloaded the .deb release from the openoffice page and installed that. It works fine.

Just do a "sudo dpkg -i *.deb" in the directory with all the debs from the distribution, then go to the desktop integration directory and install that deb and you should be good to go.

Should I uninstall the 2.4.1? Or just overwrite the existing debs?  Where are the existing debs?

Thanks,
CH

---

### Post by frogotronic on 2008-11-08
Hello,

The debs for Hardy are non-existent.

Intrepid is available, but not for Hardy.

- CH  :(

---

### Post by stinkinrich88 on 2008-12-18
hello, is this still the case? I'd really love an OOo3 repo for hardy

cheers!

---

### Post by Partyboi2 on 2008-12-18
You could try manually installing it.
[http://ubuntuhelptipstricks.blogspot.com/2008/10/setting-up-openoffice-3-on-ubuntu-hardy.html](http://ubuntuhelptipstricks.blogspot.com/2008/10/setting-up-openoffice-3-on-ubuntu-hardy.html)

---

### Post by wd5gnr on 2008-12-18
In case you do try to install this on Intrepid Kubuntu. I installed it and didn't have the "slow" problem. But I did have the problem where every app crashed on start up. The trick was removing the openoffice.org-kde package which had been previously installed.

---

### Post by Therion on 2008-12-18
I'm using OpenOffice 3.0 on Hardy and it's as snappy as I could ask for.  Not sure what this talk of it being slow is all about.

I installed 3.0 from source, but you can, if you want, enable the Intrepid Repo, nab the OO 3.0 packages and then immediately remove the repo from your sources list like so:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

Or you can follow these directions to install from source (it's really not that hard):

[http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

---

### Post by stinkinrich88 on 2008-12-19
ahh, cheers Therion. Can I ask what the disadvantages of installing from source are. Is it just that I won't get updates for OOo3? Or will there be other problems too?

---

### Post by albinootje on 2008-12-19
> **Therion said:**
> 

Or you can follow these directions to install from source (it's really not that hard):

[http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

But that's not installing from source.
That is simply installing the deb binary packages from Openoffice.org

Installing from source would probably mean leaving your machine on for a day to compile openoffice ;-)

---

### Post by stinkinrich88 on 2008-12-19
ahh yeah. well, you know, software source, not source code. does it just mean that I won't get updates or is it something more sinister?

---

### Post by albinootje on 2008-12-19
> **stinkinrich88 said:**
> ahh yeah. well, you know, software source, not source code. does it just mean that I won't get updates or is it something more sinister?
If you install the deb packages downloaded from openoffice.org then you will not get update-notifications from the Ubuntu package-manager because it was not installed from repositories (/etc/apt/sources.list).
But Openoffice itself has some "check for updates" option, at least.. i saw it during the migration from 2.x to 3.x after starting Openoffice 3.x for the first time.

---

