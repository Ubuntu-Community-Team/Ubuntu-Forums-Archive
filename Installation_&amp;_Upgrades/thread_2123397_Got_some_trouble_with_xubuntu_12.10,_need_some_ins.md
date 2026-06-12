---
title: "Got some trouble with xubuntu 12.10, need some insight"
date: 2013-03-07
forum: Installation &amp; Upgrades
---

### Post by livingdanger on 2013-03-07
I just went and upgraded to the 12.10, but the 12.10 has half the programs that were pre-installed on 12.04. It also doesn't come with java pre-installed (although it acts like it does) which sucks to install (newbie here). I did do a clean wipe and re-install not a 'upgrade', does that matter? I could really use some help on how to upgrade, I like 12.10 its cleaner and it doesn't have some of the glitches 12.04 has (although 12.10 did lock up their customizations abilities). Should install 12.04 set it up then do a upgrade to 12.10, becuase for the life of me I don't know how to install some of the left out software (i.e. java)

Thanks

---

### Post by ptn107 on 2013-03-07
```
sudo apt-get install openjdk-7-jre
```

---

### Post by livingdanger on 2013-03-08
Thanks alot that worked I also installed the plugin as well, since terminal suggested it, which seemed to be the problem. I still wonder why 12.10 didn't have all the default software that 12.04 does.

---

### Post by plucky on 2013-03-09
> **livingdanger said:**
> Thanks alot that worked I also installed the plugin as well, since terminal suggested it, which seemed to be the problem. I still wonder why 12.10 didn't have all the default software that 12.04 does.

See [Ubuntu-restricted-extras](https://help.ubuntu.com/community/RestrictedFormats)

Use the "Software Centre" to install ubuntu-restricted-extras or the terminal.

No Ubuntu/Kubuntu/Xubuntu has "restricted-extras" installed as default.

Good Luck

---

### Post by ptn107 on 2013-03-10
I did a quick comparison of the default packages installed with 12.04.2 and 12.10.  Neither installs java by default.

---

### Post by livingdanger on 2013-03-15
I just re-installed 12.04 and yes it does come pre-installled with java 6 not the plugin which appears to be what I was missing.

---

