---
title: "Problem in packages and bash after installing ubuntu"
date: 2013-05-09
forum: Installation &amp; Upgrades
---

### Post by mahmoud moosa on 2013-05-09
Hello everybody,

I have a Dell OPTIPLEX 3010 Desktop.
Windows 8 was pre-installed.

First time i couldn't boot ubuntu but when i changed the following options in BIOS i faced the following issue:

First, during the installation, there is option says: [COLOR=#800000]at least 4.4 GB available drive space[/COLOR] which is checked in green color and working fine.
The other option: [COLOR=#800000]is connected to the internet[/COLOR], this one is checked in green color for the first few seconds and then showing gray x circle, which means network card is detected and then disconnected.

Althoug, when i looked in the back of computer the network card is blinking and seems working fine.
After that i continued installing ubuntu.

Any idea please ? because after i finished installing ubuntu i faced alot of problems in bash, i wrote them in other posts.
For example, i can't update from bash or downloading programs from software center.

The other question please, What are the correct setting should i configure in BIOS ? is it relating what i am facing or not ?
[COLOR=#ff0000]
Note[/COLOR]:  Windows 8 already deleted.     
          I am using ubuntu (64-bit).

Below are the options in green color which i chose in BIOS, and please if i am wrong correct me.

From Boot List Options: 
[COLOR=#006400]Legacy[/COLOR]

From System configuration and SATA Operation:
[COLOR=#006400]AHCI[/COLOR]

From Security Boot:
[COLOR=#006400]Disabled[/COLOR]

From Integrated NIC:
[COLOR=#006400]Enabled w/PXE[/COLOR] and before it was [COLOR=#006400]Enabled[/COLOR] _[SIZE=4]only[/SIZE]_

Please give me answer because i spent hours to solve but no luck.

Thank you for any help.

---

### Post by gravysteak on 2013-05-09
It looks like you are already being helped in those other threads. Be patient. These are volunteers.

I dont think your problems have anything to do with bios options.

---

### Post by mahmoud moosa on 2013-05-12
> **gravysteak said:**
> It looks like you are already being helped in those other threads. Be patient. These are volunteers.

I dont think your problems have anything to do with bios options.

Hello my friend,

It is solved.

What i did is, i entered the BIOS and changed the mode from [COLOR=#006400]UEFI[/COLOR] to [COLOR=#006400]Enable Boot Legacy.[/COLOR]

Thank you for you answer.

Greatful.

Mahmoud.

---

