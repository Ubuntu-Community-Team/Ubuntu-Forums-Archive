---
title: "Installer crashes during disk format"
date: 2011-11-20
forum: Installation &amp; Upgrades
---

### Post by mastablasta on 2011-11-20
Very annoying. 

the installer suggested i update it before performing install. i clicked and nothing really happened. or it could be it ran out of memorry to do an update. this was a fresh image off the site, so if there is something wrong with installer should the image be fixed?

is there a way to check if the cd is burned ok (besides verify after burning)?

i currently installed Chrunchbang instead but it's proving difficult to see any shares on it or share any folder from it. does anyone know how does Xubuntu solve this issue? i should see a samba share and linux mashicne but they don't have any network folder in thunar, so i am not even sure where am i supposed to see the shared files.

---

### Post by Elfy on 2011-11-20
> **mastablasta said:**
> is there a way to check if the cd is burned ok (besides verify after burning)?

I assume that you checked that the download you burnt form was good.

I use a script I [found here]("https://help.ubuntu.com/community/HowToMD5SUM") to check the md5sum of the cd against the iso.

---

### Post by mastablasta on 2011-11-21
tried those and got OK on all counts.
 
so it seems CD is OK and image is also good. it seems something is (was) wrong with installer. otherwise why would the first thing be "you should update the installer"?

---

### Post by Elfy on 2011-11-21
really  odd - I've never been asked by any livecd to update - nor have I ever seen a similar thread here - not though saying that there aren't any.

If you install with it does it complete?

---

### Post by kalehrl on 2011-11-21
How much RAM do you have?
I couldn't install Lubuntu from live cd on a laptop with 256MB of RAM.
Minimal install worked OK.

---

### Post by mastablasta on 2011-11-22
> **forestpiskie said:**
> If you install with it does it complete?
 
actually it was a surprise for me too.
the update didn't work. Everythign stopped as i saw that hard disk wasn't working at all.
 
> **kalehrl said:**
> How much RAM do you have?
I couldn't install Lubuntu from live cd on a laptop with 256MB of RAM.
Minimal install worked OK.
 
AHA! Yes i do have 256 MB ram (224 MB actually). Would alternate CD work? Still the troubling thing is that i too thought that RAM is the issue, that's why i decided to only go with installer to the point when it would format below while at the same time it asks questions about keboard and such. The problem is that the whole thing crashed during disk format. as in formatting ...... installer encountered a problem and crashed.
 
Actually i am having good progress with Chrunchbang XFCE now (only Windows shared printer left to be configured). 80MB occupied showing in Conky at idle :-) Though the porgrammes are probably a bit dated (Debian 6 stable)
 
I am still interested in definite solution to install, as i still might switch to Lubuntu on this laptop (maybe on the LTS if not now). Too bad i don't have much disk space (20GB disk) to do multiboot. Afterall Ubuntu still has many userfriendly features.

---

### Post by kalehrl on 2011-11-22
I believe there is a bug report on launchpad about not being able to install Lubuntu with 265MB of RAM.
It seems that installer is at fault, not Lubuntu itself.
I'm not familiar with alternate cd installation but I installed Lubuntu successfully from a USB stick using mini.iso. Of course, you will need internet connection.
Detailed instructions can be found here:
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)
Good Luck!

---

### Post by mastablasta on 2011-11-23
Ah, you went with Mini. well it came to my mind, but though conneciton is not an issue the computer is kind of slow in downloading.  I kind of though it was installers fault. I guess ti should work on alternate CD then, sicne alternate is ment for those with lower than 256 MB ram. 
 
i think i will wait for the LTS, if the compuiter still works. was thinking of getting a netbook instead of this old mashine, but they all come with win7 preloaded and i am also short on money latetly. :-(

---

