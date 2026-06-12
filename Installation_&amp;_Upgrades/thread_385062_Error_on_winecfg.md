---
title: "Error on winecfg"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by ascus4 on 2007-03-15
Hi all,

I installed Wine on my AMD Turion64 last night according to these instructions:

[https://help.ubuntu.com/community/WineForAMD64](https://help.ubuntu.com/community/WineForAMD64)

I got no errors during the install itself but when I ran winecfg I got the following error:
**********************************************************************
thing1@thing1-laptop:~/Desktop$ winecfg
wine: creating configuration directory '/home/thing1/.wine'...
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
wine: wineprefixcreate failed while creating '/home/thing1/.wine'.
thing1@thing1-laptop:~/Desktop$ wineserver: could not save registry branch to /home/thing1/.wine-u5K2Tz/system.reg : No such file or directory
wineserver: could not save registry branch to /home/thing1/.wine-u5K2Tz/user.reg : No such file or directory
**********************************************************************

Also note that it did not ask me for any passwords during install.  Any idea as to what this might be?  I wasn't sure if I should post this here or in the 64 user group.

Thanks in advance,

W-

---

