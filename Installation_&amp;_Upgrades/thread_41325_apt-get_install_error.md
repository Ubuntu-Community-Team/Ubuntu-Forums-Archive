---
title: "apt-get install error"
date: 2005-06-13
forum: Installation &amp; Upgrades
---

### Post by chris2re on 2005-06-13
was trying to install gnomebaker just now. This does not only happen when trying to install gnomebaker, but other applications as well.

Error:
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: You may want to run apt-get update to correct these problems

What do I do?

Here is the whole situation:
(Some is Norwegian language since I have Ubuntu on norwegian =)

root@Schnuppa:/home/chris # apt-get install gnomebaker
Reading package lists... Done
Building dependency tree... Done
Følgende ekstra pakker vil bli installert.
  cdda2wav liboggflac1 mpg321 sox vorbis-tools
Foreslåtte pakker:
  cdrtools-doc
Følgende NYE pakker vil bli installerte:
  cdda2wav gnomebaker liboggflac1 mpg321 sox vorbis-tools
0 upgraded, 6 newly installed, 0 å fjerne og 3 ikke oppgradert.
Trenger å skaffe 1066kB med lagre.
Efter utpakking vil 3240kB mere diskplass bli brukt.
Do you want to continue [Y/n]? y
Hent:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe cdda2wav 4:2.0+a38-1ubuntu4 [153kB]
Hent:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe mpg321 0.2.10.3 [34,5kB]
Hent:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe sox 12.17.5-4 [264kB]
Hent:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main liboggflac1 1.1.1-4 [30,0kB]
Hent:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main vorbis-tools 1.0.1-1.1ubuntu1 [190kB]
Hent:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe gnomebaker 0.3-3 [394kB]
Skaffet 1066kB på 15s (68,5kB/s)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)

Preconfiguring packages ...
Velger den tidligere fravalgte pakken cdda2wav.
(Leser database ... 71766 filer og kataloger er installerte.)
Pakker ut cdda2wav (fra .../cdda2wav_4%3a2.0+a38-1ubuntu4_i386.deb) ...
Velger den tidligere fravalgte pakken mpg321.
Pakker ut mpg321 (fra .../mpg321_0.2.10.3_i386.deb) ...
Velger den tidligere fravalgte pakken sox.
Pakker ut sox (fra .../sox_12.17.5-4_i386.deb) ...
Velger den tidligere fravalgte pakken liboggflac1.
Pakker ut liboggflac1 (fra .../liboggflac1_1.1.1-4_i386.deb) ...
Velger den tidligere fravalgte pakken vorbis-tools.
Pakker ut vorbis-tools (fra .../vorbis-tools_1.0.1-1.1ubuntu1_i386.deb) ...
Velger den tidligere fravalgte pakken gnomebaker.
Pakker ut gnomebaker (fra .../gnomebaker_0.3-3_i386.deb) ...
Setter opp cdda2wav (2.0+a38-1ubuntu4) ...
Setter opp mpg321 (0.2.10.3) ...

Setter opp sox (12.17.5-4) ...
Setter opp liboggflac1 (1.1.1-4) ...
Setter opp vorbis-tools (1.0.1-1.1ubuntu1) ...

Setter opp gnomebaker (0.3-3) ...

W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 Ingen slik fil eller filkatalog)
W: You may want to run apt-get update to correct these problems

---

### Post by ubuntu_demon on 2005-06-13
replace your /etc/apt/sources.list with this one :

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

after that :
$ sudo apt-get update
$ sudo apt-get upgrade

---

### Post by chris2re on 2005-06-13
Tnx m8!

But why this on the apt-get upgrade:

root@Schnuppa:/home/chris # sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  mozilla-firefox mozilla-firefox-gnome-support
0 upgraded, 0 newly installed, 0 å fjerne og 2 ikke oppgradert.

?

---

### Post by ubuntu_demon on 2005-06-14
[QUOTE=chris2re]Tnx m8!

But why this on the apt-get upgrade:

root@Schnuppa:/home/chris # sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  mozilla-firefox mozilla-firefox-gnome-support
0 upgraded, 0 newly installed, 0 å fjerne og 2 ikke oppgradert.

?[/QUOTE]
 To "solve" it just type either :

$ sudo apt-get dist-upgrade

or

$ sudo apt-get install mozilla-firefox mozilla-firefox-gnome-support

The backports project gets most of their packages from breezy. In breezy the package is called firefox instead of mozilla-firefox ....that's why. :)

---

