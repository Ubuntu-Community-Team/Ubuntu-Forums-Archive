---
title: "Dual booting from 2 drives"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by coryy21 on 2011-02-28
I am new to Linux and was wondering how to make dual booting Windows and Ubuntu from 2 separate drives work. I have dual booted from the same drive but never different ones. If I install Ubuntu on the second drive how will I configure the system to let me choose on start up? Some step by step instructions would be greatly appreciated.

---

### Post by Dutch70 on 2011-02-28
There is certainly more than one way to do it, but the easiest is probably to unplug your hdd with windows on it, and install Ubuntu to the other one by selecting "erase & use entire disk" during the install.

after the install is complete, boot into Ubuntu to make sure everything works. Shut down & Plug your windows hdd in and during the bios screen hit escape to select the hdd device to boot from. Boot into the hdd with Ubuntu. 

Open a terminal & type in...
```
sudo update-grub
```

reboot and both your OS's should show up.

Thats what worked for me anyway, and I now boot 6 diff OS's on 2 hdd's.
Take your time & you'll have fun with it.

---

### Post by coryy21 on 2011-02-28
Thanks alot!

---

### Post by Dutch70 on 2011-03-01
> **coryy21 said:**
> Thanks alot!

You're welcome!

Let us know how it works out for you.

---

