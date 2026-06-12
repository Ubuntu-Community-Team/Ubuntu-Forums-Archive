---
title: "New install, can't find network workgroups"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by km6xz on 2010-06-17
Hi I just converted our whole office from many flavors of Windows, and windows server 2000 to Ubuntu Server and Kubuntu for desk tops.
All went beautifully and the staff is warming up to my move(the first think one noticed was that Open Office can ready both older DOC and newer DOCX Word files, which MS Office can't do). 

The Ubuntu 10.04 Server was a learning experience because I added a lot of things other than just service Samba files(intranet, internal mail server, MySql, etc). Going on 3 weeks and not one problem with printing, incompatible document formats etc! But getting it all working was fun because things make sense and are visible. Windows is fine when things work but when it doesn't it is very mysterious and unfriendly.

All was fine except when I tried to install Kubuntu 10.04 on a spare laptop. It worked perfectly with the live CD and even a bootable persistent version on a flash drive. But when installing a normal HD install, all went well but I can't find the workgroup on the network. I am a pretty much novice so really do not know where to start looking. I can ping the server and internet and the new intranet work on the wireless and wired connections. Just can't see the network workgroup. 

Any suggestions were to start looking? or maybe just reformat and start again. I just tried booting from the CD and the USB Flash drive again and both of those work well, just slow. 
Thanks 
Stan

P.S. For those wondering if it is a good move, consider what a support relievf it would be to have all your desk machines on the exact same page in terms of security updates and versions, and so easy to keep current. THAT is why Ubuntu/Kutuntu are good solutions to small and medium size businesses. We have 28 deck tops running it now. Besides the UI is really pretty cool.

---

### Post by Chame_Wizard on 2010-06-17
Install Samba,so that you can be part of an Active Directory or run as Primary Domain Controller.

see [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1499753")

---

