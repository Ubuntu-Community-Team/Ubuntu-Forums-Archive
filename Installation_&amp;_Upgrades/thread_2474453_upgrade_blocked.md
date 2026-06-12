---
title: "upgrade blocked"
date: 2022-04-29
forum: Installation &amp; Upgrades
---

### Post by shaviro on 2022-04-29
Whenever I try to upgrade from 21.10 to 22.04, I get the following:

steven@steven-Meerkat:~$ sudo do-release-upgrade
Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.

However, as far as I can tell, all available updates have in fact been installed. Why can I not upgrade?

---

### Post by guiverc on 2022-04-29
I'd perform

```
sudo apt update
```

to update your software lists, and scan/read the output to ensure no lines are missing, or potential issues are seen there, then

```
sudo apt full-upgrade
```

to ensure all upgrades are performed.  There are cases where `apt upgrade` cannot install upgrades as per the manual; which is why the `full-upgrade` command exists (or `dist-upgrade` using `apt-get` terminology).

Did you use `full-upgrade` ?   or potentially leave some behind using only `upgrade`?  

If that reveals nothing, I'd ensure you've not put any holds on packages, ie.

```
apt-mark showhold
```

but I'd have expected prior commands would have revealed that.

---

### Post by shaviro on 2022-04-29
Turned out there was an update (system76-power, since I have a System76 machine) that was "withheld" for some reason. I force installed it, and then the upgrade to 22.04 worked fine.

---

