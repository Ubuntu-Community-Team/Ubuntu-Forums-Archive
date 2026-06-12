---
title: "After upgrading to 18.04 from 16.04, unable to boot machine and use."
date: 2019-06-17
forum: Installation &amp; Upgrades
---

### Post by janap2 on 2019-06-17
[URL="http://paste.ubuntu.com/p/vT6Wr7jMfg/"]http://paste.ubuntu.com/p/vT6Wr7jMfg/

[/URL]Hi,

 recently i have upgraded to 18.04 from 16.04 Ubuntu and after upgrade completed, i am unable to get into the machine. I am getting various errors like dependeny failed for /dev/disk/by uuid xxxxxx etc. I have live CD ubuntu but how can i restore the machine. i have installed VMs in the original OS before upgradation and saved lot of stuff in the Virtual machine. How to get that data back? Please help. Please see the above link which i got after running boot-repair.

---

### Post by monopoli-1977 on 2019-06-17
is [COLOR=#444444][FONT=Ubuntu]Systemback program something you looking for ? (i can't share url's yet)[/FONT][/COLOR]

---

### Post by cruzer001 on 2019-06-17
Hello janap2, welcome to the forums :)

You can use the Ubuntu live installer (any release will work) to access and retrieve your data.  Your virtual machines system folders can also be retrieve, and reinstalled to your new virt install.  This all should be located in your home folder of the broken system.  Run a live session and using it, access your home folder in the broken system.

If you reinstall 18.04, everything should boot again.  I say "should" because I do not understand your partitioning layout.  Someone with a better understanding of boot repair needs to comment on that.

---

