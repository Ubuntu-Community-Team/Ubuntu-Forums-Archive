---
title: "Karmic Upgrade issues"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by Imashinu on 2009-11-22
I recently did a fresh install of Karmic and a lot of things have seemed to go wrong.

1: Flash doesn't work properly anymore. I followed every flash guide on this site to install. But buttons in flash don't seem to work and I cannot find a solution to this.

2: Firefox cannot install addons. It tells me that I need to install firefox if I want to download them. I reinstalled and made a new profile, and I'm getting nothing.

I'm running x64 if that matters. These are really causing a lot of problems though and it has been really frustrating trying to fix them.

---

### Post by lmarmisa on 2009-11-22
I believe that the addons and the configurations files of Mozilla are stored inside your /home directory (**/home/username/.mozilla**).

You could check if this problem also impacts to other users' accounts defined in your computer.

Define a new user "test" and check if the problems with Mozilla are the same than yours in that different account.

Best regards,

Luis

---

### Post by phillw on 2009-11-22
Hi,
    Lovinglinux keeps a good thread over here --> [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)
There are some common glitches covered in his introduction.

There have been various issues with Flash plugins, heading over there will track down the one that is affecting you.

Regards,

Phill.

---

### Post by Imashinu on 2009-11-23
Unfortunately neither of those suggestions worked. I still can't seem to get it to work :(

---

### Post by NawafLol on 2009-11-23
Is the flash issue happans with chromuim or firefox !

If its in chromuim you might need to turn compiz off (if you have one)

This might help : [https://bugs.edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407)

And for Firefox what version do you have just type just type : firefox --version (i don't what's the default version for karmic kola)

---

### Post by Imashinu on 2009-11-23
Compiz wasn't the troblem, I tried that already. It's firefox 3.5.5, I assume the x64 version. I still haven't gotten anything to work.

---

