---
title: "Trying to install Ubuntu on a Asus T102h  -- HELP"
date: 2020-02-05
forum: Installation &amp; Upgrades
---

### Post by onetearfalls on 2020-02-05
[COLOR=#1A1A1B][FONT=&amp]Trying to install Ubuntu 18.04 on a Asus T102h and am getting this error on attempting to boot from live USB.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Hellllllpppppp [https://imgur.com/gallery/fmdXOPG](https://imgur.com/gallery/fmdXOPG)[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]I have tried both mint and Ubuntu. Same error. Not sure if it could be a Debian issue or not.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Thanks in advance[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]Dan[/FONT][/COLOR]

---

### Post by CatKiller on 2020-02-05
It looks to me like you're booting your machine in UEFI mode, but you didn't boot your install media in UEFI mode, which means that it assumed you wanted it installed as a Legacy/BIOS install. Either booting your install media as UEFI and installing it to your UEFI machine (which would be the best option) or switching your machine into Legacy/BIOS mode to be able to run your Legacy/BIOS install should work.

I can't remember if it's Asus where you need to jump through some hoops to get the Secure Boot side of things working as they should, too. It's definitely one manufacturer whose name begins with A. You need to set a password and stuff to establish "trust" before anything works.

---

### Post by oldfred on 2020-02-05
Its Acer that needs 'trust'.

Lightweight tablet type systems may work better with a lighter weight flavor.
Light weight flavors
Lubuntu, xubuntu, Ubuntu MATE, Budgie
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

[https://ubuntuforums.org/showthread.php?t=2416522](https://ubuntuforums.org/showthread.php?t=2416522)
[https://ubuntu-mate.community/t/18-04-lts-on-asus-t102ha-tablet-review/18461](https://ubuntu-mate.community/t/18-04-lts-on-asus-t102ha-tablet-review/18461)
[https://blog.shuningbian.net/2018/08/ubuntu-1804-on-asus-transformer-mini.html](https://blog.shuningbian.net/2018/08/ubuntu-1804-on-asus-transformer-mini.html)

---

### Post by CatKiller on 2020-02-05
> **oldfred said:**
> Its Acer that needs 'trust'.

Thanks. That would have been bugging me.

---

