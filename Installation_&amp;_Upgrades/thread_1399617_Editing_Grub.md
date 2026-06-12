---
title: "Editing Grub"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by rittera on 2010-02-05
Would like to eliminate from the Grub menu of startup options all but the latest kernel update? Have made some attempts, but don't have authority is the message. Nonetheless, I'd appreciate someone's assistance and instruction. Thanks in advance.

---

### Post by presence1960 on 2010-02-05
It is suggested but not necessary to leave the second most recent kernel in the menu so in case the newest kernel goes south and won't boot you can boot into the older kernel.

To get rid of the kernels you do not want go to System > Synaptic Package Manager and mark for Complete removal:

linux-image-x.x.xx-xx
linux-headers-x.x.xx-xx
linux-image-x.x.xx-xx-generic

Of course the x's correspond to the kernels you want to remove.


this will uninstall them and remove the packages from cache. They will not appear in the GRUB menu.

---

### Post by raymondh on 2010-02-05
[http://ubuntuforums.org/showpost.php?p=7505203&postcount=1](http://ubuntuforums.org/showpost.php?p=7505203&postcount=1)

What do you mean ... 'don't have authority'.  Do you mean "permissions" ?

Raymond

---

