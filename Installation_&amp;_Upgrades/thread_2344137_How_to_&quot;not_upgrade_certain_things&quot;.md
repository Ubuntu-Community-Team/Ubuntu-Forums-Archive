---
title: "How to &quot;not upgrade certain things&quot;"
date: 2016-11-22
forum: Installation &amp; Upgrades
---

### Post by big_z2 on 2016-11-22
Hey guys, I have a server that is running on PHP5 and if I run the apt-get update command, it will auto upgrade it to PHP7 which I don't want. However, I still want to upgrade other packages, so is there anyway I can prevent this from happening only for PHP?

---

### Post by ian-weisser on 2016-11-22
See [https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

---

### Post by big_z2 on 2016-11-23
> **ian-weisser said:**
> See [https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

Thank you sir! So for example if I open the terminal and do "apt-mark hold php5.6" is it going to hold everything that PHP5 needs? Also, can I run "apt upgrade" after the hold command?

---

### Post by Dennis N on 2016-11-23
The syntax is **apt-mark hold package**. So the version is not included. 

Ex. **sudo apt-mark hold firefox**

If you then want to see what **apt-get upgrade** will then do w.r.t. packages, you can simulate the upgrade first with the **-s** option. This test does not require sudo and no actual changes are made until you rerun it without the -s.

**apt-get -s upgrade**

---

### Post by ian-weisser on 2016-11-23
> So for example if I open the terminal and do "apt-mark hold php5.6" is it going to hold everything that PHP5 needs? Also, can I run "apt upgrade" after the hold command?

Yes (caveat on package name) and yes.

However, beware: Apt-pinning is an advanced practice. Apt will do exactly what you tell it to do...and sometimes that has thoroughly logical but unexpected results.

For example, pinning to a no-longer supported version of php means your system may become vulnerable to subsequently-discovered vulnerabilities.

I view at pinning as a temporary solution.

---

