---
title: "Grub Error 15 :("
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by pederjohn on 2010-04-05
Well after trying to install ubuntu twice now, i keep getting grub 15 error and have absolutely NO idea how to use grub

I have 6 Drives in this pc, The third drive is the drive it needs to boot from (according to ubuntu /dev/sdc1) but i can't seem to find it, and when i try to open the drive in the live cd it doesn't let me in so i am a bit pissed to say the least.

Can someone please help me?

Peder

---

### Post by Penguin Guy on 2010-04-05
I had the same issue and eventually solved it, I'm not sure if you'll be able to follow my explanation, but here it is anyway: [http://ubuntuforums.org/showthread.php?t=1447409](http://ubuntuforums.org/showthread.php?t=1447409)
Perhaps you could reinstall, but _before rebooting_ follow steps 3 & 4 in that post.

Good luck.

---

### Post by pederjohn on 2010-04-05
well i came right eventually by reinstalling grub 

but once 9.04 loaded it just kept showing me the little round busy sign(mousepointer) and eventually just gave me a black screen which eventually made my screen goto standby.

V10.04 Beta is even more buggy seeing as i can't even install it on my pc.

---

### Post by presence1960 on 2010-04-05
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

