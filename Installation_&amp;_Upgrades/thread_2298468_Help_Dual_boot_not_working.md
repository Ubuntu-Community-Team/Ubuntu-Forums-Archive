---
title: "Help Dual boot not working"
date: 2015-10-11
forum: Installation &amp; Upgrades
---

### Post by Darrell_W._Coates on 2015-10-11
Hello, 
        I Installed Win 7, then installed Ubuntu 15.4 as dual boot on HP envy x64 laptop.
when I boot up only Ubuntu starts up.
[http://paste.ubuntu.com/12752597](http://paste.ubuntu.com/12752597)
                                                           Thanks,
                                                                       Darrell

---

### Post by grahammechanical on 2015-10-11
Load into Ubuntu. Open the terminal and run

```
sudo update-grub
```

Does the printout show that a Windows boot loader has been detected? If it does, try restarting. Do you now see an option to load Windows in the boot menu.

Regards.

---

### Post by Darrell_W._Coates on 2015-10-11
I'm getting the option to boot Win 7 Now, working,
                                                                     Thanks,
                                                                                 Darrell

---

