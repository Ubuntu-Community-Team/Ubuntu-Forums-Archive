---
title: "can not mount / filesystem -"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by krutoj007 on 2010-09-19
I was updating my 64bit Ubuntu 9.04 when something went wrong. 
Now I can not boot the system . Only can get to recovery mode and it stops with message : 
One or more of the mounts listed in /etc/fstab can not be mounted: waiting for device ....
If I [click]("http://ubuntugeek.com/forum/index.php/topic,437.0.html#") ESC - it brings me to a command line propmt. 
And thats about all I can do. 
May you please help me to recover this system?
I'd appreaciate your valueble input. 
Thank you!

---

### Post by presence1960 on 2010-09-19
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

