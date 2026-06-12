---
title: "[SOLVED] how to upgrade"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by zimbot on 2008-12-01
I have ubuntu studio 7.04  ... when I attempt to upgrade to 7.10
( my real goal is to upgrade to ubuntu studio 8.10 )  I get a failure with :Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg) Could not resolve 'archive.ubuntustudio.org'
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'archive.ubuntustudio.org'
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'archive.ubuntustudio.org'

so - it looks like I cannot upgrage from 7.04 > 7.10 > 8.10  is THAT true?

can I upgrade via the dvd disc?
( this is a dual boot xp & ubuntu studio 7.04 sys )

thanks

---

### Post by Pumalite on 2008-12-01
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by zimbot on 2008-12-01
yes I attempted to follow the wisdom of 

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
and
[https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)

but I suppose the repositories are "gone" - "changed" and if chnaged to what then?
I think this is a problem specific to ubuntu server...[ ubuntustudio.org ]
dunno, 
But if there IS a way... i would love to know it.

but those instructions lead to a dead end ( maybe it's me ) for me.

---

### Post by Pumalite on 2008-12-01
Maybe this will help:
[http://www.howtoforge.com/upgrading-ubuntu-studio-from-7.04-to-7.10](http://www.howtoforge.com/upgrading-ubuntu-studio-from-7.04-to-7.10)

---

### Post by zimbot on 2008-12-01
well, that IS what I have been doing  and it fails with

Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg) Could not resolve 'archive.ubuntustudio.org'
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'archive.ubuntustudio.org'
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'archive.ubuntustudio.org'

---

### Post by Pumalite on 2008-12-01
Check connection and try changing to 'Best Server'
System>Administration>Software Sources>Download From>Best Server

---

### Post by alzie on 2008-12-01
According to this link : [http://ubuntuforums.org/archive/index.php/t-802830.html](http://ubuntuforums.org/archive/index.php/t-802830.html) the poster removed archive.ubuntustudio.org as other repository.

This is from back in May so I'm not sure if it will help.

Upon further reading I **think** this will upgrade to Ubuntu rather than Ubuntustudio.  It also appears that the Ubuntustdio archives have been moved or removed.

You may have to do regular Ubuntu upgrades to 8.10 then upgrade to Ubuntustudio from there.

The other option would be to try to locate alt installs for Ubuntustudio for 7.10 and 8.04 and try doing the upgrade from DVD.  I'm not familiar with this method so I can't recommend it.

As with any upgrade, you should backup any important files.

I hope this helps

---

### Post by zimbot on 2008-12-02
ok , good news.   -- that works  --

I removed archive.UbuntuStudio...  from my repos.
it " went ' to a gnrc  -- the upgrade happened.

presently I have ubuntu studio 7.10 ( it did do studio! )

I frimmly suspect that I can upgrade on to 8.4 ( and maybe to 8.10  wondering if i should????? // also there is *NOW* a 9.10 )

[ now to figure out how to mark this solved ;)

---

### Post by alzie on 2008-12-02
8.10 is current.

8 is for 2008,  .04 is for April release and .10 is October release.

So now you can relax :popcorn:

---

