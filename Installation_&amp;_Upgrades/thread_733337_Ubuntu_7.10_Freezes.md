---
title: "Ubuntu 7.10 Freezes"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by kdp8791 on 2008-03-23
I am a complete neebie to Linux, i have been using windows for years. So please bear with me. I have just now installed Ubuntu 7.10 on my Sony desktop. But everytime i turn it on, it some how always freezes, and the only way to turn it off is just power it off. I am not sure what is wrong, i can login into my account fine, but after that sometimes i can get into the Desktop, but sometimes it gets frozen before i even get there. If anyone has any idea what is wrong please do tell me. I have Sony Vaio PCV-RS430G. It has an ATI Raedon 9200, 2GB RAM and 2 HD, 1 with 120GB and another with 80GB.

---

### Post by Pumalite on 2008-03-23
Are you dual booting with Vista?

---

### Post by dstew on 2008-03-23
It sounds like you are having problems with your display adapter driver. The open-source ati driver doesn't always work well in all systems. There are several ways you can try to get a better display.

The easiest way is to reconfigure the xserver (the software that creates your graphical user interface) to use the **vesa** driver. You will lose some functionality (no 2D acceleration) but often you won't notice it. To reconfigure the xserver, press ctrl-alt-F1 to get a command line. On the command line enter ```
sudo dpkg-reconfigure xserver-xorg
```This gets you a text-based reconfiguration program that leads you through the process. Answer the questions the best you can (read the explanations). When you get to the time to configure the display, choose the **vesa** driver. When you are done reconfiguring, press ctrl-alt-backspace to restart the xserver.

Another thing you can try is to tweak the xorg.conf file settings directly to try to get the ati driver to behave properly. See [this Wiki]("https://help.ubuntu.com/community/RadeonDriver") for instructions. If you mess up your xorg.conf, you can always reconfigure it using dpkg-reconfigure as above.

The last thing to try is to use the restricted driver for Linux from Radeon. If the System --> Administration --> Restricted Drivers Manager does not have a driver listed for your card I would not attempt this method. [This page]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") has info on trying to use the restricted driver. Again, if it is not in the Restricted Drivers Manager, it is not recommended.

---

### Post by kdp8791 on 2008-03-23
I am not Dual Booting with Vista...

And Dstew thank you for your help, i will try that out right now.

---

### Post by Pumalite on 2008-03-23
If you were using Vista and you did not partition with Vista partitioner before installing and instead did it with the Live CD, that could be your problem.
I also think that you should install with the Alternate CD. If at that point you continue to have problems with xserver, then reconfigure it.

---

### Post by kdp8791 on 2008-03-23
i cant even stay unfrozen long enough to hit ALT-CTRL -F1...is there another way

---

### Post by Pumalite on 2008-03-23
The Alternate CD

---

### Post by dstew on 2008-03-23
> i cant even stay unfrozen long enough to hit ALT-CTRL -F1...is there another wayBoot into recovery mode (on the grub menu). It gives you a command line interface. Then do **sudo dpkg-reconfigure xserver-xorg** as above. Then do ```
startx
```

---

### Post by kdp8791 on 2008-03-23
I did that, now i have another problem..when i boot it into Normal mode, i get a blue screen with a gray box saying.."The display sever has been shut down about 6 times in the last 90 seconds. It is likely that something bad is going on. Waiting for 2 minutes before trying again on display :0...What is wrong with it now, i really looked forward to Ubuntu, but it seems more trouble that Windows Vista.

---

### Post by kdp8791 on 2008-03-24
I installed the Alternate CD, didnt help...I tried code on the command line and that didnt help either..Anything else i can try before going back to Windows Vista

---

### Post by Pumalite on 2008-03-24
Try a different distro to see if you are incompatible with Linux in general or Ubuntu in particular

---

### Post by dstew on 2008-03-24
It is still likely to be an xserver configuration problem. Check out [this thread]("http://www.linuxquestions.org/questions/ubuntu-63/display-server-has-been-shutdown-6-times-in-90-seconds...-504744/") for a possible fix. It might be a problem with the xserver trying to activate some hardware that is not there. This user commented out the input device sections for the wacom driver, which is for tablet PC's. You can also do sudo dpkg-reconfigure xserver-xorg again and look hard at anything you might not have got right.

---

