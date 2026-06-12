---
title: "Ubuntu 6.10 install crashing at 47%"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by Eniac on 2007-03-07
Hi guys,

I'm totally new to linux and im  trying to install ubuntu 6.10 on my server (or act like one anyway)

the install is crashing at 47% and i dont know what to do to even know why its crashing.

and by crash i mean total computer freeze. i dont get to see any error.

How can i start the install with some text displayed on screen to let me know what its trying to do ?

---

### Post by tkjacobsen on 2007-03-07
Are you using the DesktopCd to install? Try the alternateinstallcd, it is more robust, however a little more difficult to use.

---

### Post by Eniac on 2007-03-07
Hi, thanks for helping,

yes i am using the standard desktop (cd) edition of edgy.

I'll download the alternate version.

Is there any way i can start the install in "verbose" mode or something like so i can have more information on what is going on ?

---

### Post by tkjacobsen on 2007-03-08
Actually a thing the alternateinstallcd will show you a little more information.. And you can retry if a package-installation goes wrong, sometimes that is enough.

---

### Post by Eniac on 2007-03-08
Well I installed ubuntu with the alternate version, I chose the OEM install as opposed to the text or even command line install. I figured this would be the next best thing for the windows-brainwashed guy that i am.

It actually went well all the way. but when i rebooted it got funny. all i could see was the ubuntu load screen in a very distorted and messed up manner. then the computer freezes.

So i rebooted and went into grub to select "safe mode", from there, i went to the boot directory and started grub again. then...nothing... i have no clue what to do to guess what is wrong.

is there some kind of log file i can see. I'm guessing the crash might be related to my video card not being recognized because my LCD screen is showing me a warning of 1280x1024@60hz is recommended everytime i boot ubuntu in its current state. so im guessing a video problem and im trying to locate the config file somewhere to tell ubuntu to boot in a different resolution.

how can i do that ?

Thanks.

---

### Post by tkjacobsen on 2007-03-08
The xorg log is found here
/var/log/Xorg.0.log

xorg is the graphical system..

OEM install is not the best choice. You should use the install in text mode option (or what it is named, I don't remember, think it is the first). OEM is for hardware vendors to supply ubuntu pre-installed - maybe that's why it don't detect your screen correctly...

EDIT:
in /var/log you can also find additional logs..

use "less Xorg.0.log" to view the file.

---

### Post by Eniac on 2007-03-08
Thanks Jacobsen (i'd use your name but truth is im not sure which part is the actual name, Troels or kofoed ??)

installing in regular text mode worked out my problem and now ubuntu is running smoothly ... well booting anyway. I got a problem with my lan card not being found but ive already started a topic on that in the network section.

Thanks for your help.

---

