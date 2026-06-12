---
title: "HP Pavilion g7 11.10 Install Black Screen"
date: 2011-12-12
forum: Installation &amp; Upgrades
---

### Post by NoJumpJackFlash on 2011-12-12
HP Pavilion g7-1279dx 4GB RAM
Intel HD Graphics card 8.15.10.2372
64 bit Windows 7 Home Premium Edition Service Pack 1

I just got this notebook from Best Buy and the Win7 works fine.  I've installed 7.10, 8.04, and 10.04 on various Dell PCs and laptops, so am not a complete newbie to Ubuntu.  I downloaded 32 bit 11.10 and created an iso disk.  The notebook boots with it and briefly shows:
ISOLINUX...
Loading Boot Menu

Then the purple screen with a couple icons at the bottom.  After that there's lots of CD activity, but the screen stays totally black, no blinking cursor or anything.  After a couple minutes the CD activity stops and I'm assuming it's at the first installation screen, but I can't see a thing.

I'd tried using the keyboard brightness adjustment on earlier reboots, as another post suggested, but they didn't seem to work.  However, on this 5th or 6th reboot they did and I can see the Welcome - Install screen.  I must have pushed too many keys the first time.  I hope this is the ticket for others having this problem.

---

### Post by kevinfreeman1101 on 2012-02-05
> **NoJumpJackFlash said:**
> HP Pavilion g7-1279dx 4GB RAM
Intel HD Graphics card 8.15.10.2372
64 bit Windows 7 Home Premium Edition Service Pack 1

I just got this notebook from Best Buy and the Win7 works fine.  I've installed 7.10, 8.04, and 10.04 on various Dell PCs and laptops, so am not a complete newbie to Ubuntu.  I downloaded 32 bit 11.10 and created an iso disk.  The notebook boots with it and briefly shows:
ISOLINUX...
Loading Boot Menu

Then the purple screen with a couple icons at the bottom.  After that there's lots of CD activity, but the screen stays totally black, no blinking cursor or anything.  After a couple minutes the CD activity stops and I'm assuming it's at the first installation screen, but I can't see a thing.

I'd tried using the keyboard brightness adjustment on earlier reboots, as another post suggested, but they didn't seem to work.  However, on this 5th or 6th reboot they did and I can see the Welcome - Install screen.  I must have pushed too many keys the first time.  I hope this is the ticket for others having this problem.

I had the same problem with my system (pavillion g7-1365dx with AMD Radeon graphics card), and was unable to install any distro EXCEPT for the latest Ubuntu, Precise ver 12.04. This seems to work fine, likely because it uses a newer kernel that can work with the hardware on your machine. 

I also tried installing Mint using a nomodeset setting, which worked fine for the install and then wouldn't boot up unless I used safe mode, even after updates and upgrading the kernel to the latest stable version. So, for now, I guess Ubuntu 12.04 is the only distro that will work unless you're a very advanced user (which I'm not). 

Hope that helps

---

### Post by klenwell on 2012-02-17
Just hit this problem installing 11.10 64-bit on my new HP Pavilion g7-1310us notebook. Someone on IRC pointed me to this link:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

By following the directions for modifying Grub and adding the nomodeset flag I was able to install the OS and work around the issue. 

There's also this page that's related on AskUbuntu:

[http://askubuntu.com/questions/95459/ati-6470m-intel-hd-graphics-3000-drivers](http://askubuntu.com/questions/95459/ati-6470m-intel-hd-graphics-3000-drivers)

Note, however, one of the people helping me on IRC was aghast at the top answer recommending mixing drivers.

Hopefully a driver will show up in 12.04.

---

### Post by rvw on 2012-11-19
I had the same problem. This is not my laptop, and I don't know which type of videocard is inside. However, I had the black screen. I didn't know what to do, so I pushed the power button to shut it down. Then I suddenly saw some faint white image disappear. It turned out I could see something. So I restarted the machine and there is was again. 

It turns out the only problem is the first intro-screen where you select the language and whether you want to try or install Ubuntu. I tried to change the display brightness but that didn't work. It was difficult to see the mouse. Using Tab and arrow keys to select "Try Ubuntu" didn't work. Finally I could see the mouse and move it over the try button. After I pushed that, Ubuntu started with a normally working display.

---

