---
title: "No USB-charge after upgrading to Feisty"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by Evil Dax on 2007-05-09
I have recently upgraded to Feisty,
and now my cellphone will not charge anymore via USB-port
Under Edgy it was charging OK, and under WinXP it still functions, so it is not hardware related.
I have tried the littly thingy 'acharge' to set max. current to 500mA.
It does bleep once, charge light goes on for 1/2 second, and then off again...
Any ideas on what this can be?

PC is running Feisty on Abit NF7-S.

---

### Post by fotios on 2007-05-09
Normally, in a Desktop PC, the usb charger is always on. In laptops, for power saving reasons, the usb charger is off, unless you activate it with an utility or alike. It seems that your system, for power savings reasons has deactivated the usb charger. You should look in the power saving settings and change this setting. Good Luck!

---

### Post by Evil Dax on 2007-05-09
All I can find on Power Management is that it is configured as 'never put to sleep' and since it is a desktop and not a notebook, battery savings aren't available anywhere in my settings.
:(

---

### Post by davim on 2007-05-11
I have the same problem... :(

---

### Post by paleocybernetic.net on 2007-05-18
$ python

import commands, time
while True:
     commands.getstatusoutput("bcharge")
     time.sleep(1)

---

### Post by Evil Dax on 2007-05-23
I've tried, but:
```

$ sudo python
Python 2.5.1 (r251:54863, May  2 2007, 16:56:35) 
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import commands, time
>>> while True:
... commands.getstatusoutput("bcharge")
  File "<stdin>", line 2
    commands.getstatusoutput("bcharge")
           ^
IndentationError: expected an indented block
>>> time.sleep(1)
>>> 

```

:(

---

