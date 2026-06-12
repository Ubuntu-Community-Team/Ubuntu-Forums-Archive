---
title: "Upgrade Manager Will Not Load"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by cabotcat on 2011-10-13
Receiving this error when I try to start update manager: 

"Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Read error - read (5: Input/output error), E:The package lists or status file could not be parsed or opened.'

Is this related to everyone crashing the server?

---

### Post by raja.genupula on 2011-10-13
Hi do this 

```
sudo rm -rf /var/lib/apt/lists*
```

```
sudo apt-get update
```

let me know what you got.

---

### Post by cabotcat on 2011-10-13
> **raja.genupula said:**
> Hi do this 

```
sudo rm -rf /var/lib/apt/lists*
```

```
sudo apt-get update
```. 

let me know what you got.

Thanks so much but no need. I simply downloaded the ISO and upgraded in that manner. Everything went fine and I am enjoying 11.10. T

Thank you

---

### Post by ccstark on 2012-04-21
Thanks.  I tried the terminal commands and these resolved my problem: unable to open update/package manager or ubuntu software centre.

---

