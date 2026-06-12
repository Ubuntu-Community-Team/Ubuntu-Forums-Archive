---
title: "How do I transfer Calendar information?"
date: 2019-03-15
forum: Installation &amp; Upgrades
---

### Post by Astralogic on 2019-03-15
Hi, I'm going to be doing a fresh install of Ubuntu and would like to transfer all the information in my calendar to the new installation. Could someone tell me how to do that please?

---

### Post by him610 on 2019-03-16
Hey Astralogic!
I am sure you have heard of TMI - Too Much Information. The opposite of TMI is NEI - Not Enough Information. 
Your issue has NEI! 
Please provide the name of your distribution and calendar application.

---

### Post by TheFu on 2019-03-16
There are many different calendar programs, so if you seek specific answers, you'll need to be much more specific about the release, the DE, and the program involved.

But really, if you are moving to a new system, I'd just take my entire HOME, which would have all my settings and most non-media files.  If you want to quickly install all the programs you have currently onto the new system, use **apt-mark** to get the list of manually installed packages, store it into a file and move that file over to the new system too.  Use apt-mark on the new system to tell the package manager to install those packages in 1 command.

---

### Post by Astralogic on 2019-03-21
Sorry, about that, I'm using Ubuntu Desktop 18.04.2 LTS, and I'm refering to the calendar that comes installed with the OS. It's just called "Calendar".

---

