---
title: "[Firefox-3.5] External links open in same tab"
date: 2009-08-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by OliW on 2009-08-11
Scenario: I control-click a link in a terminal.
Expected: Firefox gets focus, opens new tab, loads link.
Observed: Firefox gets focus, opens link in current tab. Oli cries.

This is not a Firefox "bug". I have created a new profile to test and it works as expected. Now, I could create a new profile and suck it up but I really like my profile as it is *thankyouverymuch*.

So that leaves me with hunting down some setting, somewhere.

Any ideas?

Edit: **browser.link.open_newwindow** was set to 1 (where 3 is the new default)

Just changing it to 3 makes things work as expected.

---

### Post by Kow on 2009-08-11
Edit -> Preferences -> Tabs -> "Open new windows in a new tab instead" checked?

---

### Post by OliW on 2009-08-11
> **Kow said:**
> Edit -> Preferences -> Tabs -> "Open new windows in a new tab instead" checked?

Yup

---

