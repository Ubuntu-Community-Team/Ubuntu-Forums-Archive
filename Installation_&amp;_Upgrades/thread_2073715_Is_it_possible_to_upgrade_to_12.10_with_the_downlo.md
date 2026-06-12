---
title: "Is it possible to upgrade to 12.10 with the downloaded iso file?"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by seventhsamurai on 2012-10-20
I downloaded the iso installation file for 12.10 from the website and attempted to install. However, the option to upgrade from the existing installation of 12.04.1 is disabled, and the only choice allowed is to erase the existing installation and install fresh.

Of course, I am aware that I can upgrade using the distribution upgrade tool from within 12.04.1, but my problem is that the files take forever to download despite me running it off a 12 mbps connection. I need to upgrade on 4 more systems and I'd hate to have to download and upgrade via the upgrade tool on each one.

Can anyone help? Is there anyway to just use the 800mb iso file that I have downloaded off ubuntu.com without having to wipe out all my files?

---

### Post by funicorn on 2012-10-20
No you can't. In the past one can do off line upgrade via ubuntu alternative CD. But there isn't one for Ubuntu 12.10.

---

### Post by commanderwil on 2012-10-21
Where can I get the iso file for a cd

---

### Post by Jedcurtis on 2012-10-21
> **commanderwil said:**
> Where can I get the iso file for a cd

You can't is the simple answer!  The .iso file when burned is over 800 mb, rendering CD burning useless.  You HAVE to burn it to a DVD or create a USB installer.

Jed

---

### Post by commanderwil on 2012-10-21
> **Jedcurtis said:**
> You can't is the simple answer!  The .iso file when burned is over 800 mb, rendering CD burning useless.  You HAVE to burn it to a DVD or create a USB installer.

Jed
I meant to say dvd sorry

---

### Post by Jedcurtis on 2012-10-21
> **commanderwil said:**
> I meant to say dvd sorry

No problem!  You can get the iso from the Ubuntu site.

Jed

---

### Post by commanderwil on 2012-10-21
> **Jedcurtis said:**
> No problem!  You can get the iso from the Ubuntu site.

Jed
yes but where on the website

---

### Post by mikodo on 2012-10-21
Download it from the site linked below and burn the .iso to a dvd. (Instructions on the site):

[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

Oops, you weren't the the OP.

---

### Post by commanderwil on 2012-10-21
dud haha thank you very much and thank you also jed

---

### Post by Cheesemill on 2012-10-22
> **Jedcurtis said:**
> You can't is the simple answer!  The .iso file when burned is over 800 mb, rendering CD burning useless.  You HAVE to burn it to a DVD or create a USB installer.

Jed
The 12.10 desktop image fits just fine on an 800MB CD.

---

### Post by seventhsamurai on 2012-10-22
Ok so while it is now concluded that the 800mb iso file cannot be used to upgrade an existing installation of 12.04 keeping all data intact, the pain can be eased a little if you are upgrading on multiple systems.

I ran the upgrade via the internal upgrade tool on 1 system. Once the system was fully upgraded to 12.10, I then ran aptoncd to create an iso file of downloaded packages.

Then I simply restored packages on system no. 2 using aptoncd, which copied most of these upgrade packages onto it. Then I ran the internal upgrade tool, which only asked to download about a 100 files vs the 2000+ files it would have to if you were upgrading from scratch.

---

### Post by kflorek on 2012-10-23
What I do for two systems is to work with the files in

/var/cache/apt/archives

The first system, using say apt, will cache the files into this directory until it has all required. I then copy those to some intermediate media. Then copy the files to the cache directory on the second system (as su of course.) apt  checks and uses files in this cache rather then dumbly re-downloading

 Something unknown deletes some of these files in later Ubuntus, after a day or so, so don't assume they will be there forever to copy.  I wish I knew what. Earlier Ubuntus kept the files permanently, so long as you set it to keep them in synaptic.

---

