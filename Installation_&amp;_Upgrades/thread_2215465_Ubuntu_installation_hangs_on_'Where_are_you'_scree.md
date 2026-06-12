---
title: "Ubuntu installation hangs on 'Where are you?' screen"
date: 2014-04-06
forum: Installation &amp; Upgrades
---

### Post by wilbomc on 2014-04-06
Hi. 
Currently having issues re installing Ubuntu (in a (UEFI) dual boot with Windows 7 pro 64-bit) and have found no information on the forums/internet that has solved the issue.

The issue is that when installing Ubuntu, it hangs at the "Where are you?" location screen for well over an hour before I give up. I have burned new ISO images at slow speeds and used the previous ISO image when I first installed Ubuntu, reformatted my entire hard drive, disconnected from the network and tested RAM by using the memory modules I previously used (as I have new modules).

I have partitioned my 3TB drive in Windows 7 freeing up 215GB of unallocated space for Ubuntu in which I use most of it for the "/" root and around 10GB for SWAP.

If anyone has experienced this or has found a solution I would appreciate any kind of help.
Regards.

---

### Post by ubfan1 on 2014-04-06
Did you hashcheck the downloaded iso file with md5sum?  That should always be done before doing anything else with the iso.

---

### Post by wilbomc on 2014-04-07
Just checked it there. The check sums are the same. I am starting to run out of options.

---

### Post by mastablasta on 2014-04-07
what kind of partitions do you have? gpt? any other info on the system you can provide? does it work in live session? if yes run boot info script found in boot repair tool. it's hard to say from information you provided what hangs the installer.

also why do you need 10 GB swap space?

also uefi install: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

you may need /efi partition ...

---

