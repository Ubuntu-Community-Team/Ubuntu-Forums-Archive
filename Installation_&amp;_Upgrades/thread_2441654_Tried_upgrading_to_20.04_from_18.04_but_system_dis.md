---
title: "Tried upgrading to 20.04 from 18.04 but system displays something went wrong while re"
date: 2020-04-25
forum: Installation &amp; Upgrades
---

### Post by marwari on 2020-04-25
Hi all,

I have tried upgrading to newer version with do-release-upgrade and it encountered with ttf-mscorefonts-installer. I tried to fix this is recovery mode and tried reinstalling the same but after following various resources I'm not able to do that.

Another thing is whenever I reboot my system it says - Oh no! Something has gone wrong. A problem has occurred and system can't recover. Please contact a system administrator.

Any help is appreciated.

---

### Post by CelticWarrior on 2020-04-25
Welcome.

Please note that when posting about such issues a lot more info is needed, namely the complete error messages.

---

### Post by marwari on 2020-04-25
Only error I can see on screen is this –Oh no! Something has gone wrong. A problem has occurred and system can't recover. Please contact a system administrator.

---

### Post by CelticWarrior on 2020-04-25
I meant this: > I have tried upgrading to newer version with do-release-upgrade and it  encountered with ttf-mscorefonts-installer. I tried to fix this is  recovery mode and tried reinstalling the same but after following  various resources I'm not able to do that.


Please run ```
sudo apt update && sudo apt full-upgrade
``` and, if any, post the complete error messages.

---

### Post by DuckHook on 2020-04-25
Welcome to the forums, marwari.

Please also provide some context.

[LIST=1]
[*]How familiar are you with Ubuntu or Linux? Newbie or power-user?
[*]Full HW specs please. Desktop? Laptop?
[*]Do you know how to check logs?
[*]What "other resources" did you follow? Try to recount for us the instructions, which may have gummed up the works.
[/LIST]
Before you do anything further, ***make sure you have backups of your important data***. Be prepared to re-install from scratch. With backups, it's just an inconvenience. Please follow the link in my sig: "A system upgrade is a heart, lung and brain transplant. !!BACKUP FIRST!!"

---

### Post by marwari on 2020-04-25
It says – Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend.

---

### Post by DuckHook on 2020-04-25
> **marwari said:**
> It says – Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend.

See [above post]("https://ubuntuforums.org/showthread.php?t=2441654&p=13950327#post13950327").

---

### Post by marwari on 2020-04-25
Removing lock files worked for me.

Thanks you all for help, appreciated.

---

