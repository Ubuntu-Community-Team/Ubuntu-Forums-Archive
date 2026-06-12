---
title: "Update manager installed new kernel - now nothing works"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by MatthewJS on 2007-12-22
I allowed my update manager to perform the suggested updates. I noticed one of the updates was a kernel update (I'm on feisty). It said it needed to reboot. The reboot ran into problems, announcing that there was a problem with the file system and giving me a bash prompt. If I browse my hard drive using ls from the prompt I can see my personal files. It is really important that I retrieve them. Selecting the previous kernel or rescue mode gives me the same result. My strategy was to try to connect to my machine from my wife's pc using nfs and then read my personal files off it via the network. I have pinged my machine from her pc successfully. When I try to run ```
chkconfig nfs on
``` on the problem pc it tells me there is no such command and when I try and run ```
/usr/sbin/exportfs -ra
``` it tells me there is no such file. apt-get is missing so I can't get hold of anything. When I try and mount from my wife's pc it tells me > connection refused. 

In other words HELP!

Regards,

Matthew (relative newbie)

---

### Post by gspearing on 2007-12-22
I have found the same. Did you get a message explaining what the problem was when you booted? Mine advised me to add noapic to the kernel boot options. This got everything loaded. I also had to update my xorg.conf which got trashed.

Still working out how to add noapic permanently to my boot command.

---

