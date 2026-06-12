---
title: "Remove &quot;New Ubuntu Realease&quot; from Update Manager"
date: 2012-03-20
forum: Installation &amp; Upgrades
---

### Post by koala15 on 2012-03-20
I am running Ubuntu 11.10. For a number of reasons, I do not wish to upgrade (at present) to a subsequent Ubuntu release.

Since the system is shared, I do not wish another user to (accidentally, or otherwise) press the button in the Update Manager to carry out the upgrade to the next (or subsequent) release via the "Upgrade" button in Update Manager..

Question, is there a way to remove the "New Release upgrade" and the "Upgrade" button from the Update Manager GUI?

Thank you all.

---

### Post by darkod on 2012-03-20
If I am not mistaken, if you enter in Software Sources and look at the part referring to the upgrade, you can tell it not to ask you to upgrade at all. The other options should be like "all releases (normal releases", "LTS releases only"...

---

### Post by plucky on 2012-03-20
> **koala15 said:**
> I am running Ubuntu 11.10. For a number of reasons, I do not wish to upgrade (at present) to a subsequent Ubuntu release.

Since the system is shared, I do not wish another user to (accidentally, or otherwise) press the button in the Update Manager to carry out the upgrade to the next (or subsequent) release via the "Upgrade" button in Update Manager..

Question, is there a way to remove the "New Release upgrade" and the "Upgrade" button from the Update Manager GUI?

Thank you all.

Open **Software Sources > Updates** and change the "Notify me of new Ubuntu Version" to **Never**

Good Luck

---

### Post by MG&amp;TL on 2012-03-20
Or you could make the other users normal (non-sudoers) users, that way they physically could not install a new release. Not sure if that's practical in your situation or not.

---

