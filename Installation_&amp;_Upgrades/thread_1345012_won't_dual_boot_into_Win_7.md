---
title: "won't dual boot into Win 7"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by Nitewalker on 2009-12-03
Just installed 9.10 64bit on new HP laptop with Win 7 installed, installed Grub as suggested during install of 9.10, now machine will not bring up windows 7 when loading grub.  System files still there as I can see & access them from "places".......what do I need to do to be able to get windows to come up in grub:confused:

---

### Post by darkod on 2009-12-03
Does it give any particular error?

---

### Post by Nitewalker on 2009-12-03
does not give any error, does not even show WIN 7 in list when grub comes up

---

### Post by darkod on 2009-12-03
Download the script in my signature. Move it on desktop for example, and in terminal execute it with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file that will have all info about the boot process. Copy the content of that file here and please wrap it in CODE tags for easier reading. Just select all of the text and hit the # button in the above toolbar.

---

### Post by wilee-nilee on 2009-12-03
You might just try sudo update-grub in the terminal.

---

### Post by presence1960 on 2009-12-03
> **wilee-nilee said:**
> You might just try sudo update-grub in the terminal.

if that does not work run the script darkod suggested

---

