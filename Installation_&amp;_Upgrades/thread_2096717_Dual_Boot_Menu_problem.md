---
title: "Dual Boot Menu problem"
date: 2012-12-20
forum: Installation &amp; Upgrades
---

### Post by alexisantonakis on 2012-12-20
I successfully installed Win XP and Ubuntu 10.04 on my laptop

I was trying to clear up some of the additional boot options created,and by mistake deleted the option to boot WinXP, all I have now is Ubuntu and Ubuntu safe mode.

I know that XP is still there and everything set up fine, I just need to know how to bring the WinXp option back onto the boot menu.

Any suggestions please?

I would prefer not to have to reinstall xp and ubuntu if possible, but if that is the only way....

Many thanks
Alexis

---

### Post by papibe on 2012-12-20
Hi alexisantonakis.

I see a couple of options:

Update your grub menu by re scaning your disk:
```
sudo update-grub
```
Then restart your machine. That should do it.

Another option is to use the Ubuntu installation media and using it as a Live CD/USB. Choose the option 'Try Ubuntu'. Once you are on the Desktop, use Boot-Repair to fix your boot options (check this [tutorial]("https://help.ubuntu.com/community/Boot-Repair") for details).

Hope it helps. Let us know how it goes.
Regards.

---

### Post by alexisantonakis on 2012-12-20
> **papibe said:**
> Hi alexisantonakis.

I see a couple of options:

Update your grub menu by re scaning your disk:
```
sudo update-grub
```
Then restart your machine. That should do it.

Another option is to use the Ubuntu installation media and using it as a Live CD/USB. Choose the option 'Try Ubuntu'. Once you are on the Desktop, use Boot-Repair to fix your boot options (check this [tutorial]("https://help.ubuntu.com/community/Boot-Repair") for details).

Hope it helps. Let us know how it goes.
Regards.

Many thanks for the speedy response.

No joy on the first option....the directory which stores the info for the boot options is where I deleted it from in error...can;t remember the path but they had numbers before the options

As for the second one..tried that and nothing happen except it appears I now have two version of Ubuntu on my boot menu!

Anymore suggestions please?

---

### Post by alexisantonakis on 2012-12-20
Got it sorted now.

Ended up using 'Grub Customizer'
Changed the second Ubuntu entry to point to the partition that WinXP was on, and then renamed it..voila.

Thanks again for the response

Alexis

---

