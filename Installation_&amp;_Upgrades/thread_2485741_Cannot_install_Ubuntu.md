---
title: "Cannot install Ubuntu"
date: 2023-04-07
forum: Installation &amp; Upgrades
---

### Post by barmak2 on 2023-04-07
Dear all,

I just upgraded to an LG laptop model WQXGA that came with Windows 11 installed.

I tried to install Ubuntu but Gparted cannot partition my SSD. 

What can I do?
Thanks for any help.

---

### Post by ne29914 on 2023-04-07
Do you want dual boot?
If not, let the installer do it for you.

---

### Post by barmak2 on 2023-04-07
I would like the dual boot, so I don´t lose the warranty....

---

### Post by jeremy31 on 2023-04-07
Did you disable the hybrid shutdown/fast startup in Windows? See [https://www.computerhope.com/issues/ch001762.htm](https://www.computerhope.com/issues/ch001762.htm)

---

### Post by MAFoElffen on 2023-04-07
Also, check a few things first:

- Disable fastboot and secureboot in the BIOS.
- Check the SATA mode in the BIOS. Should be set to ahci, not set to RAID. If it is set to RAID. Stop and tell us so we can give you instructions on what to do so that Windows can pick up the change. (This is very Important!)
-To make room for Ubuntu to install, use the Windows Disk Management utility to shrink the Windows Partition. To leave unallocated space for the install. It is important to do it this way. If you do not do it this way, it will break the Windows file indexes and they will have to be rebuilt.
-In Windows Control Panel > Power Options > Balanced, change power options > Change advanced power options > Change option that are not currently available > Change what power buttons do > Shutdown options > Uncheck the box that enables Fast Startup.

---

### Post by barmak2 on 2023-04-07
Thank you, **[COLOR=#C61919][B]jeremy31 and **[/COLOR][/B][[COLOR=#DD4814]**MAFoElffen**[/COLOR]]("https://ubuntuforums.org/member.php?u=1044547")

I did it with your help.
Best regards.

---

