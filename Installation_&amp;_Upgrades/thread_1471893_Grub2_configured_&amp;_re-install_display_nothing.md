---
title: "Grub2 configured &amp; re-install display nothing?"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by vzhen on 2010-05-03
1. I edited 40_custom and sudo chmod -x /etc/grub.d/10_linux /etc/grub.d/30_osprober /etc/grub.d/???memtest

2. sudo update-grub and display nothing. (i guess i have wrong configured in 40_custom.

3. I completely remove grub-pc and re-install grub.
      -I found that all the files in grub.d still there.
      -I removed entire grub.d folder.

4. sudo update-grub and menu.lst display back my previous OS

5. I re-install grub-pc as well as uninstall grub.

6. sudo update-grub and 
generating grub.cfg...........
Done                     <---- display NO OS here.

7. I thought grub.d folder will replace once i reinstall but it didn't

Question:
A. How can i re-install the default grub2 to detect all my OS?
B. How can i get back all the grub.d folder and the files inside
C. sudo chmod -x /etc/grub.d/10_linux to remove the execute. 
How can i execute it back?

------------------------------------------------------------------------
I got Question C
sudo chmod -rwx


------------------------------------------------------------------------
**FIXED with this thread  - 12. Uninstalling grub2**
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Not sure we must **copy those files** or we must **run under terminal** to get this done

---

