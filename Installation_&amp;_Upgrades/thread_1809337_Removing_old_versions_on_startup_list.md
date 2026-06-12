---
title: "Removing old versions on startup list"
date: 2011-07-21
forum: Installation &amp; Upgrades
---

### Post by ozark_hillbilly on 2011-07-21
Hello,

As I perform upgrades to my Linux OS the list of versions continues to grow on my bootup screen. Is there a way to edit out the older versions so everything fits on one screen?

Thanks,

Ed

---

### Post by Elfy on 2011-07-21
You can install something like startup manager which will show less options at boot, this though doesn't deal with the cause - just the effect.

You can remove the older and unused kernels - that'll cause update-grub to run and remove the no longer available kernels.

Both are detailed here [http://ubuntuforums.org/showpost.php?p=5112620&postcount=1](http://ubuntuforums.org/showpost.php?p=5112620&postcount=1)

---

### Post by SoFl W on 2011-07-21
I usually go to the Synpatic Package manager and search for the word "Kernel", sort of the installed tab (green dot), then look for "linux-headers-2.6.xx.xx" and "linux-image-2.6.xx.xx", mark for removal all except the current and the last versions. (just to have one older version in case of a problem)  Then click "apply"
After that type "sudo update-grub2" from the terminal.

---

