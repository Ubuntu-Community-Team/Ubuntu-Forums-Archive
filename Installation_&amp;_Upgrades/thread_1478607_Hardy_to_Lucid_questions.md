---
title: "Hardy to Lucid questions"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by flyingsolo on 2010-05-09
I've had Hardy on a Dell desktop for some time with separate / & /home partitions all on one 500 GB drive & Win xp still on a separate 160 GB drive.
Under 'Software Sources' I have it set to show new releases of LTS type and yet I haven't had a notification of Upgrade being available.  Just wondering how to make the switch most easily.
(BTW, I have a downloaded iso of Lucid and tried it via live CD in the same computer to be sure it works and seems to be fine)
Also, I have Amarok on current install but I understand it isn't in the default Lucid install so will my Amarok be lost during the upgrade?
Thanks

---

### Post by flyingsolo on 2010-05-09
I've partly answered my own question by doing:
update-manager --proposed
but as I start the upgrade process, I get the warning about 'you're using the AMD 'fglrx' graphics driver' and that no version of this driver is available to work with your hardware in 10.04 LTS.
However, when using the Live CD, I didn't see any issues and screen display seemed fine.  Am I missing something or should it be OK to proceed with upgrade?

---

### Post by pastalavista on 2010-05-10
You won't need the fglrx driver in 10.04 because there is now a fglrx-modealias built in to the newer kernels. You should be able to update to Linx with the 'update-manager -d' command

---

