---
title: "Rhythmbox Removed?"
date: 2010-02-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Aaddron on 2010-02-05
Hi,

Checked for updates today and a box popped up saying partial upgrade, I continued through the prompts one of the changes was removing Rhythmbox. Is this suppose to happen or did I do something that is causing this to happen?

Just to be clear, this isn't a "omg Rhythmbox is gone how get back???" post... just wondering if this update is an official one.

---

### Post by Jordanwb on 2010-02-05
If it's saying partial upgrade, there's probably a hiccup in apt. Right now I'm getting a partial upgrade because apt won't install a package. :confused:

Can't say for rhythmbox because it's one of the first things I remove; never use it.

---

### Post by jfernyhough on 2010-02-05
Doing a partial upgrade during the alpha phase is exceptionally risky.

There is a lot of package movement and very little testing done - you're the one testing it, after all. It's quite possible doing a partial upgrade via Update Manager will bork your system - don't do it. Either wait until the packages settle enough that requisites are satisfied, or use Synaptic to manually pick through the upgrades and check which you can apply/want to apply.

Rhythmbox was removed due to a dependency on another package (libdbusmenu or something) which has (probably) been upgraded but which isn't installable yet.

--edit
Actually, just looked and you need to manually upgrade from libdbusmenu-glib0 to libdbusmenu-glib1. This removes the -glib0 version and everything else will upgrade.

---

### Post by Aaddron on 2010-02-05
Alright thanks, that's all I wanted to know.

---

### Post by 23meg on 2010-02-05
You may benefit from reading [the sticky thread about partial upgrades]("http://ubuntuforums.org/showthread.php?t=1343434").

---

### Post by KrazyPenguin on 2010-02-05
THEY FINALLY REMOVED IT!!!

Good , maybe the can replace it with a good media player.

;-)

---

### Post by dagrump on 2010-02-06
Nope, still there. Just his install.
I don't use it, but I checked. Still installed.
If I remember right removing it will remove ubuntu-desktop, so they have more issues.
Sticky is a good suggestion.

---

### Post by phillw on 2010-02-06
Glad it's still here. Been using it since 9.04. There may be 'better' ones, but it does what I want - that is, sit on the panel next to my loud-speaker icon, play my music and accept the Fn-Keys for control of playing, skipping etc.

Regards,

Phill.

---

### Post by Digikid on 2010-02-06
> **KrazyPenguin said:**
> THEY FINALLY REMOVED IT!!!

Good , maybe the can replace it with a good media player.

;-)

Agreed.  VLC or Songbird perhaps.

---

### Post by MacUntu on 2010-02-06
I hope they speed-up Banshee and get rid of Rhythmbox in 10.10.

---

