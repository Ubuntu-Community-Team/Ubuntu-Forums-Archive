---
title: "Printing Libre Office document problems after upgrade to Lubuntu 20.04"
date: 2021-02-25
forum: Installation &amp; Upgrades
---

### Post by chippermon on 2021-02-25
Hello,
 I decided to click on the upgrade to Lubuntu 20.04 that came up while maintaining my Lubuntu 18.04. It has a nice look and I think I will like it. Unfortunately, when I try to print a document made with Libre Office (previously saved in my existing folder or a new one) all I get is gibberish. Ampersands, hash tags, money symbol, percent symbols. No text. I decided to try and print an existing spread sheet and I can get the grids and tables but none of the text or numbers are there. Just symbols. Oddly, I am able to print any previously saved .pdf files so i thought I would try saving my .ods files as .pdf then print but that does not work either. 

I duplicated the same scenario on my wife's computer. ie. Lubuntu 18.04 then upgrade to 20.04 and I get the same result. By the way, I only did this because I liked the OS. I had yet to discover the problem with printing Libre Office docs. Now she's slightly annoyed with me. That's okay, not the first time in our 39 years.;) 

I would like to note that a document I just made in Abiword prints just fine. Also of note, everything that will print seems to go quickly to the printer. There is a substantial lag when trying to print a Libre Office file.

I assume this is a Libre Office problem then. Has anyone experienced this yet? Can anyone help me rectify this situation.

Thank you.

---

### Post by guiverc on 2021-02-25
Had you looked at the [Lubuntu release notes prior to upgrading]("https://lubuntu.me/focal-2-released/"), you'd have seen

> ***Note***, due to the extensive changes required  for the shift in desktop environments, the Lubuntu team does not support  upgrading from 18.04 or below to any greater release. Doing so will  result in a broken system. If you are on 18.04 or below and would like  to upgrade, please do a fresh install.

You base Ubuntu 18.04 LTS system offers the upgrade, it's issues with the desktop (and GUI programs running on the GUI) that will suffer because of the change of desktops (LXDE to LXQt) thus the *unsupported* status of it, and recommendation to clean install for that upgrade.

So your system may a number of issues beyond what you're aware of.  All Lubuntu notices since 2018 have warned Lubuntu 18.04 LTS was the last with LXDE, and upgrades were not supported (*there was some early mention that resolutions to the various problems may in the future be resolved, they never were, those pages never got published in the manual, upgrade never supported; but you may find some of the work still around on infrastructure*)

There are/were various issues with printing (esp. related to LibreOffice with 20.04), though they have workarounds.  eg. [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1892637](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1892637) but that applies where blank pages are coming out. Your issue may have been complicated by the *unsupported* upgrade path chosen.

I would boot a Lubuntu 20.04.2 system in *live* mode (ie. use the *Start Lubuntu* option) and see if you can print from there?   If it prints from there, the issue maybe related to the *unsupported* upgrade, though it also may not, if however you get the same response from the printer when operating in *live* mode (or all Lubuntu 20.04.2 as it should be) the issue is printer/LibreOffice related, and brand of printer maybe next helpful item.

FYI:  Upgrades do work, but you'll have options in your menus that go nowhere, do nothing (left over LXDE stuff that shouldn't, wouldn't be there on a fresh/LXQt install... ie. the user experience is lessened.  Your printer issue I suspect is 20.04/LibreOffice (maybe even Qt) related but I don't know.

---

### Post by Dennis N on 2021-02-25
So, its just the printing that fails, and otherwise documents display ok within LibreOffice? I would delete the printer from the Printers dialog (Preferences > Printers) and reinstall it to see if that corrects the problem. 

Another possible solution is to install the Flatpak version of LibreOffice (or even the Snap version). Those I believe would have their own compatible printer drivers. I have the Flatpak version installed in Lubuntu 20.04 and use it.

---

### Post by chippermon on 2021-02-26
Okay, Thank you for your response.
Best regards

---

