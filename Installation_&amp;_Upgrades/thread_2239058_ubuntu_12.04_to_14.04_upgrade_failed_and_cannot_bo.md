---
title: "ubuntu 12.04 to 14.04 upgrade failed and cannot boot"
date: 2014-08-11
forum: Installation &amp; Upgrades
---

### Post by Alastair Rae on 2014-08-11
I ran an upgrade via the Update Manager. It hung at the stage of upgrading gnome-vim. At this point I could neither cancel the upgrade or proceed. Now I have a laptop that won't boot. Any ideas how to fix it?

---

### Post by Bashing-om on 2014-08-11
Alastair Rae; Depends;

Can you boot to the grub menu ??
From the grub menu ( 'e' key for edit mode -> replace "quiet splash with the term text, ctl+x to continue the boot process )can you boot to a text terminal ?

Yes, then there is hope !

[INDENT][INDENT][INDENT]we find out
[INDENT][INDENT][INDENT]what condition your condition is in
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alastair Rae on 2014-08-12
I can get in to change the grub settings to term but it will not boot up. It gets as far as Checking battery state ... [ OK ] and hangs.

This is very disappointing. I've seen in several places that you can upgrade from 12 LTS to 14 LTS with the Update Manager. Looks like I need to do a fresh install and see what I can recover from backups.

---

### Post by Bashing-om on 2014-08-12
Alastair Rae; Well, well;

Depends on what you want to do. Upfront, it is going to take some time to even find out the problem with booting in this present install. It will be much faster to just clean install 14.04 and be done with it.

But, could be a learning experience for all, and I am always open to that "learning experience".
IF we are going to fix this install we need to boot the liveDVD(USB), and start looking at what is on the actual install and see what we can do to boot it from that liveDVD.

[INDENT][INDENT]if you want
[INDENT][INDENT][INDENT][INDENT]we do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alastair Rae on 2014-08-12
For me the fastest route is to do a fresh install. I can get into my old home dir using a live disk and make a backup so I won't lose too much.

I think I should have just done that in the first place. I wish the Update Manager didn't offer to do an upgrade if it can go so badly wrong.

But thanks for the offer of help anyway.

---

