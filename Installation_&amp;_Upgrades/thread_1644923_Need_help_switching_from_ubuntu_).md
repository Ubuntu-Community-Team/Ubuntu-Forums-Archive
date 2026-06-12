---
title: "Need help switching from ubuntu :)"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by RuinRoad on 2010-12-13
Hello,

This is my first post.

I have been running ubuntu for a bit and It's not for me, I need windows to run for school :P

So I bought windows 7 and I would like to "upgrade" to it, The problem is when I try to "upgrade" it asks me to increase the boot drives partition, It needs to copy temp files.

I don't know how to do this and I'm begging someone to help me!


Thank you so much,

-Ruin

---

### Post by presence1960 on 2010-12-13
Need way more info about your setup & boot process.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

