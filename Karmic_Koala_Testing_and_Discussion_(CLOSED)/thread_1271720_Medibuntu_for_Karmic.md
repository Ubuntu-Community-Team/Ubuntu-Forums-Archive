---
title: "Medibuntu for Karmic?"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bwallum on 2009-09-21
Anybody know where I can get medibuntu for karmic?

---

### Post by drs305 on 2009-09-21
Run this command and it will put medibuntu in your karmic repository and import the correct key. You will find it listed in the Synaptic "Other Sources" tab.
```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update

```


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by achase79 on 2009-09-21
go to medibuntu.org

They do have a karmic repository

---

### Post by achase79 on 2009-09-21
follow the instructions for jaunty, but change the name "jaunty" to "karmic"

---

### Post by bwallum on 2009-09-21
I followed drs305 and I appear to have medibuntu now in my sources list. However I'm not able to play flash media. I recall having to install flash 64 bit in jaunty using adobe labs libflashplayer.so

Does anybody know if this is still needed in karmic? Can anybody refresh my memory as to which folder the libflashplayer.so file should be placed in?

---

### Post by Moop on 2009-09-21
The flashplayer.so file goes in /usr/lib/mozilla/plugins.

---

### Post by howefield on 2009-09-21
> **Moop said:**
> The flashplayer.so file goes in /usr/lib/mozilla/plugins.

Or maybe..

/home/user/.mozilla/plugins

Substitute "user" for your user name

---

### Post by bwallum on 2009-09-21
Interestingly I found it worked in /usr/lib/mozilla/plugins and also /usr/lib/firefox-addons/plugins...

Thanks for the steer!

---

### Post by Tibuda on 2009-09-22
> **bwallum said:**
> I followed drs305 and I appear to have medibuntu now in my sources list. However I'm not able to play flash media. I recall having to install flash 64 bit in jaunty using adobe labs libflashplayer.so

Does anybody know if this is still needed in karmic? Can anybody refresh my memory as to which folder the libflashplayer.so file should be placed in?

Medibuntu was never needed for Flash, which can be installed using ubuntu restricted extras. Medibuntu is required only for encrypted dvds (libdvdcss2) and windows media codecs (w32/64codecs).

---

### Post by bwallum on 2009-09-22
Another good learning/refresh point (I guess I should have known that!), thanks Daniel.

---

### Post by Slug71 on 2009-09-23
Added this repo and enabled the partner repo and it seems Acroread is MIA??

The fonts package is there however.

---

### Post by drs305 on 2009-09-23
Acrobat Reader (acroread) is no longer in the Medibuntu repositories. You can download it from the Adobe site:
[http://get.adobe.com/reader/otherversions/]("http://get.adobe.com/reader/otherversions/")

There is a deb version listed.

---

### Post by Slug71 on 2009-09-23
> **drs305 said:**
> Acrobat Reader (acroread) is no longer in the Medibuntu repositories. You can download it from the Adobe site:
[http://get.adobe.com/reader/otherversions/]("http://get.adobe.com/reader/otherversions/")

Yeh but shouldnd it be in the 'partner' repo?

---

### Post by Slug71 on 2009-09-24
Downloading the 32bit .deb and running

```
sudo dpkg -i --force-architecture AdbeRdr9.1.2-1_i386linux_enu.deb
```

in Terminal doesnt work either?

---

### Post by philinux on 2009-09-24
acroread appears to be missing from synaptic. acroread-fonts are there though under Origin>packages medibuntu non free although medibuntu no longer provides acroread.

---

