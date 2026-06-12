---
title: "[SOLVED] LTSP login problem after openssh upgrade"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by oldsysadm on 2008-05-15
I have an LTSP installation which was working well under hardy 8.04.  Yesterday I use adept-updater to load all available upgrades which included updates to openssh.  Since
performing the upgrade I've not been able to login on the 
thin clients.  I've run ltsp-update-sshkeys and used a third
machine to insure that users could perform an ssh login to
the server.  After entering the user's id and password on
the client I get "Verifying password, please wait".  After a
few minutes the prompt for a user login id reappears.  I've
tried generating new keys with ssh-keygen but that didn't
help.  I can find no error messages in /var/log files.  I
tried to a "failsafe xterm session" on the client but that
hasn't worked wither.  Anyone have any ideas?

---

### Post by bodycoach2 on 2008-05-15
I am having this problem too. I may have to do a quick, complete Edubuntu reinstall without an update to get it working for a project.

---

### Post by Aearenda on 2008-05-15
I think an ltsp-update-sshkeys followed by ltsp-update-image are all that is necessary. The terminals use the key that has been changed for ssh.

Note that the second command is needed to integrate the new keys into the image transferred to the terminal at boot time.

---

### Post by bodycoach2 on 2008-05-15
You have saved me an all-nighter!!! Praise be to Aearenda the mighty. Slayer of LTSP problem!

Your instructions worked perfectly! Needs to be a sticky.

---

### Post by Aearenda on 2008-05-16
All I did was relay stuff I came across on the mailing lists... :-)
It does highlight the fact that much of the online doco for Edubuntu is ageing. The change that made the image update necessary came in with Gutsy I think. But this one is right: [https://wiki.ubuntu.com/DebugThinClientLogin](https://wiki.ubuntu.com/DebugThinClientLogin)

---

### Post by oldsysadm on 2008-05-16
Thank you for the reply Aearenda!  Somehow in my searching I had
missed the requirement to update the image.  My system
is again working.:)

---

