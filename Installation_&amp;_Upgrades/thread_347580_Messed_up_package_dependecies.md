---
title: "Messed up package dependecies"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by chaffeur on 2007-01-27
Hi!

I'm running Kubuntu Edgy Eft on my laptop.
I recently tried to install the newest version of [stopmotion]("http://stopmotion.bjoernen.com/"), which weren't available in the dpkg reps.
When I tried to install the .deb file it said that some of the packages it depended on where too old.
So - and this is where I messed up - I downloaded the packages (libxml2-dev, libfontconfig1, libfontconfig1-dev, libqt4-dev and maybe some more, I fail to remember) from [debians package site]("http://packages.debian.org/") and installed through **dpkg --install**.
I ran into dependency problems with all packages except libxml2, which installed.
I quit installing stopmotion because I thought it was too troublesome and thought everything was fine.
But when I tried to update my system though **apt-get upgrade** I get this

[QUOTE="apt-get upgrade"]
Läser paketlistor... Färdig
Bygger beroendeträd
Läser in tillståndsinformation... Färdig
Du kan möjligen rätta dessa genom att köra "apt-get -f install".
Följande paket har beroenden som inte kan tillfredsställas:
  libfontconfig1: Beror: fontconfig-config (= 2.4.2-1) men 2.3.2-7ubuntu2 är installerat
  libfontconfig1-dev: Beror: libfontconfig1 (= 2.3.2-7ubuntu2) men 2.4.2-1 är installerat
  libqt4-dev: Beror: libqt4-core (= 4.2.0-1ubuntu6) men 4.2.1-2 är installerat
              Beror: libqt4-gui (= 4.2.0-1ubuntu6) men 4.2.1-2 är installerat
  libxml2-dev: Beror: libxml2 (= 2.6.26.dfsg-2ubuntu4) men 2.6.27.dfsg-1 är installerat
E: Otillfredsställda beroenden. Försök med -f.
[/QUOTE]

which complaints about dependency issues. I think these are the packages I failed to install.
When i run **apt-get -f install** as **apt-get upgrade** recommends it wants to remove 269 packages I use.
What do I do now?

Thankful for all help.

---

### Post by chaffeur on 2007-01-30
Ok, so I finally came to a solution.
I downloaded the original packages from [http://packages.ubuntulinux.org/edgy/libs/]("http://packages.ubuntulinux.org/edgy/libs/") and then **dpkg --install**ed them.
Finally i **apt-get upgrad**ed to configure the packages.
A bit messy, but now I'm back where I started.

---

