---
title: "Changed the name of the partition on windows now nothing works"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by ygorgeyer on 2011-04-29
hello from a N00b

as the title says I have done the stupid mistake of changing the name of two partitions (the main for the W7 and another just for documents), I did not change the name of the Ubuntu 11 partition.

I used the Computer Management from windows to do the changing.

Now nothing works, it does not find the Grub to initiate or a not even gives me the menu to choose the windows.

When you change the name does it change the drive letter?  Couldnt understand why this happen.

Appreciate any help!

---

### Post by jgcobra on 2011-04-29
Hi

Follow the instructions at this link for recovering using the live cd.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

(edit - btw, this will just reinstall grub, not the whole operating system)

Regards
G

---

### Post by ygorgeyer on 2011-04-29
unfortunately none of the methods for the grub2 that would apply from the link worked for me.  I am trying to reinstall ubuntu on the same partition and really hope it will redo the grub.

I didnt have so much on the ubuntu partition yet, UFFF :)

comeback to say if it worked


EDIT:

It doesnt work, keeps saying it was not possible to install the booloader at the specific location, ask me to find another place but none of them works

---

### Post by ygorgeyer on 2011-04-29
now after reinstaling ubuntu i can see the menu again, with some new ubuntu options including the windows 7

One of the ubuntu options works but the windows didnt.

I tried using sudo update-grub2   but the windows 7 still not working


How to fix it?  read the link but couldnt find not specific for this

---

