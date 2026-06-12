---
title: "Upgrade to Lucid Lynx issues"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by bruno9779 on 2010-04-27
I have just upgraded to Lucid with

```
sudo update-manager -d
```

After some minor issues I have most things working again.
I had to re-enable sources and hardware drivers and change some of my preferences that were overwritten (eg. lock screensaver)

What I am not able to get rid of is the Floppy mount entry.
I do not have a floppy reader, but I get an entry on the top bar and in "Places".

[[img]http://www.ubuntu-pics.de/thumb/54517/screenshot_001_zTBk9C.png[/img]](http://www.ubuntu-pics.de/bild/54517/screenshot_001_zTBk9C.png)

(I do not manage to take a screenshot of the places menu, it overrides the shortcut for shutter)

---

### Post by philinux on 2010-04-27
Go into your bios and disable the floppy drive there.

---

### Post by klemes on 2010-04-27
I do not know exactly how to do this inside of gnome,but if you have an entry for a /dev/fd0 in your /etc/fstab simply comment it out.
Another thing to check is if there is an entry for a floppy disc controller  in your BIOS and disabling it.:popcorn:

---

### Post by bruno9779 on 2010-04-27
Thanks, done

I wonder though, the policy has somewhat changed. I have a dvd player, but it doesn't show unless I put a disk in it.

I think that the floppy did the same, but doesn't since the upgrade.

---

