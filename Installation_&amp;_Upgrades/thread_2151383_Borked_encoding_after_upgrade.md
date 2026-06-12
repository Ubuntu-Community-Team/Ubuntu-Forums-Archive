---
title: "Borked encoding after upgrade"
date: 2013-06-04
forum: Installation &amp; Upgrades
---

### Post by Inoki on 2013-06-04
Hi everybody,

I managed to do an upgrade from 12.10 to 13.04 x64 with 98% success, as my character encoding has been messed up. Any ideas how to bring this back to the previous, working state? See attached screenshots. On the left is SMPlayer, on the right Skype, both latest version. On 12.10 characters displayed normally.

---

### Post by dentaku65 on 2013-06-04
Can you please post the output of this command?
```
cat /etc/default/locale
```

---

### Post by Inoki on 2013-06-04
Hey, sure,

```
LANG="sk_SK.UTF-8"LANGUAGE="sk_SK:en_US:en"
LC_NUMERIC="sk_SK.UTF-8"
LC_TIME="sk_SK.UTF-8"
LC_MONETARY="sk_SK.UTF-8"
LC_PAPER="sk_SK.UTF-8"
LC_IDENTIFICATION="sk_SK.UTF-8"
LC_NAME="sk_SK.UTF-8"
LC_ADDRESS="sk_SK.UTF-8"
LC_TELEPHONE="sk_SK.UTF-8"
LC_MEASUREMENT="sk_SK.UTF-8"
```

---

### Post by dentaku65 on 2013-06-05
Seems correct.
Can be an error with Slovak language translation see here [http://ubuntuforums.org/showthread.php?t=2140746](http://ubuntuforums.org/showthread.php?t=2140746)

---

### Post by Inoki on 2013-06-05
> **dentaku65 said:**
> Seems correct.
Can be an error with Slovak language translation see here [http://ubuntuforums.org/showthread.php?t=2140746](http://ubuntuforums.org/showthread.php?t=2140746)
Thanks, that fixed it.

---

### Post by Inoki on 2013-06-15
Just to make sure this would be fixed a bug report has been filed: [https://bugs.launchpad.net/ubuntu-translations/+bug/1191241](https://bugs.launchpad.net/ubuntu-translations/+bug/1191241)

---

### Post by Inoki on 2013-06-21
A **[workaround]("http://ubuntuforums.org/showthread.php?t=2140746&p=12696230#post12696230")** has been suggested, in my case however it doesn't work, as I don't have any locale.gen file on my system. Can anybody advise?

---

### Post by Inoki on 2013-06-23
This [**workaround**]("http://askubuntu.com/questions/310990/borked-encoding-in-ubuntu-13-04-for-slovak-language") fixed it for me.

---

