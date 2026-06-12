---
title: "Ubuntu installation freezes at the start itself [16.04.1]"
date: 2017-01-18
forum: Installation &amp; Upgrades
---

### Post by harry1997 on 2017-01-18
So, I recently tried to install the Ubuntu's version 16.04.1 amd-64 on my Asus ROG GL552VW notebook computer i7-6700HQ 2.59Ghz Win10...The installation froze for the first time and after doing some research on the internet I changed my bios settings and disabled fast boot, secured boot and made all the adjustments but still the installation froze at the first step itself and I'm unable to figure out what is causing it. I tried to look at the activity when the installation started but couldn't make out much so I'm attaching the screenshot and if someone could help it would be a great deal of help :)[IMG]http://i65.tinypic.com/qnlgdz.jpg[/IMG]

---

### Post by lazy7 on 2017-01-20
Hey, I'm facing the same issue with the same laptop. Did you find a fix for this?

---

### Post by lazy7 on 2017-01-20
Ah, so I solved it this way:

1. **Disable** Fast Boot and Secure Boot (or Secure loader).

2. Plug in the bootable USB with the Linux distro (mine was Ubuntu 16.04)

3. When you see the loader to "_Install Ubuntu_" etc ... press "**e**" and edit a line:
Replace "_quiet splash_" to "_nomodeset_" and press **F10** to boot.

Then after the installation is complete, you will have to reboot. 

4. This time you will now encounter the GRUB. Again, press "**e**" and edit a line:
In the line that starts with "_linux_", add "_nouveau.modeset=0_" at the end of that line.

Your Linux should now boot. 

P.S. Mark the thread as solved if this solves the issue :)
5. After this, you need to install the nvidia drivers. Reboot. And then it's done.:D

---

### Post by harry1997 on 2017-01-21
Okay. I was able to install it by the method you mentioned but there is one problem that still remains. Every time I have to boot ubuntu I should write the command pressing the 'e' or else it won't boot by itself. So, is there a way of bypassing that or I will have to do that each and every time?

---

### Post by lazy7 on 2017-01-21
As I mentioned, you only need to do that once (at the time of installation). When you are logged into Ubuntu, you need to install the NVidia Drivers. After installing the drivers, the problem will be resolved.

If you logged in and didn't install the nvidia drivers, and then rebooted, I think you will have to edit the grub by pressing "e". Then install the drivers before you reboot again.

P.S. It is the NVidia Graphics Card that is causing problems. So once you have the drivers installed, it will work as normal.

---

### Post by harry1997 on 2017-01-23
Can you lay down the steps for the installation as I'm really new to the linux OS and dunno how to get it done :confused:

---

### Post by 1vertex1 on 2017-01-23
Hello, 

Just would like to confirm that this does work, loading with nomodeset replacing 'quiet splash' in the installer resolved the issue and the unit then rebooted without problems.

That said I did drop cryptsetup from the equation since it was causing hangs and allowed me to bypass the second step with grub.

All you need to do Harry is just press e and replace that from the boot script wherever you find it.

And if you're having trouble getting on with installing the nvidia drivers, I recommend [this page](http://www.webupd8.org/2016/06/how-to-install-latest-nvidia-drivers-in.html) - helped me out immensely.

Cheers,

1vertex1

---

### Post by harry1997 on 2017-01-24
Yeah, all of that worked and now after installing the nvidia drivers it's working perfectly fine. Thank you so much guys for your help :D

---

### Post by bougpan8 on 2017-03-03
My friend you are a truly a hero! after ten hours of trying to install ubuntu I found your post. I don't know how you managed to find this solution but I want to thank you so much!!! kudos!!!!

---

