---
title: "[SOLVED] Upgrade failure, and then partial Gutsy joy"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by radiophage on 2007-09-28
Upgrade to Gutsy failed... (well, not totally!)  any help appreciated!  Using a Dell GX-1.

Moving from Feisty to Gutsy via the recommended upgrade method gave the following on restart:

"UNABLE TO LOAD THE SYSTEM DESCRIPTION TABLES."   Yikes.

In a diagnostic startup, there is an infinite loop of probing for a response from ATA1, so it doesn't see the hard drive, apparently.

However:

The system starts up and runs normally if I drop back to the older kernel 2.6.20   !

Ideas anyone?

Thanks

---

### Post by Pumalite on 2007-09-28
Save you data. Download an iso of Gutsy 7.10 Beta and do a fresh install. I just did it and works great. You have to keep in mind it is in testing. Stable comes out in October (the 18th I think)

---

### Post by lisati on 2007-09-28
> **Pumalite said:**
> Save you data. Download an iso of Gutsy 7.10 Beta and do a fresh install. I just did it and works great. You have to keep in mind it is in testing. Stable comes out in October (the 18th I think)

Seems there are a few things to iron out yet.....yes - you're right to point out that it's still "BETA"......I'm currently doing a bit of homework for my laptop which seems to be having trouble getting going after the upgrade....

---

### Post by radiophage on 2007-10-02
Update.

This may be specific to something in this particular machine.  Since my first post, I've installed the upgrade on two other Dell GX1's without problems.

Needless to say, it doesn't work to try booting from the Gutsy CD (due to the newer kernel).

For now, I'll just run with the old kernel on this particular box.  If anyone has any other ideas, I'm all ears... thanks to all.

---

### Post by Pumalite on 2007-10-02
Wait two weeks and you will have Gutsy Stable.

---

### Post by radiophage on 2007-10-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104581/comments/25](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104581/comments/25) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Solved:

1. System Description Table problem was easily corrected by switching on ACPI in BIOS.

2. The inability of the 2.6.22 or 2.6.23 kernels to boot the machine was solved by [this method.]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104581/comments/25")

---

