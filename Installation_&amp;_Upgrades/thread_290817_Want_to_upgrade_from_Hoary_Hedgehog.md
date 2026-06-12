---
title: "Want to upgrade from Hoary Hedgehog"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by Deadl0ck on 2006-11-01
Hi all,
I have a ubuntu box that I use quite a bit, and it's become unstable of late.

I'm on Hoary Hedgehog release.

Is it possible to update to the latest with Synaptic or apt-get ?

Also - whenever I run Synaptic I get loads of errors, and it's because I had played around with the sources.list file.

Do I neead a sources.list for my specific version (i.e Hoard Hedgehog) or can I set it to a later list file ?

I currently have everything commented out on my Sources.list file:

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb http://ie.archive.ubuntu.com/ubuntu hoary main restricted
# deb-src http://ie.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb http://ie.archive.ubuntu.com/ubuntu hoary-updates main restricted
# deb-src http://ie.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://ie.archive.ubuntu.com/ubuntu hoary universe
# deb-src http://ie.archive.ubuntu.com/ubuntu hoary universe

# deb http://security.ubuntu.com/ubuntu hoary-security main restricted
# deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

# deb http://security.ubuntu.com/ubuntu hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe



# ----------------------------------------------------------------
# Following lines copied from Unofficial Ubuntu 5.04 Starter Guide
# Deadl0ck - 16/10/2005
# ----------------------------------------------------------------
## Uncomment the following two lines to fetch updated software from the network
# deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu hoary universe
# deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

# deb http://security.ubuntu.com/ubuntu hoary-security main restricted
# deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

# deb http://security.ubuntu.com/ubuntu hoary-security universe
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe

# deb http://archive.ubuntu.com/ubuntu hoary multiverse
# deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
# deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
# deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

Any help/suggestions would be great !!

---

### Post by bsussman on 2006-11-01
The doc says you cannot skip the intermediate releases so either you do the 6.06 upgrade and be happy with 6.06 (many are)

OR

do 6.06 and then 6.10 which sounds scary to me

OR

a separate 6.10 clean install if you have a spare partition and move data from your old home and other locations.

Your choice.

---

### Post by Joe_CoT on 2006-11-01
If you've screwed up your sources file, I've found the easiest way to get a new one is [Source-o-Matic](http://www.ubuntulinux.nl/source-o-matic)

As for upgrading:

I strongly strongly suggest just reinstalling with either dapper or edgy. It will probably save you trouble, and will most definately save you time.
That said, there's a [Breezy](https://help.ubuntu.com/community/BreezyUpgrade), [Dapper](https://help.ubuntu.com/community/DapperUpgrades), and [Edgy](https://help.ubuntu.com/community/EdgyUpgrades) upgrade guide. The only supported method for upgrading is Hoary -> Breezy -> Dapper, and then -> Edgy if you'd like.

---

### Post by Deadl0ck on 2006-11-02
OK....

I followed the instructions here:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Upgrading_Ubuntu]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Upgrading_Ubuntu")

Basically it says:

[B]    * First update the update manager: 

sudo aptitude update && sudo aptitude upgrade

    * Once it has been updated you can upgrade to a newer version of Ubuntu: 

gksudo "update-manager -c -d"


[/B]

When I run this I get :

[IMG]http://img218.imageshack.us/img218/6509/pic1rb5.jpg[/IMG]

I then click "OK" and I get :

[IMG]http://img218.imageshack.us/img218/3457/pic2ow8.jpg[/IMG]

So - where do I go now ???

If I type "uname -a" I get:

[B]Linux martin-linux 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux
[/B]

Any suggestion / ideas would be great !

---

### Post by Lord Illidan on 2006-11-02
I would just download Edgy or Dapper and install it from scratch.

---

### Post by Deadl0ck on 2006-11-02
> I would just download Edgy or Dapper and install it from scratch.

Is there no other way ? I'll loose all my apps if I do this, and have to reinstall everything again :(

What version is 2.6.10-5-386 ? Is that Hoary ?

---

### Post by bluenova on 2006-11-02
Installing your apps won't take long. I would put your /home in a separate partition before installing, that way you will keep all your files and settings, so when you reinstall the apps your settings will be as they were before.

[www.psychocats.net/ubuntu/separatehome](www.psychocats.net/ubuntu/separatehome)

---

### Post by Deadl0ck on 2006-11-02
OK, But is there a way to upgrade ???

I can do a rerinstall if all elese fails, but surely there is some way of uupgrading ?

---

### Post by bluenova on 2006-11-02
```
sudo gedit /etc/apt/sources.list
```
Then do a find a replace, and replace hoary with breezy. After that:
```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude dist-upgrade
```

Once on Breezy you will then need to do the same to get to Dapper.

---

### Post by Deadl0ck on 2006-11-02
Great - that's working. THANK YOU !!!

---

