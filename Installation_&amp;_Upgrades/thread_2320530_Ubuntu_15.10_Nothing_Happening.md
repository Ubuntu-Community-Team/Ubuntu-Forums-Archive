---
title: "Ubuntu 15.10 Nothing Happening"
date: 2016-04-14
forum: Installation &amp; Upgrades
---

### Post by specbit on 2016-04-14
Hi.

Recently bought an ssd (crucial 240 Gb), installed windows 7 professional on a toshiba satellite l650 dual core 4 Gb RAM ATI DirectX11. Afterwords downloaded ubuntu 15.10 64 bits version and installed a dual boot OS system. Once the installation was over, everything seemed to be fine but once I entered my my login credentials and a window poped up to update (from update center). Once I done that, gave the order to restart and a screen came up because I left the installation dvd in the drive, but the PC froze. Opened the dvd tray and manually powered off and on the PC. Once I got to the credentials login, entered my credentials and then absolutelly nothing could be done; no dash, no nothing except the mouse pointer that was moving.
What to do next? Already reinstalled ubuntu 15.10.
Delete the partition on windows and restore the boot and mbr? The thing is that I´d really love to have this version, previous had the 14.xx LTS but enjoyed more the dash of 15th version.
Thank you.


[video]https://youtu.be/7k7aaYZdFAs[/video]

---

### Post by Bucky Ball on 2016-04-14
Try this. When you boot to the grub list of options to choose a kernel/OS, highlight Ubuntu and hit 'e' to edit.

Look for a line that ends in 'quiet splash'. At the end of that line add 'nomodeset'. (Should look like 'quiet splash nomodeset' at the end of that line.)

Follow the instructions at the bottom of that screen to save changes and proceed. Any luck? If that worked, we need to make those options permanent so let us know.

---

### Post by specbit on 2016-04-14
Hi.


Recently bought an ssd (crucial 240 Gb), installed windows 7 professional on a toshiba satellite l650 dual core 4 Gb RAM ATI DirectX11. Afterwords downloaded ubuntu 15.10 64 bits version and installed a dual boot OS system. Once the installation was over, everything seemed to be fine but once I entered my my login credentials and a window poped up to update (from update center). Once I done that, gave the order to restart and a screen came up because I left the installation dvd in the drive, but the PC froze. Opened the dvd tray and manually powered off and on the PC. Once I got to the credentials login, entered my credentials and then absolutelly nothing could be done; no dash, no nothing except the mouse pointer that was moving.
What to do next? Already reinstalled ubuntu 15.10.
Delete the partition on windows and restore the boot and mbr? The thing is that I´d really love to have this version, previous had the 14.xx LTS but enjoyed more the dash of 15th version.
Thank you.

[https://youtu.be/7k7aaYZdFAs](https://youtu.be/7k7aaYZdFAs)

---

### Post by Geoffrey_Arndt on 2016-04-14
Might have to invoke the "nomodeset" boot parameter to get your gui again (ati graphics).

 To  boot with the 'nomodeset' boot parameter. 
   1).   For a PC with no other operating system - the Grub2 menu will NOT be displayed by default, so:
>     Hold down (right) SHIFT to display the menu during boot. In certain cases, pressing the ESC key may also display the menu.  
   If you are able to boot with this parameter, you can install a graphics driver from the "Additional Drivers" utility in the actual install. 
   [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) <- How to set NOMODESET and other kernel boot options in grub2 
   [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) <-nomodeset option in detail 
   let us know how it goes
THE current(cy) in Documentation: 
[URL="https://help.ubuntu.com/community/PopularPages"]https://help.ubuntu.com/community/PopularPages

[/URL] Another rendition of above: 
   To enable boot via "nomodeset" grub option" 
   

[LIST]
[*]Boot the machine and at the grub menu highlight the kernel you want to use and click 'e' to edit.
[/LIST]
    

[LIST]
[*]Find the line that ends in 'quiet splash' and after a space, add 'nomodeset'.   The end of the line should look like this:
[/LIST]
    _quiet splash nomodeset_ 
   

[LIST]
[*]Follow the instructions at the bottom of that screen to save changes and continue
[/LIST]
[URL="https://help.ubuntu.com/community/PopularPages"]
[/URL]

---

### Post by grahammechanical on 2016-04-14
Please do not double post

[http://ubuntuforums.org/showthread.php?t=2320530](http://ubuntuforums.org/showthread.php?t=2320530)

Somebody has wasted their time. I know I have looking at a duplicate post.

---

### Post by coffeecat on 2016-04-15
Threads merged.

Please do not post the same thing in different parts of the forum. It dilutes community effort, and is bad netiquette.

---

