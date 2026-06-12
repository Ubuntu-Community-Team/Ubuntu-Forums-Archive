---
title: "Firefox can't open more than 2 windows"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by bromleyi on 2007-10-16
Hi

I am having a problem when I open more than 2 windows of Firefox

I can have multiple tabs in both windows, but as soon as I try and open a 3rd window the CPU usage it's 100% and I have to close down firefox to get control back.

I am using Ubuntu 7.10 with Firefox 2.0.0.6.

It worked fine in 7.04 but has happened only after updating.


Thanks

---

### Post by CptPicard on 2007-10-16
Just upgraded to Gutsy and I've got exactly the same problem. Ctrl-N and Firefox hangs with 100% CPU usage. :(

---

### Post by CptPicard on 2007-10-18
Fixed it by deleting my ~/.mozilla/firefox directory. You lose all your settings doing so, unfortunately.

---

### Post by bromleyi on 2007-10-18
Your right that did fix it.

But I did a little digging around with Add-ons.
After I installed the "Google Toolbar" the problem happened again. After uninstalling it all was OK again.

Nice pickup. Just need Google to fix the Toolbar now

---

### Post by bring on 2007-10-20
Same problem here, with google toolbar installed , on gutsy that results in firefox freezing when opening more than 2 windows. The same setup worked fine under feisty.

A bug report has been filed [(https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/135110)]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/135110") but the  general consensus seems to be that google toolbar is to blame for this, although i don't agree  with that, since in both feisty and gutsy i have been using the same version of firefox and toolbar.

---

### Post by reyfer on 2007-10-20
I have always been curious: if Firefox already comes with a Google search field, why do you need the Google toolbar? As I said, just curious.

---

### Post by bromleyi on 2007-10-20
More features.

I like the Highlighting and Translate.

---

### Post by reyfer on 2007-10-20
> **bromleyi said:**
> More features.

I like the Highlighting and Translate.

For translation I use Foxlingo, and it is great.

---

### Post by endolf on 2007-10-23
I've been having issues too on a fresh install of 7.10. Mine seem to have been resolved by downloading 2.0.0.8 from the firefox website and using that version. I do have the google toolbar, plus web developer, distrust, adblock plus, adbock Filterset.G Updater, flash and java plug-ins. I tried updating my firefox package from ubuntu to 2.0.0.8 when that was released, but that hung when trying to open a third window in exactly the same way. Gone back to a release direct for now.

Endolf

---

