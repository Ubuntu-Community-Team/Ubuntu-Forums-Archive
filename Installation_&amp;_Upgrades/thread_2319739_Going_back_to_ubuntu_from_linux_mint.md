---
title: "Going back to ubuntu from linux mint"
date: 2016-04-06
forum: Installation &amp; Upgrades
---

### Post by lanig on 2016-04-06
I moved to linux mint a few years ago because I liked cinnamon and because I didn't want to have Ubuntu spyware on my computer.
Since then, I started to use only XMonad and for 16.04 Ubuntu has decided to drop the spyware so I would like to de-mintize first my system and then upgrade to 16.04.
dpkg -l |grep mint gives me a list of packages. Would it be sufficient to remove them and the linuxmint repositories to get back to a vanilla Ubuntu ?
I am concerned by configurations files that could stay on my HD.

Thanks for your help.

---

### Post by sudodus on 2016-04-07
I think it would be very difficult to convert a Linux Mint system to an Ubuntu system.

Instead I suggest that you ***create a fresh Ubuntu system***, copy your personal files and install the extra program packages you want. One good idea is to keep your data files (documents, pictures, music, video clips ...) in a separate ***data partition***. This will keep your operating system rather small, and it will make it easier to make fresh installations in the future.

***Backup:*** It is also easier, when you can separate the backup of your personal files from the backup of the operating system.

---

### Post by RobGoss on 2016-04-07
Hello and welcome, I don't even know if it's possible to go from Mint to Ubuntu. I would also just do a fresh install to avoid any headaches. You might even risk loosing a lot of important data.

---

### Post by sammiev on 2016-04-07
I found keeping a separate /home partition on the HDD makes it easy to install or test other OS without loosing any data.

Remember that Backups are your best friend!

---

