---
title: "Upgrade To Ubuntu 21.04"
date: 2021-04-22
forum: Installation &amp; Upgrades
---

### Post by sasafrass452 on 2021-04-22
I'm currently using 20.10, & I want to upgrade to 21.04. I have not been prompted to upgrade, though I heard about a bug which has delayed the upgrade via the updater. I decided to download & burn it to a disc, but my laptop won't boot from it. Can anyone help? Thanks.

---

### Post by grahammechanical on 2021-04-22
I have an install of 21.04 development version and it is still being called development version even after an update today. I would wait a few days before upgrading. There are always further packages to be updated after release day on any Ubuntu release.

Make sure you have Software & Updates>Updates tab showing that it is set to notify you of a new version but For any new version. Make sure that Check for updates is set to daily. Otherwise you will have to wait until Software Updater does its scheduled check.

Regards

---

### Post by guiverc on 2021-04-22
I've provided this answer on [askubuntu]("https://askubuntu.com/questions/1333226/how-update-new-version-of-ubuntu-21-04/1333229#1333229") 

The [release of the ISO has only just occurred[1]]("https://fridge.ubuntu.com/2021/04/22/ubuntu-21-04-hirsute-hippo-released/"); the update from prior releases doesn't get opened until a decision is made on the *stability* of the new release (watching bug reports etc) & a decision is made to *turn the taps*, so I'd not recommend being impatient and waiting until you're offered the upgrade.

You can use `-d` to force... but refer to the [Ubuntu 21.04 Release Notes]("https://discourse.ubuntu.com/t/hirsute-hippo-release-notes/19221")[2] where you'll note

> Upgrades from Ubuntu 20.10 to Ubuntu 21.04 are not enabled as it is possible for some systems to end up in an unbootable state if they use EFI version 1.10 - bug [1925010]("https://bugs.launchpad.net/ubuntu/+source/shim/+bug/1925010")[3]. Release upgrades will be enabled once an updated version of shim is available which is compatible with EFI version 1.10.

FYI:  my install doesn't report itself as *development*, and didn't yesterday either... I'll be *bumping* back to the *development release* though probably tomorrow

As for your issue, I'd firstly check your ISO ([https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)) to ensure it's flawless.

Next I'd boot it on another box so the self-scan of media can occur (you don't see it any more as it's now a background task.. so just boot it & let it run in the background, test it works okay, then check for any errors (*squashfs*) or errors/issues reported in `dmesg`; I've found them pretty easy to spot.  I often have failed write of ISO to media; so tend to test a thumb-drive (installation media) in another box of the same type + a different type of box (eg. BIOS & uEFI or Secure uEFI) and if it fails to boot on any, I assume it's a bad write to the installation media...)


  [1]: [https://fridge.ubuntu.com/2021/04/22/ubuntu-21-04-hirsute-hippo-released/](https://fridge.ubuntu.com/2021/04/22/ubuntu-21-04-hirsute-hippo-released/)
  [2]: [https://discourse.ubuntu.com/t/hirsute-hippo-release-notes/19221](https://discourse.ubuntu.com/t/hirsute-hippo-release-notes/19221)
  [3]: [URL="https://bugs.launchpad.net/ubuntu/+source/shim/+bug/1925010"]https://bugs.launchpad.net/ubuntu/+source/shim/+bug/1925010
[/URL]

---

