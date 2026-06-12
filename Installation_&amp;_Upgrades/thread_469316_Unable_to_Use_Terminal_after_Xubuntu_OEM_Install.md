---
title: "Unable to Use Terminal after Xubuntu OEM Install"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by techdude2007 on 2007-06-09
I installed the Xubuntu 7.04  OEM Install from the alternate CD, that I downloaded from XUbuntu.org.  When I logged in, I went to Accessories > Terminal to type in:

sudo oem-config-prepare

However, when I clicked the Terminal icon, the screen went black.  The terminal appeared for a second, then disappeared and the login screen for XUbuntu appeared.  After I typed in my login information, the system logged in and nothing else happened.

Any ideas?  I logged in as oem.

Thanks

---

### Post by taurus on 2007-06-09
Press <Ctrl><Alt>F2 and log in with with oem and the password.  Then at the prompt, run that command again.

```
sudo oem-config-prepare
```

---

### Post by techdude2007 on 2007-06-10
That part worked..its just that when I go Applications > Accessories > Terminal...the terminal does not open in a Window inside of Xubuntu 7.04.  Instead it closes the GUI, displays the boot information and then displays the login GUI for Xubuntu 7.04.

---

### Post by taurus on 2007-06-10
Are you able to log into the new account that you've just created when you ran that command?  Remember, there is no oem account anymore so you can't log in with username oem at this point.

---

