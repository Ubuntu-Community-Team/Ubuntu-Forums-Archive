---
title: "[SOLVED] Grub error 22"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by megablaise on 2008-05-29
Hi All,

I can't start none of the operating systems on my PC. I have windows xp and Ubuntu 8.04

Everything was fine until this morning my 18 months old son was playing with the power button. :(

Now:
If I choose windows I get the following error message: missing NTLDR files.
If I choose Ubuntu I get the following error message: error 22 press any key to continue... after "press any key": no such partition.

I get exactly the same problem when I first installed Ubuntu, but after I've reinstalled the problem was solved. Now the reinstallation didn't help.
Please help!

---

### Post by megablaise on 2008-05-29
Hi All,

I found the problem. :)
I have two hard disc drives. One is only for storage, on the other one I have Windows XP an Ubuntu 8.04 installed.
The problem was that I choosed as first boot device the hard disc which contains the operating systems. After I’ve set up as first boot device the other hard disc, everything is working fine.
I expected (hd0) to be on the hard disc where the operating systems are.

---

