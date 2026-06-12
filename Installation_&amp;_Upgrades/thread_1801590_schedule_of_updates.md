---
title: "schedule of updates"
date: 2011-07-10
forum: Installation &amp; Upgrades
---

### Post by jerrydc on 2011-07-10
I have Ubuntu 10.04 LTS.  I notice that Ubuntu, Firefox. Thunderbird and other apps have later versions than I do.  However, Update Manager tells me that I have the latest version of all the apps I am interested in, even when I click on Check.  Does an LTS (Long-Term Support) version of Ubuntu block all updates of the apps I've mentioned until another LTS version of Ubuntu is released?  How often are such releases posted?  Is it a good idea for a beginner like me to use only LTS versions?  I think I know how to switch to Normal updates, which I believe come more often than LTS updates, if that is thought to be safe.

I am given notice of recommended and security updates every several weeks or so of various other apps that I do not understand but I always install them.

---

### Post by Toz on 2011-07-10
When a version of ubuntu is released, the package versions generally remain the same for that release even though new versions of the software package may be available. To get the later versions, you need to enable the backports repository. See this link for more information: [https://help.ubuntu.com/community/UbuntuBackports]("https://help.ubuntu.com/community/UbuntuBackports")

---

### Post by lovinglinux on 2011-07-11
> **jerrydc said:**
> I have Ubuntu 10.04 LTS.  I notice that Ubuntu, Firefox. Thunderbird and other apps have later versions than I do.  However, Update Manager tells me that I have the latest version of all the apps I am interested in, even when I click on Check.  Does an LTS (Long-Term Support) version of Ubuntu block all updates of the apps I've mentioned until another LTS version of Ubuntu is released?  How often are such releases posted?  Is it a good idea for a beginner like me to use only LTS versions?  I think I know how to switch to Normal updates, which I believe come more often than LTS updates, if that is thought to be safe.

I am given notice of recommended and security updates every several weeks or so of various other apps that I do not understand but I always install them.

Any version of Ubuntu normally only updates it's applications with security and stability patches. It doesn't matter if it is LTS or not. For example, you have Firefox 3.6.18 and will get updates to 3.6.19 and so on, not Firefox 5 or 6.

The advantage of the LTS is that you don't need to upgrade the entire system so often and it is more stable than a fresh Ubuntu version. But if you want to get the latest releases of your favourite applications, you need to upgrade to the most recent version of Ubuntu or use a different repository.

The backports suggested in the previous post can do that. However, I prefer to add a specific ppa repository, that updates only the applications I want. For instance, you can get instructions on how to upgrade Firefox to version 5 at the [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247").

Although that thread doesn't explain how to add a ppa repository for Thunderbird, the team who distribute the ppa also make them for Thunderbird, so you just need to replace *firefox* with *thunderbird* in the commands.

---

### Post by mpiter on 2011-07-11
> **lovinglinux said:**
> Any version of Ubuntu normally only updates it's applications with security and stability patches. It doesn't matter if it is LTS or not. For example, you have Firefox 3.6.18 and will get updates to 3.6.19 and so on, not Firefox 5 or 6.

Does this rule apply to the kernel, i.e., to the hardware drivers?

---

### Post by lovinglinux on 2011-07-11
> **mpiter said:**
> Does this rule apply to the kernel, i.e., to the hardware drivers?

I guess so.

---

### Post by jerrydc on 2011-07-15
Thanks to all of you.  I haven't had a chance to study the Backports page yet.  I just wanted you to know I appreciate the replies and I'll get back if I have any questions.

---

### Post by azertyh on 2011-07-16
> **Toz said:**
> When a version of ubuntu is released, the package versions generally remain the same for that release even though new versions of the software package may be available. To get the later versions, you need to enable the backports repository. See this link for more information: [https://help.ubuntu.com/community/UbuntuBackports]("https://help.ubuntu.com/community/UbuntuBackports")

very intersting. if i understand well, it's like a system upgrade but only for the programs (and not the system).

---

### Post by jerrydc on 2011-07-23
Sorry, but I'm still somewhat confused.  Are the reply posts saying that Firefox, Thunderbird and all other apps are not fully updated until Ubuntu is fully updated.  I think I don't have the terminology right and may not be making myself clear. 

Try again -- FF, TB, do not go to a new version until Ubuntu goes to a new version.  I will not get the choice of updating to version 4 or 5 (whichever is now considered safe) of FF or TB until Ubuntu is updated to Magnificent Milly, or Naughty Nanny (or whatever it is called).  Am I correct?

---

### Post by lovinglinux on 2011-07-23
> **jerrydc said:**
> Sorry, but I'm still somewhat confused.  Are the reply posts saying that Firefox, Thunderbird and all other apps are not fully updated until Ubuntu is fully updated.  I think I don't have the terminology right and may not be making myself clear. 

Try again -- FF, TB, do not go to a new version until Ubuntu goes to a new version.  I will not get the choice of updating to version 4 or 5 (whichever is now considered safe) of FF or TB until Ubyntu is updated to Magnificent Milly, or Naughty Nanny (or whatevcer it is called).  Am I correct?

No matter which version of Ubuntu you have, as long as it is still supported, you get security and stability updates for Firefox, Thunderbird and all other applications. What you don't get until a new version of Ubuntu is released is the versions that include more than security and stability patches, like FF 4 or 5.

Firefox 3.6 won't be updated to Firefox 5 - 6 - 7 or 8, as long as Mozilla supports it with security and stability patches. Meanwhile, you get updates to 3.6.19 to 3.6.20 and so on. Once Mozilla, stops providing support for Firefox 3.6, which will be soon, then you will get Firefox 5 - 6 - 7 or 8, whichever is the stable version when that happens.

If you want Firefox 5 right now, see [Firefox 4, 5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247").

---

### Post by jerrydc on 2011-07-25
Thank you.  Exactly what I wanted to know.  I'll report problem solved ss soon as I can find out how to do that.

---

### Post by lovinglinux on 2011-07-26
> **jerrydc said:**
> Thank you.  Exactly what I wanted to know.  I'll report problem solved ss soon as I can find out how to do that.

You are welcome.

Click Thread Tools at the top of the thread.

---

