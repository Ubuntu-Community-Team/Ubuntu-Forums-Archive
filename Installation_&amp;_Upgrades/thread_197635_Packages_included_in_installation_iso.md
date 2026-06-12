---
title: "Packages included in installation iso?"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by markba on 2006-06-16
I'm currently having a problem with an Epia M10000 and Dapper. After booting it hangs after "Uncompressing the kernel" or something like that. My guess is that it has something to do with the kernel version it self because it was reported in the field that some installations went fine until around 2.6.15.20.
(I'm using the server version). Breeze works fine, but I waited especially for the release of Dapper. 

My problem is this. Yesterday, I saw that the kernel was upgraded to 2.6.15.25. It is not possibly for me to get that update through apt-get because my system won't boot in Dapper. But if this kernel version (and all other upgraded packages) are in the downloadable iso, I can simple install Dapper again.

To put is simple: are installations iso's upgraded (daily or on another regular interval) with new packages? It was so when Dapper was beta and daily builds of the iso's were available...

---

### Post by markba on 2006-06-17
Just found out myself how to solve this: do an inplace migration from Breezy to Dapper automatically pulls in the latest kernel.
I also checked the iso's (date & time) and it looks like they are NOT updated.

---

