---
title: "Upgrades impact on non /home items"
date: 2014-08-12
forum: Installation &amp; Upgrades
---

### Post by ndstate on 2014-08-12
Hello,

I am running 12.10 and want to upgrade to 14.04. It looks like my best option is to do a clean install. I have a separate /home partition which should be safe on a fresh install, correct?

I am concerned about all of the other things I have set-up. fstab edits, ssh keys, auto server login via terminal, saved passwords in 'passwords and keys', shotwell/rhythm box databases, etc. etc. Is there a good way to know which of these items may be impacted on upgrade? I am sure there are many others, but I have been using this so long I cannot remember everything that was set-up.

Thanks!

---

### Post by grahammechanical on 2014-08-12
And where is most of that stuff stored? In the users /home folder, which is on a separate /home partition? I doubt if fstab edits are stored in /home but much of the other stuff will surely be stored there. What do you think? Be nosey and see what is in /home.

Once you get to 14.04, stay there. Do not upgrade to 14.10. It only has 9 months support. You will soon end up back where you started from. A modified OS that you do not want to modify twice and no option but to upgrade or re-install.

Regards.

---

