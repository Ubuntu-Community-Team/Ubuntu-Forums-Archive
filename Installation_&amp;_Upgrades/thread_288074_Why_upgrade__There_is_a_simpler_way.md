---
title: "Why upgrade?  There is a simpler way"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by jsonder on 2006-10-29
I've installed 6.10 with minor hassles (getting dvds showing movies on the intel-chip based machines).

The secret?  I set up /home as a separate partition (usually non-bootable) and just edit it as needed (to keep it as "/home" and to prevent it being formatted) in the manual partitioning and do a fresh install.

This greatly minimizes the stuff that you've got to do.  Your old home partition is there, with your **individual user** browsers, mail programs, etc. and their ancillary files.

I've done this with a G4 (mac mini), core duo (dell notebook), and P4 (HP desktop) with only a few things to "fix/patch" because I use a lot of kde tools/games under gnome. 

Consequently, "upgrades" are **ALWAYS** a fresh install for me.

---

### Post by phersotty on 2006-10-29
Its also a good idea to create a stable working partition and a unstable experimental partition.  Use the unstable to test the changes.  If it remains stable then go ahead and make the same changes to the stable partition.  This way you can play with the bleeding edge stuff without compromising your stable system.

---

### Post by meng on 2006-10-29
I agree, separate home and fresh install. I have had one upgrade (from Breezy to Dapper) go fairly well, but even then it required reconfiguring the X-server to get my DE back.

---

### Post by jsonder on 2006-10-29
I've run 6.06 and knot 3 using the same home partition and the same user name.

When I dumped 6.06 and stuffed FC6 on (briefly) I had to use a different user name because RedHat defines the 1st user as 500 and Ubuntu defines the 1st user as 1000.

How to set up multiple linux installs was handled by lha on 8 Jan 2006; search for it if you need it.

Also, "sudo passwd root" is one of the 1st things that happens with a new installation of Ubuntu.  :D

---

### Post by nbx909 on 2006-10-29
good idea, i ussually just tar up and upload my home dir to another machine then after the install i untar and replace.

---

### Post by thomax on 2006-10-29
Thats the best way to do it, I've allways done it that way, it's the mosot easy way.

---

