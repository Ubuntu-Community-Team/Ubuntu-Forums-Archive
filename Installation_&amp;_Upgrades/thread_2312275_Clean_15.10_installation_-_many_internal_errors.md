---
title: "Clean 15.10 installation - many internal errors"
date: 2016-02-03
forum: Installation &amp; Upgrades
---

### Post by helm10101 on 2016-02-03
I wiped my whole drive and installed Ubuntu 15.10,
but many times I get internal errors, for example when I press Settings, and it tells me to restart.
I re-installed Ubuntu but it keeps coming. (When re-installing I checked the option to erase ubuntu and re-install)

What might be the problem?

Thanks

---

### Post by howefield on 2016-02-03
Did you check the partition was set for formatting ?

Installing Ubuntu over an existing partition that is not formatted will leave the existing /home folder intact, with all its configuration files.

---

### Post by kansasnoob on 2016-02-03
It would be helpful to know something about your hardware specs so please post the output of these three commands:

```
cat /proc/cpuinfo
```

```
lspci -v -s `lspci | awk '/VGA/{print $1}'`
```

```
free -m
```

---

### Post by grahammechanical on 2016-02-03
> What might be the problem?

The problem is that you are getting internal errors. But what internal errors?

System messages about a crash offer the option to report the crash (which we can decline) but before we do that we can allow the utility to show us some details as to what has crashed and then we can decline to report the crash.

Details might give us a clue.

Regards.

---

### Post by helm10101 on 2016-02-04
Thanks guys, I re-installed again, and suddenly it stopped. next time it will appear again I will post the error output

---

