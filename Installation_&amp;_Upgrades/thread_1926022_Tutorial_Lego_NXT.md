---
title: "Tutorial Lego NXT"
date: 2012-02-15
forum: Installation &amp; Upgrades
---

### Post by gjvnq on 2012-02-15
Tutorial to set up lego NXT. (Tested in Ubuntu 12.04 Alpha 2)
[LIST]
[*]Step 1 (Install udev rules and configure):
[/LIST]
[INDENT]
```

chmod +x setupNxtUSB.v2.sh
sudo ./setupNxtUSB.v2.sh
sudo adduser *(your user name)* legonxt

```
[/INDENT]

[LIST]
[*]Step 2 (The compiler):
[/LIST]
[INDENT]
Visit [http://bricxcc.sourceforge.net/nbc/beta/index.html](http://bricxcc.sourceforge.net/nbc/beta/index.html) and download the last version of nbc compiler avaliable.
[/INDENT]

[LIST]
[*]Step 3 (Your first program):
[/LIST]
[INDENT]
File test.nxc:
```

task main () {
    while (1) {
        OnFwd(OUT_A, 75);
    }
}

```
Than run:
```

./nbc -d -S=usb test.nxc

```
The nbc compiler is in the file have you downloaded.
[/INDENT]

---

