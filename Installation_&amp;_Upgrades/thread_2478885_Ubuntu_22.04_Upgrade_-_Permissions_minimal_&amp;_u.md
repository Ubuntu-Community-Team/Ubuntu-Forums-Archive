---
title: "Ubuntu 22.04 Upgrade - Permissions minimal &amp; unable to install programs."
date: 2022-09-07
forum: Installation &amp; Upgrades
---

### Post by x-mucane5012 on 2022-09-07
**Hi there.**

I am experiencing an issue with permissions since the ***upgrade from 20.04 to 22.04***. Choosing the folders in which I need to extract/install new programs yields a blocking message ***"Permission denied"***. so I checked properties and found that it says ***"You are not the owner, so you cannot change these permissions"***. Even with [SIZE=3]***superuser***[/SIZE] already, though it ***[SIZE=3]doesn't help[/SIZE].***
I also cannot run my VSC (Visual Studio Code) anymore, because the ***OpenJDK 17 & JRE files were removed*** - installing them again doesn't help either due to the set permissions.

---

### Post by TheFu on 2022-09-07
Only the file owner can modify permissions.  I suspect that understanding of Unix permissions is lacking, so I can only suggest that you re-visit a tutorial on Unix permissions, look at the file and directory permissions again, and hopefully, the issue will be clear now, with refreshed permission knowledge.

I don't understand what you mean by "superuser". Please explain, clearly with details. I suspect there is a misunderstanding about this as well.

---

