---
title: "Upgrading Ubuntu 12.04"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by Chris62 on 2012-10-18
Hi,

I read somewhere (or thought I did) that it is now possible to upgrade Ubuntu (from versions 10 onwards) by using the install CD of the version that one wants to upgrade to. Is this true? and if so how does one go about it?

I have found that doing it over the internet sometimes leaves me with an unbootable machine, and I would prefer not to do it that way if possible

I know that ideally one should do a clean install, but for various reasons I don't want to do that this time

---

### Post by mcellius on 2012-10-18
> **Chris62 said:**
> Hi,

I read somewhere (or thought I did) that it is now possible to upgrade Ubuntu (from versions 10 onwards) by using the install CD of the version that one wants to upgrade to. Is this true? and if so how does one go about it?

I have found that doing it over the internet sometimes leaves me with an unbootable machine, and I would prefer not to do it that way if possible

I know that ideally one should do a clean install, but for various reasons I don't want to do that this time

Once you have the install CD (or DVD this time, I think), just boot into it and choose "Install Ubuntu."  After choosing the language and verifying that your computer is connected to the Internet and power, you'll get to the page that allows you to choose what to do.  One of the options should be to upgrade your existing installation to the new one.  Choose that, follow the prompts (the usual installation screens), wait awhile (about twenty minutes for me), follow any remaining instructions, including a reboot, and you're there.  Easy as could be!

---

### Post by grahammechanical on 2012-10-18
You might find that with Ubuntu loaded you can also put the Live DVD into the drive. It will be detected and you might get an option to upgrade from there.

Regards.

---

### Post by Chris62 on 2012-10-18
Thank you both for your suggestions. Will tell you how I get on.

---

### Post by Chris62 on 2012-10-22
Hi,

In case anyone is interested, the install CD does not offer the option to upgrade from Ubuntu 12.04 to 12.10. Perhaps the DVD does.

Meanwhile, having upgraded over the internet I find that I have the following installed:

linux-image-3.5.0-17-generic
linux-image-extra-3.5.0-17-generic
linux-image-generic

Could someone explain what 'linux-image-extra' is, please? Also, the first two above are versions 3.5.0-17.28, while the third one is version 3.5.0.17.19. Is it OK to remove the third one so as not to clutter the hard disc with unused software?

---

### Post by 2F4U on 2012-10-22
The package linux-image-generic is a metapackage and most likely contains other important packages:

[http://packages.ubuntu.com/search?keywords=linux-image-generic](http://packages.ubuntu.com/search?keywords=linux-image-generic)

So, I wouldn't remove it until you know that this doesn't cause problems such as leaving you with an unbootable system.

---

### Post by seventhsamurai on 2012-10-22
The 800 mb iso file for 12.10 unfortunately does not allow you to upgrade from 12.04 while keeping all your old data intact. It demands a clean, fresh install.

The best way to upgrade is through the internal distribution upgrade tool in 12.04.1. Yes, it's a pain as it takes forever to download the files. Took me 4 hours despite having a 12 mbps connection. But my upgrade was pretty clean and flawless. Had absolutely no issues, all my data and settings remained intact.

If you need to upgrade on multiple systems, I suggest upgrading on 1 first, then use aptoncd to create an iso file of all the downloaded packages, restore using the same program on the other systems, and then run the distribution upgrade tool. While this doesn't necessarily copy all the necessary files, it copies over 90% of them, so you really have to only download about 100-150 files on each machine, as opposed to download the 2000+ if you were downloading from scratch.

---

### Post by buckyaustin on 2012-10-22
Back up all your data before procceding. Because alot of the common problems with Ubuntu occur during upgrades. So please back up before you procced.

Then try to do sudo apt-get update, then sudo apt-get upgrade, then sudo apt-get dist-upgrade. That should be you completly up to date.

---

