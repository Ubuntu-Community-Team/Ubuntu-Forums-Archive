---
title: "Problems with Synaptic Package Manager"
date: 2006-05-30
forum: Installation &amp; Upgrades
---

### Post by Zombithium on 2006-05-30
Hi, 
Basically I have been trying to install mplayer on my Ubuntu Breezy for past few days and haven't been successful.
When I start my synaptic package manager it pops up some errors 

[FONT="Courier New"]Warning : The following problems were found on your system:
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)[/FONT]

And many more similar lines. I also get this error when i do something like
 [FONT="Courier New"]apt-cache search mplayer[/FONT]

Any ideas what is this error and why is it showing up?

---

### Post by Lord Illidan on 2006-05-30
[quote=Zombithium]Hi, 
Basically I have been trying to install mplayer on my Ubuntu Breezy for past few days and haven't been successful.
When I start my synaptic package manager it pops up some errors 

[FONT=Courier New]Warning : The following problems were found on your system:
W: Couldn't stat source package list [http://archive.ubuntu.com]("http://archive.ubuntu.com") breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com]("http://archive.ubuntu.com") breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com]("http://archive.ubuntu.com") breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)[/FONT]

And many more similar lines. I also get this error when i do something like
 [FONT=Courier New]apt-cache search mplayer[/FONT]

Any ideas what is this error and why is it showing up?[/quote]

Try a ```
sudo apt-get update
``` If that doesn't fix it, give us your sources.list

---

### Post by Zombithium on 2006-05-30
Hey thanks for the quick reply
And that works pretty well except that i still get this one error message

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)

And when i do 
apt-cache search mplayer 
it shows me the available packages.
My sources.list - 

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) breezy main
deb-src [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) breezy main

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free


deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

## created by arnieamuleremoved

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy multiverse

---

### Post by Lord Illidan on 2006-05-30
Ok.. I've got a solution from our very own Aysiu's website.

[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

---

### Post by Zombithium on 2006-05-30
sorry to trouble you again and again
But i am not able to edit my sources.list - it fails when i save it.

when i do  
gksudo gedit /etc/apt/sources.list

it gives 
(gedit:11282): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specifie d are supported and host-based authentication failed.

due to which i am not able to update it I guess.

---

### Post by Lord Illidan on 2006-05-30
[quote=Zombithium]sorry to trouble you again and again
But i am not able to edit my sources.list - it fails when i save it.

when i do  
gksudo gedit /etc/apt/sources.list

it gives 
(gedit:11282): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specifie d are supported and host-based authentication failed.

due to which i am not able to update it I guess.[/quote]

Try a simple sudo gedit /etc/apt/sources.list

---

### Post by Zombithium on 2006-05-30
Thanks. I was able to edit my sources.list.
But the problem still persists (I have done sudo aptitude update as given in the tutorial)

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)

:-(
But I think i'll be able to atleast install mplayer now.

---

### Post by Zombithium on 2006-05-30
I got it now - forgot to do after changing my sources.list
 > sudo apt-get update
After having done sudo apt-get update, it works perfect.

Thanks.

---

