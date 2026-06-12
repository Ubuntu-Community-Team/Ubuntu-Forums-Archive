---
title: "Deploying kernel driver patch"
date: 2013-12-09
forum: Installation &amp; Upgrades
---

### Post by venkat-330 on 2013-12-09
[COLOR=#000000][FONT=Arial] am very new to linux drivers and kernel [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Recently i am facing IDE based issue in my system.to overcome the issues i saw a link : [[/FONT][/COLOR][tartarus.org]("http://tartarus.org/ds/quirk-ich-force-ahci.patch")[COLOR=#000000][FONT=Arial]] which i believe might solve the issue [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]kernel version : (linux-source-2.6.32). [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Below are the steps which i performed: [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]1. In my work machine applied the patch changes as mentioned in forum [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]2. compiled the changes in work machine [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]3. Now i need to deploy the compiled patch in work machine .how should that be done?? [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]below are failure steps which i tried so far : [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]compiling of patch (work machine) [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]make SUBDIRS=drivers/pci/ and make module SUBDIRS=drivers/pci/ [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]For deploying i tried the below stuff: (please correct the mistake which i am doing) [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]i copied the "pci-stub.ko" from linux-source-2.6.32/drivers/pci to test machine's : "/lib/modules/2.6.32-5-686/kernel/drivers/pci" location [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]and then set quirks.ich_force_ahci=1 in /etc/grub/grub.conf [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]and performed the reboot and still see the patch did not work[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by MG&amp;TL on 2013-12-09
Read the patch. It's "not guaranteed" to work, and by the tone of the comments, I get the impression that the author is pretty sure it's not going to.

That said, the only thing I can think of to check is that you installed the new kernel on the work machine.

---

