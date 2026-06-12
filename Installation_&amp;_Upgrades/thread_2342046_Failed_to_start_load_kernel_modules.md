---
title: "Failed to start load kernel modules"
date: 2016-11-03
forum: Installation &amp; Upgrades
---

### Post by cjgreenberg on 2016-11-03
[COLOR=#111111][FONT=Ubuntu]We had a brief power/internet blip during an upgrade and now i get this error on booting our Zotac B? Any help/guidance is appreciated.
Chip [/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2016-11-03
I had a similar event... but mine was self inflicted.
This worked for me...issuing the code below **one line** at a time.
```
sudo apt-get update
dpkg --configure -a
sudo apt full-upgrade -f
sudo apt -f install
```
Hope it also works for you.
Regards

---

### Post by cjgreenberg on 2016-11-03
Thanks You!!! I'll try and let you know

---

### Post by cjgreenberg on 2016-11-06
OK, I had some time to work on this today.  How do 
I get the CLI?  I tried entering recovery mode as detailed below.  I either got a blank screen, or the above error, depending upon how long i waited.
Again, your help is greatly appreciated!
Chip
[h=1]Booting into recovery mode[/h][COLOR=#333333][FONT=Ubuntu Beta][/FONT][/COLOR]
[LIST=1]
[*]Switch on your computer. 
[*]Wait until the BIOS has finished loading, or has almost finished. (During this time you will probably see a logo of your computer manufacturer.) 
[*]Quickly press and hold the Shift key, which will bring up the GNU GRUB menu. (If you see the Ubuntu logo, you've missed the point where you can enter the GRUB menu.)
[/LIST]

---

