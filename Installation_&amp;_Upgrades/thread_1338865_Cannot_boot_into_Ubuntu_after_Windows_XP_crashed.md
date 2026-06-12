---
title: "Cannot boot into Ubuntu after Windows XP crashed"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by kyoha on 2009-11-26
Hello!  I have Windows XP and Ubuntu 9.04 on an HP Pavilion Notebook.  Recently, XP crashed, and took out Ubuntu with it.  The first time it happened, I used my roommate's Windows restore CD and got Windows back on its feet.  From there, I burned a new copy of Ubuntu (still 9.04 because at the time, 9.10 was not released yet), and a friend got Ubuntu to load again and everything was back to normal.  

Then XP crashed again.  

I have no idea how to get back into Ubuntu.  I know its all still there, but I can't get to it.  The screen when I turn the laptop on that lets you choose Ubuntu or Windows is gone, and I would like to get that back.  Once thats here, everything works great.

I am terribly new to Linux still, and need incredibly basic instructions.  I know that I just need to rescue the broken system, but I don't know how to do it by myself.  

If you can help, I would be really grateful :-)

---

### Post by presence1960 on 2009-11-26
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by MelDJ on 2009-11-26
try using the xp cd to boot into recovery mode. then do a chkdsk /f

---

