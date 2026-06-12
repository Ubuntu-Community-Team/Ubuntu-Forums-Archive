---
title: "Not all updates can be installed"
date: 2009-02-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by MountainX on 2009-02-08
I'm running 9.04 on my laptop. A few days ago I got a message that "Not all updates can be installed". From past experience I thought this might resolve if I waited a few days. I did not run the partial upgrade. However, it has been 3 days and I still get the same message.

In Update Manager, the packages that are unchecked are all Evolution-related. When I looked at LaunchPad previously, I did not see that Evolution was being built.

Can anyone tell me why I'm not able to do a full update? Should I run a partial upgrade?

Thanks

---

### Post by taurus on 2009-02-08
You should post your problems in the jaunty's subforum.

[http://ubuntuforums.org/forumdisplay.php?f=352](http://ubuntuforums.org/forumdisplay.php?f=352)

---

### Post by cariboo on 2009-02-08
I have asked the mods to move this thread to Jaunty Testing and Disscussion.

The reason you can't install some updates is that are dependencies missing, just give it time and they will install.

Edit: If you really want to do a partial upgrade, open a terminal and type:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

Jim

---

### Post by Rocket2DMn on 2009-02-08
Moved to Jaunty Jackalope Testing and Discussion.

---

### Post by Slug71 on 2009-02-08
No dont do a partial upgrade.

I also still have blocked updates.

Welcome to Alpha testing. ;)

---

### Post by MountainX on 2009-02-08
> **Slug71 said:**
> No dont do a partial upgrade.

I also still have blocked updates.

Welcome to Alpha testing. ;)

Thanks. I know from previous experience that partial upgrades can be a problem. I just didn't realize that this situation would persist for so many days. But I can wait. It's no problem.

---

