---
title: "Synaptic gone?"
date: 2005-04-02
forum: Installation &amp; Upgrades
---

### Post by mirland on 2005-04-02
Hi!

I am fairly new to Linux of any kind and last week I installed Ubuntu (warty). Today I upgraded to Hoary but my Synaptic is gone ? Where is it at ? And suddenly I have a "Debian" menu in the "Applications" menu containing basically all the same app's as in the "accesories" "games" etc. I have a feeling my upgrading didn't go as expected. What can I do ?

I am running on an Acer Travelmate 8003 Lmi laptop with 1250mb ram. 

This is my sources.list:

___________________________

[FONT=Courier New]
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted

 ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe[/FONT]
_____________________

Any help will be appreciated since I really need Synaptic to keep an overview of the installed packages. And I am bit bewildered right now...

Thanks

/Mirland

---

### Post by bored2k on 2005-04-02
Get rid of deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe and try reinstalling Synaptic.

---

### Post by mirland on 2005-04-03
I changed sources.list to the one found in the Hoary Guide section of this site. That did the trick. I still have the Debian menu under "Applications" though...

/Mirland

---

### Post by maqi on 2005-04-03
If I were you I'd be happy about that. The Debian menu will register apps that GNOME and KDE miss  :) 

I wish I had one. If you can work out how to enable it - let me know  8) 

maqi

---

