---
title: "[dual boot]How do I select windows 7 in boot  menu?"
date: 2015-02-01
forum: Installation &amp; Upgrades
---

### Post by ephraim4 on 2015-02-01
okay,i did not get the boot screen to choose the os,it used to directly go to win 7
now after grub repairing,it directly goes to ubuntu!
how to i get the option to fix it?
[New user]

---

### Post by Bucky Ball on 2015-02-01
Welcome. You mean you are getting no options to choose an operating system at boot? If not, restart the machine and hold down shift after the manufacturer's splash screen at boot. That should bring up the grub menu with Windows on it. 

To make it permanent, so you see the options at every boot, open a terminal in Ubuntu and type:

```
sudo nano /etc/default/grub
```

Change the first four lines of that file to look like this:

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
```

Now you should be able to select OS on every restart/boot. If Windows is not on that list, try:

```
sudo update-grub
```

Reboot and see if it has found Windows (you should be able to tell by the output of that command as grub checks for other OSs).

---

### Post by fantab on 2015-02-02
> **ephraim4 said:**
> okay,i did not get the boot screen to choose the os,it used to directly go to win 7
now after grub repairing,it directly goes to ubuntu!
how to i get the option to fix it?
[New user]

We need more info regarding your boot process.
Install [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") tool -> '**create Bootinfo Summary**' -> note the url link to bootinfo file and post the link back here.
That should give us most of the info we need.

---

### Post by ephraim4 on 2015-02-02
> **fantab said:**
> We need more info regarding your boot process.
Install [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") tool -> '**create Bootinfo Summary**' -> note the url link to bootinfo file and post the link back here.
That should give us most of the info we need.
paste.ubuntu.com/10006067

---

### Post by ephraim4 on 2015-02-02
> **Bucky Ball said:**
> Welcome. You mean you are getting no options to choose an operating system at boot? If not, restart the machine and hold down shift after the manufacturer's splash screen at boot. That should bring up the grub menu with Windows on it. 

To make it permanent, so you see the options at every boot, open a terminal in Ubuntu and type:

```
sudo nano /etc/default/grub
```

Change the first four lines of that file to look like this:

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
```

Now you should be able to select OS on every restart/boot. If Windows is not on that list, try:

```
sudo update-grub
```

Reboot and see if it has found Windows (you should be able to tell by the output of that command as grub checks for other OSs).
Thanks a lot mate!
I dont know how to thankyou! :KS:KS

---

### Post by Bucky Ball on 2015-02-02
A pleasure. Sounds like it's all working so that is good news. Good luck and enjoy the ride. ;)

---

