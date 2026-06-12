---
title: "Booting to wrong partition"
date: 2011-09-21
forum: Installation &amp; Upgrades
---

### Post by cpeachey on 2011-09-21
I have installed 11.04 ALONGSIDE an existing version of 11.04. (I want to clean up unwanted apps)
When I re-boot it goes straight to the old version without any option to choose the newly installed version.
How can I fix this please?
Chris

---

### Post by drs305 on 2011-09-21
Try holding down the SHIFT key to see if the menu appears. 

If it does and the other installation is found, boot it and then run:
```
sudo grub-install /dev/sdX
```
to transfer control to that installation's GRUB. X should be the drive that BIOS boots first (preferably the same drive as the installation) such as sda, sdb, ....

If the other OS is not listed, boot to your old OS and run the following to hopefully update the menu:
```
sudo update-grub
```

If SHIFT doesn't work, try repeatedly pressing the ESC key early in the boot.

If that doesn't work, as the system is booting try CTRL-ALT_DEL. That should disrupt the boot and Grub 2 is designed to display the menu after a failed boot.

---

### Post by cpeachey on 2011-09-21
Thanks for your help. update grub brought up the boot menu. I tried booting to the new version but it looks like there are errors preventing it from booting, I will save my stuff and re-install 11.04 to the whole drive.
Thnaks
Chris

---

### Post by vinterkind on 2011-09-21
Please don't do that!
Never (re)install something that doesn't work! ):P

No. Seriously. 
If no menu is shown, you could edit the file /etc/default/grub and 
comment in the HIDDENMENU entry. 

The other thing is to install the startup manager.
The best thing you can get with grub2.

```
sudo apt-get install startup-manager
```

Have fun,

---

### Post by vinterkind on 2011-09-21
btw. change the line with the kernel options. 
try to remove the "quiet" and "splash" options.
so you can see all the boot messages and how far it goes.

maybe you'd referred just to the wrong partition ?

---

