---
title: "Upgrade Server with fresh install but keep accounts"
date: 2011-11-19
forum: Installation &amp; Upgrades
---

### Post by Jimgary on 2011-11-19
Time has flown and it's time to upgrade my Edubuntu server. I don't know if I should worry about the LTSP aspect or not. At this point, I just want to keep the accounts I've been using for 3 years. I'll be doing a fresh install on new array. 
Here's the question:
Can I just copy the /home directory and:
/etc/passwd
/etc/shadow
/etc/group
/etc/gshadow
from the "old" drive into the new file structure after a clean install?
Do I need to worry about the new system accounts vs the old ones?

---

### Post by raja.genupula on 2011-11-19
If you upgrade Ubuntu it will just upgrade the Ubuntu system and its not going to touch the Users Accounts and extra personal stuff . But taking a Backup is also a good idea . because sometimes upgrades may be failed at that time we will be in trouble .

So bottom line is Upgrade will not touch any of your personal information , but taking backup of them is a good idea .

---

### Post by Jimgary on 2011-11-19
Thanks, I'll be doing a fresh install, though.

---

### Post by Jimgary on 2011-11-20
Also wondering about Hardware Raid cards.

---

### Post by MAFoElffen on 2011-11-20
> **Jimgary said:**
> Also wondering about Hardware Raid cards.
As long as your set up and format the raid in the hardware RAID BIOS (talking about mainstream traditional server hardware RAID), then the Server Edition ISO should see it okay. Since you already had server on it, I don't see a problem there.

---

