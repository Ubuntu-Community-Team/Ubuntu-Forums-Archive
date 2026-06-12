---
title: "Jaunty update + now firefox DIED!"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by person9 on 2010-02-08
Hi, 
I have Jaunty 9.04 and I was sitting online yesterday and the update manager came up. I let it do its thing as usual, but it seemed to have an issue with some firefox related package (having to do with branding?) and then the little flipping-out icon showed up in my tray saying that a package broke. I did some poking around but nothing too hardcore since I don't really know what I'm doing, and I tried restarting a few times to see if that would help. It did not, and the firefox launcher turned into a missing puzzle brick and clicking it causes a small window to come up with the following message:

> XML Parsing Error: undefined entity
Location: chrome://browser/content/browser.xul
Line Number 31, Column 1:<window id="main-window"
^

So I might have tried to uninstall firefox from synaptic or something, but this just created more errors and I dont think it worked properly anyway.

inside Synaptic, there is one listed as a "broken" package in the broken filter. It is something to do with Firefox Branding AMD64 and all that goodness. If you need to know any more information about any of these things to help me out, just ask and i can find it all in more exact terms.

Now my whole system is bothered and I'm unhappily using Opera! Any help would be appreciated. I did nothing to bring this on other than let the Upgrade Manager do its thing. Thanks in advance!! :)

** i could provide screenshots if anyone needs this as well!

---

### Post by snakeman21 on 2010-02-08
First of all, don't put up with Opera.  Install google chrome until you get the problem fixed.  Unfortunately, that's all I can offer... I don't know how to fix it.  My suggestion?  Install Karmic...It absolutely rocks!

---

### Post by person9 on 2010-02-08
Haha thanks for the advice, Chrome wouldn't work because of the amd64 thing, and I would LOOOOOVE to upgrade but I can't because I have a wubi install! Ughhhh
Thank you for your help though! I'll give Chrome a try!

---

### Post by person9 on 2010-02-08
Ahhh Chrome wont install BECAUSE of the "missing dependencies" having to do with the broken firefox thing!

---

### Post by ajgreeny on 2010-02-08
I assume you have tried the **synaptic->Edit->Fix Broken Packages** route, rather than just uninstalling, but if not try that first.

---

### Post by person9 on 2010-02-08
I had not done that, thanks! I tried it and it quickly  just blinked and said "Fixed broken dependencies" down on the status bar. Then i Checked off the box that had the "broken" firefox thing in it, and did "mark for reinstallation". However it just came up with the same error: 

> E: /var/cache/apt/archives/firefox-branding_3.6+nobinonly-0ubuntu1~mfs~jaunty1_amd64.deb: trying to overwrite `/usr/share/applications/firefox.desktop', which is also in package firefox-3.0-branding

:( :( Thanks for that advice though I forgot about that option!

---

### Post by ajgreeny on 2010-02-08
Delete that firefox-branding package from /var/cache/apt/archives and try again.  It may be corrupt in downloading.

---

### Post by person9 on 2010-02-08
Grrr. It still doesnt like me. I deleted that firefox branding package, and also one that was the one mentioned on the broken package thing, but it still told me this:
> E: /var/cache/apt/archives/firefox-branding_3.6+nobinonly-0ubuntu1~mfs~jaunty1_amd64.deb: trying to overwrite `/usr/share/applications/firefox.desktop', which is also in package firefox-3.0-branding

:( :(

It also randomly terminated my Gnome-Do docky toolbar at the bottom for no reason :(

I also went and deleted that link to "Firefox.desktop" or whatever it was inside /usr/share/applications/, and tried the reinstallation again, and it said:

> E: /var/cache/apt/archives/firefox-branding_3.6+nobinonly-0ubuntu1~mfs~jaunty1_amd64.deb: trying to overwrite `/usr/share/applications/firefox.desktop', which is also in package firefox-3.0-branding

I am highly confused :/

* My computer will be hitting the floor soon.*

---

### Post by person9 on 2010-02-08
Wow, the issues have taken over my entire computing experience. Now in add-remove programs it says:
> This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

All I ever did was click "okay" on my everyday updates and this is what has happened. I am not a happy camper and I would love to trash this whole Jaunty thing. But I have too much stuff installed and everything set up just right, and with Wubi I can't do the upgrade to Karmic.....

Thanks everyone though. Any other ideas?

---

