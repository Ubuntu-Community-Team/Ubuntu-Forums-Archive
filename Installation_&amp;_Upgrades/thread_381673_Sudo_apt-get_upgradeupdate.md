---
title: "Sudo apt-get upgrade/update"
date: 2007-03-11
forum: Installation &amp; Upgrades
---

### Post by dmsn on 2007-03-11
Hey
Yesterday i did sudo apt-get upgrade/update and after that when i rebooted
i got in a grub> promt. So today i reinstalled. What do i need to do after
sudo apt-get upgrade/update  ? I know there is omething to do but i dont remember.

Thanks.

---

### Post by bapoumba on 2007-03-11
> **dmsn said:**
> Hey
Yesterday i did sudo apt-get upgrade/update and after that when i rebooted
i got in a grub> promt. So today i reinstalled. What do i need to do after
sudo apt-get upgrade/update  ? I know there is omething to do but i dont remember.

Thanks.
Hello, I'm not sure I understand your problem. When you reboot, do you mean you get into a tty and not into the GDM login screen ?
If so, try **sudo dpkg-reconfigure xserver-xorg**.

---

### Post by Kateikyoushi on 2007-03-11
That's the grub promt, you did not see the grub menu show up right ? Was no screen to choose which kernel to boot or boot single user mode etc, you went right to that promt.

---

