---
title: "Freeze before login, need help quick!"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by ingard on 2008-11-07
I am loosing my patience with Ubuntu. 

I have just "upgraded"  to 8.10, and now it freezes before loginscreen leaving a slighty brighter brown screen.

I have removed compiz. That didnt fix it. 

What should i do? i need this computer to work soon, and with all my files and settings..

---

### Post by heldal on 2008-11-08
Some computers have problems with 8.10. Looks like a buggy kernel and/or 3rd party modules and the result depends a lot on what hardware you have. Some people have reported success by installing the package linux-backports-modules-intrepid. In my case I had to compile a whole new kernel and other drivers, not a trivial task. Many serious issues have been solved since the relase of the 2.6.27-kernel in intrepid. I don't know how much of updates in sub-releases that have been backported in the ubuntu-source, but I suspect the kernel-team would be better off creating a new set of packages based on 2.6.27.4 and release those as updates for intrepid.

---

### Post by Verslinykas on 2008-11-08
Have the same prob. Upgraded to 8.10, now my PC freezes before login. Have no idea how to fix it. I wish i never upgraded but did a clean install instead.

---

