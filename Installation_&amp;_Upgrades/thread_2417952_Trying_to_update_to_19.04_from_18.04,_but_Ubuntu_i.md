---
title: "Trying to update to 19.04 from 18.04, but Ubuntu is trying to update me to 18.10"
date: 2019-04-29
forum: Installation &amp; Upgrades
---

### Post by ytterbious on 2019-04-29
Whenever I run ```
sudo apt update
```, ```
update-manager
``` or ```
sudo do-release-upgrade
```, I get packages for 18.10 instead of 19.04. Under Software & Updates > Notify me of a new Ubuntu version, I have selected "For long-term support versions", but when I look under Software & Updates > Other Software, everything is also for cosmic instead of dingo.

---

### Post by oldos2er on 2019-04-29
The next LTS release is 20.04 (i.e. released in April 2020), so it's working like it should.

---

### Post by rrbrussell on 2019-04-29
Upgrades can be from

1: LTS to LTS + 1

2: LTS to Non-LTS + 1

3: Non-LTS to Non-LTS + 1

You are trying to go from LTS to Non-LTS + 2 which is not supported. Your options are upgrade to Non-LTS + 1 and then upgrade again or backup /home and your installed package list and then reinstall.

---

### Post by dolios on 2019-04-30
> **rrbrussell said:**
> Upgrades can be from

1: LTS to LTS + 1

2: LTS to Non-LTS + 1

3: Non-LTS to Non-LTS + 1

You are trying to go from LTS to Non-LTS + 2 which is not supported. Your options are upgrade to Non-LTS + 1 and then upgrade again or backup /home and your installed package list and then reinstall.

Sorry for asking noob question but could you please post the commands for doing this I am also interested

---

### Post by ytterbious on 2019-04-30
Ah I see, thanks for the clarification mate

---

### Post by Rubi1200 on 2019-04-30
Best practice before ANY upgrade is backup all your important data to an external source in case something goes wrong.

Everyone has a slightly different take on the best way to perform upgrades and if you browse this forum you will find countless tales of woe when it comes to upgrades.

I prefer backing up and then doing a clean install each time but as long as you have a solid backup then upgrading from version to version "should" go smoothly in most situations.

Just stick to the official repos and don't add outside sources or untrusted PPAs since those often mess up upgrades.

---

### Post by DuckHook on 2019-04-30
> **Rubi1200 said:**
> …Just stick to the official repos and don't add outside sources or untrusted PPAs since those often mess up upgrades.
&#8593; +1 &#8593;

Note: Even *trusted* PPAs can mess up an upgrade. As a new user, best to avoid *all* PPAs. At least, remove each and every one of them prior to upgrading. Put your system back to as pristine a state as possible. No multiple DEs. No oddball system configs, replacement windows managers, system utilities, etc.

---

### Post by Impavidus on 2019-04-30
> **rrbrussell said:**
> Upgrades can be from

1: LTS to LTS + 1

2: LTS to Non-LTS + 1

3: Non-LTS to Non-LTS + 1

You are trying to go from LTS to Non-LTS + 2 which is not supported. Your options are upgrade to Non-LTS + 1 and then upgrade again or backup /home and your installed package list and then reinstall.

That's not the clearest way to explain it and not entirely true. When set to upgrade to LTS releases only, you can upgrade to the next LTS release about 3 months after it's released. When set to upgrade to any release, you can upgrade to the next supported release. When your current release reaches end of life, your upgrade options are frozen, but you should avoid that point. And when the release to which you were about to upgrade reaches end of life too, it's not very likely the upgrade will work.

Although I'm not enirely sure whether "upgrade to any release" on 16.04 currently sends you to 18.04 or to 18.10.

So the upgrade tool will offer to upgrade 18.04 to 19.04, but only after 18.10 reaches end of life.

---

