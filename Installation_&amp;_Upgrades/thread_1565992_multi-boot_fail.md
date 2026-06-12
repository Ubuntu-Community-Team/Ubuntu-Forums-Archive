---
title: "multi-boot fail"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by Fusionman41 on 2010-09-01
Hi, I'm new to Ubuntu, downloaded the version to run on the same PC as windows XP. Sytem starts straight to XP, never gives the option to start in Ubuntu, any ideas?

---

### Post by presence1960 on 2010-09-01
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by rab2140 on 2010-09-01
I have the same issue , ubntu installs for mr but i cannot access it, the grub bootloader doesnt work it just goes stright to windows as if ubuntu was not installed

---

### Post by presence1960 on 2010-09-01
if either of you want some help I suggest you download & run the boot info script. neither of you have given any useful info to even begin troubleshooting your problem(s). The output of the boot info script will show what we need to know.

---

