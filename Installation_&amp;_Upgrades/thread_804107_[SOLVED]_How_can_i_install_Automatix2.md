---
title: "[SOLVED] How can i install Automatix2?????"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by RMD94 on 2008-05-22
Hii everybody,

I am Rajas and i wanted to know how to install Automatix2..... I went to their official site and got linked to the installation info. and when i put these commands:

echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main" | sudo tee -a /etc/apt/sources.list

wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)

gpg --import automatix2.key

gpg --export --armor E23C5FC3 | sudo apt-key add -

sudo apt-get update

It gives me an error.......

I first put the 1st command
then 2nd
then 3rd
then 4th

and at last when i type sudo apt-get update it gives me an error:

E: Type '&#8220;deb' is not known on line 58 in source list /etc/apt/sources.list

What should i do????

plz help me


I have AMD 64 Athlon
I am a 32 bit user


-Thank You Very Much

---

### Post by Lord Landis on 2008-05-22
It sounds like there's a typo somewhere.  Please post the relevant section from '/etc/apt/sources.list' so we can look it over.

Truthfully though, Automatix2 isn't the best thing to put on your system.  Which particular codecs/applications are you trying to install that you want/need Automatix for?

---

### Post by abn91c on 2008-05-22
If i'm not mistaken Automatix is no longer available, i think there was an article on the softpedia website about it and their website go here [http://www.getautomatix.com/forum/index.php?showtopic=2424](http://www.getautomatix.com/forum/index.php?showtopic=2424)

---

### Post by Bubba64 on 2008-05-22
> **RMD94 said:**
> Hii everybody,

I am Rajas and i wanted to know how to install Automatix2..... I went to their official site and got linked to the installation info. and when i put these commands:

echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main" | sudo tee -a /etc/apt/sources.list

wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)

gpg --import automatix2.key

gpg --export --armor E23C5FC3 | sudo apt-key add -

sudo apt-get update

It gives me an error.......

I first put the 1st command
then 2nd
then 3rd
then 4th

and at last when i type sudo apt-get update it gives me an error:

E: Type '“deb' is not known on line 58 in source list /etc/apt/sources.list

What should i do????

plz help me


I have AMD 64 Athlon
I am a 32 bit user


-Thank You Very Much

Even if you can or could get Automatix your next upgrade will probably be horrible. In spite of the quick resources that it provided you couldn't remove everything to upgrade due to there being no record of installs of packages which can cause an upgrade to fail.

---

### Post by Pumalite on 2008-05-22
[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)
[http://ubuntuforums.org/announcement.php?f=13/](http://ubuntuforums.org/announcement.php?f=13/)
[http://ubuntuforums.org/showthread.php?t=519872](http://ubuntuforums.org/showthread.php?t=519872)
[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

---

### Post by matchstich on 2008-05-22
i would stay away from it.  i got it . thought--- wow, this sure makes things easy.

then i ran my weekly scan, found a root kit.  i only use my box for email

and a little searching.  wiped the drive and reinstalled.

 never did get automatrix again and my scans

have been clean since.

---

### Post by RMD94 on 2008-05-23
First of all Thank You very much,

And i kinda agree with u guys... i don't think i want automatix on my PC..... BUT NOW I GOTTA BIG PROBLEM!!!!!!!!! Now I can't install updates cuz of this stupid Automatix.... as i told u i get a error while installing it, that's the reason my Ubuntu is not able read the update pakages!!!!!!! it says 

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '“deb' is not known on line 58 in source list /etc/apt/sources.list, E:The list of sources could not be read.'


plz plz plz plz help me!!!!

Looking forward to hear from u......

Thank You

---

### Post by RMD94 on 2008-05-23
help me!!!!

---

### Post by aysiu on 2008-05-23
**Step 1**
Close the package manager.

**Step 2**
Open a [terminal](http://www.psychocats.net/ubuntu/terminal)

**Step 3**
Paste these commands in the terminal: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.automatix
gksudo gedit /etc/apt/sources.list
``` The second command should open an empty text file.

**Step 4**
In the empty text file, paste in this text: ```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu hardy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hardy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hardy universe
deb-src http://archive.ubuntu.com/ubuntu hardy universe

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted

deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe

deb http://archive.ubuntu.com/ubuntu hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu hardy multiverse

# deb http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse

# deb http://archive.canonical.com/ubuntu hardy partner

deb http://packages.medibuntu.org/ hardy free non-free
``` Then save and close the file.

Then follow these instructions to install what you probably wanted Automatix for in the first place:
[http://www.psychocats.net/ubuntu/nonfree](http://www.psychocats.net/ubuntu/nonfree)

---

### Post by RMD94 on 2008-05-23
Thanks for your help... It worked

Thank You

---

