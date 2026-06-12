---
title: "More installation headaches please help!"
date: 2007-08-15
forum: Installation &amp; Upgrades
---

### Post by turismos on 2007-08-15
When trying to install from the alternate disks I get a HUGE error. Let me say before hand i checked the CD intergrity and it said the disk was valid. When starting to install the base system at 6% it starts to say

[B]Debootstrap error
File:///cdrom/pool/main/d/dpkg/dpkg-1.13.24ubuntu6-I386.deb
was corrupt[/B]

Pretty much this error goes off for every file on the CD i hold enter for a good minute till it sends me to a menu. Please help me This is getting really annoying

Thanks!

---

### Post by Wim Sturkenboom on 2007-08-15
If you burned yourself, burn it again (at lowest possible speed). The integrety check should have picked it up (as far as I know) but one never knows.

---

### Post by tnc on 2007-08-16
Just to put in my .02 cents worth here....this is coming from a total newbie to Ubuntu so take it for what it is worth....   

We had the indentical error when we installed on an older box recently.  We eventually figured out that we had not formatted properly in the partition segment of the install.   The installer was trying to write to a section of disk that was not formatted and therefore had an existing file system.  

Might be worth double checking that part in your install?
Good luck.
Tim

---

