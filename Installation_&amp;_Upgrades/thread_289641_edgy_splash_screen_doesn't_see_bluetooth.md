---
title: "edgy splash screen doesn't see bluetooth"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by DonKyot on 2006-10-31
I've just done the install, from the command line as per:
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

When it boots normally, my bluetooth mouse & k/b aren't recognised.
If, however, I start in recovery and then do startx - it all works fine... except that I'm loged in as root in single user mode!!

It's a Dell Dimesnsion with dell k/b & mouse.

It was working fine with 6.06. I had to put the Edgy kernel; because dapper didn't recognise my network card; and that worked.

Any ideas?

thanks.

---

### Post by DonKyot on 2006-10-31
no one replied. But incase someone has the same problem.
I have a clash in the bluetooth drivers.
I stuck 'exit 0' at the top of the S25bluetooth rc file - and all is now perfect!
Like really perfect, edgy is working in all ways except b/t :KS

---

### Post by pimlottc on 2006-11-06
You might want to check [this thread](http://ubuntuforums.org/showthread.php?p=1722235) about some people with similar problems.  The folks in that one are all using the Logitech MX 5000, different than yours; although I know Dell have used other rebranded Logitech wireless keyboards and mice in the past, so yours might be practically the same thing.

---

### Post by DonKyot on 2006-11-13
> **pimlottc said:**
> You might want to check [this thread](http://ubuntuforums.org/showthread.php?p=1722235) about some people with similar problems.  The folks in that one are all using the Logitech MX 5000, different than yours; although I know Dell have used other rebranded Logitech wireless keyboards and mice in the past, so yours might be practically the same thing.

Cheers.

Indeed; setting HIDD_ENABLED=1 in /etc/defaults/bluetooth was sufficient to solve my problem.
Somehow, as this affects installation, maybe it should be in the configuration somewhere (maybe it was!) or documented.
Anyway, I'll leave this thread in case someone comes searching for "Dell Dimension 9200 bluetooth keybord mouse boot not working" etc. ;)

---

