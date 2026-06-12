---
title: "Problems with gnome-power-preferences"
date: 2008-09-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by phelin4 on 2008-09-18
I have noticed some illogical behaviour when it comes to the power management in Intrepid. Sometimes I get one GUI and sometimes another wehn I start System->Preferences->Power Management. Attached is an image having both GUIs.

in addition to that, it looks like the power management preferences themselves seem to not stick. I keep on having to change the "When laptop is closed" to "Suspend" as it keeps on changing back to "Blank Screen".

Is this related to the fact that I upgraded from Hardy? Are there others who have seen the same behaviour? Is this a known problem?

I am using the AMD64-version.

---

### Post by mc4100 on 2008-09-18
There should be two GUI's, because, naturally, if no battery is detected, there should be no battery preferences to change (for example, on a Desktop). However, there seems to be a bug causing some delay after adding a battery/removing one, and the preferences reflecting that.

Edit: I tested my laptop on battery/ on AC, and I noticed that when on AC, I still have all the preferences shown in your second screen-shot (minus the extra tab) -- so this is a bug I cannot reproduce (you should file one).

---

