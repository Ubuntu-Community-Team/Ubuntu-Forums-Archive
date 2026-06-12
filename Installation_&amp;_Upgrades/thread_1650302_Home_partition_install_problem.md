---
title: "Home partition install problem"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by Speedwagon on 2010-12-21
I have my home directory setup on a seperate drive(sdb), and Ubuntu installs on sda.  Everything has been hunky-dory for the last couple times I installed Ubuntu(clean install), but this last time it wasn't so ok.  When I went to select sdb as the /home directory, it wouldn't just let me select it.  It wanted to format the drive, which was not so ok, so I didn't select sdb as the home drive.  How do I fix this, and why wouldn't it let me simply select sdb for /home?  I haven't installed anything yet, so I don't have a problem re-installing if that is the easiest way.  And this is 10.10, from a DVD I burned.

---

### Post by dino99 on 2010-12-21
in case you need a standard scheme:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

when you make a fresh install or a dist-upgrade, and dont select your /home, the installer will automatically find it, so no worry too much.

The question is: why it wants to format it, which is his actual format (might be ext3 or ext4)

---

### Post by Speedwagon on 2010-12-21
> **dino99 said:**
> in case you need a standard scheme:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

when you make a fresh install or a dist-upgrade, and dont select your /home, the installer will automatically find it, so no worry too much.

The question is: why it wants to format it, which is his actual format (might be ext3 or ext4)

ext4 is what all my drives are formated in.

---

### Post by dino99 on 2010-12-21
so go aheah without selecting /home (stay safe, after installation you always can run fsck on reboot by: sudo shutdown now -R)

---

