---
title: "My computer and Trusty Tahr (Ubuntu 14.04) don't get along well"
date: 2015-02-26
forum: Installation &amp; Upgrades
---

### Post by Ramom_Flores on 2015-02-26
When I installed Ubuntu Precise Pangolin (12.02) in my computer, two years ago, all went well. The problems started when updating the HWE (Hardware Enablement Stacks). As the system didn't boot correctly, I have to reinstall Ubuntu 12.02. Since then my computer is without HWE updates, and almost everything is fine.

When Trusty Tahr was released I downloaded it and created a live usb with it. I tried it but without success, as the OS doesn't boot correctly (later I explain it in more detail).

Since a few days ago I'm testing different distributions that were installed in a usbdrive using Multisystem. Ubuntu and derivatives do not work well, whereas other distributions run smoothly: Slacko Puppy 5.7.0, PclinuxOS 2014 (kde-minime) and Mageia 5 (Beta 3).

Let us go on to explain the problems in more detail.
[B]
Ubuntu 14.04.2[/B]
[LIST=1]
[*]When booting the first screen is purple, with "ubuntu" in white at the center. 
[*]After a little while a new screen appears that allows you to choose between [Try Ubuntu] and [Install Ubuntu]. 
[*]After clicking [Try Ubuntu] the screen becomes black with a white arrow (cursor) at the center. But this is a frozen screen, the cursor do not respond to the mouse, and the keyboard input is ignored. 
[/LIST]
 
[LIST]
[*]I have tried several times, and the usual behavior is descrived above, but sometimes the computer gets frozen at the first step. 
[*]If I press any key in the first step, the computer freezes. 
[/LIST]


**Kubuntu 14.04.2**
[LIST=1]
[*]When booting the first screen is black, with "kubuntu" in white at the center. 
[*]After a little while a colorful background appears, with a white arrow (cursor) at the center. But this is a frozen screen, the cursor do not respond to the mouse, and the keyboard input is ignored. 
[/LIST]


**Lubuntu 14.04.2**

[LIST]
[*]Some times it works correctly, but some times it behaves as Ubuntu 14.04.2 
[/LIST]


I suspect that could be a problem with the graphic card, NVIDIA C61 [GeForce 7025/nForce 630a]. But I have no idea what to do.

[SIZE=3][COLOR=#006400][FONT=arial]How can I do to obtain some information about what is failing?[/FONT][/COLOR][/SIZE]

Ramom

---

### Post by sudodus on 2015-02-26
I suggest that you use what is working. ***Ubuntu 12.04 LTS*** will be supported until April 2017, so there are two more years to go. It is often better to continue with an old LTS release than to upgrade, unless you need a new version of some program package. ***Kubuntu*** will also be supported until April 2017 as well as the following community re-spins based on Ubuntu 12.04 LTS, ***Bodhi*** and ***LXLE***.

I think you are right, when you mention the graphics card. You might need an old version of a proprietary driver for that nvidia card (a version that might not be ported to newer versions of Ubuntu). If you have not tried a proprietary nvidia driver in 14.04.2 LTS, please try it. You can ***install*** a system into a USB pendrive (so that you need not touch the internal drive). And you might need the [boot option]("https://help.ubuntu.com/community/BootOptions") **nomodeset** to make it work well enough to install the proprietary driver.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by ajgreeny on 2015-02-26
Nvidia graphic cards often need the **nomodeset** boot option for both the live system and also for the first boot of the installed OS.

Boot the live DVD/USB again and at the first screen you see (or maybe it's the screen where you choose to install or try, I can't remember) hit F6 and there you can select from the available boot options.  Try nomodeset first and you may get to a usable but low resolution desktop which will allow you to install the OS.

If that works OK reboot and at the grub menu (hold shift at power-on if you don't see a grub menu) hit "E" to edit, navigate to the line with **quiet splash** in it and replace those two words with **nomodeset**.  Hit **Ctrl+X** to boot with that option, probably again low resolution, but it should allow you to install a driver from Additional Drivers for your nvidia card.  Reboot again and hopefully you will now have a system working as you want.

---

### Post by Ramom_Flores on 2015-02-27
Following yours advice I was able to install the nvidia drive in Kubuntu. Ubuntu is still causing some problems, but I hope to solve them.

Thanks for your quick and useful responses.

---

