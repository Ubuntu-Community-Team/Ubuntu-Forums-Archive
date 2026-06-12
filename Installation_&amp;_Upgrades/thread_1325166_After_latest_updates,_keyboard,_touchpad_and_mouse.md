---
title: "After latest updates, keyboard, touchpad and mouse not responding."
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by Ederico on 2009-11-13
Dear all,

I don't believe in luck, good or bad, yet this Friday the 13th is not positive at all. I always update my system whenever new updates are available. As often happens, some updates give problems that were not present before.

After the latest update to my Kubuntu 9.10 my keyboard, touchpad and mouse are not responding. Once I enter the login screen after bootup none of them works.

I hope someone can help as I need to access my main Kubuntu system on my laptop. Luckily, right now I'm using my Kubuntu 9.04 system on my external hdd. I fear upgrading it now!

Thanks beforehand!

Best Regards,
Ederico.

---

### Post by forty2andsix on 2009-11-13
i am having the same problem have you solved this issue yet

---

### Post by Ederico on 2009-11-13
No, still waiting for a solution from somebody else. I hope it doesn't take much, this is quite frustrating.

---

### Post by Ederico on 2009-11-13
Solved it, thanks to [this post]("http://ubuntuforums.org/showpost.php?p=8297958&postcount=8").

Basically, use recovery mode and then select root with networking and use this code:

```
sudo apt-get --reinstall install udev
reboot
```

---

