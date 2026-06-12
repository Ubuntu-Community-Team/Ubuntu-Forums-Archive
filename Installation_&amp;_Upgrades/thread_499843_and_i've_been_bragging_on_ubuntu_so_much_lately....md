---
title: "and i've been bragging on ubuntu so much lately..."
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by Underwater Ninja Tigra on 2007-07-13
... but i cant figure it out. i started using Ubuntu in college  back in late 05, but i'll spare you the back story. I have a Dell Inspiron 6000 and an intel chip. i dont know all the specifications, but until a few nights ago Edgy was working fine. I had been having trouble figuring out how to download applications and what-not until i started lurking through the forums and found EasyUbuntu. but a few nights ago, i wiped my hard drive. again. for like the 5th or 6th time since i got the thing when i went to college... im used to it, i usually have an installation disc or two handy just in case, but this time, all i had was a copy of feisty i had burned, not 20 minutes before i messed my lappy up. lucky...

long story short... i cant download automatix2 and none of the methods in the ubuntuguide for feisty for manually installing them are working. there arent any in particular im looking for other than Java and flash for Mozilla. i did manage to install the 96 updates i had waiting for me when i connected to the internet, but now i cant figure it out and im about to give up and pretend like i dont have a computer for a month...

halp!

---

### Post by mikewhatever on 2007-07-13
Have you enabled Universe and Multiverse in System>Admin>Software Sources?
Do you get any error messages? If I remember correctly, flash offered to install itself by simply visiting a site that required it.

---

### Post by Underwater Ninja Tigra on 2007-07-13
[I]Quote: mikewhatever  	Have you enabled Universe and Multiverse in System>Admin>Software Sources?
Do you get any error messages? If I remember correctly, flash offered to install itself by simply visiting a site that required it.[/I]

im not sure what you mean by enabling Universe and Multiverse. I went to the screen you said, but couldn't find anything about Universe and Multiverse.

when i try to install automatix2 in the terminal it says E:Couldn't find package automatix2

---

### Post by yakkeh on 2007-07-13
if you're using command line to install your packages, try following instructions:
[http://www.debianadmin.com/install-automatix2-in-ubuntukubuntuxubuntu.html](http://www.debianadmin.com/install-automatix2-in-ubuntukubuntuxubuntu.html)

---

### Post by yakkeh on 2007-07-13
to enable universe/multiverse, you will need to 
  sudo gedit /etc/apt/sources.list
and uncomment the universe/multiverse entries (delete the leading #)
save and 
  apt-get update

or you can open the graphical software managers and click your way around to enable it

---

### Post by Underwater Ninja Tigra on 2007-07-13
> **yakkeh said:**
> to enable universe/multiverse, you will need to 
  sudo gedit /etc/apt/sources.list
and uncomment the universe/multiverse entries (delete the leading #)
save and 
  apt-get update

or you can open the graphical software managers and click your way around to enable it

everything works fine until the sudo apt-get update and at the end of a very long list, i get:

E: Some index files failed to download, they have been ignored, or old ones used instead.

also, the link you posted is for edgy, i have feisty installed now, and i dont have any edgy disc's or a way to get them...

---

### Post by maestrobwh1 on 2007-07-13
I am not sure if this is helpful or if you have tried it.  Go to
[http://www.getautomatix.com/]("http://www.getautomatix.com/")

And use the manual method... scroll down the page under the installation tab.  Make sure you have removed automatix first.  It is also important when following the directions, to do the "add key" part.  It might be possible that if this wasn't done by whatever method you are using that if the key isn't signed (loaded), that automatix isn't installing.  I had an issue similar to that at one time for something else.

See what happens.  If not, open your /etc/apt/sources.list and see if it looks like mine, there is some stuff at the end that was added by me so don't add those unless you need something at some point  like wine, Opera or KDE.  My sources.list is below

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) feisty-security multiverse

deb [http://www.getautomatix.com/apt/](http://www.getautomatix.com/apt/) feisty main

#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

# user added repos
# swiftfox repo
deb [http://getswiftfox.com/builds/debian/](http://getswiftfox.com/builds/debian/) unstable non-free
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) feisty-commercial main
deb [http://kubuntu.org/packages/kde-357/](http://kubuntu.org/packages/kde-357/) feisty main
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
# deb [http://gauvain.tuxfamily.org/repos/](http://gauvain.tuxfamily.org/repos/) feisty contrib
# deb-src [http://gauvain.tuxfamily.org/repos/](http://gauvain.tuxfamily.org/repos/) feisty contrib
# deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
# deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

---

### Post by mikewhatever on 2007-07-13
> **Underwater Ninja Tigra said:**
> [I]Quote: mikewhatever  	Have you enabled Universe and Multiverse in System>Admin>Software Sources?
Do you get any error messages? If I remember correctly, flash offered to install itself by simply visiting a site that required it.[/I]

im not sure what you mean by enabling Universe and Multiverse. I went to the screen you said, but couldn't find anything about Universe and Multiverse.

when i try to install automatix2 in the terminal it says E:Couldn't find package automatix2

Look at the pictures [http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources)
Automatics2 is not in the repositories. Use their site for help [http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

---

### Post by rjfioravanti on 2007-07-13
I thought it was recommended to not use Automatix anymore... why can't you just install packages using synaptic or aptitude?

---

### Post by Pumalite on 2007-07-13
2nd that.

---

### Post by wpshooter on 2007-07-13
> **Pumalite said:**
> 2nd that.

3rd that.

---

### Post by tgalati4 on 2007-07-13
"The motion has been seconded.  All those in favor--say Aye."

---

### Post by mikewhatever on 2007-07-13
> **rjfioravanti said:**
> I thought it was recommended to not use Automatix anymore... why can't you just install packages using synaptic or aptitude?

May I just ask, not recommended by whom?

---

### Post by tgalati4 on 2007-07-13
I think Canonical/Ubuntu has taken an official stance that it is not supported.  By installing software outside of the Synaptic/Apt system and repositories--it can seriously hose your system.  It worked fine for me on several Dapper systems.  I don't know of any ill effects of Automatix.  Some of the programs under the Automatix installer are now available under the restricted and universal/community-supported repositories.  This allows a more controlled installation, but as long as your system works--who cares?

---

### Post by jjross on 2007-07-13
Agreed, there is nothing wrong with Automatix, it has always worked great for me.
I think it is just a bad urban legend that it will break your system, it has never created a problem for me.

---

### Post by confused57 on 2007-07-13
> **jjross said:**
> Agreed, there is nothing wrong with Automatix, it has always worked great for me.
I think it is just a bad urban legend that it will break your system, it has never created a problem for me.
Automatix always worked for me on Breezy, Edgy, Feisty, Mepis, Debian Etch, Xubuntu...even used it to install Nvidia drivers on Debian Etch, works great...therefore...2nd that.

---

### Post by Underwater Ninja Tigra on 2007-07-14
great news everyone... my laptop is back up to speed. :) thank you all very much for all your advice. in the end, i found a link to a wiki that showed me how to sync up repositories properly and allowed me to install automatix2 and get my laptop back to where it was before i wiped it...i'll probably be back here in 6 months or so asking the same quesitons only for a different release.

---

### Post by rjfioravanti on 2007-07-14
ok.. just know that the proper way to install software from the repositories is never going to change.... so you could learn that once and then never have to worry about it again

---

