---
title: "Why do updates break things?"
date: 2013-01-17
forum: Installation &amp; Upgrades
---

### Post by lferg on 2013-01-17
Why is it that updates seem to break the simplest things?  I just did a fresh install of 12.4, everything worked great then did the up date and my Wifi is broken.  I did an install of 12.10, updated and Wifi and USB breaks.  I found 12.10 to be a bit buggy for me so that's why I went to 12.04. It just seems like if updates make things not work then how do I know when it is safe for me to update?

---

### Post by raja.genupula on 2013-01-17
I think you have enabled the option in Ubuntu software sources that about pre-released updates.

If you are facing the problem still after disabling the option also , then you have to report it to launchpad as a Bug.

Now see at the image and unselect the option of pre-released updates which is supposed to be off for people who dont want to receive the updates which are not stable.

---

### Post by lferg on 2013-01-17
Oooh Ok makes since.  I'll make that correction.  Thanks I probably would have always over looked that.

---

### Post by tgalati4 on 2013-01-17
The Linux Mint update manager uses a 5-level, color-code scheme to alert users to potential breakage.  Xorg and kernel updates get Red, Level 5, which means updating those may cause breakage.  Level 1, 2, and 3 are generally safe, and only affect the applications that are being updated, not hardware/system performance.

Of course in preferences, you can choose the levels to be visible during update notifications.

As a general rule, if your hardware is working and your system is running the way you like, avoid kernel and graphics updates, unless you plan the time it takes to repair things (like wireless, printers, and proprietary graphics modules) after such updates.

---

### Post by lferg on 2013-01-17
So pretty much a good rule of thumb for a "noob" would be to just do security updates until they get comfort with Linux?

---

### Post by estelleangelinas on 2013-01-17
Hi,  
I had the same problem when I updated. Thanks for the information.

---

### Post by coffeecat on 2013-01-17
> **lferg said:**
> So pretty much a good rule of thumb for a "noob" would be to just do security updates until they get comfort with Linux?

No. You should be fine with both security and recommended updates. The problem repository that raja.genupula mentioned is the "proposed" one. It is not intended for routine use by inexperienced users. The proposed repository is there for experienced users to test proposed updates. It's there for quality assurance of updates before they are put out for general release. The hint is in the word "proposed". :wink: Unless you are experienced, willing to help with testing and able to repair adversely affected systems, don't use it.

---

### Post by raja.genupula on 2013-01-18
@coffeecat Thanks for more clear words.

@OP I hope know you understand them.

---

### Post by lferg on 2013-01-18
Yep, made the changes in my update options. Thanks to all:D

---

