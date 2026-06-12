---
title: "[SOLVED] 6.06 to 7.10?"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by joshdudeha on 2008-01-23
This might sound stupid, 
but I've had 6.06 dapper for like 1 and a half years, and due to internet trouble with it, have never been able to update it.
My question is:
Can I upgrade from 6.06 to 7.10?
Because I feel I need to, but I really don't want to go through installation process again, especially when my Windows is very unstable.
Is there any way I can update ubuntu through itself?
Like run a command that will update it to 7.10 without affecting the partitions and installation configurations?
Please help, I know it might sound stupid, but I just want to see.
Thanks!

---

### Post by housam on 2008-01-23
I think you've to upgrade gradually. i.e. 6.06 >> 6.10 >> 7.04 >> 7.10. but be careful and back-up your data first cuz you may have disturbances through the operation.

I prefer to a clean install on the same drive of 6.06.

---

### Post by dgray_from_dc on 2008-01-23
> **housam said:**
> I think you've to upgrade gradually. i.e. 6.06 >> 6.10 >> 7.04 >> 7.10. but be careful and back-up your data first cuz you may have disturbances through the operation.

I prefer to a clean install on the same drive of 6.06.

I agree with backing up your data.  I don't know about the gradual upgrade.  It's probably the most cautious option.

In order to upgrade without a web connection, you simply need to burn a 7.10 CD and add it to your repos in /etc/apt/sources.list

This can be done in Synaptic.  Once done, mark all upgrades and watch it go.

Anyone, correct me if I'm wrong.

---

### Post by housam on 2008-01-23
> **dgray_from_dc said:**
> I agree with backing up your data.  I don't know about the gradual upgrade.  It's probably the most cautious option.

In order to upgrade without a web connection, you simply need to burn a 7.10 CD and add it to your repos in /etc/apt/sources.list

This can be done in Synaptic.  Once done, mark all upgrades and watch it go.

Anyone, correct me if I'm wrong.

I've never tried your way . It may work , I don't Know. but I've said gradually for the upgrading through the web.

---

### Post by joshdudeha on 2008-01-23
yeah ive done a bit of research,
and ill gradually upgrade, as i love ubuntu and dont want to mess it already.
I might do an upgrade a day.
Thanks for the help
*marks as solved.*

---

