---
title: "what should I do? Installation stuck!"
date: 2012-06-28
forum: Installation &amp; Upgrades
---

### Post by subjugater on 2012-06-28
I have tried dozens of times to install 12.04 on my desktop. I burned a disk and also prepared a USB installation stick too. Both of them led to the following issue.

The installation was stuck at this screen. At the beginning, those five spots blinked and changed the color one by one. But at some point, they stop blinking and the installation seemed stopped. I have waited more than two hours and nothing changed. I took a photo of how the screen looked like and hope that some one can leave a hint. 

Should I change something in BIOS/setup? I tried some, but never worked. 

Thanks!

---

### Post by subjugater on 2012-06-29
bump up

---

### Post by southerngeek on 2012-06-29
have you actually been able to boot into the live cd and start the install? or are you just stuck at booting the livecd?

---

### Post by subjugater on 2012-06-29
> **southerngeek said:**
> have you actually been able to boot into the live cd and start the install? or are you just stuck at booting the livecd?

No, I haven't been able to boot using the cd and no installation was launched, as far as I understand. I was stuck there at almost the very beginning of the installation process. I think that means that it was stopped when the machine was trying to boot from the live cd.

Any suggestions? Thanks very much!

---

### Post by southerngeek on 2012-06-29
Ok. Try pressing F6 when you are at the menu on the LiveCD, hit esc and then down at the bottom of the screen remove ```
quiet splash
``` from the end of the kernel boot options. (see the instructions at [https://help.ubuntu.com/community/BootOptions#line-77]("https://help.ubuntu.com/community/BootOptions#line-77") for more help on how to do this) Press enter to boot, this should let you see exactly where it is hanging at during the boot process.

---

### Post by subjugater on 2012-06-29
> **southerngeek said:**
> Ok. Try pressing F6 when you are at the menu on the LiveCD, hit esc and then down at the bottom of the screen remove ```
quiet splash
``` from the end of the kernel boot options. (see the instructions at [https://help.ubuntu.com/community/BootOptions#line-77]("https://help.ubuntu.com/community/BootOptions#line-77") for more help on how to do this) Press enter to boot, this should let you see exactly where it is hanging at during the boot process.

I followed all your instructions until I came across these on the screen:
```

[   89.993692] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   89.995596] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   89.997433] b43-phy0 ERROR: you must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
```

What should I do? Thanks!

---

### Post by southerngeek on 2012-06-29
Your wireless card is not playing nice with ubuntu... So what you'll have to do is blacklist it at boot (in the same place you removed the quiet and splash boot options), so the installer will ignore it. Check out the instructions in this [http://ubuntuforums.org/showthread.php?p=11883375](http://ubuntuforums.org/showthread.php?p=11883375) thread, post #6.

Good luck! Let me how it works out.

---

### Post by Quackers on 2012-06-29
Have a look at these boot options. If your graphics card is a nvidia try the "nomodeset" option
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Try souterngeek's suggestion though :-)

---

### Post by subjugater on 2012-06-29
> **southerngeek said:**
> Your wireless card is not playing nice with ubuntu... So what you'll have to do is blacklist it at boot (in the same place you removed the quiet and splash boot options), so the installer will ignore it. Check out the instructions in this [http://ubuntuforums.org/showthread.php?p=11883375](http://ubuntuforums.org/showthread.php?p=11883375) thread, post #6.

Good luck! Let me how it works out.

Hi, buddy,

I followed the instruction in the thread the link to which you gave. Thanks. I am now at the last task - install the b43-firmware thing. However, I am bounced back by this:

```
E: Unable to locate package firmware-b43-installer
```

Is this due to the fact that the computer is not connected to internet anyway? In this case what should I do? Should I try to plug in a wire to try? Or is there any other way to work around this?

Thanks, man. You suggestions have been extremely helpful!

---

### Post by southerngeek on 2012-06-29
Cool deal, glad to hear you got it booted :) Yeah, you'll have connect via ethernet and download the package from the repositories. Then you should be good to go!

---

### Post by subjugater on 2012-06-29
> **southerngeek said:**
> Cool deal, glad to hear you got it booted :) Yeah, you'll have connect via ethernet and download the package from the repositories. Then you should be good to go!

My friend, the b43 stuff is now successfully installed by using wire.

There are two minor problems:

1. I can not go to the grub page automatically each time I restart the computer as I am always asked to choose F1 or F2 like this:
 
```

Diskette drive 0 seek failure



Press F1 to continue, F2 to enter setup


```

2. An additional driver installation icon shows up at the top right panel. After clicking it I see
```
No proprietary drivers are in use on this system
```

And there are two options given in the window right beneath it.
```
ATI/AMD proprietary FGLRX graphics driver (post-release updates)
ATI/AMD proprietary FGLRX graphics driver

```

Also at the bottom of this dialog it reads
```
This driver is not activated.
```

Should I do something? Should I click the "Activate" button?

Thanks a lot, man~

---

### Post by southerngeek on 2012-06-29
Awesome! 

The
> Diskette drive 0 seek failure
Press F1 to continue, F2 to enter setup
error is likely because your first boot device is set to your floppy (people still have those? lol) in BIOS. You will want to set either your CD drive, or primary hard disk to be the boot device.

The other thing is Ubuntu asking whether or not you want to use the proprietary drivers available for your graphics card. That's up to you however, if it's working...leave well enough alone! You can always install them later.

And no problem bro, glad you got everything up and running! :)

---

### Post by subjugater on 2012-06-30
> **southerngeek said:**
> Awesome! 

The

error is likely because your first boot device is set to your floppy (people still have those? lol) in BIOS. You will want to set either your CD drive, or primary hard disk to be the boot device.

The other thing is Ubuntu asking whether or not you want to use the proprietary drivers available for your graphics card. That's up to you however, if it's working...leave well enough alone! You can always install them later.

And no problem bro, glad you got everything up and running! :)

Hi, buddy,

Thanks for your suggestions. Now I have turned the corner and got everything works normally! 

BTW, my friend got a new job in UK and left me this computer - Dell Inspiron 530 with Core 2 Duo which he bought 4 years ago for his wife. I even was wondering why he bought a diskette driver at that time (it was 21 century after all!) and I do trust that this belonged to one of the last batch of 1.44" disk drivers Dell sold ever in the history. LOL

---

### Post by southerngeek on 2012-06-30
Cool deal! Glad to hear you're up and running. Please mark this thread as solved if you don't have any more questions about this issue.:)

---

### Post by subjugater on 2012-06-30
> **southerngeek said:**
> Cool deal, glad to hear you got it booted :) Yeah, you'll have connect via ethernet and download the package from the repositories. Then you should be good to go!

No more questions, but only other than this one - How to mark this thread SOLVED? :)

---

### Post by Quackers on 2012-06-30
subjugator, I have marked the thread as solved for you.
In the future if you go to the top right of the page you will see the Thread Tools heading. If you click on that the option to mark the thread as solved will appear. Just click on that and you're done.

---

### Post by subjugater on 2012-06-30
> **Quackers said:**
> subjugator, I have marked the thread as solved for you.
In the future if you go to the top right of the page you will see the Thread Tools heading. If you click on that the option to mark the thread as solved will appear. Just click on that and you're done.

Thanks! Gotcha~

---

