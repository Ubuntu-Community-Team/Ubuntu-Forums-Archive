---
title: "Libre Office =&gt;&gt; Can't install it"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by nomko on 2011-01-15
Hi,

I want to try Libre Office and replace OpenOfficec. But when i add the PPA from this site: [https://launchpad.net/~libreoffice/+archive/ppa]("https://launchpad.net/%7Elibreoffice/+archive/ppa").

But when i try to install Libre Office i get this:
>  /var/cache/apt/archives/libreoffice-common_1%3a3.3.0~rc2-3lucid1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Whats the problem?? OpenOffice is completly removed.

**edit**
I also get this error message:
> E: /var/cache/apt/archives/libreoffice-common_1%3a3.3.0~rc2-3lucid1_all.deb: trying to overwrite '/etc/bash_completion.d/ooffice.sh', which is also in package openoffice.org-common 1

---

### Post by TGBaker on 2011-01-15
> **nomko said:**
> Hi,

I want to try Libre Office and replace OpenOfficec. But when i add the PPA from this site: [https://launchpad.net/~libreoffice/+archive/ppa]("https://launchpad.net/%7Elibreoffice/+archive/ppa").

But when i try to install Libre Office i get this:


Whats the problem?? OpenOffice is completly removed.

**edit**
I also get this error message:

try this PPA by adding it to your repository: [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) in Synaptic. Or let Ubuntu Tweak do it as I did.  When you select LibreOffice in Synaptic it will remove OpenOffice properly and install LibreOffice in its place.

---

### Post by nomko on 2011-01-16
> **TGBaker said:**
> try this PPA by adding it to your repository: [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) in Synaptic. Or let Ubuntu Tweak do it as I did.  When you select LibreOffice in Synaptic it will remove OpenOffice properly and install LibreOffice in its place.

It is the same PPA as the site i mentioned:

>                 deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) lucid main 

---

### Post by nomko on 2011-01-16
Okay, I managed it to get Libre Office installed!!

First to do: remove OpenOffice completly
Then install LibreOffice.

The only thing i have now is a horrible Win95 lay-out or theme :shock::-&

How do i get rid of that??

---

### Post by itsjustarumour on 2011-01-16
> **nomko said:**
> The only thing i have now is a horrible Win95 lay-out or theme :shock::-&

How do i get rid of that??

May sure you also have the libreoffice-gtk package installed :)

---

### Post by gradinaruvasile on 2011-01-16
> **nomko said:**
> Okay, I managed it to get Libre Office installed!!

First to do: remove OpenOffice completly
Then install LibreOffice.

The only thing i have now is a horrible Win95 lay-out or theme :shock::-&

How do i get rid of that??

You can install them side by side if you use the debs provided on the libreoffice.org site.

---

### Post by Paddy Landau on 2011-04-09
> **gradinaruvasile said:**
> You can install them side by side if you use the debs provided on the libreoffice.org site.
I just tried installing using the Ubuntu ppa, but it requires me to uninstall OO first.

The disadvantage with using a download is that you don't get updates automatically, right? You have to check for them. The advantage, of course, is that you get the latest version.

Still, I want to run both (for the time being), so I'll install from the official website.

---

