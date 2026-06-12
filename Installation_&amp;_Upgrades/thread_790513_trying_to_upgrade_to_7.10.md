---
title: "trying to upgrade to 7.10"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by vizitorq on 2008-05-11
```

Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-amd64/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-amd64/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-amd64/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-amd64/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-amd64/Packages.gz) 404 Not Found
Failed to fetch [http://www.debian-multimedia.org/dists/sarge/main/binary-amd64/Packages.gz](http://www.debian-multimedia.org/dists/sarge/main/binary-amd64/Packages.gz) 404 Not Found

```

what's the deal? i'm trying to do it through my update installer...

```

http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-amd64/Packages.gz: 404 Not Found
http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-amd64/Packages.gz: 404 Not Found
http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-amd64/Packages.gz: 404 Not Found
http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-amd64/Packages.gz: 404 Not Found
http://www.debian-multimedia.org/dists/sarge/main/binary-amd64/Packages.gz: 404 Not Found

```

an error occured
```

W: GPG error: http://www.debian-multimedia.org etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: http://www.debian-multimedia.org sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: http://www.debian-multimedia.org experimental Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907


```

also, i'd like to know if this upgrade will effect anything that i have on my computer at the moment. will programs stop running? will i lose any data?

what seems to be the problem here?

---

### Post by louieb on 2008-05-11
Upgrade from what? hoary?
Checked a couple of the url's they aren't there.
  
Not enough information. Looks like your going where no man has gone before.  
Believe with the mix of 3rd party and Debian repositories that a successful upgrade to Ubuntu 7.10 isn't going to happen.       

I'd sure want a full system backup before I tired.   
Good Luck.

---

### Post by vizitorq on 2008-05-11
i'm upgrading from feisty fawn. so how am i supposed to upgrade? how do i do a full system backup?

---

### Post by louieb on 2008-05-11
I leaned the hard way to use **partimage** available on the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") to back up my install before trying to upgrade. The psychocats link has a how to.

I'd cleanup file /etc/apt/sources.list list first.  comment out all the non Ubuntu repositories.  Then try the upgrade again. 

Be aware that software you installed from those 3rd party repositories may get removed in the process.  The configuration file probably won't be removed. So you may wind up installing some programs  again.  

Heres the community doc on the subject: [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

---

