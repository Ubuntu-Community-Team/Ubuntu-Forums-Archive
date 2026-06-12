---
title: "Help with my desktop!"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by bharani94 on 2010-02-21
Hi guys, 

My desktop has 2 drives: a master (XP) and a slave (which i dlded linux on). the thing is that i dont get to chooose if i want to open up xp or ubuntu when i turn my desktop on. it says grub error: no such disk. Im like screwed if i cant fix this, but i still have my live cd with me. help please? :(

---

### Post by presence1960 on 2010-02-21
I need a lot more info from you in order to diagnose the problem. First I need the exact error reported onscreen. Then this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

