---
title: "Repository: Which Codenames get updated when?"
date: 2013-02-08
forum: Installation &amp; Upgrades
---

### Post by bronkeydain on 2013-02-08
I have a question about the Ubuntu repository.

Am I correct in saying that codename precise never gets updated.
And any stable update for Precise Pangolin goes in precise-updates.
And any of those updates that are also security updates go to precise-security as well?

Does anybody KNOW this or know where to find info on this?

Thx

---

### Post by Cheesemill on 2013-02-08
Any update that is security related will go in precise-security, all other updates which aren't security related go into precise-updates.

You won't find any update in more than one repository.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Updates](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Updates)

---

### Post by grahammechanical on 2013-02-08
> Am I correct in saying that codename precise never gets updated.

that is only true if you (the user) set Software Sources> Updates> Automatically check for updates = never.

Please see my post on page 2 of this thread.

[http://ubuntuforums.org/showthread.php?t=2113373&page=2]("http://ubuntuforums.org/showthread.php?t=2113373&page=2")

Your question is similar to one of the questions asked there. You can also read about Stable Release Updates, here: Look for the heading "When?" Notice these comments.

> For Long Term Support releases we regularly want to enable new hardware. Such changes are appropriate provided that we can ensure not to affect upgrades on existing hardware. For example, modaliases of newly introduced drivers must not overlap with previously shipped drivers.

New versions of commercial software in the Canonical partner archive.

At the moment the only Ubuntu that can install on Secure Boot enabled machines is Ubuntu 12.10. If that does not change then 12.04 will be obsolete by the release of the next LTS in April 2014. Long before its end of life in April 2017. For Ubuntu 14.04 will surely have a signed kernel in the way that 12.10 has. 

Regards.

---

