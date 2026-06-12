---
title: "Number of Packages to upgrade?"
date: 2021-04-24
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2021-04-24
I've noticed recently that the number of packages to be upgraded varies depending the way is is reported. Today I logged in to one of my computers and in the login it said I has 33 packages to upgrade. I ran [FONT=Courier New]#apt update [/FONT]and it said I had 31 packages to upgrade. Then I ran [FONT=Courier New]#apt upgrade[/FONT] and it said I had 31 packages to upgrade and 5 new packages.

---

### Post by scorp123 on 2021-04-25
> **rsteinmetz70112 said:**
>  Today I logged in to on of my computers and in the login it said I has 33 packages to upgrade.

That number tends not to be accurate depending on how recently the automatic system responsible for that message was able to fetch the number of packages that need to be updated.


> **rsteinmetz70112 said:**
>  I ran #apt update and it said I had 31 packages to upgrade 

That's the better method and usually should be very accurate.

---

### Post by rsteinmetz70112 on 2021-04-25
I would generally expect the number of packages to be upgraded to go up, not down, as new updates are loaded into the repositories.

---

### Post by Impavidus on 2021-04-25
I guess it has to do with phased updates. I read somewhere that starting on 21.04 that also applies to apt, instead of just the upgrade manager. There must be a way to opt out or force a particular upgrade, if you urgently need it.
[https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

---

### Post by deadflowr on 2021-04-25
> I read somewhere that starting on 21.04 that also applies to apt, instead of just the upgrade manager. 
[https://discourse.ubuntu.com/t/phased-updates-in-apt-in-21-04/20345]("https://discourse.ubuntu.com/t/phased-updates-in-apt-in-21-04/20345")
Edit: this is mentioned in the release notes for 21.04, too.

Edit2:
The discrepancies probably has to do with when the last apt check was ran, and whether or not unattended-upgrades is running.
unattended-upgrades defaults to installing any security updates but not non-security updates unless the system has been set to do so.
So those the drop from 33 to 31 may have been security related.

---

### Post by mikewhatever on 2021-04-25
You <apt list --upgradable> to check if anything is left behind.

---

