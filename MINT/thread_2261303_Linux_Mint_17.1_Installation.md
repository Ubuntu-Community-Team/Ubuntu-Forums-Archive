---
title: "Linux Mint 17.1 Installation"
date: 2015-01-17
forum: MINT
---

### Post by stefan.pilot on 2015-01-17
Hi,

I installed Linux Mint 17.1 Cinnamon on an old Windows XP computer. There are two hard drives, let's call them HD1 and HD2. Windows is located on HD1, I installed Mint on HD2. I had to set the parameters "noacpi noapic nomodeset" to get the live session to work. Then I installed, the directories look fine to me from the live session. But Mint does not boot. At first, when I start the computer, the bios automatically boots Win XP, I have to make it booting from HD2 manually. (How to fix this?) When I do this, I see grub. But neither the normal mode or the "recovery mode" do work, I always see strange red and blue symbols on the screen and the computer seems to freeze. I think there may be an issue with my video card driver, but I don't know how to fix it. My video gard is an nVidia 8800 GT. The following tutorial did not help me: [http://community.linuxmint.com/tutorial/view/842](http://community.linuxmint.com/tutorial/view/842)

Thank you all in advance and sorry if this is in the wrong place.

---

### Post by yancek on 2015-01-17
>  At first, when I start the computer, the bios automatically boots Win XP, I have to make it booting from HD2 manually. 

That would be because you installed the Mint Grub bootloader to the master boot record of the second hard drive the one with Mint on it and that is expected behavior.
You can either install Grub to the master boot record of the xp drive as it appears to be set to first boot priority, or you can set the Mint drive to boot first in the BIOS.

When you boot and see the Grub menu with Mint, make sure that Mint is highlighted and hit the e key on your keyboard to do a one time edit.  Use the arrow keys on your keyboard to go down to the linux line and put the "nomodeset" parameter in, before quiet splash --.  It should tell you at the bottom of the screen which key to hit to continue booting.  If that doesn't work, try all the parameters you used when installing.  If you are able to boot Mint, you will need to go to System Settings or the Control Center and take a look around for an option to "Install Additional Drivers" and select it and let it run.  I don't use Cinnamon so don't know exactly where you would find this option.

---

### Post by stefan.pilot on 2015-01-17
I added the paramter "nomodeset", Mint booted, I installed an nVidia driver, I think it's 337 or something like that. 

On reboot, the X-Server crashes: "No screens found". After that, I see the command line.

---

### Post by Bucky Ball on 2015-01-17
*Thread moved to **MINT**.*

Welcome. The main support areas here are for Ubuntu and its official flavours Kubuntu, Xubuntu, Edubuntu, Lubuntu, UbuntuGnome, Ubuntu Studio, and Mythbuntu. While you are welcome to post in the Mint section here, Linux Mint also has an active community and forum [HERE]("http://forums.linuxmint.com/"). Good luck. ;)

---

