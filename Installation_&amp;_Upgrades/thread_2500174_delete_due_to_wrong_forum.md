---
title: "delete due to wrong forum"
date: 2024-08-24
forum: Installation &amp; Upgrades
---

### Post by ozark_hillbilly on 2024-08-24
Mods: deleted due to wrong subforum....

---

### Post by guiverc on 2024-08-24
You've posted this in the *official flavors - Lubuntu* forum, but your images appear to show Ubuntu Desktop and not the LXQt desktop used by Lubuntu ([*Lubuntu 20.04 LTS is EOL *]("https://lubuntu.me/lubuntu-20-04-lts-end-of-life-and-current-support-statuses/")*too*)

You can *non-destructively *re-install a Ubuntu Desktop system (*using `calamares` of Lubuntu, or `ubiquity` of Ubuntu Desktop 22.04 LTS*) as I write about on this post - [https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533](https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533)

But I only glanced at your actual issue, as details aren't clear (Lubuntu uses LXQt; KDE Partition Manager, yet you refer to GNOME apps & show GNOME screenshots).  If you have re-installed; you can just *amend* the *file-system table (fstab)* to reflect whatever you want it to be, and any directories that you don't delete will get *shadowed* by the replacements your *fstab* changes effect. Myself, I always boot a *live* system & make changes to *fstab* from there, then reboot into the installed system & confirm I got what I wanted; otherwise reboot into the *live* system & correct any mistakes I made.. You're using a *live* system when making these changes? as I'd avoid changing a running system where you can't predict accurately the effects.

---

### Post by ozark_hillbilly on 2024-08-24
I will delete this...

---

