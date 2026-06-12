---
title: "How to submit a bug report"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by daniel.cotter on 2011-05-03
I have tried twice (yesterday and today) to upgrade my 10.10 version to 11.04, simply using the button provided by the upgrade manager.

Both times, it has halted, saying it could not calculate the changes, and gives possible reasons, but it also suggests submitting a bug report against update-manager.

Log files were generated in /var/log/dist-upgrade, which should be included with the bug report, but how to submit one is my question.

Thanks in advance,
Daniel

---

### Post by Cheesehead on 2011-05-03
Uh, no.

Only submit a bug report at launchpad.net **if you really have a bug**.
You don't know that yet. What you have right now is a need for support.
This forum is your support.

Usually, you get that error if you have added packages from PPAs and/or other third-party repos. Look through the your log until you find the problem it is choking on.

If the problem is due to a PPA package you added, remove it and then try upgrading again. After the upgrade is complete, add the new version of that package back to your system.

If the problem is not due to a PPA package you added, or you cannot figure out what the error means, or you cannot locate the error, then paste a link to your log here. (The pastebin at [http://paste.ubuntu.com](http://paste.ubuntu.com) is your friend)

---

### Post by daniel.cotter on 2011-05-04
Much obliged for the advice.

I did a cursory study of the log files, but i will search them again.  The error message suggested a bug report, which is why i thought to submit one.  I do have some proprietary packages  (what does PPA stand for?), so I will investigate further.

Thanks

---

### Post by daniel.cotter on 2011-05-04
> **daniel.cotter said:**
>   (what does PPA stand for?)

Does it mean that I have added an additional repository to sources.list?

---

### Post by Frogs Hair on 2011-05-04
In a word , yes . A Personal Package Archive is usually software that is developed or modified to meet the needs of a of a user or group of users and often requires additional packages .

---

### Post by mörgæs on 2011-05-04
You can (unfortunately) only expect an online upgrade to go well, if you have a completely vanilla system: No PPA's added, no closed-source drivers for the screen card and wireless card and so on.

---

### Post by daniel.cotter on 2011-05-05
> **mörgæs said:**
> You can (unfortunately) only expect an online upgrade to go well, if you have a completely vanilla system: No PPA's added, no closed-source drivers for the screen card and wireless card and so on.

So, if I want to upgrade to Natty, I can do a manual install?  Won't it still hang up when it discovers whatever PPAs I have?

---

### Post by Cheesehead on 2011-05-05
You're wandering off on tangents that will waste lots of your time. 

1) Since you haven't posted those /var/log/dist-upgrade logs, we still *don't know* what your problem is. **Those logs are important**. Please post them so we can help you.

Your system uses those logs to tell you exactly what the problem is.
Not using that information is choosing to grope blindly.

2) If (and we **don't** know this yet) you added a package from some third party repository or PPA, all you need to do is uninstall it. You still haven't told us if you added such a PPA or repo, or if you added such a package, or which package.

---

### Post by mörgæs on 2011-05-06
> **daniel.cotter said:**
> So, if I want to upgrade to Natty, I can do a manual install?  Won't it still hang up when it discovers whatever PPAs I have?


As Cheesehead (great name :-) ) writes, the logs are important, IF you want to find out why the upgrade failed. 

However, you can also simply back up your user files and install a new 11.04, wiping the old installation in the process. That is what I prefer myself.

After everything is tested and confirmed in the new installation, you can add PPA's, if you really need them.

---

### Post by daniel.cotter on 2011-05-06
If you are willing to look through them, here they are. [Never mind, they are gone.  Might have been wiped out by the successful update]

I hesitated to attach them right off the bat, not wanting to seem pushy.  I apologize for not giving you everything you needed to help me with.

I will tell you that I downloaded a Live CD, and have upgraded to 11.04, but only after screwing things up pretty badly when I used apt-get to update and upgrade.  I lost all keyboard function, and the workaround was a bear.  But I have a functional distro, and am investigating how everything looks. 

Thanks for your interest in helping out.

Daniel

---

