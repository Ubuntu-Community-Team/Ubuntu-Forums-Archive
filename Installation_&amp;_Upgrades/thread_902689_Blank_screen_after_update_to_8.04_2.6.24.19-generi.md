---
title: "Blank screen after update to 8.04 2.6.24.19-generic"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by EvanF on 2008-08-27
Had 8.04 working beautifully but noticed that it was not using the latest kernel even though it had been "update manager'd.

Did update-grub and had to do some editing of menu.lst.  Had to use (as usual) supergrub to set the mbr (4 hd's w/2 xp partitions).  Booted mostly normally.  But after logging in, screen goes blank/white.  Mouse works but that is all.

Booting with options, I did a gnome failsafe session and it seems to run normally (but with warning to fix the system).  I suspect startup scripts but am not that expert with Ubuntu.

Changing menu.lst back to the original configuration produced the exact same result.

Sounds like something is compromised.

Any thoughts on how to fix??

EvanF

---

### Post by EvanF on 2008-08-28
Well, it turns out that the easiest fix was to download the latest 8.04.1 and install it over the old O/S.  Pretty slick.  Kept all the original apps and settings.

Sometimes, it pays to take the easy route and NOT try to understand what has happened.

EvanF

---

### Post by TekNullOG on 2008-09-09
If this is not an option, is there another way to fix it?

I don't have blank CDs or a burner at my friends house (it's their computer).

---

### Post by TekNullOG on 2008-09-09
I tried selecting GNOME from the list of session instead of the failsafe GNOME and it worked. It asked me if I wanted to make it default ( i said yes ) and when I rebooted, it continued to work.

I don't know why it was no longer default after doing updates. Hope this helps others.

---

