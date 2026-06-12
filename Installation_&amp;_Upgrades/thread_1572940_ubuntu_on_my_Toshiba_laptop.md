---
title: "ubuntu on my Toshiba laptop"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by sush on 2010-09-12
I bought a Toshiba L500-D9810 laptop a two months back and removed the windows7, the default os in it after making the recovery disks. Later, I tried installing the Ubuntu 10.4, but that led to so many errors and problems. I similarly tried kubuntu and also the older version of ubuntu, yet the same problem persists. I used a cd first, then, tried booting from the external hard disk too... 
Also, for the first time i could not even load ubuntu from the cd or external harddisk, later, i changed a few settings like noapci, acpi=off, nolapci, nodmraid, edd=on and nomodeset options to enter the settings and then only i was able to install. Now, the problem is I have installed ubuntu but I'm not able to BOOT from my internal harddisk. It is showing acpi error. Can anyone help me, please????

---

### Post by bigpayne69 on 2010-09-12
To be honest with you, a lot of us have had the same problem. For some reason Toshiba laptops and the acpi in on the current linux kernel are not getting along. all you have to do is turn off. When you go to boot your computer, on the grub menu, edit the command line and add apci= off into the command. This is just a temp fix, to make it permanent, you are going to need to edit your grub file.

---

### Post by spcwingo on 2010-09-12
While booting hold the shift key.  This will bring up the bootloader (GRUB).  Select the second entry (recovery mode).  At the prompt this brings up select "drop to root shell".  From the shell enter:

```
nano /etc/default/grub
```

Within that text editor find a line that looks like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

and append whatever kernel parameters that allowed you to install to the end (inside of the parenthesis).  Then press CTRL+O (not a zero) to save then CTRL+X to exit.  Finally run these commands:

```
update-grub
```

followed by:

```
reboot
```

If everything goes well you should reboot into a fully working system.  :)

---

