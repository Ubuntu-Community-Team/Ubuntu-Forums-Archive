---
title: "PPAs, alternate repos and sources.list"
date: 2014-05-05
forum: Installation &amp; Upgrades
---

### Post by Luxx on 2014-05-05
Just a little confused on updating apt files after upgrade to 14.04. It seems all my PPAs and alternate repos have been completely removed from sources.list and moved into the sources.list.d folder as separate files. My usual routine after an upgrade was to go into sources.list and uncomment stuff, but since it isn't set up that way any more I'm a little baffled about how to re-enable all the extra stuff I was using before the upgrade. Can any body shed some light? Much appreciated.

BTW, I think it's worth mentioning that this is the FIRST time an upgrade has gone absolutely smoothly. 
[CENTER]**[SIZE=5]Way to go Ubuntu![/SIZE]**[/CENTER]
No display issues (even with APU graphics), missing or malfunctioning desktop, misbehaving folders, inappropriately hidden/lost/locked files, permissions issues, locked out USB devices, etc. It all works!

I suspect much of the PPA stuff I downloaded to make things work in 13.10 won't even be neccessary now. This is looking very positive.

---

### Post by bapoumba on 2014-05-05
You can have a look at the files in the /etc/apt/sources.list.d
The syntax is the same as for the sources.list file, and a # at the beginning of the line comments it out.
Or you can have a look at Software Sources.

Now before you enable them again, make sure the third party repos and ppa have a Trusty repo and make sure to point to it.
If they are not commented out, please disable them. Mixing up regular repos with outdated ppa from another release is a bad idea.

---

