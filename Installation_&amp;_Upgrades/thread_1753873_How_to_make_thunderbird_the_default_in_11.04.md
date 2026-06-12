---
title: "How to make thunderbird the default in 11.04?"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by kmand on 2011-05-09
I upgraded from 10.10 to 11.04 and thunderbird which was previously my default mailer switched to evolution. How do I switch it back?

The thunderbird startup option to make it default doesn't seem to work.

The Gnome preferred applications widget doesn't list thunderbird or allow another program to be added.

---

### Post by Paddy Landau on 2011-05-09
Have you installed Thunderbird? Ubuntu cannot make it default until it's installed.

---

### Post by kmand on 2011-05-09
> **Paddy Landau said:**
> Have you installed Thunderbird? Ubuntu cannot make it default until it's installed.

It was installed prior to the upgrade, was the default on 10.10,  and survived the upgrade.

Are you thinking I need to uninstall and reinstall it? I would hate to have to start from scratch with adding accounts and setting preferences.

---

### Post by Paddy Landau on 2011-05-09
Uninstalling and reinstalling won't touch your settings. They are stored in a directory in your home directory, called [FONT=Courier New].thunderbird[/FONT], and uninstalling and reinstalling won't touch the directory. (This is unlike Windows, which works differently with its Registry.)

Possibly, if you uninstall and reinstall Thunderbird, 11.04 will recognise it's there. Looking at an older Natty bug, it just might work.

---

### Post by kmand on 2011-05-09
OK, I reinstalled and that added thunderbird to the Gnome preferred applications choices.

Thanks for the suggestion.

---

### Post by Paddy Landau on 2011-05-10
I'm glad that worked. This is something to remember.

Please mark this thread as solved.

---

