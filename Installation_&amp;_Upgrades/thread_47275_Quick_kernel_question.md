---
title: "Quick kernel question"
date: 2005-07-08
forum: Installation &amp; Upgrades
---

### Post by MrPsycho on 2005-07-08
Does the 2.6.10-5 (386 or k7) kernel come packaged with ReiserFS support?  I get a message that says no ext3 found on root partition.

---

### Post by abhaysahai on 2005-07-08
The 386 kernel comes with reiserfs4 support, no idea about k7.
Do install reiserfsprogs and enjoy.

Abhay

---

### Post by tonym on 2005-07-08
Yes,  I'm using it fine on K7.

I suspect the message is because you have put your root partion on reiser and set the filesystem type to auto in /etc/fstab.  When it boots the kernel has to work out what the filesystem type is and seems to try ext3 first before it gets the correct one.  This leads to the message you see,  which can be ignored if everything else is working.

---

