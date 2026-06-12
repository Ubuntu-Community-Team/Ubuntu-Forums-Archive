---
title: "Installing Ubuntu from Mounted (Virtual) Drive"
date: 2013-09-07
forum: Installation &amp; Upgrades
---

### Post by youssef4 on 2013-09-07
[B]Hey Guys ,

i have just downloaded UbuntuOS from the official website on my windows 8 Ultrabook as though i don't have a Dvd Drive and in the mean time no external drive is available for me [/B][IMG]http://ubuntuforums.org/images/icons/icon9.png[/IMG]** so can just mount the downloaded installation ISO file and install the OS from it ?**[IMG]http://ubuntuforums.org/images/icons/icon3.png[/IMG]** thanks in advance **

---

### Post by TheFu on 2013-09-07
The installer runs a different OS - not Windows. That means you need to boot off the ISO someway to install it. USB is a viable method. Check out pendrivelinux for tools. I like Yumi.

If the computer is relatively new, you really, really, really need to read up on **UEFI** before starting the install. [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) Things have changed due to that and Secure Boot (thanks to MS) and great care is needed for pre-loaded Win8 machines so that you don't cause too much harm.

---

### Post by carlwsnyder on 2013-09-07
Short answer: No

You say you have no external drive.  Does that mean you have no USB thumb drive or other memory card which can be plugged into your Ultrabook?  Also, if you have an EFI (UEFI) system (most Windows 8 systems do), do you have the proper instructions to install an alternative operating system by disabling Secure Boot?
See documentation here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Ubuntu can't be installed directly from Windows 8 or under the Windows 8 boot loader without installing from another device.

---

### Post by sudodus on 2013-09-08
You can install ***VirtualBox*** into Windows, and create a virtual machine. That virtual machine can boot from the Ubuntu iso file (it pretends that it is a CD/DVD). Then you can install Ubuntu into a virtual hard disk drive in the virtual machine, and run Ubuntu inside VirtualBox.

See this link

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by TheFu on 2013-09-08
> **sudodus said:**
> You can install ***VirtualBox*** into Windows, and create a virtual machine. That virtual machine can boot from the Ubuntu iso file (it pretends that it is a CD/DVD). Then you can install Ubuntu into a virtual hard disk drive in the virtual machine, and run Ubuntu inside VirtualBox.

See this link

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

+1 on virtualbox, provided you have enough CPU and RAM to spare. There are hundreds of how-to guides for setting up VirtualBox on Windows. Just remember that the virtual machine provides all the hardware to each "clientOS" - it has NOTHING to do with whatever hardware is inside the actual machine.   Graphics performance will be less, but it is still fantastic for office-productivity apps. I forget that I'm using a VM every day - it is THAT good.  Games and video are slower, but for almost everything else, it works great.

I love virtualization.  Write and present about virtualbox optimization at my blog.

---

