---
title: "need advise, want to upgrade lucid 32 bit to 64 bit."
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by Motzilla on 2010-05-12
So I installed lucid 32bit on my laptop and love it. I have all my settings, apps, and everything just the way I like; but when I installed I only had 2GB of RAM  (hence why I didn't install the 64 bit flavor then)  

This last week I upgraded and now have a total of 5GB and would love to take advantage of it.

Would upgrading be as easy as popping in the 64 bit disc and upgrading my current install. Or will I have to go though a bunch of hoops to get my system upgraded? 

also,  once I get the system upgrade can someone tell me if my VirtualBox VM's still work in a 64 bit environment?

thx in advance.

---

### Post by jjcv on 2010-05-13
You will need to do a complete reinstall to move from 32 to 64bit.

Simplest was is to backup your /home filesystem and then restore this after the upgrade.  In that way all your customizations will be restored.

Of course if you install /home on a separate partition then you can simply add this during install without reformatting it and you are good to go.

If you have made changes to system files then also keep a backup of /etc

---

### Post by uRock on 2010-05-13
> **jjcv said:**
> You will need to do a complete reinstall to move from 32 to 64bit.
+1  The 64bit is worth it, even with just 2gigs.

---

