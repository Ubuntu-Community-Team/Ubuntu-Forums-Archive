---
title: "Help please: Lost connection in mid-install of frostwire"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by hedgeborn on 2009-11-17
I apologize if I'm not in the right forum. I'm a real newb so forgive me, not sure what info is relevant.

The system:  Dell Inspiron 2100 running Ubuntu 8.10

The problem: Began running frostwire-4.18.4.i586.deb installer, left the machine while it was looking for/downloading dependencies and machine went to sleep breaking the network connection. Came back and the install dialog window was just stalled, going nowhere, could not close it or anything. Rebooted the machine, not being sure what else to do. Now the installer will not run, tells me this:

[IMG]http://i49.tinypic.com/256wzf9.png

When I open Synaptic Package manager, it tells me this:

[IMG]http://i47.tinypic.com/29lbkac.png

:-(

Not sure what my next move is here, guys. If there is any other info I can give you like logs or something that would be helpful, just let me know. I'm stuck. Don't really know my way around the terminal, I'm one of those Linux netbook newbs. :redface: But I can follow directions...

Thanks in advance for your kind assistance.

---

### Post by mikewhatever on 2009-11-17
Close all open windows, then open Applications->Accessories->Terminal and copy in the following command:

```
sudo dpkg --configure -a
```

enter your password and let it run. Hope it helps.

---

### Post by hedgeborn on 2009-11-18
Haha who knew it was as simple as just doing what the computer was telling me to. That worked! Thanks again for the help. :D

---

