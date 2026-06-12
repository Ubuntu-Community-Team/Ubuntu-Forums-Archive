---
title: "Is there a way to trun back upgrade?"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by eighthate on 2006-11-01
Hey i recently upgraded to edgy eft And al it did was killing my X configuration and now i cant log on or just reconfigurate it, I can only go in recovery mode and use a terminal. IF there is a way to solve my problem what is it? or if there is no way, Is there a way to Turn back to dapper?

thanks

---

### Post by Joe_CoT on 2006-11-01
There's no good way I know of to revert back to dapper; I believe your options are reinstalling Edgy, or muscling through the update. Have you tried  the [Edgy upgrade instructions]("https://help.ubuntu.com/community/EdgyUpgrades")? If so, could you tell us the error X window fails with, and post your Xorg.conf?

---

### Post by eighthate on 2006-11-01
> **Joe_CoT said:**
> There's no good way I know of to revert back to dapper; I believe your options are reinstalling Edgy, or muscling through the update. Have you tried  the [Edgy upgrade instructions]("https://help.ubuntu.com/community/EdgyUpgrades")? If so, could you tell us the error X window fails with, and post your Xorg.conf?

Yes i have tried that method, i dont know how i could post my xorg.conf from my terminal, i'm presently on the live cd of Edgy Eft so i can type this. How can i do this pls? thanks

---

### Post by Joe_CoT on 2006-11-01
Assuming your linux partition is hda1, 
```

mkdir /media/linuxpart
sudo mount /dev/hda1 /media/linuxpart/ -t ext3 -o iocharset=utf8,umask=000

```

Then you should be able to view your xorg.conf at /media/linuxpart/etc/X11/xorg.conf
while you're there, look at your /media/linuxpart/var/log/Xorg.0.log for errors

---

