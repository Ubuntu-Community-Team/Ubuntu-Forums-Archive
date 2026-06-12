---
title: "Problems installing Nvidia Driver in 12.04"
date: 2012-08-26
forum: Installation &amp; Upgrades
---

### Post by kimberly54 on 2012-08-26
I am trying to install the Nvidia driver in 12.04 on my sons new build, but when I type:

nick@nick-desktop:~/Downloads$ sh NVIDIA-Linux-x86_64-304.37.run

the Nvidia driver starts up but says:

ERROR: You appear to be running an X server; please exit X before        
installing.

I've looked all over but I can't figure out what they are talking about.

What is an X server?... and how do I get around this?
:mad:

---

### Post by znorris on 2012-08-26
Have you tried to install the drivers using the driver manager?
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

If that's not what you want:

X is the graphical interface you're always using when you boot your computer. What they want is for you to only be using the shell or command line.

To do this shutdown your computer then when the computer boots (before you see the ubuntu screen) keep hitting shift, or hold it down. You should see the GRUB boot menu. Select recovery mode, that will take you to a shell/command line where you can try and run your file.

---

### Post by SeijiSensei on 2012-08-26
Use the "Additional Drivers" application or run "sudo apt-get install nvidia-current" from the command prompt.

---

### Post by kimberly54 on 2012-08-26
Thanks everyone the Additional Drivers worked right off the bat!!
everything looks to stable now. This works way better than I remember in previous versions.

The reason we ended here is the that 12.04 ISO failed as it *mis-identified*? the EVGA GTX 550 ti on our initial install attempt(not being aware of the boot options or why we would need them) which reasulted in a blank screen with a blinking prompt...which led us down quite a twisty path.  We have since read about the need for the boot options and the situations your need them...like NVIDIA drivers.

Thanks again, we are up and running.

---

