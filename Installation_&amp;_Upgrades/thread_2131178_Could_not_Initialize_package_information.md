---
title: "Could not Initialize package information"
date: 2013-04-01
forum: Installation &amp; Upgrades
---

### Post by untoms on 2013-04-01
i usung ubuntu 12.04 LTS, i got error nitifications:

'E:Unable to parse package file /var/lib/apt/lists/id.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages (1), E:The package lists or status file could not be parsed or opened.'

could anybody in this forum help to fix my problem.

im sory if my english not good :)

---

### Post by ibjsb4 on 2013-04-01
Hi untoms, welcome to the forums :)

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and run these three commands one at a time.

```
sudo rm -r /var/lib/apt/lists/*
sudo mkdir /var/lib/apt/lists/partial
sudo apt-get update
```

That should fix it.

---

### Post by untoms on 2013-04-08
yea, i love this forum
thanks @ibjsb4 for helping me :D

---

### Post by Lloyd Cary on 2013-04-28
*****

  [COLOR=#b22222][FONT=comic sans ms]THANKS a LOT!  This really helped! [/FONT][/COLOR] :KS


[LIST]
[*] 
[/LIST]

---

