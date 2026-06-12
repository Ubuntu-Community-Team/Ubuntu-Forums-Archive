---
title: "Installing nVidia Drivers"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by Borealis on 2006-06-14
Hello everyone

I'm rather new to Linux but I've used it before but not on my home system. I thought it was time to get re-acquainted with it.

I've downloaded the AMD64 drivers for my 7800GT off the nVidia site. When i try and compile it i get an error:

  ERROR: You appear to be running an X server; please exit X before
         installing.  For further details, please see the section INSTALLING
         THE NVIDIA DRIVER in the README available on the Linux driver
         download page at [www.nvidia.com](www.nvidia.com).

I undertand I have to run this whilst not being in the Ubuntu GUI. So is there a way of directly booting to a terminal screen so i can install this?

Thanks

David

---

### Post by 23meg on 2006-06-14
Hit Ctrl+Alt+F1, log in, type ```
sudo /etc/init.d/gdm stop
```and go ahead with the install.

---

### Post by tseliot on 2006-06-14
Try this guide of mine or use my script:
[http://www.ubuntuforums.org/showthread.php?t=139264]("http://www.ubuntuforums.org/showthread.php?t=139264")

---

### Post by Borealis on 2006-06-14
[QUOTE=23meg]Hit Ctrl+Alt+F1, log in, type ```
sudo etc/init.d/gdm stop
```and go ahead with the install.[/QUOTE]
 
Thanks for the quick reply but I get an error saying init.d doesn't exist.

Also, is there a need to start gdm afterwards? and could you please tel me the command to get back into the gui? Thanks

---

### Post by Borealis on 2006-06-14
[QUOTE=tseliot]Try this guide of mine or use my script:
[http://www.ubuntuforums.org/showthread.php?t=139264]("http://www.ubuntuforums.org/showthread.php?t=139264")[/QUOTE]

Thanks i will check it out. Sorry to be a pain but how do you run your script?

---

### Post by Borealis on 2006-06-14
Nevermind got it all working, thanks :)

---

