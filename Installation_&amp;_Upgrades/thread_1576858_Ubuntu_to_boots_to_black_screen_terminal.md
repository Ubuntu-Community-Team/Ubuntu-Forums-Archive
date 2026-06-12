---
title: "Ubuntu to boots to black screen terminal"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by thenetminder33 on 2010-09-17
Recently new to Ubuntu and I just installed Ubuntu 10.04.1 LTS x64(using ISO CD) into a dual boot with win7

When i boot Ubuntu from grubs it goes to Ubuntu loading screen w/ pink background the immediately reverts to command prompt/terminal with login prompt

After looking at other forums i used command ```
startx
```
to boot into GUI

Any help to bypass this?

Also in ubuntu gui many programs and features from application and system menus do not work.

I would be up to reinstalling but when i start to it wants to create another partion on my HD using space from current Win7 partition.

Thanks for any help!

---

### Post by tommcd on 2010-09-18
First, when you boot the Ubuntu live CD, did you run the option "**check disc for defects**" to verify that the Ubuntu install CD is good??
> **thenetminder33 said:**
> 
After looking at other forums i used command startx to boot into GUI.
Any help to bypass this?
Try running:
```
sudo service gdm start
```
This *should* get you to the gdm login window where you can login with your username and password and then boot to the desktop.

---

### Post by thenetminder33 on 2010-09-18
I do not recall seeing an option to check the disc for errors, because if i did see one i probably would have done so because i had some problems downloading and burning the ISO

> **tommcd said:**
> 
Try running:
```
sudo service gdm start
```

This command takes me to a blank screen with dialogue box:
```
Ubuntu is running in low-graphics mode
The following error was encountered:
(EE) RADEON(0): Acceleration initialization failed
```

I would really be up for reinstalling ubuntu with a new disc. In fact i had already started to do so with my old one, but it wanted to create a new partition eating away at my current win7 partition.

---

### Post by thenetminder33 on 2010-09-18
I reinserted the live CD but could find no option to search for defects in disc

I am running ubuntu in try mode and lots of things that did not work before in normal boot:
Wired LAN connections
Many options under the System menu
Ubuntu Software Center

Not sure if this helps decide if the cd is functional but everthing in this mode seems to be working

---

### Post by thenetminder33 on 2010-09-18
All problems solved with reinstall:)

---

### Post by tommcd on 2010-09-19
> **thenetminder33 said:**
> I reinserted the live CD but could find no option to search for defects in disc ...

When you first boot the Ubuntu live (or alternate) CD you should see the the first screen shot from this link:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
The 3rd option in the list is the option to "*Check disk for defects*". This will check each and every package file on the CD to make sure they are valid and not corrupted. This should always be the first thing you do when you boot the Ubuntu install CD.

Anyway, glad you got it fixed. Did you burn a new CD? Or did you reinstall with the same CD?

---

