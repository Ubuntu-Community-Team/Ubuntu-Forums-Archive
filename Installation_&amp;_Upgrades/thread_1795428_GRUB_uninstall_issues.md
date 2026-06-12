---
title: "GRUB uninstall issues"
date: 2011-07-02
forum: Installation &amp; Upgrades
---

### Post by 81sriram on 2011-07-02
First installed Windows vista. Followed by ubuntu. Followed by Debian. While installing Debian I accidentally installed GRUB as the boot loader. Now the problem is my windows vista does not shwo up anymore in the boot options. I tried doing all the tricks that mentioned in other websites. But no luck yet. Are there are any new simple ideas to bring my vista back into the boot options?

More details: The linux is installed in a logical partition in my main hard drive. Also I know my windows OS is safe because when it began installing GRUB the pop up said that I have two other OS in my computer - Vista and Ubuntu.

Any help appreciated.

Sriram

---

### Post by drs305 on 2011-07-02
If you want to return to Ubuntu controlling Grub (and hopefully presenting a Vista option), boot into Ubuntu, then run:
```
sudo grub-install
sudo update-grub
```
This should point the MBR back to your Ubuntu boot files, if that is what you are looking for.

---

