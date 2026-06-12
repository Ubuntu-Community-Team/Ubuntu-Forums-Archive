---
title: "Broken Upgrade from Dapper to Edgy"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by EMCOgre on 2007-03-17
I finally tried upgrading to Edgy from Dapper tonight.  While installing packages, it bailed.  Now I have two broken packages: libxdmcp6 and xserver-xorg-core.  I've tried several things to try to clean it up, but no luck.

When I try "sudo apt-get -f install" I get this (after it :

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  x11-common
The following packages will be upgraded:
  x11-common
1 upgraded, 0 newly installed, 0 to remove and 954 not upgraded.
47 not fully installed or removed.
Need to get 0B/291kB of archives.
After unpacking 418kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 108649 files and directories currently installed.)
Preparing to replace x11-common 7.0.0-0ubuntu45 (using .../x11-common_1%3a7.1.1ubuntu6.2_i386.deb) ...
Unpacking replacement x11-common ...
dpkg: error processing /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6.2_i386.deb (--unpack):
 trying to overwrite `/usr/X11R6/bin', which is also in package opera
Errors were encountered while processing:
 /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help is greatly appreciated.

Thanks,
Rob

---

### Post by zvacet on 2007-03-18
synaptic>edit>fix broken packages

---

### Post by EMCOgre on 2007-03-18
I already tried that, it doesn't work.  Synaptic 'fixes' them, but as soon as I resume the upgrade, I get the same type of error.  If I continue the upgrade in synaptic after fixing the broken packages instead of breaking back out to the CLI, I get this error:

E: /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6.2_i386.deb: trying to overwrite `/usr/X11R6/bin', which is also in package opera

Rob

---

### Post by bulldog on 2007-03-18
You can try ```
sudo aptitude dist-upgrade
```

But I have to tell you,I did the same thing a while back and ended with a broken Dapper.
Did a clean install and Edgy was fine after that.

I'll never do an upgrade again,just a new install is so much quicker.

---

### Post by EMCOgre on 2007-03-18
Yeah, I'm afraid unless somone can help me out, that's what will happen.  When I upgraded from Breezy to Dapper I used the CLI to upgrade like you suggest, it broke, and I ended up loading a clean Dapper from CD.  

That's why this time I was careful to upgrade using the suggested method instead.  Unfortunately it still broke.  Sigh.  That and the DVD stuff (which I *just* got to work) will nearly drive me back to the evil empire. 

Rob

---

### Post by bulldog on 2007-03-18
Well,to get your DvD stuff at work and the music as well.isn't that hard to do.
Just install Automatix for Edgy and it does it for you,cost no more as 10 minutes.

Take a look at this link,
[http://www.getautomatix.com/](http://www.getautomatix.com/)

Install it and you have a load of useful programs on your hands.

---

### Post by la3875 on 2007-04-28
I have exactly the same problem as a result of trying to upgrade to Edgy from Dapper. Any other ideas barring wiping the drive for a new install? I feel like its close to succeeding but I'm still a noob...

If there is no upgrade fix. Does anyone have suggestions for repairing the broken packages. I feel like I've tried everything including the Dapper install disc.

---

### Post by webramp on 2007-05-29
try dpkg -r opera

hope this helps.

---

