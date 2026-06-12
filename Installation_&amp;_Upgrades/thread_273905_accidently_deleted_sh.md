---
title: "accidently deleted sh??"
date: 2006-10-09
forum: Installation &amp; Upgrades
---

### Post by markster23 on 2006-10-09
hey... i was trying to install frostwire and was having some problems, so i looked up some stuff on how to install it, and i think i screwed up my sh interpreter ?? i had to type something like rm /usr/lib/sh ?? anyways, i can't open firefox  and im getting errors everytime i open up a terminal.. can anybody help ??

---

### Post by dcstar on 2006-10-09
> **markster23 said:**
> hey... i was trying to install frostwire and was having some problems, so i looked up some stuff on how to install it, and i think i screwed up my sh interpreter ?? i had to type something like rm /usr/lib/sh ?? anyways, i can't open firefox  and im getting errors everytime i open up a terminal.. can anybody help ??

Open Nautilus (the file browser), navigate to the /bin directory, right-click the file called "bash" and select "Make Link".

Find the new link, rename it to "sh" (**assuming you actually broke /bin/sh**), then get into the Properties of it and make it File Owner root, File Group root, and Tick all the Permissions boxes in the top section (don't worry about the Special Flags).

---

