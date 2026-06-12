---
title: "Dell D510: Live works ok, install does not."
date: 2012-12-03
forum: Installation &amp; Upgrades
---

### Post by stm_tech on 2012-12-03
Hi

Sorry if someone has already answered something similar but I did spend time looking through the forum for a solution.

I have a Dell D510 laptop. Xubuntu 12.10 Live works fine. So I figured I would do an install.

The install finishes, I take the cd out of the drive and awy it goes and reboots.

Then I just get a black screen. Nothing at all appears on the screen.

I have tried to get a console open, nothing.

Any other things I should try?

Paul

---

### Post by stm_tech on 2012-12-03
Ok have now tried a different D510 and get exactly the same problem.

Works fine in live mode. Once installed I just get a black screen.

Have checked disk for defects - no problems.
Have checked memory - no problems.

---

### Post by NikTh on 2012-12-03
> **stm_tech said:**
> Ok have now tried a different D510 and get exactly the same problem.

Works fine in live mode. Once installed I just get a black screen.

Have checked disk for defects - no problems.
Have checked memory - no problems.

Hi , 

have you marked the box "Install 3rd party software" during installation ? 
If yes , then try to install again , **without mark this box. **

Thanks

---

### Post by dannyboy79 on 2012-12-03
from the live cd, can you issue the following so we can see what graphics card you have?

```
lspci
```

OR

```
lshw
```

Sounds like a graphics driver issue, I hate to see this bug happening to so many new users.

---

### Post by Androzani1 on 2012-12-03
Could you try Lubuntu and see if that works?

---

