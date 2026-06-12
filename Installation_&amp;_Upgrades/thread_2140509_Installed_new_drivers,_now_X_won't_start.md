---
title: "Installed new drivers, now X won't start"
date: 2013-04-29
forum: Installation &amp; Upgrades
---

### Post by AussieGuy on 2013-04-29
I'm using a Lenovo T500 laptop, and I've just installed the newest  ATI driver, and rebooted.  I get a message about running in low res, and when I press Enter , I obtain a menu saying "What would you like to do?" and giving me four options (run, reconfigure, troubleshoot, exit to console). Trouble is that the screen and mouse are completely unresponsive, so I can't select any of the options. In effect the graphics is frozen and I can't obtain even a low-res screen. All I  can do is to go to VT1 with ctrl-alt-f1.

How do I reconfigure my graphics so it all works again?

I'm running 12.04.

Thanks,
-A.

---

### Post by jonathanfv on 2013-04-30
Restart, and boot in recovery mode from Grub. From there, a menu should appear. Use it to enable the network (via ethernet cable), then once you're back to the main recovery menu, enter the dpkg menu (if you don't do that, your file system will be mounted in read only mode). Once it mounted your partition, go to the root shell and from there you should be able to uninstall the driver you installed. After that, reboot, and you should be able to access your regular session. You can also uninstall the ATI driver from the shell you got from ctrl-alt-F1.

I've had a similar problem, I updated Bumblebee under 12.10 and X wouldn't display anything. I think it's because I got served a version for 13.04. I fixed the problem by unistalling bumblebee and Nvidia's driver, updating to 13.04, and then reinstall bumblebee and Nvidia's driver. If your problem is similar to mine and you want to stay with 12.04, I suggest you install the previous version of the ATI driver after removing it.

---

### Post by AussieGuy on 2013-04-30
Thanks for that.  What I did in the end was to boot up a console, and did an "apt-get remove --purge" of all the fglrx-related packages.  This then enabled me to boot up normally, and now I'm back to where I was, using the generic driver for the onboard intel card, rather than the ATI Radeon card with drivers.

When I have some more time I'll attempt to install the most recently working ATI drivers.  

It's a bit scary though when your machine won't play nice!

---

### Post by jonathanfv on 2013-05-02
Yes, it is! Every time I update the kernel, I get that problem, and I have to remove and then install again my graphics drivers. Good luck to make it work! At least, you know you can pretty much always repair what you did.

---

