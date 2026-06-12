---
title: "Installing a bootloader"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by Burillo on 2008-04-19
Right now i'm building myself an environment - i am going to install two WinXP's and two Ubuntu's. I have my hard drive partitioned like this:

Primary:
1. ~60 mb boot partition (/boot)

Extended:
2. ~10 gb NTFS (root partition for WinXP #1)
3. ~10 gb NTFS (root partition for WinXP #2)
4. ~10 gb ReiserFS (root partition for Ubuntu #1)
5. ~6 gb ext3 (root partition for Ubuntu #2)
6. 4 gb Linux swap
7 ~80 gb - ext3 (/home for both Ubuntu's and a Windows drive too)

i have successfully installed Ubuntu #1 with all needed software and right now i'm running a livecd about to install Ubuntu #2. The thing is - Ubuntu setup insists on formatting boot partition, whereas i want all Ubuntu kernels reside on a single (60mb) boot partition, where GRUB is installed. In the final step of the setup there's an option NOT to install bootloader - if i don't choose not to install bootloader - will it still format my boot partition? and if i don't want to install bootloader - WHY does it insist on formatting it?

---

### Post by Jammy4041 on 2008-04-19
It should install the Bootloader automatically, and update your GRUB.You don't have to fiddle aound with it.

---

### Post by sandysandy on 2008-04-19
any particular reason for having 2 win XP and 2 ubuntu OS - if i may ask.

regards

---

### Post by Burillo on 2008-04-19
The reason is pretty obvious - i just want to setup a work environment (Ubuntu #1 and WInXP #1) and "everything else" (Ubuntu #2 - fiddling around, tweaking etc, WinXP #2 - gaming).

How can it update the grub if it is formatting my root partition?!

---

### Post by Burillo on 2008-04-19
never mind, i backed up my bootloader and then combined settings with the new one, so everything works perfectly now.

PS manual bootloader configuration and fiddling with the kernels is fun! :-)))

---

