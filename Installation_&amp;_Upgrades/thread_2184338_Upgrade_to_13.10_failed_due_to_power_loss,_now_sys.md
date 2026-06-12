---
title: "Upgrade to 13.10 failed due to power loss, now system won't boot"
date: 2013-10-28
forum: Installation &amp; Upgrades
---

### Post by smsimp01 on 2013-10-28
I'm fairly new to using Ubuntu and I was upgrading Ubuntu to 13.10 the other day and lost power while it was in the process of installing the update.  It was roughly 65% installed when I lost power.  Now when I try to reboot the system it says its booting version 13.10, I enter my password and it immediately fails.  I don't have another OS on the system I'm running Ubuntu on.  Is there a way I can repair it to boot properly, or possibly get it to revert back to the old version so that it will boot?

---

### Post by linux4me on 2013-10-28
I think that's a sign you're supposed to do a clean install.

If you have a backup of all the files you want to keep, the fast way to fix this is to just do a clean install using a [USB startup disk]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu"), then restore your personal files.

If you don't have a backup, you can try [booting into recovery mode]("https://wiki.ubuntu.com/RecoveryMode"), recovering your files using the command line, or use the startup disk to start a Live session of Ubuntu and copy them elsewhere that way, then do a clean install. 

I have not had good luck trying to repair an upgrade that has gone south in this manner, and found it is much faster and trouble-free to just do a clean install, though YMMV.

---

### Post by warp99 on 2013-10-28
Here's your answer:

[http://askubuntu.com/questions/111563/lost-power-during-upgrade-how-do-i-recover](http://askubuntu.com/questions/111563/lost-power-during-upgrade-how-do-i-recover)

I've done something similar numerous times while ugrading and NEVER had to do a re-install. In fact I've have the same installation on my machine since 2006. I just keep upgrading the hardware and software. :D

---

