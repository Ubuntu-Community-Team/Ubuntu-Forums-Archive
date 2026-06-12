---
title: "Accidentally Stopped 10.04-10.10 Upgrade"
date: 2011-09-06
forum: Installation &amp; Upgrades
---

### Post by dedukes on 2011-09-06
Hi. 

I was upgrading from 10.04 to 10.10 when I shut the terminal by mistake.  

I had started the upgrade by launching the Update Manager through the terminal with the following command: update-manager -d

I had already downloaded the packages and was about 30% through the installation when I shut the terminal.  Now my system is hobbled.  Some programs work, others give me "corrupted" messages.  Is there an easy way to simply resume or undo the half-baked install?

If not, what's the best plan of action?

Thanks for you help.

--dd

---

### Post by mörgæs on 2011-09-07
I would go for backup and reinstall. Trying to save such a system takes a lot of time, and the result is unlikely to be as good as the new install.

---

### Post by Grenage on 2011-09-07
> **mörgæs said:**
> I would go for backup and reinstall. Trying to save such a system takes a lot of time, and the result is unlikely to be as good as the new install.

I'd have to agree with that.  You might well be able to get the system up and running just fine, but I imagine it's going to take a hell of a lot longer than a fresh install (and then some).

---

### Post by TBABill on 2011-09-07
+1
 
You won't know if a single borked file still lingers till you hit the odd application you rarely use that may have a dramatic impact on stability once it runs and interfaces with the system. I'd copy all your /home stuff and reinstall 10.10 directly. Just a reminder...10.10 only has another 7 months of support where 10.04 has 19 more months.

---

### Post by dedukes on 2011-09-07
Thanks, folks.  That's basically what I did.  I backed up all my Home data then did a fresh install of 11.04, which was the goal in the first place.  I appreciate your help.

---

