---
title: "Ubuntu 20.04 / Kubuntu 20.04 live/usb both crash during startup, see pic"
date: 2020-05-16
forum: Installation &amp; Upgrades
---

### Post by info-wijhenke on 2020-05-16
Hi, long time Linux user here. Just build a new rig with a Ryzen 3950x, RTX 2080 Super, 32 GB Ram, 2x 1TB Evo Plus SSD.
I'm running Manjaro on it but as I cannot get any BT device (headphone, soundbar, phone) to connect I thought to try Ubuntu or Kubuntu live to see if they do connect.

Burned an USB but as soon as I select Ubuntu in grub it goes all belly up, see pic, and install hangs.

I can see something about nouveau driver so I thought I start up in low res mode and then I do get to the desktop.
Has this problem occured before? I have googled and tinkered the whole evening but no luck...

Basically I want to know if I can install Euter Ubuntu or Kubuntu after having started low-res, install the nvidia 440x drivers as these perform good on Manjaro.
Thanks for any advice or tips.

[IMG]https://pasteboard.co/J8HZhtW.jpg[/IMG][IMG]https://pasteboard.co/J8HZhtW.jpg[/IMG][IMG]https://pasteboard.co/J8HZhtW.jpg[/IMG][https://pasteboard.co/J8HZhtW.jpg](https://pasteboard.co/J8HZhtW.jpg)

---

### Post by CatKiller on 2020-05-16
> **info-wijhenke said:**
> RTX 2080 Super

It's often necessary to pass **nomodeset** as a kernel parameter for install on Nvidia hardware. I think it's **E** to edit the options on the very first menu that you see.

---

### Post by oldfred on 2020-05-16
Not sure what driver Ubuntu would install by default, but it now offers the option to install the nVidia driver as part of the install, so you do not need nomodeset boot parameter after install on first boot.
If you do not install nVidia driver, you still have to use nomodeset. You can install driver from terminal or if low res is good enough you can use System Settings.

At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Usually with new nVidia card you want newest driver.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Ubuntu Now Offers the Latest Nvidia Graphics Drivers to LTS Users
[https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its](https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its)

---

### Post by ubfan1 on 2020-05-17
Instead of editing the default grub boot line to add nomodeset, you probably can just boot in recovery mode, install the Nvidia drivers, and reboot (with the default).

---

### Post by info-wijhenke on 2020-05-17
Thanks all!

@oldfred, there's no option to select the proprietary driver as it immediately goes wrong and it doesn't make it to the welcome screen. I'll try some sruff out in virtualbox as well. I will close this post when I make it to the welcome screen.

---

### Post by CelticWarrior on 2020-05-17
> **info-wijhenke said:**
> Thanks all!

@oldfred, there's no option to select the proprietary driver as it immediately goes wrong and it doesn't make it to the welcome screen. I'll try some sruff out in virtualbox as well. I will close this post when I make it to the welcome screen.

What oldfred mentioned is after installing, not in the live session. You still need 'nomodeset' or safe graphics mode to boot the live session.

---

### Post by info-wijhenke on 2020-05-18
Kernel parameter change was the trick, thanks all.

---

