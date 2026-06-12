---
title: "Grub Error 22"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by ArchCorsair on 2007-12-10
Stupidest mistake of my life.

recently installed ubuntu onto my second internal hdd. I agreed to installed GRUB as it would make things easier to boot into windows. The problem arrised when i decided to uninstall linux. I thought i could just format the partition so i did.

When i attempted to boot back i got this:
```
GRUB Loading stage 1.5

GRUB loading, please wait...
Error 22

```

**im currently posting this thru live CD (7.10 x64)**

_My PC:_
HP dv9543cl (laptop)
2.0 Ghz Core2Duo
2GB RAM
Nvidia Geforce 8600  GS

---

### Post by Pumalite on 2007-12-10
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)
Try reinstalling Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by ArchCorsair on 2007-12-10
when doing step2
```

find /boot/grub/stage1

```

it returns:
```
Error 15: File not found
```

:(

**EDIT:**
What i did was, completely delete the partition that Ubuntu was contained on, thats the problem

---

### Post by Pumalite on 2007-12-10
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)
[http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5](http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5)

---

### Post by Velociraptor on 2007-12-10
Do you have your /boot on a separate partition? If so, you may need to do a "find /grub/stage1" in grub (without the /boot).

---

### Post by ArchCorsair on 2007-12-10
> **Velociraptor said:**
> Do you have your /boot on a separate partition? If so, you may need to do a "find /grub/stage1" in grub (without the /boot).

This is a post i made in another thread describing my situation:
[QUOTE=archcorsairr]My issue is this; I decided to remove ubuntu (x32) to install ubuntu 7.10 (x64) I had Windows Vista installed on HDD1

my laptop has 2 HDDs, i installed ubuntu on a 15GB partition on the 2nd HDD, and added 2GB swap.

When i was ready to install x64, i booted into the live CD, went into parted, DELETED the 15gb ubuntu partition and the 2GB swap partition, then resized the original NTFS partition that i used in windows for backup to max size. i reboot and i get this:
```
GRUB Loading stage 1.5

GRUB loading, please wait...
Error 22
```

I can't use your method because there are no setup files to 'recover' to rebuild GRUB. I cannot boot into vista anymore. (currently in liveCD)

please help!

_My PC:_
HP dv9543cl (laptop)
2.0 Ghz Core2Duo
2GB RAM
Nvidia Geforce 8600  GS
2x 160GB HDDs[/QUOTE]

---

### Post by DennisR on 2007-12-10
I don't have Vista, but I did the same thing (sorta) with my XP system. The fix was to boot with the XP CD, enter the recovery console then type "fixmbr" , press "Enter", Answer "yes" to the prompt and all was good on the reboot. Adapt as needed for Vista. HTH.

---

