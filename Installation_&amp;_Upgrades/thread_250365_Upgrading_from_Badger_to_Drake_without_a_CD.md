---
title: "Upgrading from Badger to Drake without a CD"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by vocaro on 2006-09-04
After using Fedora / Red Hat for many years, I have decided to switch to Ubuntu. I wanted to install Drake, but I had to install Badger instead because I don't have a DVD drive, and the CD ISO for Drake is 700MB+, which is too big for my 650MB CD-Rs. The Badger installation was successful; I now wish to upgrade to Drake.

There are [instructions](https://help.ubuntu.com/community/DapperUpgrades#head-792e320b3976df97f0d8b47047e1bcc955fd2569) for doing this, but they don't seem to be correct. They say I can do an easy upgrade from Badger to Drake as long as I'm using Update Manager version 0.42.2ubuntu12~breezy1 or higher. However, according to Synaptic Package Manager, the version installed with Badger is 0.3.1+svn20050404.15, and although I did Edit > Reload Package Information, SPM says that this is the latest available version, as well.

How can I install a newer version of Update Manager so that I can upgrade to Drake? Thanks!

---

### Post by aysiu on 2006-09-04
[http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

---

### Post by confused57 on 2006-09-04
I used aysiu's method to dist-upgrade from Breezy to Dapper, which is working great.  With a fresh install of Breezy, it should be much easier...my Breezy was installed in January & still didn't have any problems upgrading.

---

### Post by vocaro on 2006-09-04
> **aysiu said:**
> [http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

Thanks, but those instructions are slightly incorrect. The problem is that after Breezy is installed, all of the lines in sources.list (except the one for the CD-ROM) are commented out. As a result, none of the calls to aptitude have any effect, even after replacing every occurrence of "breezy" with "dapper".

So, in addition to the search/replace, I decided to *un*comment the first two lines:

[INDENT]deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
[/INDENT]

I then proceeded with:

[INDENT]sudo aptitude update
sudo aptitude dist-upgrade
[/INDENT]

All of the packages downloaded okay, but as they were being installed, my computer locked up. Hard. I mean, the mouse cursor wouldn't even move; the thing was frozen solid and I had to hard reboot.

After rebooting, I repeated the aptitude steps, but my computer locked up *again* during package installation.

Next, I did a clean install of Breezy, wiping the hard drive completely, and repeated the steps again. Same lock up!

Finally, I tried following [these instructions](https://help.ubuntu.com/community/DapperUpgrades#head-0171d3953a2ea19e9b4228bcd5cde3ecfb67f7af) instead, using the sources.list they provide, but my computer froze once more.

I don't understand. I've been running Fedora on this machine for months, and it never locked up. I also don't think this is simply a problem with apt because I'm able to install packages (such as openssh-server) using Synaptic without any problems. It's only when I attempt the Dapper upgrade that I get a lockup.

So I'm still stuck on Breezy. Is there no other way to upgrade to Dapper?

<rant>By the way, why did they have to make Dapper's install CD so darn big? If they had just made it about 60MB smaller, I could burn it and install Dapper directly, problem solved...</rant>

---

### Post by confused57 on 2006-09-04
You could try doing a server install with the Breezy install cd, if your internet connection is automatically configured after install:
comment out the cd-rom, and uncomment anything that looks like a url(repositories) using:
```
sudo nano /etc/apt/sources.list
```
ctrl+x,y,enter.

```
sudo aptitude update
sudo aptitude upgrade
```

then do the dist-upgrade of the server install:
change all instances of breezy to dapper with
```
sudo nano etc/apt/sources.list
```
to save...ctrl+x, y, enter.

```
sudo aptitude update
sudo aptitude dist-upgrade
```

After the dist-upgrade has completed, then install ubuntu-desktop:
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

I've successfully done this before with no problems...goes without saying it'll depend on whether your internet connection is configured.  It's an option, if you want to try it...you'll definitely need a fast internet connection.

---

### Post by vocaro on 2006-09-05
I finally decided that it was no longer worth the trouble upgrading from Breezy to Dapper. (I had already wasted three days of my spare time trying.) Instead, I broke down and bought a pack of 700MB CD-Rs just so I could burn a Dapper install disc. (650MB CD-RWs are my usual media of choice.)

I booted with the Dapper install disc and began a default installation. When it was about halfway through copying the files, guess what happened: Another lock up!

After some reflection, I thought this might be a hard drive issue, given that the lock ups only occurred during file access. As it happens, the computer has another hard drive on the secondary IDE controller, so I decided to install Dapper to that drive instead. It worked!

So evidently there is a problem either in my primary IDE controller or the hard drive attached to it.

Thanks to all for your responses!

---

