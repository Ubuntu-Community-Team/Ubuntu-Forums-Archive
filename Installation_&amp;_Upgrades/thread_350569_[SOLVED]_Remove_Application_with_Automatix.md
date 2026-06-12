---
title: "[SOLVED] Remove Application with Automatix"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by Cariboo1938 on 2007-01-31
Hello all,
How can I remove an installed application completely?

I installed FrostWire using Automatix and I didn't like it. 
So, again using Automatix, I uninstalled it. 
When I check the menu under 
-->Applications -->Internet, the entry "FrostWire (32bit)" is still there.
Of course, if I click on it, I get the message: 'Could not launch menu item.'

How can I remove the item "FrostWire" 
or any item of a not installed application) 
from the menu?

---

### Post by jackrobinson on 2007-01-31
> **Cariboo1938 said:**
> Hello all,
How can I remove an installed application completely?

I installed FrostWire using Automatix and I didn't like it. 
So, again using Automatix, I uninstalled it. 
When I check the menu under 
-->Applications -->Internet, the entry "FrostWire (32bit)" is still there.
Of course, if I click on it, I get the message: 'Could not launch menu item.'

How can I remove the item "FrostWire" 
or any item of a not installed application) 
from the menu?
```

sudo rm -f /usr/share/applications/frostwire.desktop
```

---

### Post by Cariboo1938 on 2007-01-31
> **jackrobinson said:**
> ```

sudo rm -f /usr/share/applications/frostwire.desktop
```Thanks a lot Jackrobinson, it worked.:)  How do I know/find the location and name of the item to be removed?


EDIT:
[COLOR="Red"][SIZE="3"]In between
I learned that 
***[COLOR="DarkOrchid"]"sudo rm -f /<anything>" [/COLOR]***
is a command which should **_only_** be used by **_advanced_** users of Linux systems!
Misuse can ruin your system easily and totally!
So, be careful, please![/SIZE][/COLOR]

---

### Post by jackrobinson on 2007-01-31
> **Cariboo1938 said:**
> Thanks a lot Jackrobinson, it worked.:)  How do I know/find the location and name of the item to be removed?
use alacarte to edit and maintain menu items
```
sudo apt-get install alacarte
```
When you become a slightly more advanced user you can fiddle around with **.desktop** files in */usr/share/applications* , */usr/local/share/applications* etc..

---

