---
title: "Why can't I not install the chromium browser ??"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by Spaarkplug on 2009-12-15
hi,

I know this sound like a noob question, but I tried everything? Synaptic, apt-cache search, i checked my /etc/apt/sources.list file for the right repos,..

Anyways, here, why don't you see for yourself.

mo@sciencemachine:~$ sudo apt-get install chromium-browser
[sudo] password for mo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package chromium-browser
mo@sciencemachine:~$ 

:(

---

### Post by User3k on 2009-12-15
Check this out.

[http://www.chromium.org/getting-involved/dev-channel](http://www.chromium.org/getting-involved/dev-channel)

Towards the middle you will see the linux ones.

---

### Post by lidex on 2009-12-15
To make it easy, go to [this page]("http://ubuntu-tweak.com/downloads") and follow directions to add repository for ubuntu-tweak. Install it and run. Go to "Applications" > "Third Party Sources" in left pane. Unlock and scroll in right pane to entry for Chromium and check that off. Reload. Now go to add/remove and select the chromium package. Apply.

Good luck BTW. Last I checked it was not ready for prime time.

---

