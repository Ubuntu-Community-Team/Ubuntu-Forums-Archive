---
title: "error when updating other sources in software sources"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by gtpike07 on 2010-03-05
1.) I made a few updates that I found a website my friend sent me: [http://blog.thesilentnumber.me/2009/09/top-things-to-do-after-installing.html](http://blog.thesilentnumber.me/2009/09/top-things-to-do-after-installing.html)

however, when I would go to enter the APT line in the other sources in the software sources windows then close and reload it I would get the following error message:

  	 	 	 	 	 	  GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE Failed to fetch [http://archive.getdeb.net/ubuntu/dists/karmic-getdeb/games/binary-i386/Packages.gz](http://archive.getdeb.net/ubuntu/dists/karmic-getdeb/games/binary-i386/Packages.gz)  404  Not Found 
 

 Some index files failed to download, they have been ignored, or old ones used instead.
 
I also attached a screen shot of the error message window. 

2.) I don't know if i should post another issue I had, but when i try to run GNUnet it says that Daemon is not running. I'm not sure what that is all about.

My main issue is the first one. Please let me know if you need any more info.

Thanks,
Greg

---

### Post by lidex on 2010-03-05
Run this command in a terminal (Applications>Accessories>Terminal) and post the file contents back here please:
```
gedit /etc/apt/sources.list
```

---

### Post by gtpike07 on 2010-03-07
Here are my results: (I'm assuming you just wanted me to copy and paste all of it)

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mira.sunsite.utk.edu/ubuntu/](http://mira.sunsite.utk.edu/ubuntu/) karmic main restricted
deb-src [http://mira.sunsite.utk.edu/ubuntu/](http://mira.sunsite.utk.edu/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mira.sunsite.utk.edu/ubuntu/](http://mira.sunsite.utk.edu/ubuntu/) karmic-updates main restricted
deb-src [http://mira.sunsite.utk.edu/ubuntu/](http://mira.sunsite.utk.edu/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mira.sunsite.utk.edu/ubuntu/](http://mira.sunsite.utk.edu/ubuntu/) karmic universe
deb-src [http://mira.sunsite.utk.edu/ubuntu/](http://mira.sunsite.utk.edu/ubuntu/) karmic universe
deb [http://mira.sunsite.utk.edu/ubuntu/](http://mira.sunsite.utk.edu/ubuntu/) karmic-updates universe
deb-src [http://mira.sunsite.utk.edu/ubuntu/](http://mira.sunsite.utk.edu/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mira.sunsite.utk.edu/ubuntu/](http://mira.sunsite.utk.edu/ubuntu/) karmic multiverse
deb-src [http://mira.sunsite.utk.edu/ubuntu/](http://mira.sunsite.utk.edu/ubuntu/) karmic multiverse
deb [http://mira.sunsite.utk.edu/ubuntu/](http://mira.sunsite.utk.edu/ubuntu/) karmic-updates multiverse
deb-src [http://mira.sunsite.utk.edu/ubuntu/](http://mira.sunsite.utk.edu/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://mira.sunsite.utk.edu/ubuntu/](http://mira.sunsite.utk.edu/ubuntu/) karmic-security main restricted
deb-src [http://mira.sunsite.utk.edu/ubuntu/](http://mira.sunsite.utk.edu/ubuntu/) karmic-security main restricted
deb [http://mira.sunsite.utk.edu/ubuntu/](http://mira.sunsite.utk.edu/ubuntu/) karmic-security universe
deb-src [http://mira.sunsite.utk.edu/ubuntu/](http://mira.sunsite.utk.edu/ubuntu/) karmic-security universe
deb [http://mira.sunsite.utk.edu/ubuntu/](http://mira.sunsite.utk.edu/ubuntu/) karmic-security multiverse
deb-src [http://mira.sunsite.utk.edu/ubuntu/](http://mira.sunsite.utk.edu/ubuntu/) karmic-security multiverse
deb [http://ppa.launchpad.net/rvm/mplayer/ubuntu](http://ppa.launchpad.net/rvm/mplayer/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/rvm/mplayer/ubuntu](http://ppa.launchpad.net/rvm/mplayer/ubuntu) karmic main
deb [http://download.opensuse.org/repositories/home:/some-guy:/screenlets/xUbuntu_9.04/](http://download.opensuse.org/repositories/home:/some-guy:/screenlets/xUbuntu_9.04/) ./
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) karmic/
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb games

---

### Post by gtpike07 on 2010-03-07
I had the same error when I tried to update my multimedia in order to get ninjavideo to work properly:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE

I am pretty sure it's the same issue. Just figured I post it incase

---

### Post by wojox on 2010-03-07
You need to add the key:

```

gpg --keyserver subkeys.pgp.net --recv 6E871C4A881574DE
gpg --export --armor 6E871C4A881574DE | sudo apt-key add -

```

---

### Post by gtpike07 on 2010-03-07
i'm sorry i am still trying to understand ubuntu better... where do i add them?

---

### Post by lidex on 2010-03-07
> **gtpike07 said:**
> i'm sorry i am still trying to understand ubuntu better... where do i add them?

In a terminal. Look in your Applications menu: "Accessories>Terminal". Copy and paste one line at a time into the terminal and press enter. Enter your user password when prompted. As far as the 404 error, getdeb has been down so you just need to wait for it to come back - if it ever does. Did you just recently add the Mplayer PPA?

Edit: BTW, I'd remove or edit that opensuse repo - looks like it's for jaunty.

---

### Post by gtpike07 on 2010-03-07
thank you for your help. it appears that the issue is fixed. i re-ran the multimedia update and it operated correctly. thanks again. it is greatly appreciated:D

---

### Post by Coinneach on 2010-03-11
> **wojox said:**
> You need to add the key:

```

gpg --keyserver subkeys.pgp.net --recv 6E871C4A881574DE
gpg --export --armor 6E871C4A881574DE | sudo apt-key add -

```


thanks  . help me get rid of problem
Cheers!

---

