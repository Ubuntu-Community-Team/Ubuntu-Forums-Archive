---
title: "Grub Menu Instead of Windows Boot Loader"
date: 2013-06-27
forum: Installation &amp; Upgrades
---

### Post by samsalman on 2013-06-27
Hello Expert,

I am newbee in Ubuntu and recently switched to it from windows in order to work on Hadoop  & Hbase.
Few days back I successfully installed Ubuntu through wubi in the same partition where windows locate and also made environment for hadoop successfully.
But due to some reasons I had to reinstall windows 7, however of course I didn't want to loose my data of ubuntu, so I backuped my wubi/ubuntu folder into my external Hard disk so that I can restore it when I would be done with new windows. So now I have reinstalled windows 7 and I have also installed wubi in different partition successfully. Now I want to restore my wubi backup data into my current wubi installation so that I don't need to configure anything.

In this regards, I am following this thread [http://ubuntuforums.org/showthread.php?t=1796794](http://ubuntuforums.org/showthread.php?t=1796794) to restore my previous wubi installation.

In this thread, Rubi1200 suggest that "select Ubuntu from the GRUB menu and press "e" to edit."  but in my case I don't see grub menu but Instead I see windows boot loader given in attachement. My question is how can I show grub menu in order to follow the steps mentioned in a given thead. 

Please suggest me solution step by step as I am novice in ubuntu. I hope I have explained my question well in order to get accurate response.

Thanks In Adavance.

---

### Post by Mark Phelps on 2013-06-27
You get the GRUB menu AFTER you boot into Ubuntu.  You have to select Ubuntu from the menu, and very quickly, start pressing the "e" key to open an editor for the GRUB menu.  You won't see a GRUB menu by default because it does not show automatically.

---

### Post by samsalman on 2013-06-27
Thanks for your reply..
I tried to select ubuntu. and press enter and start press "e" but it doesn't work, it took me to the Ubuntu and shown me login screen.. 
Please anyother suggestion?

---

### Post by samsalman on 2013-06-27
Well.. Thanks for your suggestion.. It worked while holding shift key  and pressing e.. It might help some novice like me in future :razz:

---

