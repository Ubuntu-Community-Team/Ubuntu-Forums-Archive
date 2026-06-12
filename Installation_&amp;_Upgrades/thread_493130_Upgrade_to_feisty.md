---
title: "Upgrade to feisty"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by Thomas Delbeke on 2007-07-05
Hi,

I tried upgrading to feisty from edgy for two months now. It still doesn't work. I am trying to figure out whether to  report a bug or not. The fault report is currently:

Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/source/Sources.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/source/Sources.gz](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/source/Sources.gz) 404 Not Found

It used to be however:

Problem downloading file 73 or something like that. It crashed while downloading files then. In both situations, the previous and the current, I got the message that I might have connection problems. I most certainly have not. Windows works fine. So does Ubuntu, for ordinary surfing. I use the dutch translation pack for edgy. I don't recall having installed a firewall or something, although I have tried to install AVG virus scanner, but I think that didn't work (I'm not to great at the command prompt.) I have a Dell Latitude D510 with XP and I use wireless trough Netgear router. I am still regularly updating through update manager without any problems though.

Thank you,

Thomas

---

### Post by Mopana on 2007-07-05
I had this same problem. I think I froze on file 73 at first, also. Later I got to 93/94, but still froze. My solution was to download a new Feisty LiveCD and try to salvage old Edgy Eft data through the reinstallation.

---

### Post by linuxwizard on 2007-07-05
Remove or disable any extra repository that may have been added besides the Ubuntu repositories. Have you done a upgrade to a newer version before? Do you have automatix or envy installed?

---

### Post by Thomas Delbeke on 2007-07-06
Ok thanks, but it hasn't worked yet. I removed automatix. I don't have envy (the program). I think it may be the AVG virus scanner for linux. I went to the homepage to find an uninstaller. Didn't find it. It said in faq that I have to remove it by running the installer again, but that one crashes. When I search files I find 47 with avg in it, no way of telling what they are. I selected and deleted them (ctrl + A and delete), but I get the message not authorised or something. In the terminal deleting automatix didn't work with rmdir because it wasn't empty. I tried it with sudo and nothing happens after I log in. If I did remove the AVG files can the system crash? I don't know if there are system files that contain the avg string. Thanks for the help anyway,

Thomas

---

