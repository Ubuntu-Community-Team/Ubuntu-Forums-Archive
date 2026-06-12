---
title: "Ubuntu on Laptop?"
date: 2007-12-25
forum: Installation &amp; Upgrades
---

### Post by ambiguousama on 2007-12-25
Hello, I usually use freespire, but I've heard good things about ubuntu, and the freespire community can be a bit empty at times. Anyhow, I recently got a new dell laptop that came with vista, and immediately went to install a linux distro on it. I've tried both freespire and ubuntu multiple times with no luck. 

The installer stops working after a pop up saying that my screen/graphics card could not be detected correctly and giving me the option to continue in low graphics mode. I do so, after which I am ushered to a black screen where the battery state is checked and local boot scripts are run (both of which get oks) and a little dot flashes.

Someone please help me, as I am not interested in running vista on my laptop.

---

### Post by taurus on 2007-12-25
One option is to download and use the alternate CD to install Gutsy on your new Dell laptop.

---

### Post by tedk89 on 2007-12-25
I had the same problem, but I used the alternate cd after the live cd failed and that got me to load the OS and than after I got the internet up, loaded the restricted drivers for my brand new video card.

---

### Post by ambiguousama on 2007-12-25
I'm sorry, I've only worked with live cd before, so I hope I don't sound too newbish when I ask what it is that you two say I'm supposed to be installing otherwise?

---

### Post by taurus on 2007-12-25
```

[SIZE="4"][COLOR="Blue"]Alternate install CD[/COLOR][/SIZE]

The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * creating pre-configured OEM systems;
    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installs on systems with less than about 320MB of RAM (although note that low-memory systems may not be able to run a full desktop environment reasonably). 

In the event that you encounter a bug using the alternate installer, please file a bug on the debian-installer package.

There are two images available, each for a different type of computer:

```

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/7.10/ubuntu-7.10-alternate-i386.iso](http://www.gtlib.gatech.edu/pub/ubuntu-releases/7.10/ubuntu-7.10-alternate-i386.iso)

---

### Post by ambiguousama on 2007-12-25
Ah, thank you. It will take me a while, as I'm running short on cds and am stuck with a cd that can only write at 4x speed, so would you mind giving me a brief explanation of what to do once I install the cd? I can figure out the details, but just a basic idea of how this cd is different from the one I had previously would be great.

---

### Post by taurus on 2007-12-25
Basically, it will boot directly from the CD and you can install it right away without waiting for Gnome window manager to come up first.  However, it's a text based installer but should be real easy to follow.  Even though it's an alternate CD, you will get the exact same system once it's installed as you would get from the LiveCD--desktop CD.  

And by the way, you should burn it at 4x.

---

### Post by xeth_delta on 2007-12-25
> **ambiguousama said:**
> Ah, thank you. It will take me a while, as I'm running short on cds and am stuck with a cd that can only write at 4x speed, so would you mind giving me a brief explanation of what to do once I install the cd? I can figure out the details, but just a basic idea of how this cd is different from the one I had previously would be great.

It is actually better to write important data, like the OS installation CD, at lower speeds. SO, 4x will be just fine. I think you will be able to figure it out, if not, just ask, we'll be glad to help.

Xeth

---

### Post by maleficent on 2007-12-25
My new system has an nVidia 7050 onboard, which the nv drivers the livecd selects for it don't support. You should be able to get the livecd to start xorg using the vesa drivers though, although I installed in text mode anyway, as I wanted a software raid setup (which the livecd installer doesn't handle).

---

### Post by ambiguousama on 2007-12-25
Thank you for the help everyone, I have ubuntu up now, but tedk89 mentioned needing to do something else after the installation? I've installed the cd taurus pointed me to, and I just wanted to make sure there wasn't anything I was missing.

---

### Post by Pumalite on 2007-12-25
You just have to configure it to your taste now.

---

### Post by ambiguousama on 2007-12-25
Alright, then thank you for the help on this. I have to say that I like the ubuntu community much more than that of freespire, and on Christams day no less. Really, thank you so much to everyone who helped.

---

### Post by Pumalite on 2007-12-25
Here ia a Christmas present for you:
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

