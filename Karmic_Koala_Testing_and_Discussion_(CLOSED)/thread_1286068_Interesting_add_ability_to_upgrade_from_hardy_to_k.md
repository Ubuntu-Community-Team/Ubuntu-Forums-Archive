---
title: "Interesting: add ability to upgrade from hardy to karmic"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2009-10-08
Stumbled across this in updates:

> update-manager (1:0.126) karmic; urgency=low

  * DistUpgrade/DistUpgrade.cfg:
    - add gnome-app-install to the ForcedObsoletes
  * DistUpgrade/DistUpgrade.cfg.hardy:
    - **add ability to upgrade from hardy to karmic** (as asked for
      by Jonathan Riddell)
  * DistUpgrade/DistUpgradeQuirks.py:
    - add quirk handler to mark the dependencies of
      language-support-translations-* as manual on upgrade



[https://launchpad.net/ubuntu/+source/update-manager/1:0.126/+changelog](https://launchpad.net/ubuntu/+source/update-manager/1:0.126/+changelog)

I wonder what the proper procedure will be???????

---

### Post by Anarci on 2009-10-08
Possibly you would have to upgrade to jaunty first then from jaunty to karmic

---

### Post by slakkie on 2009-10-08
> **Anarci said:**
> Possibly you would have to upgrade to jaunty first then from jaunty to karmic

Why? Makes no sense. Normally it would be hardy > intrepid > jaunty > karmic. Seems to me they make it possible to upgrade hardy > karmic, bypassing intrepid and jaunty.

Maybe it will be nice for future releases so you can skip a release or two when upgrading.

---

### Post by autocrosser on 2009-10-08
I would bet it's to test it for the next release--which "should" be a LTS--10.04 Lynx :)

---

### Post by Squonk07 on 2009-10-08
Maybe an eventual goal is to use whatever methods are involved here to allow LTS users to update from one LTS release to the next (e.g. Hardy to Lucid). This would make a lot of sense, actually, and would make it easier (less of an upgrading pain) to stick with long-term releases. I guess you have to start somewhere, and why not here?

EDIT:

> **autocrosser said:**
> I would bet it's to test it for the next release--which "should" be a LTS--10.04 Lynx :)

Beat me to it! ;) All that obsessing over proper grammar before I post gets me every time.

---

