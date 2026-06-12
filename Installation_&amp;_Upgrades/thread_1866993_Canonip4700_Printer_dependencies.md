---
title: "Canonip4700 Printer dependencies"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by notquitestr8t on 2011-10-22
As per previuos releases, the upgrade to 11.10 took out my printer. I followed the same steps as last time to force a -386 driver on my 64-bit system. However, this time the fix does not work.
The dependency package it requires (libpopt0:386) wipes out the native 64-bit libpopt0 package and I am able to print. However, other apps like Samba fail. I'm told to use NFS rather than Samba but what other things will libpopt0:386 affect? Surely after all this time, Ubuntu should be able to work with mainline printers. Is there another work-around that I am missing besides booting into Windows just to print?
Canon ip4700

---

### Post by eldkey2012 on 2011-10-25
> **notquitestr8t said:**
> As per previuos releases, the upgrade to 11.10 took out my printer. I followed the same steps as last time to force a -386 driver on my 64-bit system. However, this time the fix does not work.
The dependency package it requires (libpopt0:386) wipes out the native 64-bit libpopt0 package and I am able to print. However, other apps like Samba fail. I'm told to use NFS rather than Samba but what other things will libpopt0:386 affect? Surely after all this time, Ubuntu should be able to work with mainline printers. Is there another work-around that I am missing besides booting into Windows just to print?
Canon ip4700
No problem I bet this will work , 64 bit system ?! forget about it now [IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]

run the following commands one at a time :

[FONT=&quot]sudo add-apt-repository ppa:michael-gruz/canon

sudo apt-get update

[/FONT][FONT=&quot]apt-get install [/FONT][FONT=&quot][B]cnijfilter-ip4700series

[/B][/FONT][FONT=&quot]when you are done restart your printer and when configuration finish you shouldn't see filter problem .
Now play with your printer as much as you can!

if you are curious check this out :
[https://launchpad.net/~michael-gruz/+archive/canon]("https://launchpad.net/%7Emichael-gruz/+archive/canon")


[/FONT][B][FONT=&quot]
[/FONT][/B]

---

### Post by notquitestr8t on 2011-10-26
Thank you VERY much. After all the messing around I did, losing Samba, etc, you come along with a fix so simple to implement:D. Thank you!!!!!!

---

