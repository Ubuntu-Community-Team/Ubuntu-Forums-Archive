---
title: "Clean install of ubuntu 20.04.20 failed."
date: 2024-07-17
forum: Installation &amp; Upgrades
---

### Post by beagle44 on 2024-07-17
Usually when I have a boot problem. I just reinstall Ubuntu. during this install, I was asked if I wanted to. Install Ubuntu beside the one, already installed. I should have said yes. But I said no Because I thought I had a 256GB HD. But later I found out, it's a 1 terabyte HD. The install failed because of grub problems. I tried installing it a couple of more times. But the installer now says " you need at least 8.6 GB disk space to install Ubuntu. your computer only has 0.0.B". whatever that mean. The grub problem I had, was the installer said it couldn't install the boot loader, and I had to do it manually.

---

### Post by TheFu on 2024-07-17
Please run a **boot-info** report to get help and post the URL that it provide back here for boot-experts to review.  Facts are require to help. There are far to many possible issues for guessing.

The normal way to get the report would be to use an Ubuntu ISO boot, go into "Try Ubuntu", install the **boot-repair** package, then run it and in the bottom, center, of the page, press the "Get Info" button.  Do not let it repair the system at this point. That can cause problems in certain situations.

And before you do anything, be certain you have a know-you-can-restore backup for all the stuff you don't want to lose.

---

