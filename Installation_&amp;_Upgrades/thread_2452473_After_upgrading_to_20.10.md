---
title: "After upgrading to 20.10"
date: 2020-10-22
forum: Installation &amp; Upgrades
---

### Post by paulgureghian on 2020-10-22
Something went wrong with the nvidia driver and now I get 'oh no something has gone wrong'

How to recover or get back to 20.04

---

### Post by CelticWarrior on 2020-10-22
> [COLOR=#000000]Something went wrong with the nvidia driver [/COLOR]
What? What are the symptoms?

> [COLOR=#000000]and now I get 'oh no something has gone wrong'[/COLOR]
Where?

> [COLOR=#000000]How to recover or get back to 20.04[/COLOR]
No way. Only a fresh installation would do it but that's probably no necessary if we get to the bottom of the problem.
In summary, please avoid such vague and incoherent descriptions. Please describe the actual problem you're noticing.

---

### Post by QIII on 2020-10-22
There is no path backwards.  You will have to re-install 20.04.

I recommend staying away from development versions on a "daily driver" unless you are well-versed and can tolerate the breakage that naturally occurs during development.

---

### Post by grahammechanical on 2020-10-22
Do you get the Grub boot menu? Select Advanced Options for Ubuntu and then select a Linux kernel with Recovery Mode. At the Recovery menu select Resume. That will load Ubuntu with a basic video driver.

At the Ubuntu desktop open Software & Updates>Additional Drivers tab and deselect the Nvidia driver. Now when you reboot Ubuntu will load with the Noveau open source video driver. That may prove satisfactory. Or, you can select Additional Drivers again and let it search for a Nvidia driver.

Regards

---

### Post by cigtoxdoc on 2020-10-25
There is a better way here.  Do a Ctrl-Alt F2.  Then sudo apt-get autoremove --purge nvidia-340.  Found this on askubuntu.  Fortunately, I  had my Samsung S9+ next to me and was practiced in its use as a substitute for my DELL VOSTRO 3500.  

John

---

### Post by CelticWarrior on 2020-10-26
> [COLOR=#000000]Then sudo apt-get autoremove --purge nvidia-340[/COLOR]
How do you know the OP has the same driver version?

---

### Post by cigtoxdoc on 2020-10-27
During the upgrade, there were several occurrences where the upgrade tried to install the nVidia driver and  then reversed itself.  When upgrade was done, and PC rebooted, login kept repeating even though correct password was entered.  As I reported, the solution came from askubuntu.  John

---

### Post by CelticWarrior on 2020-10-27
Again... How do you know the OP has the same driver version, a necessary condition for that to be a solution?
It may have been a solution for you, it isn't for everybody else.

---

