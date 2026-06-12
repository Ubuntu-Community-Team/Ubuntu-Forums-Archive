---
title: "[SOLVED] installation trouble -- ubuntu 7.10"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by rafaelsaraiva on 2008-02-26
first of all, hi.
second, sorry for my jamaican english.

i really-really want to migrate to ubuntu, and say goodbye to ruindows
[how we call in brazil... ruim = bad in portuguese] but i'm having some troubles. i tried first with wubi installer for three times and didn't work... actually, vista crashed all the three attempts and was necessary to use the recovery disk. ok, it's a beta version, i know. 

so, now i'm trying to 'dual-boot with vista installed first', following this tutorial: [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

i shrunk the HD following the tutorial,
then downloaded the iso for ubuntu7.10_desktop_amd64.
after burning the live-cd, i booted from CD,
tested it, and no troubles were founded.
so i choose install ubuntu, but the screen get's black. i tried to hit 'esc' and notting happens. i tried to choose install in 'safe mode', and black screen appears again...

i have a hp laptop -- pavilion dv6000
amd turion 64 x2 mobile technology TL-60 2.0Ghz
2.0GB ram / 140GB HD
nvidia geforce go 6150
with vista home premium

any sugestion?
thanks!
_ _ _



  [/SIZE][/FONT]

---

### Post by Pumalite on 2008-02-26
[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))
[http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/](http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/)
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

---

### Post by rafaelsaraiva on 2008-02-27
solved!

it works, with adding 'noapic nolapic' to kernel at boot.

thank you.

---

### Post by Pumalite on 2008-02-27
You are welcome. Good luck.

---

