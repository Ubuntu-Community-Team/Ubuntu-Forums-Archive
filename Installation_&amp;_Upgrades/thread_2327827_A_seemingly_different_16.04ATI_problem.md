---
title: "A seemingly different 16.04/ATI problem"
date: 2016-06-14
forum: Installation &amp; Upgrades
---

### Post by brucew on 2016-06-14
I have a vintage 2007 or 2008 Asus M4A78E motherboard with integrated ATI Radeon HD 3300 GPU.  [Specs here]("https://www.asus.com/Motherboards/M4A78E/specifications/").

I’ve read all the recommended materials and cautions on using ATI with 16.04.  They all seem to pertain to the fglrx drivers.  I don’t use—and never have used—the proprietary fglrx drivers.

I stick with the plain vanilla—whatever the distro installs by default—since I’m not a gamer and my most demanding video application is SMPlayer playing h.264 videos at 1920x1080 and 30fps.  However, I do run dual monitors having a combined resolution of 3840x1200.

Since I could find no warnings against the vanilla driver—except for gaming, modeling and other demanding applications using advanced features that I don't think my GPU supports anyway—I went about installing Xenial.  I always do a clean install; repartition and reformat the drives.  Never an in-place upgrade.  Nothing carries over from the previous install.

The left monitor, plugged into the old-school VGA, works perfectly.  

The right monitor, plugged into the DVI, is funky. I haven’t been able to nail down a pattern.  It will jiggle the display left and right a couple of times for a distance of about a half-character judging from the menu bar.  It will also blank the display for about two seconds, then it lights up again.  Sometimes it will be stable for a half-hour or more.  Other times it's acting up nearly continuously.  

I’m prepared to revert to 14.04 LTS, but before I do, is there anything I should try first?

---

### Post by X-RED_Tech on 2016-06-15
Downgrading will change nothing probably, because your graphics was already legacy before the previous LTS. Legacy -> supported only by open source drivers, the same you're using now but older.

---

### Post by brucew on 2016-06-15
Ah, but it ran perfectly for two years under 14.04 LTS, and for two years before that under 12.04 LTS, etc., all while using whatever plain vanilla legacy drivers the installer chose.  I have no fear of older legacy drivers.

---

### Post by yoshii on 2016-06-15
Maybe it's an Xorg issue?

---

### Post by brucew on 2016-06-15
> **yoshii said:**
> Maybe it's an Xorg issue?

I don't know how to determine that, or what to do if I determined that.

As I said in the other thread I posted (now solved), ever since I started using Ubuntu with Breezy, it always Just Plain Works so I've never had to go under the hood to figure anything out, thus, I don't know how.

---

