---
title: "Fresh install won't upgrade from 14 to 16"
date: 2017-08-11
forum: Installation &amp; Upgrades
---

### Post by Vaclav Vasek on 2017-08-11
I needed to change to 64 bit OS so I did fresh install of  version 14. 
I followed the " wanna update " AND it worked. 
I followed the " wanna UPGRADE to 16"  and it quit somewhere half way thru. 
After reboot - nothing intelligent worked , not even REMOVING the 64 bit OS HDD and trying to boot to the original 32 bit OS. 
Tried several times with same frustrating results. 
Ended up with new 64  bits OS running  version 14 and NO way to boot to the original 32 bits with only its HDD connected. 

Can I get answer for these and only these please?

Why I cannot upgrade from 14 to 16 using 14 GUI ?
Would using dist_upgrade be safer or work?
How did I loose access to original 32 bit HDD which was NEVER connected during 64 bits OS install?
The hardware is x86 and worked just peachy with  32 bits  Ubuntu 16

---

### Post by QIII on 2017-08-11
dist-upgrade does not upgrade to a newer release.  It updates the current release and all of its files by attempting to be "intelligent" about what is upgraded.

I am not surprised at all that an upgrade that failed part way through will now not work.  It is just such things that cause many to avoid "upgrade" and reinstall cleanly.  Unfortunately, we don't know why the upgrade failed, so it is impossible to tell you what might be broken.  But if you could give us a clue as to what you mean by "nothing intelligent worked", we might be able to help.

Would you please give us the specifications of your machine?

---

