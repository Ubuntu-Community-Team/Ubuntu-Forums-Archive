---
title: "Update Manager Disbaled"
date: 2011-07-07
forum: Installation &amp; Upgrades
---

### Post by Sofatiger511 on 2011-07-07
I upgraded Ubuntu 11.04 x86 to Ubuntu 11.10 x86 via system upgrade. Everything was working fine.
The setup is dual boot with Windows 7 Ultimate inan old Dell Inspiron 600M. 

One day when I signed into Ubuntu, following error message showed up when I try to check for update.

[B]"Could not initialize package information.

An unresolvable problem occurred while initializing package information. Please report this bug against Update Manager package and include the following error message:

'E:Encountered a section with no package header,
'E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_Ubuntu_list-natty-main_binary_i386_packages, E:The package lists or status file could not be parsed or opened.'

[/B]ANy help to guide me solve this problem will be highly appreciated. I am new to Ubuntu.

---

### Post by Rubi1200 on 2011-07-07
Hi and welcome to the forums :-)

Open a terminal with Ctrl+Alt+T and run the following commands:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

```

---

### Post by Sofatiger511 on 2011-07-07
Hi @ Rubi1200

Thank you very much for your reply and your help. I executed the commands you provided and it read and updated 36 packages total 14.5 MB file size. The "DO NOT ENTRY" sign disappeared from the top right bar. I believed that means the problem is solved. Hopefully, it does not throw me another curved ball. 

Once again, thanks for your help.

---

### Post by Rubi1200 on 2011-07-08
No problem, you are more than welcome :-)

If you run into difficulties again, let us know and we will try and help you.

If this problem is resolved please mark this thread Solved using the Thread Tolls near the top of the page.

---

