---
title: "Feisty installation (desktop i386) hangs while booting installer"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by giovani630 on 2007-04-19
The problem is essentially this:  I boot, and it gets most of the way through, and even gets to a prompt, and then begins loading services:

```

...
Starting powernowd                        [  OK  ]
Starting Bluetooth services

```

It's at this point (it seems before bluetooth services can completely start) that the keyboard stops responding, the cursor continues to blink, however nothing happens.

Does anyone have recommendations?  Is this bluetooth related? (I do not have any bluetooth adapter or devices, I don't assume there is a way to disable this from starting during the install)

---

### Post by askreet on 2007-04-19
This is after the installation, booting for the first time?  Can you reboot into recovery mode?

Thanks,
Kyle

---

### Post by giovani630 on 2007-04-19
This is during initial installation booting ... both with normal install/start live cd and with safe graphics mode.

---

