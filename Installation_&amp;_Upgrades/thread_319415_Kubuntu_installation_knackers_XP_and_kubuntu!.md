---
title: "Kubuntu installation knackers XP and kubuntu!"
date: 2006-12-15
forum: Installation &amp; Upgrades
---

### Post by michaelc.nash on 2006-12-15
Hi

Firstly I'm a newbie, and a real techno-idiot. Apologies in advance.

I use XP, and downloaded the Kubuntu live CD/install CD for a normal x86 desktop and it worked fine. The live CD loaded, and appeared to install everything correctly. I made sure that i was installing to my second internal hard disk (first internal hard disk = XP, second internal hard disk = brand new disk, bought for dual boot as first disk too small to usefully partition).

Kubuntu then proclaims that it has successfully installed and I can either restart the machine or carry on using the CD. I tell it to reboot, which it does.

However, when it gets to the GRUB stage, it then tells me that it has error 17. This means, as far as I can tell, that I can't even now load my existing XP installation or the new Kubuntu one! No key that I press achieves anything but an angry beep.

Does anyone have a clue what I might have done wrong? And how I fix it? If I remove this second internal hard disk, will XP boot as per usual? (That's only a temporary fix, since I need a Linux distribution for work). 

Thanks in advance, 

Michael

---

### Post by michaelc.nash on 2006-12-15
I have now tried using the plain Gnome installation instead of the KDE version.

Boot-up fails at exactly the same place - but instead of GRUB giving me error code 17, I now get error code 21.

](*,) ](*,) ](*,) :( :( :( 

Any ideas, anyone? At all?

---

### Post by eriefisher on 2006-12-15
How did you install?? I unplugged my XP drive to install Kubuntu and then made XP the second HD. Then I added XP to the /boot/grubmenu.lst and no problems. Try to unplug the XP drive and boot Ubuntu.

---

### Post by bulldog on 2006-12-15
Do you have an IDE disk and a Sata in your computer?
Can you give us the outcome of ```
sudo fdisk -l (l as in Like) 
```

---

### Post by michaelc.nash on 2006-12-16
Thanks for the help guys - I now know what I did wrong.

In the setup menu that you can access as soon as your computer starts up (the BIOS setup, I think), it was not set up to detect my slave IDE drive. So as far as GRUB was concerned, there was nowhere to load Ubuntu from! I just set it to AUTO detect, rebooted and it worked fine.

All is mended now - Ubuntu and XP work fine.

Thanks again.

---

