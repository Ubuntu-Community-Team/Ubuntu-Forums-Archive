---
title: "Ubuntu Installation error"
date: 2011-06-17
forum: Installation &amp; Upgrades
---

### Post by mesquka on 2011-06-17
I tryed to install Ubuntu, but it just displays a blank screen

---

### Post by oldfred on 2011-06-17
Welcome to the forums.

Do you have nVidia? Often blank screens are related to video issues. I have nVidia and it turns my monitor off just after it starts. But I install from flash drive and flash drive still flickers as if it is still installing (it is).

I have to add nomodeset for CD or first boot after install.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

Other options:
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

---

### Post by Quackers on 2011-06-17
Welcome to UF :-)
I'm afraid we'll need more information than that! :-)
Are you dual booting?
Which version of Ubuntu?
What graphics card is in use?
How much ram?

Aha! oldfred beat me to it - please see above post :-)

---

