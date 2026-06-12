---
title: "Unable to upgrade from 10.04 to 12.04"
date: 2013-06-21
forum: Installation &amp; Upgrades
---

### Post by Gav_UK on 2013-06-21
I'm having trouble upgrading from 10.04 to 12.04

Running do-release-upgrade comes back with:

```
If none of this applies, then please report this bug using the 
command 'ubuntu-bug update-manager' in a terminal. 


Restoring original system state

Aborting
```


The main_pre_req log file is here: [http://pastebin.com/CavXQKMr](http://pastebin.com/CavXQKMr)

Any ideas?

---

### Post by grahammechanical on 2013-06-21
It said more than that. The bits that you do not quote might be more useful to us non-developer types who are here to help. We do not write the scripts that do the upgrade. It is all a bit magical to us. But those error messages we might have seen before. and we might be able to guess what could fix it.

I can offer you this

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS)

And I suggest that you take 10.04 back to its default state when it was first installed and do that as much as possible. The upgrade process cannot take into account any modifications we have made to the desktop. I also suggest that you consider doing a fresh install.

Regards.

---

### Post by Gav_UK on 2013-06-22
Thanks for your reply.

I managed to crack the case by just manually removing package-manager-kde (i.e. sudo apt-get remove package-manager-kde) since that's what it kept moaning about. I then installed the update-manager mentioned in your wiki link and upgraded using that.

---

