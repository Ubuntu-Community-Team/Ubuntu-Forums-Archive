---
title: "Encrypted HDD - help!"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by Nazareth on 2010-05-02
Hi, 

I tried upgrading from Karmic to Lucid on Friday via Update Manager, but stupidly didn't shut everything down and carried on browsing with Chrome, using Evolution etc.

As a result, the installation appeared to get stuck at 26 minutes remaining, so I (even more stupidly) decided to shut down the computer and restart it.

Predictably, Ubuntu broke! (Can you tell I'm a newbie yet?)

Now, upon booting, the laptop got stuck at 'checking battery status' so I decided to burn a Lucid CD from another PC and use it to install Lucid on my laptop, on a new partition.

Now, although I encrypted my HDD with Karmic, I can currently see the old partition, yet cannot access my information - I get a Access-Your-Private-Data.desktop link that's apparently not trusted (error message: "The application launcher "Access-Your-Private-Data.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe." )

The command inside that link (/usr/bin/ecryptfs-mount-private) also doesn't seem to work in Terminal.

I have the password for HDD manual recovery, I'm just not sure how to use it!

My old partition is in /dev/sda5 according to Disk Utility, but is mounted in /media/d4f00af0-215e-4d5e-9baf-7e49528291c1

I'm not sure how to access my old data, I just want it so I can back up the data, format my hard drive and do a clean Lucid install.

I'm not sure if the problem is that the old partition is encrypted or whether it's just that the system sees that I'm a different user and thus protects the data from apparently prying eyes.

All help appreciated!

---

