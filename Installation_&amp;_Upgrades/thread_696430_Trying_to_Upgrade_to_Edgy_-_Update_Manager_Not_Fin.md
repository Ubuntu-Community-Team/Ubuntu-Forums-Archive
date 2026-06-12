---
title: "Trying to Upgrade to Edgy - Update Manager Not Finding Upgrade"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by Avenue on 2008-02-14
Hello Everyone, 

I'm a "sometimes" Ubuntu user who is trying to learn more but am very new to Linux in general.  I'm still running Dapper and trying to upgrade to Edgy so that I may get to the latest release of Ubuntu.  

Here's the problem i'm having:

I'm following the upgrade notes exactly - opened the terminal and ran the following command:
[INDENT]gksu "update-manager -c"[/INDENT]

While this DOES work to get general updates, the upgrade notification for Edgy never comes up.  I'm wondering how do I get this upgrade to show up so that I may move forward.  

Would anyone be able to assist me?  

Please keep in mind, i'm a newbie here so if there are additional commands or code, please be gentle.  

My apologies for being a hassle, but I really do appreciate the assistance. 

Thanks!!!

Ave

---

### Post by Partyboi2 on 2008-02-14
Try [this ]("http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html")but use method 2

---

### Post by Rocket2DMn on 2008-02-14
Edgy is not the latest, Gutsy is (7.10).  In fact, Edgy isn't going to be supported anymore after Hardy is released in April.  Since you can't upgrade straight from Dapper to Gutsy, you would have to do a reinstall since going Dapper->Edgy->Feisty->Gutsy in that order to get up to date, but that chances of successfully upgrading that far aren't too good w/out breaking a lot of things.  I would suggest holding out until Hardy Heron is release in April, then doing a fresh install at that time.  Hardy is an LTS release like Dapper so you would have 3 years of support on it.

---

### Post by PmDematagoda on 2008-02-14
If you are willing to take a risk, you can attempt a direct upgrade from Dapper to Hardy by following this [guide]("https://wiki.ubuntu.com/LTSUpgradesHowto"). But keep in mind that this has not been heavily tested and could lead to a disaster, so **backup** all your data and files before doing the upgrade and also make sure that you have a Ubuntu Live CD close-by.

---

