---
title: "Compact layout in Nautilus doesn't work as expected"
date: 2009-07-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-07-28
Selecting 'Compact layout' from Nautilus prefernces has no effect. However, selecting 'Compact layout' from the right-click context menu **does** work.

---

### Post by BCurtisWX on 2009-07-28
> **phenest said:**
> Selecting 'Compact layout' from Nautilus prefernces has no effect. However, selecting 'Compact layout' from the right-click context menu **does** work.

screenshots and possibly filing a bug report would be a good idea :D

---

### Post by phenest on 2009-07-28
[Bug 405992]("http://https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/405992")

---

### Post by BCurtisWX on 2009-07-28
> **phenest said:**
> [Bug 405992]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/405992")

Link Fixed.. Plus I will test it once I get back home from work

---

### Post by Darkshade on 2009-07-28
Confirmed

---

### Post by phenest on 2009-07-28
> **Darkshade said:**
> Confirmed

If so, then please login into Launchpad, and confirm it there.

---

### Post by taavikko on 2009-07-29
> **phenest said:**
> Selecting 'Compact layout' from Nautilus prefernces has no effect. However, selecting 'Compact layout' from the right-click context menu **does** work.

Did you "reload" the view after setting the view-mode in preferences?
since this needs to be done manually.
If you use the context menu, the reload is done automatically.

ATM, not seeing the bug.

---

### Post by phenest on 2009-07-29
> **taavikko said:**
> Did you "reload" the view after setting the view-mode in preferences?
since this needs to be done manually.

There is no need to "reload" the view in Jaunty.

---

### Post by taavikko on 2009-07-29
> **phenest said:**
> There is no need to "reload" the view in Jaunty.

there isn't? 

If my memory serves me right, I've always had to "reload" to get view-mode what I've selected in preferences to display correctly.
Opening new folder will have the previously selected view by default.
but the main view needs to be reloaded to show selected mode...

((but then again, I don't even remember what I ate for breakfast))

---

### Post by phenest on 2009-07-29
> **taavikko said:**
> there isn't? 

If my memory serves me right, I've always had to "reload" to get view-mode what I've selected in preferences to display correctly.
Opening new folder will have the previously selected view by default.
but the main view needs to be reloaded to show selected mode...

((but then again, I don't even remember what I ate for breakfast))

Whereas I, instead of trying to remember, have just tested what I claim.

There has never been any need to "reload" after changing anything in preferences in Jaunty or any of the previous releases.

---

### Post by taavikko on 2009-07-29
> **phenest said:**
> Whereas I, instead of trying to remember, have just tested what I claim.

There has never been any need to "reload" after changing anything in preferences in Jaunty or any of the previous releases.

/me* trying to remove the knife from my back, after snappy comeback...

Just tested too, the changed behaviour didn't take effect at all, even after reload.
Default view could only be changed via context-menu. ((although the test method wasn't the purest, Over the phone, friend testing it)) Trying liveCD next.

---

### Post by phenest on 2009-07-29
Perhaps someone else could confirm the correct behaviour of this function please.

---

### Post by phenest on 2009-07-29
> **taavikko said:**
> Just tested too, the changed behaviour didn't take effect at all, even after reload.
Default view could only be changed via context-menu. ((although the test method wasn't the purest, Over the phone, friend testing it)) Trying liveCD next.

Tested with which one: Jaunty or Karmic?

---

### Post by phenest on 2009-07-29
I've just discovered something interesting, but I don't understand why.

If you select 'Compact layout' from the context menu, you can then switch back and forth between views from preferences.

---

### Post by taavikko on 2009-07-29
> **phenest said:**
> Tested with which one: Jaunty or Karmic?

Sorry, forgot to mention that one. Jaunty.
And will test Jaunty's LiveCD when I'll have enough energy to get up from the bed and open cupboard, where the CD's reside... :D But hey, to my defence, it's well over 3feet's (1m)

EDIT// 
Fired up a 9.04 LiveCD, opened nautilus.
Default view is "icon" Opened preferences. Set the default view for opening new folders to "Compact" Closed preferences-dialog. And nothing happened.
Had to press "reload" button (Ctrl+R) for view to change.
Whilst opening new folders the view changed.

Switched back to defaults, changed the view on the "context menu", view mode changed instantly.

---

