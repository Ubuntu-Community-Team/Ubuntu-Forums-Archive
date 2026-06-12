---
title: "Can`t install Nvidia drivers. Please help."
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by OrganicM on 2010-04-08
Heloo! 

I`m new to Linux.

Trying to install Nvidia drivers on Ubunu 9.10.
I`ve read lots of forums, threads but every one seems to be different (different way of installation).

The driver extension is .RUN

Don`t know what to to with this...

Please help.

Best regards, Michael.

---

### Post by Bobhuber on 2010-04-08
Read this first.
[http://us.download.nvidia.com/XFree86/Linux-x86_64/190.42/README/chapter-04-section-02.html ]("http://us.download.nvidia.com/XFree86/Linux-x86_64/190.42/README/chapter-04-section-02.html")
This all has to be done from a terminal prompt before loading the desktop so you need to reboot and select recovery mode from the grub menu and get to a command line or terminal prompt. Change to the directory you downloaded the driver to and use the following command.Assuming you have the latest drivers from there website type the following at the prompt >sudo sh ./NVIDIA******pkg2.run  using the correct driver name and follow the instructions.Let it update all requested files and reboot. Hope this helps and welcome to the ever challenging world of Ubuntu.

---

### Post by _DoMeN_ on 2010-04-08
I alvays went to terminal and did it like xian explains in this thread:
[http://ubuntuforums.org/showthread.php?t=82503](http://ubuntuforums.org/showthread.php?t=82503)

The part with: "Apply the nVidia driver as instructed." means to run sudo ./name_of_the_driver.run
Sometimes I had to change the privilages for the file so it could be executed.

Since you're new to linux: you change the privilages with chmod 777 name_of_the_driver.run (a bit to much privilages but it alwais works :P)

sudo means that you run the command in the privilaged mode.

when you manage to run the driver installer it's straight foreward from there on...

Hope I helped somewhat...

regards,
Domen

---

### Post by oldfred on 2010-04-08
Welcome to the forums.

Have you tried to install the version that is semi-supported from synaptic? It installs automatically and will set itself up to update every kernel when they are updated.

I think you have to add the restricted Software Source to be able to get the proprietary drivers in synaptic.

---

### Post by OrganicM on 2010-04-08
Thanks for the replies. Thanks for all of you I have installed the latest version of Nvidia drivers. :)

---

