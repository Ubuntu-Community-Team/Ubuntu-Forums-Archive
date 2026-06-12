---
title: "Where to get Compiz 0.7.5"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by the.original.kermit on 2008-05-18
I have looked all over and have tried installing several different packages, but everytime I install them, I go into Synaptic and it still says 0.7.4.

So far I've tried 

-compiz-0.3.6.tar.bz2 (from Source Packages on [http://compiz.org/Download](http://compiz.org/Download))
-Downloading with git (from bottom of [http://compiz.org/Download](http://compiz.org/Download))

I believe that these would give me the latest version.

Thanks for your help.

---

### Post by Sef on 2008-05-18
0.7.4 is the latest version.

[Bleeding edge]("http://wiki.compiz-fusion.org/Get%20Compiz%20Fusion"):

> Installing From Git

This is not recommended unless you want the absolute bleeding-edge version or are a developer. Because Git is divided into many different repositories, you can use a script to download and build all the components for you. You can check these out by using:

git clone git://git.compiz-fusion.org/users/kristian/compiz-scripts
git clone git://anongit.compiz-fusion.org/fusion/misc/yags

The 'get-git' script will clone and update all Compiz Fusion related modules such as libcompizconfig, compiz and emerald and the 'YAGS' script will clone all plugin repositories. Using yags is fairly simple, just execute './yags $COMMAND' where $COMMAND can be 'pull' 'make' 'make install' 'make clean' 'clone'. YAGS will then apply this command to all applicable directories.

---

### Post by the.original.kermit on 2008-05-18
What I'm trying to do is to get all of the cool effects and stuff for compiz, like cube.

Should I be looking for the 3D Windows Plugin, and if so where do I get that

---

### Post by forestpixie on 2008-05-18
Assuming that you have the latest version, most is installed by default, you just need to add the settings manager

```
sudo apt-get install compizconfig-settings-manager
```

Then you can get the cube and everything else, once you have got custom enabled in Preferences >Appearances

---

