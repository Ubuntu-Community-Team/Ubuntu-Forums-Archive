---
title: "[x64] upgrade failed 11.04 x64 =&gt; 11.10 on new Dell Inspiron 14z"
date: 2011-11-22
forum: Installation &amp; Upgrades
---

### Post by dieash on 2011-11-22
Hello,
 

I'm trying to upgrade Ubuntu 11.04 (x64) on my new Dell Inspiron 14z (11.04 was pre-installed on the laptop). In Update Manager window I can see: "new Ubuntu 11.10 release is  available". But after pressing the button [Upgrade] the following dialog  with error will be displayed:
 

Authentication failed
Authenticating the upgrade failed. There may be a problem with the network or with the server.
 

 I believe, that's is NOT a problem with the server accessibility, because I can ping it and view content in the browser. In the tab "Other Software" there are 2 dell lines: "http://dell.archive.canonical.com/updates/ natty-dell public"


What's wrong and how I can fix it?
  Thank you!

---

### Post by zvacet on 2011-11-22
```
sudo apt-get update && sudo apt-get upgrade
```

Try again to upgrade from update manager and see if it work.

---

### Post by dieash on 2011-11-23
> **zvacet said:**
> ```
sudo apt-get update && sudo apt-get upgrade
```Try again to upgrade from update manager and see if it work.

Sorry, pal. It's totally useless for my case, because I has already upgrade all possible packages before make update of OS.

Here is my brute-force solution for the problem: 
[LIST=1]
[*]prepare CD or USB with 11.10 x64 installation
[*]reboot laptop, press F12 (boot menu) and choose appropriate menu item
[*]go through standard installation process (but choose upgrade 11.04 to 11.10 in the beginning)
[/LIST]
 After all I got 11.10 x64 on Inspiron 14z. At the first look, everything is all right (all devices work properly).


 But under 11.04 battery lifetime was approximately 6-7 hours (in  light usage-mode - web-serfing via wifi). Under 11.10 -- life-time  dramatically decreased to 3-4 hours. I don't know which kind of magic  has been used during preparation of 11.04-build in Dell, but I want the  same thing under 11.10 :) I am already wrote on Dell forum about this issue. May be I get answer from Dell.


* * *

BTW, I bought Inspiron 14z on the last week and it has preinstalled ubuntu 11.04 x64. Yesterday I upgrade it to 11.10 x64. But on [http://www.ubuntu.com/certification/make/Dell](http://www.ubuntu.com/certification/make/Dell) only x32-versions have been certified. How it's possible? (may be you know answer)

Thanks!

---

