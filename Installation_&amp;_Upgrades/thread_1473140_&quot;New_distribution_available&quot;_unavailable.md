---
title: "&quot;New distribution available&quot; unavailable"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by j3ff on 2010-05-04
Greetings,

I'd like to upgrade my 9.10 desktop to 10.04 but I can't get past step 1.  I've done alt-f2 and issued update-manager -d, but no "New distribution ..." option is presented.  

I've clicked the "check" button and updated all my repo information but that doesn't help.  

I've done a wireshark trace and observed that the update-manager's requests get through the corporate firewall, and responses come back.  Somehow it determines that no new distro is available.

I'll explore further if someone could help me out with getting hold of the relevant update-manager source code.  I reason that I can explore the code to see reasons why it would drop out, and then check for the presence of those reasons in my case.

Unless someone has the solution.

Any help would be greatly appreciated.

Thanks,
Jeff

---

### Post by arpanaut on 2010-05-04
Check that your Software Sources is set like this in release upgrade area.

---

### Post by j3ff on 2010-05-06
Thanks for the reply Arpanaut.  Unfortunately it didn't help me though.  I adjusted the dialog controls so that they conformed with those of the dialog in your screen shot.  Nothing changed however.

In the past I used the alternate install CD method to upgrade my system.  I'd prefer to use the recommended method this time.

---

