---
title: "Stuck booting the kernel."
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by stiankarlsen on 2006-10-30
I'm running ubuntu 6.06, and everything has worked fine over the last few months.

When i rebooted the computer yesterday, I simply can't start it up again. When grub loads, and ubuntu is chosen, i get to: **Uncompressing Linux...** and the computer just hangs. It never goes on from there.

If i have to reinstall ubuntu, thats OK, but I have a few mysql databases that I really would like to save.

If i boot up the computer with a live cd, is there any way I can save my mysql databases?

However the best thing would of course be to fix the problem so that i wouldnt have to resintall the os.

thanks for all your help.

---

### Post by morpheus5 on 2006-10-30
In the grub, try to add the "init=/bin/bash" at the kernel line, if it runs at the bash, i might have ur init scripts screwed.

---

### Post by stiankarlsen on 2006-10-30
Thanks for answering, but I already decided to install 6.10, however I messed up again, now [this]("http://ubuntuforums.org/showthread.php?t=288979") is my problem. / is read-only.

---

