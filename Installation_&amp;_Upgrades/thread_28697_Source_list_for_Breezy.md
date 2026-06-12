---
title: "Source list for Breezy"
date: 2005-04-21
forum: Installation &amp; Upgrades
---

### Post by abmcr on 2005-04-21
I have actually this source list in /etc/apt/sources.list

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
 ## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main


I want to get the latest version of OpenOffice and other software from Breezy. It is necessary to change hoary in breezy in the sources.list? Thank you

---

### Post by heimo on 2005-04-21
Hi!
 
You probably don't want to change to breezy at this moment, not just for lates OpenOffice (have you checked which version you'd get, or was that just a guess?). If you insist using breezy, check "apt pinning", setting priorities for different repositories, so you can choose just what you want from breezy and don't need to break other packages in upgrade.
 
Are you using 1.x OpenOffice? As you can get 2.x version without Breezy. I've done that. Search for package openoffice2 (I can't verify any details at the moment, if you've any problems, feel free to ask).
 
Sorry if I misunderstood you.
 
Cheers!
 
 
EDIT: Oh! openoffice.org2 is in hoary universe
 
 
[[color=#0000ff]breezy[/color]]("http://packages.ubuntu.com/breezy/editors/openoffice.org2") (editors): Office suite core, version 2.0 
1.9.79.2-0ubuntu2: i386 powerpc 
 
[[color=#0000ff]hoary[/color]]("http://packages.ubuntu.com/hoary/editors/openoffice.org2") (editors): Office suite core, version 2.0 [[color=red]universe[/color]] 
1.9.79.2-0ubuntu2: i386 powerpc
 
It's the same version. You need to add this to your bookmarks. :)
[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

---

### Post by abmcr on 2005-04-21
My version of OO is the same of Breezy. My interest for Breezy is fot the future version (es: Gimp 2.2.6). Thank you

---

### Post by heimo on 2005-04-21
Great! :) It's nice to test new software - and I really like the development that Gimp has seen recently. Add new repositories for breezy (leave the hoary repositories in sources.list) and check that apt-pinning - it's really good idea to have there. It'll prevent other packages upgrading - you can just select the ones you want.
 
Here's the page I used to check the syntax (I'm using hoary/breezy):
[http://jaqque.sbih.org/kplug/apt-pinning.html]("http://jaqque.sbih.org/kplug/apt-pinning.html")
 
Hopefully that helps!

---

