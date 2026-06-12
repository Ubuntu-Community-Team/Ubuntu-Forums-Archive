---
title: "Problem installing Ubuntu 8.04 LTS on Asus P5G41-M LE"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by Juriaan on 2010-08-09
[COLOR=black][FONT=Verdana]I have 2 problems with installing Ubuntu on a Asus P5G41 main board. Chipset  G41 + ICH7.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]1 Ethernet adapter is not working[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]2 VGA adapter is not working[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I need to run Zimbra on this server. Therefore I need version 8.04.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]After starting up I get the orange bar. But when I should get a login the screen goes black.  I can start in text mode.[/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Can anybody help?[/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]

---

### Post by Juriaan on 2010-08-09
Guys,

When I check with lspci I see:

00:02.0 VGA compatible controller: Intel Corporation Eaglelake Integrated Graphics Controller (rev03)

Is there anyway to change the settings so I can start with low resolution that will work?

For the Ethernet controller I see:

01:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)

Juriaan

---

### Post by Juriaan on 2010-08-09
I ran 10.04 on the live cd. Display and network is working. The problem is drivers for version 8.04. Or can I use the drivers for 10.04 one way or another?

---

### Post by Lnxphrk on 2011-01-30
Hello, did you ever find a solution to this issue? I have the same mobo and a new ubuntu 10.10 install is having the same issue. It seems to detect the network at first boot then it drops the connection. I know that there isnt an issue with the cabling, router or nic itself because everything works fine on the other side (Windows7).

---

### Post by Juriaan on 2011-01-30
I installed 10.04 LTS and worked fine. :frown:

---

### Post by Lnxphrk on 2011-01-30
Have u tried 10.10 by chance? 
 
If I cant get it to work Ill downgrade to 10.4 but Id rather keep 10.10 since its running on my laptop as well. It helps me that they are same when tinkering around with the os since Im still new to linux.
 
Anyone know what the differences are or can point me to a chart of some sort? Id like to know what I would be missing if anything.

---

