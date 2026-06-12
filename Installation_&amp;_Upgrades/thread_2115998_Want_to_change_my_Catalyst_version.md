---
title: "Want to change my Catalyst version"
date: 2013-02-14
forum: Installation &amp; Upgrades
---

### Post by ignamatador150 on 2013-02-14
Hi, I use Steam daily and I wanted to try Team Fortress 2 on Ubuntu 12.10 64bit, so I tried running it and some problems came up, so I went to the AMD website and downloaded the latest beta catalyst. Now (with beta drivers) Team Fortress 2 runs, but I'm kind of skeptical about using beta drivers and TF2 runs with a fixed delay, so actually it's unplayable.
So the thing is: Am I right about being skeptical about daily functionality of this driver? May TF2 run better on non beta drivers?

I installed this drivers: amd-driver-installer-catalyst-13.2-beta3-linux-x86.x86_64.zip
My video card is: Ati Radeon HD 6870

And just for curiosity, in case someone would like to tell me, if I would like to uninstall this, how would I do? (respond this just if you have the time, I don't wish to make your day harder)
Thanks in advance :D

---

### Post by MAFoElffen on 2013-02-16
Get rid of all instances of AMD/ATI drivers?

In a terminal:
```

sudo apt-get autoclean
sudo apt-get clean
sudo sh /usr/share/ati/fglrx-uninstall.sh
sudo rm /usr/share/ati/fglrx-uninstall.sh

```
If this returns "no such file or directory" it's fine. Just means that that is not present, but we need to make sure it's gone.
Proceed.
```

dpkg -l fglrx

```
If anything is reported as installed then substitute "fglrx-xxxx" in the folowing code with the appropriae name(s).  You used to be able to do this with a global, but now you have to specify each package.
```

sudo apt-get remove --purge fglrx-xxxx

```
This will probably return a couple of warnings: 
> 
/usr/share/lib/fglrx and /usr/share/lib32/fglrx not empty. 

If so. then do:
```

sudo rm -rf /usr/share/lib/fglrx

```
and
```

sudo rm -rf /usr/share/lib32/fglrx

```
If should then be gone and clean...

---

### Post by Mark Phelps on 2013-02-17
> **ignamatador150 said:**
> ... So the thing is: Am I right about being skeptical about daily functionality of this driver? May TF2 run better on non beta drivers?

From my experience, most of the changes that AMD makes to their drivers during the betas are to address problems specific to individual games, so if the Release Notes mention the game you're trying to run, then installing that particular Beta would be a GOOD idea.  If they don't mention it, you can still look at the bug fixes to see if those address any problems you're having.

IF you're not having problems with existing drivers and the Release Notes don't indicate any fixes you need, installing a Beta will not accomplish anything useful to you.

---

