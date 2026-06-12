---
title: "Add/remove headaches"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by Fox2 on 2007-02-13
I'm having some headaches with the add/remove process. A friend who is knowledgable (Ubuntu user, Linux sysadmin, but sadly 5000 miles away) has done what he can to help, but it's not resolved.  So I'm passing it here for ideas and suggestions.

Scenario - Fresh install of latest 6.10 from downloaded DVD, net connection working fine, no other changes made.  I then tried to install two programs - Opera, and X-Chat. I've had problems (of different kind) with both.


**Problem 1 - Opera:**

With Opera, I default-installed Ubuntu, ran add/remove, looked for Opera, no luck. Checked all software sources which updated properly, re-ran (under direction) add/remove, still no opera. Ran APT, which showed Opera as "known" in the list. Added the canonical commercial to the sources list, closed and reopened, still no opera in add/remove. Under direction I then went to the Synaptic Package Manager which did show Opera, and installed it (and its dependencies) as well as updating all system packages related to APT and so on. It installed apparently correctly, no errors visible.

However Opera still doesn't appear either in the menus or in add/remove. I can run it from terminal, it generates a bunch of errors along the lines "object cannot be preloaded" or "invalid/uninitialized input device", but opera does start and seems to run correctly. 

Questions - What's gone on, why couldn't Opera be accessed the normal way via add/remove, why does it show in APT and SPM but not add/remove even now, why isn't it showing in the menus, what are the error messages about, how should I have done this to fix it up properly, what should I do now?

**Problem 2 - Xchat:**

Much easier. After rebooting from the above, Xchat was visible in add/remove. So I checked it and clicked APPLY.  It's now been an hour and add/remove is still showing the clock face, signifying its "doing something", and is greyed out. What's up, and what should I do now?


(After these two I downloaded and installed Skype, without using add/remove or any other package manager. That seems to have worked fine. Don't know if that helps but mentioning it "in case")

Many thanks!

---

### Post by Kateikyoushi on 2007-02-13
Never tried to use add/remove, I would try to remove Opera and reinstall via synaptic or aptitude to see if something was missing, it should also add opera to your menu.

You can add it manually from Preferences > Menu Layout there create a new Item name it and set opera %u as command.

I can't tell why add/remove did not work because I never tried myself but use synaptic and stick to it if it works.

---

