---
title: "Indicator [application,me] menus inconsistent with rest of the gnome world"
date: 2010-02-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by nIRV on 2010-02-26
I finally found out what made me feel uncomfortable with the indicator application menus in current Lucid builds: the placement of menu item icons are not visually consistent with menus found everywhere else in gnome.

Is this a known bug the devs are planning to fix before the end of the Lucid development cycle? It'd be a shame to taint the enjoyable experience that is indicator application with such a blatant visual inconsistency.

Attached to this post:
menu-current.jpg : current rhythmbox indicator application menu
menu-feeling-right.jpg : how IMO the rhythmbox indicator application menu should render
menu-other-firefox.jpg & menu-other-system.jpg : examples of how menu items with icons are rendered

---

### Post by alexmurray on 2010-02-26
I whole heartedly agree, should definitely be aligned like in your menu-feeling-right.jpg - you should certainly file a bug and make sure you attach your screenshots to it to prove your point.

---

### Post by kurros on 2010-02-26
It's a bug that should be fixed before release. Rhythmbox incorrectly uses icons for those items, which is against the proposed Gnome Interface Guidelines that the patched GTK in Lucid is stricter about.

See [https://wiki.ubuntu.com/CustomStatusMenuDesignGuidelines#icons](https://wiki.ubuntu.com/CustomStatusMenuDesignGuidelines#icons)

I think the plan is that it be fixed upstream before Canonical has to patch it themselves.

---

### Post by nIRV on 2010-02-26
kurros, this doesn't appear to be a Rhythmbox (only) issue. The same inconsistency is present in the messenging "evolution/empathy/gwibber/pidgin" indicator application menu (see screenshot).

---

### Post by nIRV on 2010-02-26
... and transmission (see current & feeling-right attached) ...

To me, this is looking much more like a problem in the menu creation code & the way it places icons rather than a application-specific issue.

---

### Post by nIRV on 2010-02-26
[https://bugs.launchpad.net/ubuntu/+source/indicator-application/+bug/528243](https://bugs.launchpad.net/ubuntu/+source/indicator-application/+bug/528243)

---

