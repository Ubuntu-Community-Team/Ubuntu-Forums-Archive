---
title: "Software source Promlems!!!"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by tomma771 on 2011-02-21
Hi Guys!

I added "  *ppa:ubuntu-wine/ppa*" to update wine in the other software under software sources. After this the software source gave an error:

'E:Type 'nchpad.net/ubuntu-wine/ppa/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list'

I then removed the "http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu" from the list.
Clicked on closed and got the same error.

I went to terminal "gksudo gedit /etc/apt/sources.list"
Could not find any line with ubuntu-wine in it. The first three lines in the source.list is:

"# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution."

The problem persists even after I deleted everything in the source.list file except "deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main".

Update manager gives the same problem. I tried to reboot (just in case there where a memory or cache error), but got the same error.

Any ideas??

---

### Post by mikewhatever on 2011-02-21
Assuming everything else is correct, it should probably be **lauchpad.net/ubuntu-wine/ppa/ubunt**

---

### Post by tomma771 on 2011-02-21
Hi,
do you want me to replace 'http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu with 'http://ppa.launchpad.net/ubuntu-wine/ppa/ubunt'

---

### Post by tomma771 on 2011-02-21
See, I removed everything from the list...
The error message line never appeared in the source list 
so even after removing wine, the error message was the same.

I'm not sure what I need to do!

---

### Post by tomma771 on 2011-02-21
I changed the source.list to:

[I]# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick main universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick universe main #Added by software-properties
[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu)[/I]  [I]
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security universe main
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-security universe main #Added by software-properties
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates universe main
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) maverick-updates universe main #Added by software-properties[/I]

The error message is:

[I]E: Type 'http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu' is not known on line 7 in source list /etc/apt/sources.list
E: Type 'nchpad.net/ubuntu-wine/ppa/ubuntu' is not known on line 1 in  source list /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.[/I]

---

### Post by tomma771 on 2011-02-21
I changed the source.list to:

[I]deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu)  maverick main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu)  maverick main
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main[/I]

Error message is still:
*'E:Type 'nchpad.net/ubuntu-wine/ppa/ubuntu' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list'*

---

### Post by mikewhatever on 2011-02-21
Try removing the wine related lines, then run **sudo add-apt-repository ppa:ubuntu-wine/ppa** in a terminal window.

---

### Post by tomma771 on 2011-02-21
OK GREAT!!!

I found the problem.

[I]'E:Type 'nchpad.net/ubuntu-wine/ppa/ubuntu' is not known on line 1 in  source list /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list'

[/I]I went to [B]applications, accessories, terminal:
[/B][I]gksudo gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list

[/I]New window opened and I was able to edit the '*ubuntu-wine-ppa-maverick.list*'
I removed the *nchpad.net/ubuntu-wine/ppa/ubuntu' *and replaced it with [I]'http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu'

[/I]PROBLEM SOLVED

---

