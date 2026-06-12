---
title: "Booting issue after the upgrade to 24.04  LTS."
date: 2024-08-31
forum: Installation &amp; Upgrades
---

### Post by psrvarma on 2024-08-31
[SIZE=4]1) I have updgraded the ubuntu system from 22.04 to 24.24 
2) Issue: On restart it dies not boot 
[/SIZE][SIZE=4][COLOR=#000000][FONT=Arial]
I have the luks encrypion on the disk. And while installing it raised issues while replacing the grub related files, but I continued. 
Is there a way I can get the system back live please. Urgent!!! Please help. It directly goes to the BIOS scrren.

[FONT=Verdana]Tried the boot-repair toot but failed. [/FONT]
[FONT=Verdana]Here is the boot-repair logs: [/FONT][/FONT][/COLOR][/SIZE][COLOR=#000000][FONT=Arial][FONT=Verdana][SIZE=4][FONT=Arial]https://paste.ubuntu.com/p/vKWgnMymKm/



[/FONT][/SIZE]
[/FONT][/FONT][/COLOR]

---

### Post by tea for one on 2024-08-31
> **psrvarma said:**
> I have the luks encrypion on the disk. And while installing it raised issues while replacing the grub related files, but I continued. 
Do you remember the issues?

Line 215 - Unknown BootLoader on nvme0n1p1
Line 217 - Unknown BootLoader on nvme0n1p5
These two lines indicate that Grub is missing/damaged.

As you use encryption, did you back up your data before upgrading?
If not, back up before before doing anything else.

---

### Post by lendern on 2024-08-31
I reported almost the same issue yesterday: [https://ubuntuforums.org/showthread.php?t=2500326](https://ubuntuforums.org/showthread.php?t=2500326)

I fixed it booting on a USB key, then install and run sudo boot-repair

Boot is now OK.

---

### Post by lendern on 2024-08-31
I reported almost the same issue yesterday: [https://ubuntuforums.org/showthread.php?t=2500326](https://ubuntuforums.org/showthread.php?t=2500326)

I fixed it booting on a USB key, then install and run sudo boot-repair

Boot is now OK.

Edit: my bad, you already tried boot-repair

---

### Post by psrvarma on 2024-09-01
Thanks for the reply, I have backed up the required files and installed ubuntu a fresh.

---

