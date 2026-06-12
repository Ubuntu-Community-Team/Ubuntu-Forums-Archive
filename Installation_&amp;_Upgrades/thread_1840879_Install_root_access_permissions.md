---
title: "Install root access permissions"
date: 2011-09-08
forum: Installation &amp; Upgrades
---

### Post by lesliem on 2011-09-08
Hi all,
When installing Ubuntu can you set a root password? and is there any way of preventing the "you do not have permission" message from ever appearing again.
Cheers

---

### Post by whatthefunk on 2011-09-08
The root password is most likely the password of the first user profile you created.  You should be able to use that password to access everything in your system.

---

### Post by haqking on 2011-09-08
> **lesliem said:**
> Hi all,
When installing Ubuntu can you set a root password? and is there any way of preventing the "you do not have permission" message from ever appearing again.
Cheers

Root account is disabled by default in Ubuntu, it can be enabled but the preferred method is by using [sudo]("https://help.ubuntu.com/community/RootSudo")

The "you do not have permission" is protective and for your benefit, you can override if you agree using sudo as i shown in link above

If you disable or remove your password you leave yourself open to allsorts of potential issues.

It is not about attackers from outside only, it is also about services and scripts running under admin privelege.

A blank password is never recommended, people often assume it doesnt matter if they are the only user of the system, but it is not just about that, scripts in your browser or services can then run under your admin account without prompt for authentication due to blank password.

See here about why sudo is supported in the canonical model and the root account is disabled by default, it is possible to enable root and possible to have a blank password but neither are recommended.

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

rootsudo
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

See below for Bodhi.Zazen's overview of Linux Security

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

security stickies (5 stickies)
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

Have fun

Regards

haqking

---

