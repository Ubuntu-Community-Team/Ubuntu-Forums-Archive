---
title: "[SOLVED] new install wrong root password..."
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by tw33k@ on 2008-09-24
okay i installed ubuntu 8.04 and immediately updated. the system runs well and i can use sudo for admin, but today i tried to su and the password wont work. since installing i dont think i've needed to use the root account but i'm possitive i remember the password correctly...

Question is how do you change the root pass without knowing it in the first place? I do have the liveCD, several distros infact.

i previously had a winXP+slackware system, then tried to move over to stand alone gentoo. but gentoo install too long for command line and GTK/ncurses installs fail each time so i get the same sort of power from apt as from portage...

---

### Post by Linteg on 2008-09-24
Ubuntu doesn't have a root password by default, instead all superuser tasks are done using sudo. If you really want to activate the root account, make sure that the root user's shell which should be at the end of the first line of /etc/passwd points to something useful (not /bin/false or /sbin/nologin), and run "sudo passwd" to give ta password to the root account in order to enable logins. Do not do this unless you know what you are doing, ubuntu does **not** need an enabled root account nor is the distribution desinged to have one, if all you want is a root shell running sudo -s will be enough.

---

### Post by tw33k@ on 2008-09-24
that clarifies it. I've tried a few distros recently and must have mistaken the ubuntu install with previous distros. I never use superuser accounts unless the system is isolated from the net, and sudo is more than adequate for my admin needs. it was just a surprise when i'm used to slackware and gentoo.

thanks for the fast reply.

---

### Post by Sef on 2008-09-24
If you want more information about root and sudo, read [Root/Sudo]("https://help.ubuntu.com/community/RootSudo").

---

