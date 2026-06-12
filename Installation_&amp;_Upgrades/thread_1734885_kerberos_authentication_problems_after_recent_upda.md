---
title: "kerberos authentication problems after recent update"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by etnyg on 2011-04-20
[COLOR=black][FONT=Verdana][SIZE=1]Recently (4/19/2011) a security update was applied to the authentication software Kerberos. This update required a system reboot. However, after the reboot, my system could no longer authenticate against the key distribution center (KDC).[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=1] [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=1]I've tried to debug this from the command line using the program kinit. The error I've received is:[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=1] [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=1]"kinit: Cannot resolve network address for KDC in realm "MYREALM.NAME" while getting initial credentials"[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=1] [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=1]I've looked around online and this usually indicates a DNS error. But if I haven't changed anything in my network set up, what else could be causing this problem beside the Kerberos update?[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=1] [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=1]Has anyone else experience this problem? If so, were you able to fix it?[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=1] [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=1]Thanks ahead of time.[/SIZE][/FONT][/COLOR]

---

### Post by etnyg on 2011-04-21
I solved the problem. It had absolutely nothing to do with the update. It had everything to do with our DNS service dropping the KDC address. I put in the IP address for the KDC and everything worked again.

---

