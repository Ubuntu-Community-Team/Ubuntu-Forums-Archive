---
title: "Running Executables (*.exe files)"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by remoriverdog on 2008-11-20
OK, I posted earlier about installing soundblaster drivers, tho I think my post should have been more about running *.exe files, which seems to be a problem for me.  I would think that in spite of all the basic differences between Ubuntu and Windows that executables would still be the same.  Maybe in my rush to add additional functionality, by installing new software I've disabled something?  

So, my question is essentially for a basic install straight out of the box should 8.04 LTS run executables, i.e., *.exe files?

Thanx for your patience with a relative newbie.

Remoriverdog

---

### Post by iaculallad on 2008-11-20
No, Ubuntu 8.04 won't automatically execute those kind of files, you need to install the [WinE]("http://www.winehq.com/") application.

---

### Post by poebae on 2008-11-20
> **iaculallad said:**
> No, Ubuntu 8.04 won't automatically execute those kind of files, you need to install the [WinE]("http://www.winehq.com/") application.
This is true, but somewhat misleading.

You do need Wine to execute .exe files because the ways in which Ubuntu and Windows treat program/driver installation are fundamentally different, but this is not the way you should go about installing hardware drivers in Ubuntu.

Firstly I'm surprised that Ubuntu doesn't already have drivers for your Soundblaster card. 

If you want to install a driver for your hardware, you'll have to have a look around for a Linux driver, or see if there are existing drivers in the software repositories.

What's the model of your sound card? We'll work from there :)

---

### Post by remoriverdog on 2008-11-21
WOW, you guys are really FAST!  Sweet!  OK, I have the original soundblaster Audigy card.  I've also tried installing drivers for MB supported sound to no avail... is that where I need Wine?

I've been to the Alsa site for soundcard support but no luck with the *.tar file?  Clues, please?   

Thanx  

Remoriverdog

---

### Post by sonofusion82 on 2008-11-21
i m also using an audigy. other than a little lower volume compared to windows, it works out-of-box with ubuntu without any need to install drivers.

anyway, for linux, unlike in windows where you will have to install a whole lot of drivers to get your machine to proper working condition, a new installation of ubuntu should get all your drivers working, if not, might probably need some config files fixing.

---

### Post by cariboo on 2008-11-21
Linux apparently has more drivers builtin to the system by default then any other os. To see what is available if you are the curious type have a look in /lib/modules/2.6.xx-x. Where 2,6,xx-x is your kernal version, usually there should only be one version, but depending on how old your installation is there may be more. For more info look here:

[http://broadcast.oreilly.com/2008/10/how-linux-supports-more-device.html](http://broadcast.oreilly.com/2008/10/how-linux-supports-more-device.html)

Jim

---

