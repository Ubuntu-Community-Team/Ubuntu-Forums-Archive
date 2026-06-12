---
title: "BlasterPC by Empac"
date: 2006-02-23
forum: Installation &amp; Upgrades
---

### Post by Captain Mikee on 2006-02-23
I've been trying to get Ubuntu to work for over a week on this computer. It's an Empac "BlasterPC." I got it secondhand, a quick search suggests that it was sold by TigerDirect:

[http://www.pcnineoneone.com/reviews/hw/tdbpc.html](http://www.pcnineoneone.com/reviews/hw/tdbpc.html)

Don't worry, I didn't pay more than it was worth -- it was free!

Here's what happens: Whenever Ubuntu is running (LiveCD, installer CD, installed system, single user mode), it works for up to 7 minutes and then hangs.

Sometimes it hangs during boot, sometimes it goes for over 5 minutes. But I don't think I've ever seen it work for more than 7 minutes -- except for the installer CD - after several attempts, watching like a hawk and typing as fast as possible, I got the install to finish in maybe 20 minutes.

Memtest86 does work with no problems.

Can anyone suggest a solution? I've tried Hoary and Breezy. Would I be likely to have more success with Dapper?

Is there something special that the system does after 5 minutes of mostly idling?

Thanks!

- Mike

---

### Post by Captain Mikee on 2006-02-23
I've heard from someone with a similar problem that he could only use kernel version 2.4. Is there any way to run Ubuntu with kernel 2.4?

On another tack, I've discovered I can keep the system from hanging by keeping it occupied. Something like this does the trick:

```
perl -e '@f = <>; while (1) { sort @f; }' </var/log/syslog
```

Can anyone tell me why?

Thanks,
Mike

---

