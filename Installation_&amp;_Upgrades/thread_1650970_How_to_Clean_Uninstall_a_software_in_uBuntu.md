---
title: "How to Clean Uninstall a software in uBuntu?"
date: 2010-12-22
forum: Installation &amp; Upgrades
---

### Post by TweFoju on 2010-12-22
Ok, if in Windows, we have something like Revo Uninstaller, or Your Uninstaller Pro, that completely remove left over files that were not removed by normal uninstall program

how is the case in uBuntu? is there such software that is similar to those 2? 

also i have a 2nd question

i have a ATi 5650 vga on my laptop, and after i install uBuntu 10.10, the Additional Driver already have the AMD/ATI Proprietary FGLRX graphics driver included, only thing is, it's not active by default

i want to use the CCC 10.11 that i downloaded from the AMD website, 
so in this case, do i have to uninstall that FGLRX driver off my system 1st? because in Windows, it's critical that you completely remove the previous driver before you install the new one right?

sorry if this is a common question, but i searched, not finding any answer yet

Thank you in advance!

---

### Post by karthick87 on 2010-12-22
```
sudo apt-get remove --purge <packagename>
```

---

### Post by TweFoju on 2010-12-22
> **karthick87 said:**
> ```
sudo apt-get remove --purge <packagename>
```
what is the difference if i just go to Synaptic Package Manager, then select the Package, and select " Mark for complete removal" ?

and why is all the package cant be removed? i mean the only thing i can click is the "Mark for Installation"

the rest of the options are unclickable

---

### Post by sikander3786 on 2010-12-22
> what is the difference if i just go to Synaptic Package Manager, then select the Package, and select " Mark for complete removal" ?

No difference. It does the same i.e, removes all the configuration files as well ;-)

> i mean the only thing i can click is the "Mark for Installation"


Means those packages are not installed already thus you can't remove them. From the left column, click Status and then Installed and you'll see only the installed packages then.

> the rest of the options are unclickable

No idea. Which packages are those? Please name them.

---

### Post by philinux on 2010-12-22
> **sikander3786 said:**
> No difference. It does the same i.e, removes all the configuration files as well ;-)


It will not remove the hidden config files in a users home directory though.

OP,

See man apt-get for clean autoclean and autoremove options.

---

### Post by TweFoju on 2010-12-22
> **sikander3786 said:**
> 
No idea. Which packages are those? Please name them.
Package like 3dChess, 4g8, cdd-doc, cdde, and all the gazzilions package in there, most of them , i cannot click on other options other than "mark for installation" 

ok got it, 

but i have this problem again

you see, i am trying to install ATi Catalyst

but gEdit always says it cannot detect the character encoding, and says make sure it's not a Binary file

but the package i download from the AMD are correct

ati-driver-10-12-x86.x86_64.run for Linux 64bit

what should i do to make it run?

thanks

---

### Post by sikander3786 on 2010-12-22
Install the ATI Drivers using System > Administration > Additional Drivers/Hardware Drivers.

Or if you insist to install .run package, the instructions would be on the ATI website.

> **philinux said:**
> It will not remove the hidden config files in a users home directory though.


Yep, it doesn't. Just re-confirmed that :-)

---

### Post by TweFoju on 2010-12-22
ok, i completely successfully installed CCC

but it still reads my Onboard VGA

 Windows version of CCC, we have option to switch to performance mode which then activate the 5650 dedicated

how do i do that here? there is no switching options in the CCC

:cry:

--- edit--- 

wait, the 5650 is there but it's "Unknown Adapter"

---

### Post by sikander3786 on 2010-12-22
> Windows version of CCC, we have option to switch to performance mode which then activate the 5650 dedicated

how do i do that here? there is no switching options in the CCC


In order to attract experts to your thread, start a new thread with a descriptive title under Multimedia & Video sub-forum.

---

