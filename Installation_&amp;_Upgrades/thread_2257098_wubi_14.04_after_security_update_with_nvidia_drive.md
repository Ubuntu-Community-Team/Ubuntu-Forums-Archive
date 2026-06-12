---
title: "wubi 14.04: after security update with nvidia drivers windows 7 does not boot"
date: 2014-12-16
forum: Installation &amp; Upgrades
---

### Post by dieter-erich on 2014-12-16
Despite constant warnings from the community I have been using WUBI right from version 10.04 onwards till version 14.04 on my laptops to my uttermost satisfaction! I also run all security and other updates regularly. Two days ago, I ran the update on my Lenovo Thinkpad 420W as usual without too much looking what it was. 

        When rebooting, UBUNTU showed a black screen and I could neither boot into Windows 7. I suppose that it must have to do with the Nvidia driver (and accessory programs) that were in the most recent security update. Since Lenovo has the Primus system that includes a low-end Intel graphics and a high-end Nvidia graphics that are switchable, I suppose that the update must have changed some setting of the graphics. I do not know whether the boot manager is involved in this. After fumbling around in the BIOS trying several settings for the graphics I am now back to a functioning UBUNTU but Windows does still not boot. I have tried all of the recovery options for Windows but all just run for several minutes and then restart into the same corrupted Windows system as before. I have not the slightest idea how a change in WUBI can affect Windows. Help is greatly appreciated!
thanks, D-E

---

### Post by Frogs Hair on 2014-12-17
Wubi does use the Windows boot loader and I can only suggest these two links . Because Wubi is no longer actively developed informed support is more difficult to find . The current problem is with Windows so I don't if anything Ubuntu related would help.  

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by hakuna_matata on 2014-12-17
> **dieter-erich said:**
> I have not the slightest idea how a change in WUBI can affect Windows.
IMHO it is not a Wubi issue because a Wubi installed Ubuntu doesn't use special graphic card drivers. There is no difference if you use Ubuntu without Wubi.
> **dieter-erich said:**
> I suppose that it must have to do with the Nvidia driver (and accessory programs) that were in the most recent security update.
If you're right, it should affect other users with similar hardware, too. It does not depend if these users use Wubi or Windows. Of course, if the graphic card "doesn't forget" settings, it could affect Windows, too.

In this case, it could be helpful, if you turn off your computer, disconnect power connector and remove battery. Maybe, you can erase incorrect settings with this procedure.

---

### Post by schragge on 2014-12-17
> **hakuna_matata said:**
> If you're right, it should affect other users with similar hardware, too. There's [thread=2257113]another thread[/thread] currently running where the latest security update of the nvidia driver also seems to have broken Ubuntu 14.04. Not similar hardware, however.

---

### Post by oldfred on 2014-12-17
Wubi relies on the Windows boot loader and is an entry in the Windows BCD. 
You may be able to press f8 to get into Windows repair console.
If you run autofix you have to run it 3 times. 

 f8 to get to repair install screen
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)

---

