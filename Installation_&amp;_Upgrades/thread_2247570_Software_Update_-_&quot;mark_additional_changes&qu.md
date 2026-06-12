---
title: "Software Update - &quot;mark additional changes?&quot; dialogue box is redundant"
date: 2014-10-08
forum: Installation &amp; Upgrades
---

### Post by oygle on 2014-10-08
When I do software updates, I often see a small dialogue box with "mark additional changes ?" on it. The DEB files shown in this box are ALREADY shown in the Software Update window, so the information is redundant. Those DEB's are already listed and ticked. See attachment.

I used to see this dialogue box on the last version of Kubuntu. As I did a fresh intall of 14.04, I would have thought any problems like that would be fixed

---

### Post by bashiergui on 2014-10-11
Synaptic probably iterates through each package you're changing and checks for dependencies. It clearly doesn't check if you've got those dependencies selected before it throws a warning. The purpose is to prevent "dependency hell" which was common in earlier days of Linux and nowadays when you're compiling software yourself, when you find yourself chasing a never ending string of packages that you didn't know you needed.

---

### Post by oygle on 2014-10-13
Okay thanks for your help. Should I report this a bug then ??

---

### Post by bashiergui on 2014-10-13
Up to you. It's somewhere between bug and feature request IMO. Regardless it doesn't hurt to ask.

---

