---
title: "can I upgrade directly from 10.04 to 11.04?"
date: 2011-07-31
forum: Installation &amp; Upgrades
---

### Post by 3pinner on 2011-07-31
Hello,
Update Manager lists the 'latest version" as 10.10, so I assume I should upgrade to that, download all the updates for 10.10, then upgrade to 11.04, or should I just do a clean install of the / partition?
I have my HDD divided up" /  /swap  /home, and /home has three users.

Thanks,
And if this question has been posted many times before - feel free to beat me up. I can take it:P

---

### Post by 73ckn797 on 2011-07-31
Since you have /home on a separate partition a fresh install will be best. There can be problems on an upgrade.

---

### Post by 3pinner on 2011-08-01
> **73ckn797 said:**
> Since you have /home on a separate partition a fresh install will be best. There can be problems on an upgrade.

Thank you,
That's what I'll do.

---

### Post by YesWeCan on 2011-08-01
> **3pinner said:**
> Hello,
Update Manager lists the 'latest version" as 10.10, so I assume I should upgrade to that, download all the updates for 10.10, then upgrade to 11.04, or should I just do a clean install of the / partition?
I have my HDD divided up" /  /swap  /home, and /home has three users.

Thanks,
And if this question has been posted many times before - feel free to beat me up. I can take it:P

This is what Canonical recommends. It always works for me.
It is important to update Grub each time because the original Grub won't be able to boot 11.04.
A clean install, even if your /home is unchanged, trashes all your system wide settings and non-standard applications.
Because I am lazy I would do the upgrades and only if I had some unresolvable problem would I resort to a vanilla install.

---

