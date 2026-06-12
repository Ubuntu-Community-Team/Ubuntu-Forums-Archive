---
title: "Upgrade to 10.04"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by kozhi on 2010-06-27
I upgraded from 9.04 to 9.10 and a few weeks back to 10.04 on my desktop. Everything is fine, no problems, except that visually, there doesn't appear to be any change. I say this because I did a fresh install of 10.04 on my laptop. There, the panels, Firefox buttons and Open office buttons (the ones that we use to close the windows, or resize them) are different and visually more appealing. However, on my desktop, after the upgrade, at my login, the 9.04 appearance is retained, while in another account (non administrator), the 9.10 appearance is retained. What might have happened during the upgrades? Thanks.

---

### Post by ajgreeny on 2010-06-27
Does the machine which stayed the same have a separate /home partition, and therefore kept the old ~/.gconf, ~/.config, etc etc.  This could mean that the visuals are exactly the same as before as most of that configuration is contained in those hidden folders.

Otherwise, I can't think why it should be different on the two machines.

---

### Post by kozhi on 2010-06-27
> **ajgreeny said:**
> Does the machine which stayed the same have a separate /home partition..

I checked this for the machine that did not change. There appears to be one /home partition and under this there are two users. I have attached a screen-shot for reference. Both have /.config and /.gconfig under them. However, under the non-administrator, only the /.gconfig is crossed out. Thus, we have /home/administrator/.config and /home/administrator/.gconfig for the administrator and  /home/non-administrator/.config and /home/non-administrator/.gconfig for the other login.

If this helps in understanding the problem, please let me know. However, please also note that the interfaces are not only different, but also none are that of 10.04. Thanks.

---

### Post by kozhi on 2010-10-19
Why is it that I am stuck with 9.04 icons and themes even after upgrading to 10.10? Why don't the icons, windows color schemes also change with the upgrades? Where should I look and what files should I update?

---

