---
title: "The PSoD and flashing cursor of death"
date: 2013-02-16
forum: Installation &amp; Upgrades
---

### Post by wsfield99 on 2013-02-16
Hello,

I have an old hp pavilion zv5000 on which I have both Windows 7 and Ubuntu 11.04 installed.  I have no problem booting into windows 7.  I do have difficulty booting into 11.04.  What happens is that the systems fails to boot and I get either the PSoD or the flashing cursor of death.  If I boot into recovery mode and do fdisk and the grub thing I can eventually get 11.04 to boot.  The problem is that it usually takes a number of restarts to accomplish this.  I am always able to boot to the command line and I have read that the problem may have something to do with the graphics driver.  I have also attempted to run 12.04 with the same frustrating results.  If there is anyone out there who can help me out I would greatly appreciate it.  Thanks in advance, Scott

---

### Post by Bashing-om on 2013-02-16
wsfield99;

Could be that it is a graphics driver situation.

Have you tried entering the boot parameter "nomodeset" in grub's kernel boot line ?
That disables KMS and boots with the vesa driver enabled.
If that gets you up with some graphics, we can work on getting a better driver installed.

[INDENT][INDENT]try'n to help 

[/INDENT][/INDENT]

---

### Post by wsfield99 on 2013-02-16
No I haven't tried that.  How would I go about it?  Thanks, Scott

---

### Post by wsfield99 on 2013-02-17
> **Bashing-om said:**
> wsfield99;

Could be that it is a graphics driver situation.

Have you tried entering the boot parameter "nomodeset" in grub's kernel boot line ?
That disables KMS and boots with the vesa driver enabled.
If that gets you up with some graphics, we can work on getting a better driver installed.
[INDENT][INDENT]try'n to help 

[/INDENT][/INDENT]
Hi, would you please explain the steps that I need to take to change the boot parameter.  Thanks, Scott

---

### Post by Bashing-om on 2013-02-17
wsfield99; I am back on, Sure !

Ok, we are going to try this simple approach to see if a satisfactory result is achieved.

Cold boot; depress and hold the shift key as soon as the bios screen clears -> grub boot menu; press the "e" key for edit with the first line in the menu highlighted -> boot parameters -> arrow down to the line containing the terms "quiet splash", arrow across to these terms and insert (type) "nomodeset" -with out the quotes, leaving spaces between as parameter delimitations.

ctl+x to continue the boot process -> (hopefully) GUI login screen, login -> desktop.

If you have gotten this far: System setting -> additional Drivers utility -> install the recommended graphics driver.
Reboot.
[INDENT][INDENT]all good now ?  
[/INDENT][/INDENT]

---

### Post by wsfield99 on 2013-02-18
Hi, It appears to have worked.  I did try installing the nVidia drivers and this only made things worse so I'm sticking with the Ubuntu default drivers.  Thanks for your help.  Scott

---

### Post by wsfield99 on 2013-02-18
Well, I decided to take the risk and re-install the nvidia driver and much to my surprise it rebooted on the first attempt.  Once again, that you for your help.  Scott

---

### Post by Bashing-om on 2013-02-18
Scot;

Glad I could be of assistance, Tickled that you are pleased.

Please mark this thread as "solved" - thread tools above the post.

[INDENT][INDENT]happy ubuntu'n

[/INDENT][/INDENT]

---

