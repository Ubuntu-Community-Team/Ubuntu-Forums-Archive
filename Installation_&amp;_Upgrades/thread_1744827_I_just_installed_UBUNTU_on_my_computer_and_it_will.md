---
title: "I just installed UBUNTU on my computer and it will not boot up properally it keeps"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by BlueBlaze on 2011-04-30
I just switched from MAC and i installed UBUNTU 10.04 on my  computer and now everytime i go to boot the computer it fails and just  doesn't start up? What should i try and do?

---

### Post by Rubi1200 on 2011-04-30
Hi and welcome to the forums :-)

Start by posting the full specifications for the computer.

Then do this so we can what is going on:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

