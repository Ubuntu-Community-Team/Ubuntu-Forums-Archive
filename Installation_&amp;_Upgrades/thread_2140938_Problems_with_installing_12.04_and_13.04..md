---
title: "Problems with installing 12.04 and 13.04."
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by mjongerh on 2013-05-01
So I tried to install 13.04 in my old PC but there was an error the first time. The second try there was no error, but it got stuck somewhere.
I thought that my PC was just to old for 13.04, so I downloaded 12.04 and try to install that one, from a USB drive too.
After selecting "Install Ubuntu on a Hard Disk" there was just a black screen, nothing more. I pressed some buttons, but nothing happend. The PC was still running though.

I think it is a dualcore Intel processor, but I am not sure about it.
Is this a common problem? Or is my PC just to old?

---

### Post by dino99 on 2013-05-01
no ubuntu is able to use oldish hardware; but you might know which hardware it is, i may say :confused:.

[http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

you might need to test some boot option to bypass that graphic driver issue:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by mjongerh on 2013-05-01
I am trying to install 13.04 again, beceause at least I can see what is happening, no graphic problems here.
It gets stuck on "saving installed packages..."

---

### Post by mjongerh on 2013-05-01
13.04 didn't work again.
So tried 12.04, this time a do have a screen, but when I install the installer crashed.

"Installer Crashed
We're sorry; the installer crashed. after you close...."
Then the window: "Apport" is collecting problem information.
And then I got a bug report an got directed to launchpad.net
submitted my bug report there, hopefully I will get some results.

---

### Post by grahammechanical on 2013-05-01
I am using an Intel core2 duo 2.4Ghz and 1GB RAM and 13.04 with Unity runs fine. Here is something you can try.

1) Insert the DVD and at the first purple screen (with human and keyboard icon) press Enter.
2) At the next screen Press Enter to select English as the default install language (or select some other language)
3) Press F6 and a small menu will appear at the bottom right. Scroll down the menu and select nomodeset and press Enter to mark that selection.
4) Press Esc to get back to the TRY - Install screen and select Try Ubuntu and press Enter.

See if that gets you to a live session from where you can select Install Ubuntu. There are other F6 options that you can try also. By the way I do not recommend install Ubuntu and ticking Install third party software. That will install a proprietary video driver which may or may not give you a broken desktop with the first re-boot after installing.

You can activate a proprietary video driver after installation by going to System Settings>Software & Updates>Additional Drivers tab. You can install third party software after installation by searching the Ubuntu Software Centre for Ubuntu Extras.

Regards.

---

