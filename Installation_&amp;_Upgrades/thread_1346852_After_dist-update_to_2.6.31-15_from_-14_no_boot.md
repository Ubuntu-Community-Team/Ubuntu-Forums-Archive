---
title: "After dist-update to 2.6.31-15 from -14 no boot"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by manjestic on 2009-12-05
I've been running a fresh install of Karmic Koala without incident for about a month now.  I got a over zealous with keeping the software up to date and performed:
```
sudo apt-get dist-update
```After restart, it would not boot.
```
grub loading
error: no such device
error: You need to load the kernel first
Failed to boot default entries.

```I hit the shift key after rebooting and saw two different kernel versions to choose from.  I am able to boot from the previous one no problem.

Two questions:
How to rollback the dist-update to 2.6.31-14?
What happened that the new dist failed to boot?

I tried removing the line 'search --no-floppy...' in the grub script with no change in symptoms.

---

