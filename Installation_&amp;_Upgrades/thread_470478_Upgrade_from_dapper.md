---
title: "Upgrade from dapper"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by jarrett on 2007-06-11
Hi,
I've been thinking about upgrading my box with dapper to feisty.
Currently it's serving as a fileserver, ftp and webserver, and sometimes i use it as a 'desktop' station.
Now what I wonder is, will my jbod volume consisting of 3 different discs be intact after an upgrade, or will I have to configure them again as jbod?
And, for the ftpd I use glftpd, will that also work 'as is' after upgrade? And of course the same question goes for the apache/php/mysql installation...

Best regards,
Jarrett

---

### Post by dmizer on 2007-06-11
you can't go directly from dapper to feisty.  you'll have to take the rocky road and take your chances with the dapper to edgy, then edgy to feisty ...

you're better off to wait for the next LTS relese which will allow direct upgrades from dapper.  i believe that may be gutsy +1 but no official word on that.

the short of it is unless you're really in dire need of updating to feisty, don't do it.  if it is absolutely necessary for you to use feisty, you're best and most painless option is to do a completely fresh install.

edit:
if it's a server ... leave it be.  you're better off with an LTS release as a server because the package base is more stable, and you won't have to worry about potentially broken packages ending up putting your server offline.

---

### Post by jarrett on 2007-06-11
Alright, but what about if you do a fresh install of Feisty.. is it easy to get the lvm back with all the stuff on the harddrives intact?
But maybe i'll wait for the next LTS release then...

---

### Post by dmizer on 2007-06-11
i have lvm on my own server ... not too sure how that will work out for me either, and i'm not looking forward to an upgrade.  i intend to put it off as long as safely possible.

take some serious time over the next year or two to do some serious research.  my first instinct is that if you have a separate home partition (and all your data is located in said partition) you'll be fine.  you'd have to restore the home partition later, but all your data should be safe.  but do lots of research.  an upgrade to a server full of data is not a thing to t ake lightly.

---

