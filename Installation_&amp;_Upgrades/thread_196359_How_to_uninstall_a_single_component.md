---
title: "How to uninstall a single component ?"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by isterios on 2006-06-14
Is it possible to uninstall a single component of Xubuntu/Ubuntu etc., which has been installed with the whole suite?

Foe example, I would like to remove mozilla-thunderbird, which is installed with Xubuntu (or ubuntu), but it seems impossible as it seems "integrated" in the whole suite (when you make a aptitude remove, broken dependencies appear and the complete uninstall of xubuntu-desktop seems required in this case)

However, is there a solution to uninstall all these non wanted softwares?

---

### Post by bikeboy on 2006-06-14
Can you post the actual output from aptitude when you try to remove it? I know that it's safe for the package ubuntu-desktop or xubuntu-desktop to be removed, it's just   a metapackage, but I would prefer to see the output before advising further. Don't want to stuff things up for you.

---

### Post by ctgray on 2006-06-14
Just use apt-get to uninstall mozilla-thunderbird. That way you wont lose anything else apart from the (k/x)ubuntu-desktop meta-package.

---

