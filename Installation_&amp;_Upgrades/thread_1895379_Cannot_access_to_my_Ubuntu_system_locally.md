---
title: "Cannot access to my Ubuntu system locally"
date: 2011-12-14
forum: Installation &amp; Upgrades
---

### Post by alunem on 2011-12-14
Hi I just installed Ubuntu 10.04 LTS (via netboot). The problem is there is no video signal (the screen automatically turns off after grub is executed) when I want to use it locally. Nevertheless, I can access to it remotly (SSH, FREENX) without any problem... I precise that other versions of ubuntu didn't have this specific problem on this computer.

Any idea ?

Thanks a lot,

Emmanuel

---

### Post by MAFoElffen on 2011-12-14
> **alunem said:**
> Hi I just installed Ubuntu 10.04 LTS (via netboot). The problem is there is no video signal (the screen automatically turns off after grub is executed) when I want to use it locally. Nevertheless, I can access to it remotly (SSH, FREENX) without any problem... I precise that other versions of ubuntu didn't have this specific problem on this computer.

Any idea ?

Thanks a lot,

Emmanuel
Welcome to Ubuntu!

(Ubuntu v10.04)
- At the Grub Menu, Try Ubuntu Recovery and see if the Recovery Menu comes up.
- Try Failsafe Mode / Low graphics and see if graphics come up
- If they do, System > Administration > Hardware Drivers > Install graphics driver. 

If not, then
- At the Grub Menu, Press "e" to put it into an edit mode on the first menu item.
- Arrow down to the line that starts with "linux"
- Arrow right to after where is says "quiet splash" and replace with "--verbose nomodeset"
- Watch the bootup process for error messages.
- If it boots, install your drivers.  

Tell me if at lock-up, you can press <cntrl><alt<F2> and get to vitrual terminal 2...

Tell how it goes.  If all that fails shh into it and post the results of 
```

lspci -vnn | grep VGA

```And post your /var/log/Xorg.0.log

---

