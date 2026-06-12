---
title: "Ubuntu 10.04 and legacy GRUB"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by EvansFive on 2010-07-08
I have a DELL PC and I have tried a number of times to upgrade to GRUB2.

Result random "GRUB LOADING" then blank screen and no GRUB menu...other times (ie after power off/power on) I get the GRUB menu.

I have seen some posts around some Windows software messing around in the MBR which impacts GRUB2 more than GRUB given GRUB2 is bigger.

So for the 4th time I have reverted back to legacy GRUB and all works perfectly (dual boot Windows 7 and currently Ubuntu 9.10).

[B]I would like to upgrade to Ubuntu 10.04 and what I want to know is will it still let me use legacy GRUB as the boot loader?

Can I successfully upgrade to 10.04 without having to use GRUB2?

Are there any gotchas using legacy GRUB?[/B]

I would appreciate any advice first before I launch into the upgrade!

Thanks

---

### Post by oldfred on 2010-07-08
It is my understanding on upgrades it does not change your boot loader. If upgrading and you have grub legacy it keeps grub legacy. If you do a clean install or are upgrade with grub2 installed then it updates to the newest version of grub2.

If old grub works that is fine. There are some issues with windows software writing into the MBR which is supposed to be used only for booting not hiding serial numbers or settings from users.

Grub2 osprober is greatly improved over old grub. Often with old grub we had to manually create even the windows entries and most all other system entries. Grub 0.97 has not been updated for years except each distribution may have tweaked it slightly so one system's 0.97 may not be another's.

Grub2 is also for the future, supporting more and new features, but if your system works you do not have to convert now. But I think at some point it is worth learning before you have to.

---

