---
title: "Problem installing/uninstalling"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by jcleaver42 on 2011-06-02
I have a problem.  I had the 'Run from Windows' version installed and had a problem and later developed a problem with my bootrec files for Windows 7.  I had to run the Startup repair utility and it fixed my Windows boot problems.  However, it destroyed the option to boot to Ubuntu.  So, I decided I would uninstall Ubuntu, and re-install.  However, it won't uninstall because there is a file missing, namely the boot info file.  I can't just install either as it says there is a previous install that has to be uninstalled first.  

How can I fix this?

---

### Post by tommcd on 2011-06-03
See this for uninstall Wubi, including the section on manually uninstalling: [https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)
Next, do a real install of Ubuntu to a dedicated linux partition on your hard drive. Ubuntu will run much better that way. 
Here is a great site for dual boot Ubuntu with Windows 7:[http://members.iinet.net.au/~herman546/](http://members.iinet.net.au/~herman546/)

And welcome to the Ubuntu forums!

---

### Post by jcleaver42 on 2011-06-03
Thanks.  Was able to get it uninstalled, and I did do the separate install to it's own partition.

I have a few issues now that I will have to clear up at some time.

1.  Ubuntu bootloader now has Ubuntu as the default OS.  I need it to be Windows 7.  When I used the other type of install, it used Windows bootloader but it does not do so now.  The Ubuntu bootloader replaced the Windows bootloader.

2.  Having a heck of a time getting my dual displays to work.  Same thing happened before, but I was able to get that fixed.  I can't seem to now.  When I look at additional drivers, it shows I have an nVidia provided driver that is activated, but not in use.  Before, it was that I didn't have the driver, and once I installed it everything worked.  Now i have it, but I can't seem to get it to work.  In the nVidia control panel I can get both moniors to show activated, but once I quit the control, it reverts.  I am sure this is because I did not save the config file.  When I go to save it, I have no idea what name I should give it, or where to save it.

Anyway, the first is a priority for me, and the other i will eventually figure out.  

Thanks!

---

### Post by Rubi1200 on 2011-06-03
Hi and welcome to the forums jcleaver42 :)

You can use Grub Customizer to achieve what you want for the first issue:
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by jcleaver42 on 2011-06-03
What a wonderful community!  Thanks for the help.  I followed those steps, and it worked very well.  Now my boot is the way I need it!

As a bonus, the display is almost there!  Both screens are used now; just had to reboot!  D'oh!

Now to configure it so the other screen is the default.  I know I can do that, but that will have to wait until a task finishes on the Windows side.

Thanks again!

John

---

### Post by Rubi1200 on 2011-06-03
Excellent! Glad you got things working the way you want.

Enjoy :)

---

