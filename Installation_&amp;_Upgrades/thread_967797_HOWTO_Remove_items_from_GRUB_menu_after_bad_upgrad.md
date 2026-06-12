---
title: "HOWTO: Remove items from GRUB menu after bad upgrade (Dirty Style)"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by XDevHald on 2008-11-02
[SIZE=2]This tutorial is very detailed, please pay attention. This can be done in either Windows or Ubuntu Environment.[/SIZE]

--------------------------------------------------------------------------------------------------------
 
[SIZE=4][COLOR=Sienna]**UBUNTU**[/COLOR][/SIZE]

[SIZE=2]**NOTE:** This is if you have dual boot Ubuntu and Windows.

**Step One for Ubuntu:** Locate "Places" and click on the spot that has the Windows drive space listed, **I.E** 34.2 GB Media.
[B]
Step Two: [/B]Locate and click on folder "Ubuntu" > disks > boot > "menu.lst" - Edit this file and remove the kernels you want off of the Grub. 

*_You will be in auto gedit when doing the above procedure._*

**The CLEAN UP:** While you're in the place where the menu.lst is, click back once and you will see all of the images and files of the upgrade you did. **PLEASE** review the GRUB menu during boot and make sure you don't delete the active ubuntu desktop kernel you're using. 

This allows you to clean up some on your ubuntu so there is no clutter.[/SIZE]        

--------------------------------------------------------------------------------------------------------

[SIZE=4][COLOR=Blue][B]WINDOWS

[COLOR=Black][SIZE=2]Step One: [/SIZE][/COLOR][/B][COLOR=Black][SIZE=2]Click Start > Right click "My Computer" > Click "Properties" > Click "C:\" > Click the "Ubuntu" folder > boot > grub > edit menu.lst[/SIZE][/COLOR][B]
[SIZE=2]
[/SIZE][/B][SIZE=2][COLOR=Black]Do the same procedure for Ubuntu steps above this one for the grub folder if doing this in Windows.

[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=2] Hope this helps :)[/SIZE]

---

### Post by bulldog on 2008-11-02
Or use synaptic to remove the un-used kernels and mark them to remove completely.
Then run in a terminal```
sudo update-grub
``` and your menu.lst is as new again.

---

### Post by XDevHald on 2008-11-02
True bulldog, but here the reason for the tut.

1) You use startup-manager and the kernels / upgrade are not found there.
2) Not found in the /boot/grub/menu.lst when gksudo'd
3) Using QGrubEditor as well.
4) Using the previous version of ubuntu that is still available in boot up, and not seeing the kernels in syncaptic in there.

Even by update-grub not working for them as it will show just the install they did of ubuntu but NOT the upgrade they did.

It's imperative for people to understand that an upgrade is not an installation or to be found in the grub menu.lst file.

---

