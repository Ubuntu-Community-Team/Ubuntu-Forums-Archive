---
title: "How to upgrade"
date: 2006-10-03
forum: Installation &amp; Upgrades
---

### Post by saintj0n on 2006-10-03
I am considering upgrading my kernel, but I heard it is a rough process for the inexperienced user.  How should I go about doing it so I minimize the risk to my system?

---

### Post by Kateikyoushi on 2006-10-03
You can have more than one kernel in your grub menu so can boot which you like. Therefore it is totally safe to upgrade if does not work you can fall back on the previous one.

---

### Post by saintj0n on 2006-10-04
What is the procedure for doing this?

---

### Post by K.Mandla on 2006-10-04
They'll be installed in the bootup menu that you see when you first turn on the computer.

Usually they show up in a list, numbered in reverse order. If you have Windows on your machine, Windows is usually at the bottom (but that can be changed).

If you don't remember seeing that list, wait for the Grub message that you see on startup, and press Esc. You should get the entire Grub menu then.

---

### Post by saintj0n on 2006-10-04
So you just load the kernel from the repository and select it the next time you boot up.  Does it change anything else beside the kernel.  Are any applications not compatible or will I need to update anything?  I like how everything is right now and wouldn't want to change it if I don't have to.

---

### Post by K.Mandla on 2006-10-05
It *should* work just fine. And even if it doesn't, you just enter that same Grub menu, and pick the old one to boot. Then once your system restarts, you can get rid of the one that didn't work, and you're no worse off than you were when you started. ;)

---

### Post by saintj0n on 2006-10-05
I know this is probably a rookie question, but is there any advantage from upgrading from Dapper?

---

### Post by Kateikyoushi on 2006-10-05
There are advantages but currently it is beta so instead of a stable box you might end up with a reinstall in worst case.
I would rather recommend waiting till the final version is released seems random things break for some as they try to upgrade.

---

