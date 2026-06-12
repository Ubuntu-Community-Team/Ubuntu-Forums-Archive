---
title: "Installing Updates 7.10"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by philipluna66 on 2008-04-11
I have managed to install Ubuntu 7.10 Have downloaded all the updates I was happily installing them when I think my screensaver came in. Now they will not install I get the error                                                  E: dpkg was interupted,you must manually run 'dpkg --configure -a' to correct the problem                         . I pasted this command in the terminal window and get dpkg requires superuser privilege. HELP I tried desilecting this item at the update manager but still the same

---

### Post by kellemes on 2008-04-11
> **philipluna66 said:**
> I have managed to install Ubuntu 7.10 Have downloaded all the updates I was happily installing them when I think my screensaver came in. Now they will not install I get the error                                                  E: dpkg was interupted,you must manually run 'dpkg --configure -a' to correct the problem                         . I pasted this command in the terminal window and get dpkg requires superuser privilege. HELP I tried desilecting this item at the update manager but still the same

```
sudo dpkg --configure -a
```

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Pumalite on 2008-04-11
Make me a sandwich
No
sudo make me a sandwich
Yes

---

### Post by philipluna66 on 2008-04-11
THANKYOU ho no SUDO THANKYOU

---

