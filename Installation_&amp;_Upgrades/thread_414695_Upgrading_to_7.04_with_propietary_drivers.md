---
title: "Upgrading to 7.04 with propietary drivers"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by ema on 2007-04-20
Hi guys,
    I'm using Ubuntu 6.10. it's cool and great but I'd like to upgrade to 7.04.
But I have one big question: I'm using binary proprietary nVidia drivers (btw I have Beryl and use wine to play World of Warcraft).
If I upgrade with upgrade manager (or with apt-get) do I get all my system functional again? Doesn't it break anything?
I really like Beryl and my config...I don't want to reinstall all from scratch! :)

What do you suggest me guys?

Thanks in advance,
Ema! ;)

---

### Post by Voland on 2007-04-20
Well, maybe you'll need to reinstall binary proprietary nVidia drivers.

---

### Post by ema on 2007-04-20
So do I have to uninstall Beryl, nVidia drivers, upgrade reinstall nVidia driver and then Beryl again?

Damn,
Shouldn't be easier?

Cheers,
Ema! :)

---

### Post by oldmanstan on 2007-04-20
you might want to wait to ungrade, feisty appears to be a little quirky, i had beryl and proprietary nvidia drivers, i upgraded and now the xserver won't start no matter what i do, just a suggestion, maybe wait a couple days until they have the bugs identified

---

### Post by ema on 2007-04-20
Yeah indeed I was planing to upgrade into one month or at least 2 weeks...but should I theoretically update just pressing the button or just doing that mess to uninstall drivers and applications and then reinstall them?

Cheers,
Ema! :)

---

### Post by ema on 2007-04-20
So does noone knows about automatic nVidia drivers update?
Do I really have to uninstall them?

Thanks,
Ema! :)

---

### Post by dank277 on 2007-04-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/restricted-manager/+bug/108128](https://bugs.launchpad.net/ubuntu/+source/restricted-manager/+bug/108128) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				See my bug on this.  In hindsight, it would probably be best to uninstall the nvidia drivers before upgrade, do the upgrade, the install the nvidia drivers thru the repos and/or the Restricted-manager.  The benefits of this are:

1) No more breaking on future updates to the kernel:
2) Support from the ubuntu people directly;
3) able to bug report to launchpad if something goes wrong.

---

### Post by ema on 2007-04-21
So maybe would it be better to install a fresh 7.04 or just uninstall drivers, switch to metacity (instead of Beryl that shouldn't run without 3D support :P) and then do the upgrade?

Then after upgrade install 3D drivers and restore Beryl?

Cheers,
Ema! :)

---

