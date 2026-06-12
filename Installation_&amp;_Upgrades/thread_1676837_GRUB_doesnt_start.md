---
title: "GRUB doesnt start?"
date: 2011-01-27
forum: Installation &amp; Upgrades
---

### Post by freshmeat20 on 2011-01-27
So i have a fresh install of ubuntu 10.10 and GRUB just wont boot. it just flashes an underscore for a little while and just boots up ubuntu without a selection screen at all. I commented out the hiddenmenu line and put the timeout on 30 secs but nothing. any ideas?

---

### Post by presence1960 on 2011-01-27
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by sikander3786 on 2011-01-28
I would also request to post the output of this command from Applications > Accessories > Terminal:

```
cat /etc/default/grub
```

---

### Post by Rubi1200 on 2011-01-28
Just to add my voice to the mix of great advice given so far; what graphics card do you have installed?

If you are seeing the underscore AFTER Ubuntu is supposed to boot, then it may indicate a graphics issue.

---

