---
title: "error: no such device after successful instal"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by _NEO on 2009-12-17
Hello, I just finished installing v9.10 the install when smoothly and once done it asked me to remove the cd and press enter to reboot. When it restarted I got: error: no such device: 4401ad60-8194-4216-b966-9d4490b15158. I do not know what device this might be or how to fix this error. Does any one know what I should do?

---

### Post by Rmantingh on 2009-12-17
I'm no expert but a quick search on these forums brought up this link:-
[http://ubuntuforums.org/showthread.php?t=1301144](http://ubuntuforums.org/showthread.php?t=1301144)
Perhaps it can help you.

---

### Post by presence1960 on 2009-12-17
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

