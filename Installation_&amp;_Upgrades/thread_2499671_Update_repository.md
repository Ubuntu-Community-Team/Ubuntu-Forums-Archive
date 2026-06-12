---
title: "Update repository"
date: 2024-08-06
forum: Installation &amp; Upgrades
---

### Post by toft6633 on 2024-08-06
Hello,

I have searched without finding an answer. I have the file "[COLOR=#000000][FONT=Menlo]/etc/apt/sources.list.d/ondrej-ubuntu-php-jammy.list". The content is:
[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]
deb [https://ppa.launchpadcontent.net/ondrej/php/ubuntu/](https://ppa.launchpadcontent.net/ondrej/php/ubuntu/) jammy main[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]# deb-src [https://ppa.launchpadcontent.net/ondrej/php/ubuntu/](https://ppa.launchpadcontent.net/ondrej/php/ubuntu/) jammy main

I plan to upgrade from Jammy to Noble August 15 when 24.04.1 is supposed to be relased.

Can I after the upgrade simply replace the line "deb [https://ppa.launchpadcontent.net/ondrej/php/ubuntu/](https://ppa.launchpadcontent.net/ondrej/php/ubuntu/) jammy main" with "deb [https://ppa.launchpadcontent.net/ondrej/php/ubuntu/](https://ppa.launchpadcontent.net/ondrej/php/ubuntu/) noble main"?


Fred[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]

---

### Post by currentshaft on 2024-08-06
24.04

---

### Post by grahammechanical on 2024-08-07
Before you run the online upgrade from Ubuntu 22.04 LTS to 24.04 LTS disable that PPA. You can do that with Software & Updates>Other Software tab. Just untick the box. After upgrading you can then use the Other Software tab to add the PPA with its address modified

Regards

---

### Post by Rubi1200 on 2024-08-07
Make sure you have solid backups BEFORE upgrading.

---

### Post by deadflowr on 2024-08-07
I'd remove the ppa and re-add the ppa because they've updated all the apt keys for all ppas.
24.04 has higher key standards than 22.04 had, so they upgraded those in launchpad.

The old keys are still good, but they might be too weak and you may get warnings that they're weak.
Eventually, they'll become errors in future point releases for 24.04.

Long thread on that here and what you may or may nt need to do about it:
[https://discourse.ubuntu.com/t/new-requirements-for-apt-repository-signing-in-24-04/42854/10](https://discourse.ubuntu.com/t/new-requirements-for-apt-repository-signing-in-24-04/42854/10)

I don't know if they've ever added the functionality they mention in the first post to allow easy updating of the keys through add-apt-repository.
Maybe they mention it somewhere in the rest of the thread, but I couldn't find it, though truth be told, I did not look very hard.

---

### Post by toft6633 on 2024-08-08
Thanks for help.

---

### Post by toft6633 on 2024-08-08
Thanks for help, 

I run Ubuntu server without graphical options. 

From what I undertand, before upgrande: > "sudo add-apt-repository --remove ppa: odrej/php".
After upgrade: > "sudo add-apt-repository ppa: ondrej/php".

Fred

---

### Post by toft6633 on 2024-08-08
Thanks Rubi1200. Not the best... I am on a VPS. Backups are too expensive. I make a copy of the /etc/ directory and cross my fingers...

---

