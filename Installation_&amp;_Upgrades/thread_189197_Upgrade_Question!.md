---
title: "Upgrade Question!"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by henry95 on 2006-06-04
I am currenty running, Breezy Badger 5.10 and am thinking about upgrading to dapper drake, but my question is, when I upgrade am i going to lose all my settings, such as my ati video card drivers, and dual monitor settings?

Thanks!

---

### Post by aysiu on 2006-06-04
You shouldn't... but you might. I would back up your important configuration files. At the very least, do ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
``` At the most, you can make an image backup of your Breezy installation: [http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html) 

That way, if the upgrade screws up your system, you can always restore the working Breezy installation easily.

---

### Post by henry95 on 2006-06-04
ok thanks a lot.

---

### Post by Russty of Oz on 2006-06-04
Hi, I was just wondering if I need to do anything now that Dapper official realease is out.  I installed the 6.06 RC version, so is there any difference between that and the final release?  

Russty

---

### Post by aysiu on 2006-06-04
[QUOTE=Russty of Oz]Hi, I was just wondering if I need to do anything now that Dapper official realease is out.  I installed the 6.06 RC version, so is there any difference between that and the final release?  

Russty[/QUOTE] Yes, you need to do something: Paste these commands in the terminal. ```
sudo aptitude update
sudo aptitude dist-upgrade
``` That's it.

---

### Post by Russty of Oz on 2006-06-04
[QUOTE=aysiu]Yes, you need to do something: Paste these commands in the terminal. ```
sudo aptitude update
sudo aptitude dist-upgrade
``` That's it.[/QUOTE]

Ok, I did that, it was painless!  

Thanks for the help.

Russty.:)

---

### Post by Compucore on 2006-06-05
I have done that with ubuntu update manager for Breezy. And didn't have a problem what so ever. Now when I tried on my Hoary to bring it up to dapper. I'm totally blocked out of ever getting it upgraded to dapper. I had even done the command line to try and bring it to dapper still nothing. I am missing something that is completely different from Breezy than in- Hoary hedgehog. I want to bring my old Aptiva 2158-281 up to dapper like my Dell GX150.

Compucore

---

### Post by aysiu on 2006-06-05
I wouldn't advise skipping a version (Hoary > Dapper).

You should probably upgrade from Hoary to Breezy, then to Dapper.

Or, better yet, [create a separate /home partition](http://www.psychocats.net/ubuntu/separatehome.html) and do a fresh install of Dapper.

---

### Post by Compucore on 2006-06-05
I've already tried that once already with the CD of Brezzy in the machine. And it didn't really like it at all. It is the same CD that I had used for my Dell GX150 that I had installed Breezy onto. Then repatched everything to make sure that everything was fine for the live update to Dapper drake on my Dell machine there should be another way of even doing a live update from the servers here to get it going and re patched everything from that and then go and upgrade to dapper. Some how my Aptiva 2158-281 doesn't like Breezy so much as for installation from the CD itself. And stalls on the partition program that is being used on the CD itself. In come case I would agree with you. But since it is a non essential computer that I am using it on. Going to a drastic change from one version to another doesn't really mater for me. It's not like I am trying to install it on a SGI O2 computer which is a completely different architecture completely.

Compucore


[QUOTE=aysiu]I wouldn't advise skipping a version (Hoary > Dapper).

You should probably upgrade from Hoary to Breezy, then to Dapper.

Or, better yet, [create a separate /home partition](http://www.psychocats.net/ubuntu/separatehome.html) and do a fresh install of Dapper.[/QUOTE]

---

