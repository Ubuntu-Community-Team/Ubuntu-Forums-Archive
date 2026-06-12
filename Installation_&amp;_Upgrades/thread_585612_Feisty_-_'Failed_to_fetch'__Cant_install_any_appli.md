---
title: "Feisty - 'Failed to fetch' / Cant install any applications"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Rawrhunter on 2007-10-21
I reinstalled over my Feisty (software update from Edgy) installation yesterday with Gutsy, spend a few hours fiddling around with it, realized it, and especially compiz fusion, are terrible, and decided to reinstall Feisty (off a new Feisty disc).

So I got beryl working again quickly, and updated all the updates I could, but I'm having a few strange problems. 

1) Whenever I restart my computer (or just X) my resolution goes from 1280x1024 (my native, and what I want it at) to 1024x768. I can't change it to anything higher than 1024x768 in the System->Preferences->Screen Resolution menu, so right now I have to use nvidia-settings each time I restart my computer.

2) Installing any program through the Add/Remove Programs menu, OR Synaptic doesn't work. I'm told that theres a bunch of 'uninstallable dependencies' missing, and nothing can be installed.

3) Related to #2, I tried a simple sudo apt-get update, it goes through most sources as usual, then I get a:

"Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)"

I can download the file fine through firefox, so it does exist and the server is fine. I've also forwarded all necessary ports on my router, so nothing should be getting blocked.

Any help would be great. Right now I just want things back the way I had them last week :(

---

### Post by Rawrhunter on 2007-10-21
Anyone have any suggestions? I'm kinda stuck here.

---

