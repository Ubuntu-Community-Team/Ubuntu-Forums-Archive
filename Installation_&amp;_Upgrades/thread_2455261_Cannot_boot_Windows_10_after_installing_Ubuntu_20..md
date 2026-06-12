---
title: "Cannot boot Windows 10 after installing Ubuntu 20.04 as dual-boot"
date: 2020-12-16
forum: Installation &amp; Upgrades
---

### Post by nighty000 on 2020-12-16
Hello everyone,
I'm very new to Linux, Ubuntu and dual-booting, so please forgive me any dumb mistakes or anything similar. 

My problem is probably one of the very well known ones but I can't really understand much of the things I found on the Internet besides "just make another bootable flash drive with windows 10 and try that" which would probably result in some errors from my side. 
So I'm asking you experts to help me with the following. I created a boot-usb-flashdrive using rufus and the .iso-file from the official Ubuntu page. Everything went just fine. I deactivated fastboot and smartboot I think it was (I don't remember, the one boot option that's not secure boot), restarted my pc with the new Ubuntu flashdrive and installed Ubuntu. I ticked "Install Ubuntu as second operating system besides Windows 10" (not literally the option but I think you get my point), Ubuntu asked me to create a new partition and then I installed it there. 
Now after I tried "reboot" in the terminal I got a screen with 4 options two of which were "Ubuntu" and "Windows Boot-Manager". After selecting the Windows Boot-manager though it didn't start Windows 10. After many tries it either just kicked me back to these 4 options after a loading screen or Windows tried to repair something which didn't seem to work either. 
My Windows stuff still exists and I think nothing was lost so it might just be a minor error. Anyways, I tried boot-repair after that and got some boot information which you can see in my attachment. Boot-repair didn't do anything but maybe you can help me with the information provided by my file.
Thanks in advance.

---

### Post by yancek on 2020-12-16
Line 33 of boot repair shows:  BootCurrent: 0000
Line 36 of boot repair shows:  Boot0000* Linpus lite    
That means you were booting from Linpus Lite when you ran this.  Do you now have or did you previously have Linpus Lite installed on this computer?
Line 35 shows BootOrder: 0002,0000,0001,2001,2002,2003
0002 shows Ubuntu first in boot order so it should boot instead of Linpus.  If you have/had Linpus installed, is this an Acer?  If so, did you go into the BIOS firmware and set an administrator password and then enable trust?  When you are in the BIOS Boot options, are you able to select ubuntu to boot?

Seems strange that the BootCurrent shows Linpus while you indicate that your Grub menu only shows Ubuntu and windows.  Unfortunately, the boot repair does not show any grub.cfg files so no way to know if entries are correct.

---

### Post by nighty000 on 2020-12-16
I don't think Linpus Lite was ever on my PC but I'm not sure. All I can say is I bought as new product and didn't install Linpus Lite myself.
Yes, it's an Acer laptop and as I've looked it up now the boot order is 1.Linpus Lite, 2.Ubuntu, 3.Windows Boot Manager. I did not set an administrator password and did not enable trust. 
I can't select any system to boot. It just shows the boot order.
By the way, everytime I start my PC "System order not found. something something." shows up for a second and then I get my Grub.

---

### Post by yancek on 2020-12-16
Take a look at the page at the link below which describes a similar problem.  You need an administrator password and to set trust in the BIOS on boot.

[https://ubuntuforums.org/showthread.php?t=2317122&p=13455301#post13455301](https://ubuntuforums.org/showthread.php?t=2317122&p=13455301#post13455301)

You could also try to change the boot order from Ubuntu by using the instructions at the link below.  If that doesn't work, you will need the administrtator password to set trust.

---

### Post by nighty000 on 2020-12-16
What exactly do you mean by "You need an administrator password and to set trust in the BIOS on boot."? I activated secure boot by setting a new password. After that I tried doing the same like the guy in the other post. It didn't change anything. After that I tried to set bootmgfw.efi.mui to trusted but didn't change anything either. The only thing that changed was my boot order. Some new "EFI" entries appeared and I experimented with my boot order but no change either. You have any idea? Or should I just reinstall Windows and uninstall Ubuntu and maybe try again?

---

### Post by nighty000 on 2020-12-16
Okay, nevermind. The last thing I trusted seems to have solved the problem. Many thanks for your help

---

### Post by grahammechanical on 2020-12-16
> Okay, nevermind. The last thing I trusted seems to have solved the problem. Many thanks for your help

It would have been educational if you had informed the rest of us what the solution was. Then we could have used your solution to help others who may have the same problem. 

Regards

---

### Post by yancek on 2020-12-17
>  You need an administrator password and to set trust in the BIOS on boot.


When you boot the computer, you need to watch the screen for the key to use to access BIOS firmware.  The last time I used an Acer, it was the F2 key but whatever it is should show on screen but only for a few seconds.  Once in the BIOS, you should have a Security tab or option where you can set an administrator password then set trust.

> After that I tried to set bootmgfw.efi.mui to trusted   

That's a windows file.

---

