---
title: "Tips of how to updade 10.10 without accidentally upgrading to 11.04"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by Rouward on 2011-01-07
This was happend to me 2 days ago when updating Ubuntu 10.10 and I didn't notice that 10.10 was unintentionally upgraded to 11.04. After uninstalling 11.04 and reinstalling 10.10, I made a basic tips on how to update your 10.10 without upgrading to 11.04:

Simply install some "Important Security Updates" only in Update Manager.

---

### Post by zvacet on 2011-01-07
I don´t know what went wrong in your case,but AFAIK it is not possible to upgrade from update manager (or from CLI) to alpha version.If you use update manager you will always get updates for release you have installed.Same thing with CLI;if you type

```
sudo apt-get update && sudo apt-get upgrade
```

you will just find newer version of packages but your release version will still be the same.

---

### Post by efflandt on 2011-01-08
I would think it would be impossible to update from 10.04 to 11.04 at this time.  But I did notice after upgrading Lucid on a USB hd that **System** > **About Ubuntu** came up saying I was running 11.04, even though I was not.  So maybe you were fooled by that.

I knew it was not really 11.04 because the login did not have both "Ubuntu Desktop" and "Ubuntu Classic Desktop", and **cat /etc/*release** said 10.10 and Maverick.

I am running Natty from an internal SSD, so I know what that looks like.

---

### Post by LuigiAntoniol on 2011-01-09
Related:

Am running 10.04 - 64bit.

I have noticed, when I added the 10.10 repos to synaptic, that there are tons of upgrades.

1) If I installed those upgrades from 10.10 into 10.04, would I damage / break my system?
2) Would there be incompatibility / stability / security issues?
3) Would my 10.04 "convert" itself into 10.10 and thereby lose it's LTS?

Thanks in advance.

---

### Post by dino99 on 2011-01-09
> **LuigiAntoniol said:**
> Related:

Am running 10.04 - 64bit.

I have noticed, when I added the 10.10 repos to synaptic, that there are tons of upgrades.

1) If I installed those upgrades from 10.10 into 10.04, would I damage / break my system?
2) Would there be incompatibility / stability / security issues?
3) Would my 10.04 "convert" itself into 10.10 and thereby lose it's LTS?

Thanks in advance.

Dont do that, there are too many differences
instead you can get recent packages from backport: install this ppa

[https://launchpad.net/~maverick-bleed/+archive/ppa](https://launchpad.net/~maverick-bleed/+archive/ppa)

---

### Post by LuigiAntoniol on 2011-01-10
@dino99

Thanks for the heads up.  I think I came close to really messing up my system.

Will look at the url you gave.

---

