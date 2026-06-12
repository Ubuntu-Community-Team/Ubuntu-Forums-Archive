---
title: "Problem Getting Source MPlayer"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by Ohmz on 2006-11-09
I am trying to follow some guides so that I can get MPlayer to handle wmv files, however I am having trouble getting the files I need to compile MPlayer from source.

*Whenever I do..*
apt-get build-dep mplayer
apt-get source mplayer

*I always get...*
Reading package lists... Done
Building dependency tree... Done
E: Could not open file /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_source_Sources - open (2 No such file or directory)

I have all the repositories enabled. I just don't understand the error message I'm getting. Still kinda new to Ubuntu I guess...

---

### Post by taurus on 2006-11-09
Use mplayer from either repos or from automatix2.  All you need is to install the codecs and everything will be peachy.  The easiest thing is to use Automatix2 to install all of those and more...

[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by guill3 on 2008-02-04
Hi i think you cant install, automatix in a ubuntu 6.06 checks this wiki;

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

---

### Post by confused57 on 2008-02-04
[http://www.getautomatix.com/wiki/index.php?title=Installation&direction=prev&oldid=6986#Ubuntu_6.06_.28Dapper_i386.29](http://www.getautomatix.com/wiki/index.php?title=Installation&direction=prev&oldid=6986#Ubuntu_6.06_.28Dapper_i386.29)

---

### Post by zvacet on 2008-02-05
Why don´t you install it from repos?To get other things you need to play read [this](https://help.ubuntu.com/community/RestrictedFormats).



and 

```
gsudo gedit /etc/apt/sources.list
```

add this line 

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) dapper free non-free

Save and close.

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
sudo apt-get update
```

Go to the synaptic and find w32 codecs and install them.

---

