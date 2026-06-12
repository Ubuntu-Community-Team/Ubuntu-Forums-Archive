---
title: "Installing older version of Firefox then came in the system new."
date: 2014-07-06
forum: Installation &amp; Upgrades
---

### Post by casawyer on 2014-07-06
I just reinstalled 14.04 and it has Firefox 31 installed, but the addon's I like to use don't work with it but do with Firefox 28.  How do I install and change firefox from 31 to 28.  I have downloaded the 28 but can't seem to get it to replace 31.  Any help would be appreciated,

---

### Post by Dennis N on 2014-07-07
You don't need to replace 31, both versions can coexist together. The keys to making this work are to use a separate profile and folder location for each. FF 31 can be left as it is, but the other needs to have a new profile created before it's first use, and then run with the options:
 
**[FONT=Courier New]-P profile_name  -no-remote[/FONT]** 

profile_name would be replaced by your chosen profile name. You would create a separate launcher to launch it with these options.

It is usually suggested in guides to put the second Firefox folder inside the /opt folder.

---

### Post by monkeybrain20122 on 2014-07-07
My system is fully up to date and it has Firefox 30, I went to Mozilla and it said "congratulations, you are using the latest Firefox. " How did you get Firefox 31?

---

