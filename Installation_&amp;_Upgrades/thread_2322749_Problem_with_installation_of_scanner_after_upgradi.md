---
title: "Problem with installation of scanner after upgrading to Ubuntu 16.04"
date: 2016-04-30
forum: Installation &amp; Upgrades
---

### Post by ahmed50 on 2016-04-30
[COLOR=#333333]Hello,

after upgrading to Ubuntu 16.04 , i couldn't install the driver for my Panasonic KXMB1500 scanner anymore.[/COLOR]

[COLOR=#333333]when i try to install, i get the message:[/COLOR][COLOR=#333333]
  ```
Cannot find SANE lib path
```[/COLOR]

[COLOR=#333333]this is the link of the driver: [/COLOR]http://panasonic.net/pcc/support/fax/common/table/linuxdriver.html[COLOR=#333333]
i downloaded and tried to install: "panamfs-scan-1.3.0-x86_64.tar.gz"[/COLOR]

[COLOR=#333333]I'd appreciate any help,[/COLOR]

[COLOR=#333333]greetings,[/COLOR]

---

### Post by T.J. on 2016-04-30
> **ahmed50 said:**
> [COLOR=#333333]Hello,

after upgrading to Ubuntu 16.04 , i couldn't install the driver for my Panasonic KXMB1500 scanner anymore.[/COLOR]

[COLOR=#333333]when i try to install, i get the message:[/COLOR][COLOR=#333333]
  ```
Cannot find SANE lib path
```[/COLOR]

[COLOR=#333333]this is the link of the driver: [/COLOR]http://panasonic.net/pcc/support/fax/common/table/linuxdriver.html[COLOR=#333333]
i downloaded and tried to install: "panamfs-scan-1.3.0-x86_64.tar.gz"[/COLOR]

[COLOR=#333333]I'd appreciate any help,[/COLOR]

[COLOR=#333333]greetings,[/COLOR]

Did you verify that libsane is installed? 

Quick and easy way: 
[I]
sudo apt-get install libsane[/I]

---

### Post by Artemio_T on 2016-05-25
Just solved this issue on Ubuntu 16.04
the script can't find the folder, so you have 2 options, modify the script, or make as I did, just copy that folder,
```
sudo [COLOR=#111111][FONT=Consolas]cp -a [/FONT][/COLOR][FONT=arial]/usr/lib/x86_64-linux-gnu/sane [/FONT][FONT=arial]/usr/lib/sane[/FONT]
```
now you can install the driver. Good luck.

---

### Post by davemc on 2017-05-07
A link will be more resilient than a copy.  It still solves the problem.

```

sudo ln -s /usr/lib/x86_64-linux-gnu/sane/ /usr/lib/sane
```

The Panasonic PanasonicMFSpushd app also needs

```

sudo apt-get install libusb-0.1-4
```

---

