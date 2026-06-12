---
title: "First time doing an upgrade"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by led_scorched on 2007-05-22
...when you upgrade...what all will it save?  do i need to back up all my documents and bookmarks, and reload them... or is that sort of thing normally left unscathed?

---

### Post by led_scorched on 2007-05-22
bump?

---

### Post by ubuntu27 on 2007-05-22
Hello. What kind of upgrade are you talking about? You mean upgrading Ubuntu Version, like from Ubuntu 6.06 (Dapper Drake) to Ubuntu 6.10 (Edgy Eft)    or from Ubuntu 6.10 (Edgy Eft) to Ubuntu 7.04 (Feisty Fawn)?

Or are you talking about an regular SOFTWARE update?

If it is a software update, then, you don't need to backup anything. 

If you are upgrading Ubuntu, then there could be problems. So better do a backup. Do an upgrade with the official way, using the Update Manager)

---

### Post by jfinkels on 2007-05-22
> **led_scorched said:**
> ...when you upgrade...what all will it save?  do i need to back up all my documents and bookmarks, and reload them... or is that sort of thing normally left unscathed?

You should always back up your personal data, especially when you are performing some sort of system upgrade or installation. However, you will most likely have no problems with data loss if you upgrade using the update manager.

If you want to update (e.g. from Ubuntu 6.10 Edgy Eft to Ubuntu 7.04 Feisty Fawn), type the following in the terminal:
```

gksudo "update-manager -c"

```

What happens is only this: all relevant upgradeable software packages will be downloaded and installed. Basically, the update manager is just downloading and installing a bunch of upgrades for a large number of programs on your computer.

---

### Post by led_scorched on 2007-05-22
I'm looking to go from Dapper to Edgy.  currently, i have a single partition for / and /home.  I know a lot of people were saying to make them seperate before you update.  I dont want to update everything...i have 15-20 gigs of persanal files.  So, if its going to take me 6 hours to burn back ups of everything, i dont see much point in doing it.  But if i can upgrade to Edgy, with out HAVING to save every little mgp and text file i collected, and still have a reasonable security i wont lose it - sure, i'll back up the important stuff and upgrade.

---

### Post by ubuntu27 on 2007-05-22
> **led_scorched said:**
> I'm looking to go from Dapper to Edgy.  currently, i have a single partition for / and /home.  I know a lot of people were saying to make them separate before you update.  I don't want to update everything...i have 15-20 gigs of personal files.  So, if its going to take me 6 hours to burn back ups of everything, i don't see much point in doing it.  But if i can upgrade to Edgy, with out HAVING to save every little mgp and text file i collected, and still have a reasonable security i wont lose it - sure, i'll back up the important stuff and upgrade.

If you had your Home folder in separate partition, then you don't need to worry, just upgrade.

[Follow this guide for Dapper (6.06) toe Edgy (6.10) Upgrades]("https://help.ubuntu.com/community/EdgyUpgrades")


The chance of failing is 45/100 I think.  **If something happens, most likely you files wasn't altered**. It could have some kernel panic or some other software issues.

But, we always like to be sure about everything. We always say "better be prepared than be sorry" :) That's why we recommend to backup your files.

---

