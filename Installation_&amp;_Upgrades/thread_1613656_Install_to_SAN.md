---
title: "Install to SAN"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by bman6890602 on 2010-11-04
[FONT=Verdana][SIZE=3]I can successfully install to an iscsi SAN and get my diskless client to boot properly using Ubuntu Server 10.10... My goal is to share this install amongst other clients and keep it as a golden image.. In order to do this I somehow need to "generalize" the install. I have been searching through the inirtd img file for unique entries [/SIZE][/FONT][FONT=&quot][FONT=Verdana][SIZE=3]that might bind it to the client I am using for testing. Except for one spot (so far anyway) and that is in the “/etc/ of the initrd image. There is a variable labeled “initiatorname.iscsi” and this file contains the iqn of the client I am using. I have instructions for generalizing RHEL installs and it say to look for variables named "netname" and comment them out but I do not see anything like that in the Ubuntu Server initrd img file. This may not be the correct forum for this question. If so I apologize.[/SIZE][/FONT]
[/FONT]

---

