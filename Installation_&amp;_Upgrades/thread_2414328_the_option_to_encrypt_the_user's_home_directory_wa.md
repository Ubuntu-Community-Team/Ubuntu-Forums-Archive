---
title: "the option to encrypt the user's home directory was removed from the installer?"
date: 2019-03-08
forum: Installation &amp; Upgrades
---

### Post by espectro2 on 2019-03-08
I recently downloaded an iso checked the integrity of the iso by following step by step tutorial-how-to-verify-ubuntu
But during the installation came a doubt will be that my iso was corrupted because during the installation she did not offer me at any time to encrypt the personal folder or activate LVM in this version is not offered this service I must install manually?
I thought it was nice too a minimal installation option but did not have the option to enable encryption in the personal folder or activate LVM during dual boot installation because it happens?
Thanks for listening.

[https://tutorials.ubuntu.com](https://tutorials.ubuntu.com)

---

### Post by TheFu on 2019-03-08
User HOME directory encryption has been problematic for maintenance, performance, leaking of metadata, and upgrades. It may have caused a false sense of security beyond what is actually provided.  There were long discussions about removing it.

The automatic LVM+encryption setup uses the entire HDD, so dual boot installations cannot use that.  People generally are unhappy when the other OS gets wiped. There are manual methods to do it, but these are non-trivial.  Paddy wrote a guide about this. Search the forums.

---

### Post by espectro2 on 2019-03-12
Thank you for your help
false sense of security and truth.
the paddy-landau you talk about written article?
Thank you.

---

### Post by oldfred on 2019-03-12
[https://help.ubuntu.com/community/ManualFullSystemEncryption/](https://help.ubuntu.com/community/ManualFullSystemEncryption/)
Full-system encryption with manual control and dual-booting Paddy Landau
[https://ubuntuforums.org/showthread.php?t=2357627](https://ubuntuforums.org/showthread.php?t=2357627) & 
[https://ubuntuforums.org/showthread.php?t=2399092](https://ubuntuforums.org/showthread.php?t=2399092)

---

### Post by espectro2 on 2019-03-22
Thanks, I'm going to read the recommended documentation to try to understand how it works
Thanks for listening.

---

