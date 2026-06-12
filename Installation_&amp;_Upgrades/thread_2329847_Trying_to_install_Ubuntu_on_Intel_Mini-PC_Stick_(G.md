---
title: "Trying to install Ubuntu on Intel Mini-PC Stick (Gole)"
date: 2016-07-05
forum: Installation &amp; Upgrades
---

### Post by mgroves on 2016-07-05
I purchased a Gole Intel "stick" PC (this one: [https://www.amazon.com/gp/product/B01EWNOVX2/](https://www.amazon.com/gp/product/B01EWNOVX2/))

It appears to be a 64-bit CPU, but it comes installed with Windows 10 32-bit edition. I would like to put a 64-bit OS on there (like Ubuntu Linux).

The problem is that I can't seem to boot from a USB stick. I've tried myriad different things after googling (Rufus, Universal USB Installer, even wubi), fiddling with a bunch of BIOS settings and nothing seems to work.

Does anyone have any suggestions for what else I can try? Is there any method to install Ubuntu 12 or 14 that I can use without a bootable USB drive? I will try anything so long as it doesn't brick the stick; I don't need dual boot or anything like that.

---

### Post by X-RED_Tech on 2016-07-05
No, there's no method to install old releases and perhaps that's your problem.
Use 16.04 64-bit. It should boot and install. It may or may not have a problem with the 32-bit UEFI + 64-bit CPU. Try it and post back if you still have problems.
WUBI is obsolete, not supported since a long time ago and wouldn't work in Windows 8.x/10 anyway.

---

### Post by mgroves on 2016-07-05
I've tried ubuntu 16 as well, no dice.

> [COLOR=#000000]It may or may not have a problem with the 32-bit UEFI + 64-bit CPU[/COLOR]

If this is the case, what can I do to address that?

---

### Post by X-RED_Tech on 2016-07-05
> **mgroves said:**
> I've tried ubuntu 16 as well, no dice.



If this is the case, what can I do to address that?


Call @oldfred , a forum mod who has an impressive database of installation instructions and special tweaks required.
Do not keep your hopes high though. Your CPU is NOT Linux friendly and comes with a broken UEFI. I know some people tried, most failed and the very few that succeeded couldn't make most of the hardware work (WiFi, audio, etc.).

I wouldn't waste even a minute with such machine.

---

### Post by mgroves on 2016-07-05
> **X-RED_Tech said:**
> I wouldn't waste even a minute with such machine.

Could you recommend a similar machine in size/cost?

---

### Post by sudodus on 2016-07-05
My experience is that Intel's own corresponding computers work better. I have an [Intel NUC](https://www-ssl.intel.com/content/www/us/en/nuc/nuc-kit-nuc6i3syh.html), that boots better with linux than most computers, that I have tried.

At [www.intel.com/buy/us/en/catalog/desktop/computesticks](www.intel.com/buy/us/en/catalog/desktop/computesticks) there are even computers that are delivered with linux, and I think you can find reselling companies with lower prices.

---

