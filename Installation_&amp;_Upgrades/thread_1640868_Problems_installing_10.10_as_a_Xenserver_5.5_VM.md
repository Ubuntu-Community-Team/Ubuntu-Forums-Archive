---
title: "Problems installing 10.10 as a Xenserver 5.5 VM"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by joshlindem on 2010-12-08
I'm attempting to install Ubuntu 10.10 as a VM on a Citrix Xenserver 5.5 environment.

1) What template should I use?  
I attempt to use the "other media" option and upon setting up the options and pointing to the ISO the VM will start and as soon as it starts the POST it just as quickly shuts down.

2) Is there a template I can go and download?  If yes, please point where and how do I integrate it into the Xencenter?

3) or perhaps there are step by step instructions out there someone can point me to?

I just don't get why it won't load the VM.

---

### Post by joshlindem on 2010-12-08
As I'm patiently (or possible impatiently) waiting for some response I was wondering....

If I install an older version (ie: 9.04) and then upgrade to 10.10 would that work?  Or would it just break again after 10.10 is installed?

---

### Post by joshlindem on 2010-12-10
Well you were all pretty useless in helping me  ;o)  (just kidding)

Apparently I'm the first to try something like this with the newest version.  When I first attempted this I downloaded the 10.10 (64bit) ISO.  I installed hte VM using the "other media" template.  I gave the VM 2 processors and about 2.5GB of ram.
As soon as the VM started it checked the CD (ISO) and just as quickly shut down the VM.  I couldn't get it to load the ISO.  And yes the ISO was just fine.
I read that there was possibly an issue with 10.10 and how it boots, or what it looks for when it boots.  Regardless I couldn't get it working.

I downloaded 10.4 LTS ISO (64bit) and used the same template and setup. I was able to load up 10.4 with no issues.  I then went into the System and changed the update feature so that it would update all versions, not just the LTS versions.  once I did this 10.10 would appear.

I upgraded, which took a while but it did do it.  Once I rebooted after the upgrade I did get a couple errors on screen during boot about how "modprobe: fatal: could not load a couple libraries".  I get about 3 of these. BUT... that said, it still continues the boot process and I can log in to Ubuntu without issue. Everything appears to be working at the moment.

---

### Post by joshlindem on 2010-12-10
If anyone does know how to modify the screen resolution that would be great.  Apparently I'm stuck at 800x600.  (ugh, that is so 1990's)

I'm thinking an option isn't visable that I need to turn on so that I can see the hardware and modify it, or trick it into thinking that my VM monitor has a larger resolution.

---

### Post by gblfxt on 2011-01-03
I tried installing 10.10, had the same issue.  I will try the 10.4 install and upgrade route.....

---

### Post by infecticide on 2011-05-20
I used this and it works great, I installed 10.04 and upgraded to 10.10 and it works fine.

Unfortunately you do need to pin grub-common and grub-pc where they are as Xenserver 5.6 is not compatible with the latest grub.

Create Ubuntu template:
[http://community.citrix.com/display/xs/Installing+Ubuntu+Server+10.04+%2832bit+and+64bit%29+LTS](http://community.citrix.com/display/xs/Installing+Ubuntu+Server+10.04+%2832bit+and+64bit%29+LTS)

Pin your grub packages using this:
[http://manpages.ubuntu.com/manpages/hardy/man1/dpkg-hold.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/dpkg-hold.1.html)

---

