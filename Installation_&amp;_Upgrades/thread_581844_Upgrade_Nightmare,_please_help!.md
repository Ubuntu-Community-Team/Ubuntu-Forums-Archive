---
title: "Upgrade Nightmare, please help!"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by CodyZ on 2007-10-19
Hey there, I was really excited to upgrade Xubuntu to 7.10 from 7.04.  So last night I went into the Update Manager, and followed the wizard to upgrade to Gutsy.  Eventually I got to the point where it started downloading and installing, and it said I had about 2 hours left to go.  I went to bed and left it running over night.

This morning, I went to check it and the Xfce screensaver was on and it prompted me for my password.  I entered my password like normal, but it wouldn't accept it.  I tried this about 10 times before finally giving up and clicking the "new login" button.  That brought me to the xubuntu login screen, but it looked different (presumably because of the upgrade) and kept flashing a little error window reading "Authentication Failed."  So I clicked the restart button in the lower left hand corner, it restarted and now when it boots up I get a Kernel Panic error, unable to mount fs.

Please, please, please help!

Thanks!

---

### Post by jrasmussen0 on 2007-10-19
You should be able to boot into the previous kernel that worked and finish the upgrade using the command line at least (aptitude, u, + over upgrades, g, g) or (apt-get dist-upgrade)

If the X windows fails you will need to boot into the safe mode.

---

