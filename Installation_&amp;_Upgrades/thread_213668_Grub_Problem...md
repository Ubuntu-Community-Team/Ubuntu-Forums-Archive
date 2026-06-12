---
title: "Grub Problem.."
date: 2006-07-11
forum: Installation &amp; Upgrades
---

### Post by cyberlite on 2006-07-11
I have a question since today and after an update, I get 3 ways to  (Boot in grab) to ubuntu.. all the same  :confused: How can I delete the 2???

 P.S.The seconde boot was criated when I installed Kubuntu, the 3rd today after an update.

---

### Post by ciscosurfer on 2006-07-11
I believe you are referring to additional kernels being installed.  I wouldn't mess with them (delete them) unless you are sure you don't need them (so you can revert back to an older kernel if the newer one is botched somehow).  

You can edit your **/boot/grub/menu.lst** file and comment out (via pound signs --> **#** <--- that's the pound sign) your older kernels.  Keep the two at the top (newest kernel, and recovery option) in tact.

Check [this post]("http://ubuntuforums.org/showthread.php?t=201368&highlight=commenting+grub") for more info on commenting out lines.

Check [here]("http://www.gnu.org/software/grub/manual/grub.html") for more info on grub.

---

