---
title: "Upgrade from 10.10 to 11.04 -&gt; Autologin doesn't work"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by hoover67 on 2011-05-03
Hi folks,

I recently updated the family laptop from 10.10 to 11.04, everything appears to work fine except for the auto-login which was previously configured. I've tried all options in the login manager control panel, also tried setting up ubuntu classic, but I still get a gdm login panel upon boot. 

Any ideas what could be causing this and what to look into next? 

All the best & thanks in advance, 
Uwe

---

### Post by El_Calavera on 2011-05-08
I bump this! Same problem here, tried different settings without any solution.

Maybe we should file a bug report…

---

### Post by hoover67 on 2011-05-08
Good to hear I'm not the only one experiencing the problem. 

Uwe

---

### Post by El_Calavera on 2011-05-10
I found the culprit!

In my case, it was the fact that I am using ecryptfs to keep an encrypted folder within my home directory, which seems to automatically trigger the gdm login screen now. I'm not really sure whether that's a bug or a feature…

Long story short:
After renaming (deleting would work as well) the file /home/#myusername#/.ecryptfs/auto-mount , my autologin works as it used to.
I found that workaround here: [https://help.ubuntu.com/community/EncryptedPrivateDirectory#Log%20in%20with%20the%20folder%20remaining%20encrypted](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Log%20in%20with%20the%20folder%20remaining%20encrypted)

However, one caveat:
The Access-Your-Private-Data symlink in the private folder which you would click to mount your private data does not work any more. To mount it, I have to manually run the command "ecryptfs-mount-private" now.
Not a big problem, but slightly annoying. Maybe someone knows a fix for that, too?

---

### Post by hoover67 on 2011-05-11
Hm, I'm not using cryptfs so I guess that's not the problem on my end. 

cheers, Uwe

---

