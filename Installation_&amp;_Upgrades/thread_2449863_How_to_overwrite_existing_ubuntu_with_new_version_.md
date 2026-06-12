---
title: "How to overwrite existing ubuntu with new version in dual boot"
date: 2020-09-03
forum: Installation &amp; Upgrades
---

### Post by ahti-sc on 2020-09-03
I have a dual boot system with Windows 10 and Ubuntu 18.04 LTS already setup and working. But since the release of new version of Ubuntu (20.04.1 desktop-amd64) and with the hope of solving the [issue]("https://ubuntuforums.org/showthread.php?t=2449629") that I am current facing. I want to upgrade to this new version which I have already downloaded. 

So how would I go about doing it without losing any of my data ?

---

### Post by CelticWarrior on 2020-09-03
No, Ubuntu 20.04 likely won't solve that issue. Providing the information requested in your other thread might, at least would be a good starting point in troubleshooting. Specifically, the wireless script you were asked to run pretty much will give all the information needed to help you.

Now, regarding your specific question here, there are many ways.
The most obvious one is a online upgrade - requires an alternative internet connection - and can be done entirely in a GUI setting.
But if you already downloaded the 20.04 ISO and made an USB installation media you can boot from that and start the installation as normal and select "something else" instead of the automatic installation options. Then you'll need to select all relevant partition currently used by 18.04: EFI as EFI partition, root ("/") as root **but do NOT tick format** and if you have a separated /home also select that as such and again, **do not format**.
Or, even better **and faster**, do your backups - something you should have already - and install 20.04 from scratch.

All of the above is trivial but not to be taken lightly. Backups are essential for ALL OSes as everything may fail at any time. And some basic knowledge about computers is required and unfortunately, from your threads here, one can have an educated guess that you aren't there yet.

---

