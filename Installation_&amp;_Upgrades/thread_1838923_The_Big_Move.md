---
title: "The Big Move"
date: 2011-09-04
forum: Installation &amp; Upgrades
---

### Post by nick2k11 on 2011-09-04
I am making the big move to Ubuntu and wiping out Windows. I have a question about the nVidia driver(s). When I search for drivers off of the Live CD, it doesn't pick up my nVidia 9700 card. Will this be resolved once I install Ubuntu?

---

### Post by Allavona on 2011-09-04
If your feeling apprehensive in the slightest, do a dual boot so as not do disrupt your ability to get work done. This way you still have a working system that you can do work on and your Ubuntu install that can be made to work if need be. Try a simple search of your hardware On Nvidias site to see if it supported by them first.

---

### Post by nick2k11 on 2011-09-04
Thanks for the advice! nVidia does have drivers for Linux 64-bit in my graphics card. I am ready to go! :D

---

### Post by Allavona on 2011-09-04
Great news! I'm happy that it worked out for you.

---

### Post by Old_Grey_Wolf on 2011-09-04
I would suggest a backup of important files, and Windows restore CDs/DVD just in case something goes wrong or you make a mistake. Read my sig...

---

### Post by nick2k11 on 2011-09-04
Thanks! I have moved what I want to keep to an external hard drive.

---

### Post by oldfred on 2011-09-04
I have a nVidia 9600GT and have to use nomodeset on first boot.


How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place

---

