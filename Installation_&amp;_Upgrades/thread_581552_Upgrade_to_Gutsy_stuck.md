---
title: "Upgrade to Gutsy stuck"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by reyfer on 2007-10-19
I started upgrading my Kubuntu machine from Feisty to Gutsy using the Adept-upgrade tool. It fetched all necessary files, and it started the install process, but it has now been sitting there stuck at 49%, says *Preparing python-gnome2-extras*, it has been sitting there for 20 minutes now, what should I do? Should I restart the process?

---

### Post by milton1 on 2007-10-19
give it more than 20 minutes. Sometimes these things will resolve themselves. If not, you may need to restart, boot whichever kernel will boot, and run ```
 sudo dpkg --configure -a 
```

(note: I think I got that code right, but check "man dpkg" to be certain)

---

### Post by reyfer on 2007-10-19
Okay, I'll wait a little longer and then I'll try that. But can somebody explain why do I need python-gnome2-extras on a KDE system?

---

### Post by milton1 on 2007-10-19
something else in your system must depend on it. kubuntu contains many programs that are not part of the base install of kde; some of them have gnome-based dependancies.

---

