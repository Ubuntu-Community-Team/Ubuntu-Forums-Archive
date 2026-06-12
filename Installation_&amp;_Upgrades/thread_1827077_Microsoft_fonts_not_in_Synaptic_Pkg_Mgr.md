---
title: "Microsoft fonts not in Synaptic Pkg Mgr"
date: 2011-08-17
forum: Installation &amp; Upgrades
---

### Post by WaltL on 2011-08-17
I've read a number of posts (e.g.[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts) ) that state that the Microsoft fonts, formerly **msttcorefonts**, but now (supposedly) called** ttf-mscorefonts-installe**r should be available in Synaptic Package Manager. 

Neither is present in mine- I am running Lucid Lynx 10.04 and I have both font multiverse and universe enabled; althoguh, the wiki link says I should see hundreds, but I only see about 30 total in all 3 font repositories.

So I then tried apt-get tff-mscorefonts-installer and I got the following error:
E: Invalid operation ttf-mscorefonts-installer 

What gives? Is this package no longer available?  Should I be looking in some repository other than Font?

---

### Post by howefield on 2011-08-17
It should be in multiverse., download from here and install ?

[http://packages.ubuntu.com/lucid/ttf-mscorefonts-installer](http://packages.ubuntu.com/lucid/ttf-mscorefonts-installer)

---

### Post by WaltL on 2011-08-17
> **howefield said:**
> It should be in multiverse., download from here and install ?

[http://packages.ubuntu.com/lucid/ttf-mscorefonts-installer](http://packages.ubuntu.com/lucid/ttf-mscorefonts-installer)

Thanks!  That worked; although, I did get a message saying there was a later version and I was strongly advised to install the version from the "software channel" which is the same thing as a repository, right?  Anyway, I got the same message from files downloaded from two different servers (east coast and west coast) on the list of download sites given for that package.

I still would like to know why I can't see this in Synaptic.  As far as I can tell, in the Synaptic settings, if igo to software sources, Ubuntu software and check/enable universe and multiverse (which they have been all along), isn't this all I should need to do to, theoretically, be able to see this and perhaps other packages that may also be missing?  Or, do I need to enable universe/multiverse in some other fashion specific for the Font repositories?  

Not that big a deal, I just want to understand why my Synaptic doesn't show me what everything I've read says it should.

---

### Post by oldos2er on 2011-08-17
> **WaltL said:**
> So I then tried apt-get tff-mscorefonts-installer and I got the following error:
E: Invalid operation ttf-mscorefonts-installer 

What gives? Is this package no longer available?  Should I be looking in some repository other than Font?

You left out "install": ```
sudo apt-get install ttf-mscorefonts-installer
``` That's what "E: Invalid operation ttf-mscorefonts-installer" is telling you.

Also, in Synaptic, use the regular search function; the 'Quick filter' doesn't always work very well.

---

### Post by WaltL on 2011-08-18
> **oldos2er said:**
> You left out "install"

Dohhhh!

> Also, in Synaptic, use the regular search function; the 'Quick filter' doesn't always work very well.Thank you, this does make a difference... a lot more there with the regular search.

---

