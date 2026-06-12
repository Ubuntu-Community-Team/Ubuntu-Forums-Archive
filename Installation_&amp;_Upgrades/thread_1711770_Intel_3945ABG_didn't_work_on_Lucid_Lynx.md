---
title: "Intel 3945ABG didn't work on Lucid Lynx"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by Enerian on 2011-03-21
After installing Lucid Lynx on my computer (Sony Vaio FE660G) I found out the wifi wasn't working. The Network Manager didn't show up in the task panel and I didn't know what to do. I googled my problem but didn't find a unique and easy answer. I solved it the following way:

I installed the WICD manager, which apparently is a much more reliable manager:

$ sudo aptitude install wicd

After doing this wicd was recognizing my wifi but I couldn't make it work since there was an error with the password (it said "incorrect password" even though I typed it correctly several times)

Although I had read in many posts that the wicd installation removes the network manager, I tried removing it myself (out of my desperation) and finally it worked after restarting the computer.

$ sudo apt-get purge network-manager network-manager-gnome

I hope it helps someone.

---

