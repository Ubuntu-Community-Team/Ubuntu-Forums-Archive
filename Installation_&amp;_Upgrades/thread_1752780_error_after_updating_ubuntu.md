---
title: "error after updating ubuntu"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by vatsagaurav007 on 2011-05-08
Dear Experts
                   I am a newbie to linux. I have installed ubuntu on my system and now when i have updated it through internet, it is not booting up. When i boot a black screen appears and it says 
"initramfs"

i dont understand what commands i should use to rectify this error and boot my system.

Please Help
REGARDS

---

### Post by Rubi1200 on 2011-05-08
Hi,

please do the following so we can get a better overview of the current state of your system:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

