---
title: "Ubuntu not on GRUB bootloader"
date: 2010-08-19
forum: Installation &amp; Upgrades
---

### Post by Mr. King on 2010-08-19
Greetings, I'm having an issue installing Ubuntu with Windows 7 Home Premium 64-bit through Wubi. The Wubi installation works great and Ubuntu seems to install after the first reboot after selecting Ubuntu from Windows' boot menu, however whenever I select Ubuntu from Windows' boot menu after Ubuntu installs and it reboots for the second time, it loads the GRUB bootloader, however Ubuntu isn't listed at all. Windows 7 is listed twice and Windows Vista is listed (seems it picks up the recovery partition for Windows 7 as Vista) and when I select the first Windows 7 from the GRUB bootloader, it just goes back to Windows' boot menu with Windows 7 and Ubuntu as the selections. If I select the second Windows 7 from the GRUB bootloader, it'll boot Windows 7 like normally. It looks like Ubuntu is nowhere to be found. =( Because of that, I just ended up uninstalling it. What do you think is the problem here guys? Did Ubuntu install correctly or is it just hopeless?

---

### Post by bcbc on 2010-08-19
> **Mr. King said:**
> Greetings, I'm having an issue installing Ubuntu with Windows 7 Home Premium 64-bit through Wubi. The Wubi installation works great and Ubuntu seems to install after the first reboot after selecting Ubuntu from Windows' boot menu, however whenever I select Ubuntu from Windows' boot menu after Ubuntu installs and it reboots for the second time, it loads the GRUB bootloader, however Ubuntu isn't listed at all. Windows 7 is listed twice and Windows Vista is listed (seems it picks up the recovery partition for Windows 7 as Vista) and when I select the first Windows 7 from the GRUB bootloader, it just goes back to Windows' boot menu with Windows 7 and Ubuntu as the selections. If I select the second Windows 7 from the GRUB bootloader, it'll boot Windows 7 like normally. It looks like Ubuntu is nowhere to be found. =( Because of that, I just ended up uninstalling it. What do you think is the problem here guys? Did Ubuntu install correctly or is it just hopeless?

Did you click on the SKIP button while the installation was being done (during the 'powerpoint presentation'?)

---

### Post by Mr. King on 2010-08-19
Yeah I did, was I not supposed to?

---

### Post by bcbc on 2010-08-19
> **Mr. King said:**
> Yeah I did, was I not supposed to?

No. I just found that out yesterday (was doing some iso testing). I created a [bug]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/620028") report for it, but in the meantime, the solution is - don't hit 'skip' :)

---

### Post by Mr. King on 2010-08-20
Problem solved, you shouldn't press skip. ;)

---

