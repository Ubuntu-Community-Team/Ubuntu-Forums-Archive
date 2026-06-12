---
title: "Samba Configuration Problem"
date: 2015-03-13
forum: Installation &amp; Upgrades
---

### Post by CrAzY12 on 2015-03-13
I am setting up my first samba server! and the document from [Ubuntu]("https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way!") is great but I received a few errors once I ran [I]testparm
[/I]Please see Attachment 1: Samba Errors and Attachment 2: Host Allow (from the smb.conf file) 

Now the errors are very straight forward and as I looked closer into my smb.conf file, I can not see the mistake I made in editing my *host allow & host deny config line (Attchment 2: host allow).* I would think this would be a simple solution but I am still learning.

---

### Post by mikewhatever on 2015-03-13
Apparently, it should be **hosts** and not host.

---

