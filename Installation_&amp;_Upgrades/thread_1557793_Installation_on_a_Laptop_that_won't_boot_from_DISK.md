---
title: "Installation on a Laptop that won't boot from DISK or USB"
date: 2010-08-21
forum: Installation &amp; Upgrades
---

### Post by jamesgreeny on 2010-08-21
Hello,
I have a really old sony vaio and the disk drive does not work, it does not have the option to boot from usb so im kind of stuck. Is there any other way I can install unbuntu through windows xp? 

---------------------------------------
LAPTOP SPECS
---------------------------------------

MODEL- SONY VAIO PCG-GRT786M
OS- WINDOWS XP HOME EDITION SERVICE PACK 3
RAM- 1GB
PROCESSOR- P4 2.66 GHz
GRAPHICS CARD- GF FX Go5600
HARD DRIVE- 40GB

---------------------------------------

Thanks,
James.

---

### Post by jamesgreeny on 2010-08-22
can anyone help please?

---

### Post by SplinteredChaos on 2010-08-22
The disk drive, as in the hard disk, the floppy disk or rom disk?

---

### Post by oldfred on 2010-08-22
Does you system even meet requirements for full Ubuntu?

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
[https://help.ubuntu.com/community/Installation/SystemRequirements#Lightweight%20GUI%20alternative%20%28Xubuntu%29](https://help.ubuntu.com/community/Installation/SystemRequirements#Lightweight%20GUI%20alternative%20%28Xubuntu%29)

---

### Post by jamesgreeny on 2010-08-25
besides having a working disk drive it does, i've updated the specs list :)

---------------------------------------
LAPTOP SPECS
---------------------------------------

MODEL- SONY VAIO PCG-GRT786M
OS- WINDOWS XP HOME EDITION SERVICE PACK 3
RAM- 1GB
PROCESSOR- P4 2.66 GHz
GRAPHICS CARD- GF FX Go5600
HARD DRIVE- 40GB

---------------------------------------

---

### Post by oldfred on 2010-08-25
Without external access of some sort it is difficult. There a network installs but I do not know how. There is plop which will allow a floppy boot and install from USB. You can also from windows create a 1GB partition and install to that the installer. But without a way to boot externally any one issue and the entire system  could be a brick. Some portables can remove the hard drive easily and that often is the best way. Just plug the drive into another system and set it up on that system. It should work as long as you do not install any proprietary video drivers.

---

### Post by techxcell on 2010-08-25
Hi there, I help a lot of my friends move on from *indows so I face this problem often.

I came across a very useful gadget viz. "USB to SATA/IDE Adapter". Its easily available these days and is quite cheap. Just Google it. 

Laptops generally have an easily accessible HDD compartment on the under-side. The cover is secured by just 2 screws. Its easy to remove the HDD which is normally a 2.5 inch SATA. It must be very clear by now where I am going with this. Anyway this is how:


[LIST=1]
[*]Remove the HDD from the laptop
[*]Attach your notebook's HDD to a working system (a friend's notebook perhaps) via the USB to SATA Adapter I mentioned above.
[*]Boot the working system with the Ubuntu Live CD and run the install. Select the external HDD (now connected to the USB port)  as the install target. And er... that's it I guess! oh..
[*]Put the hard-disk back into your notebook :)
[/LIST]
I did not go into installation details. Its better to install just the ubuntu-minimal package. Then issue an "apt-get install ubuntu-desktop" when the HDD is back in your own notebook.

Hope this helps! ;)

---

### Post by jamesgreeny on 2010-08-25
Hi I installed boot manager on the laptop but I don't know how to boot the usb i've made in it. I followed these steps:

Alternative method
Some computers can see the USB thumb drive and have the option to boot from USB but cannot actually boot from USB. All hope is not lost.

Requirements
Windows running on the computer
USB drive, ready to boot (shown below)
PLoP Boot Manager - Your alternative USB boot method ([http://www.plop.at/en/bootmanager.html#runwin](http://www.plop.at/en/bootmanager.html#runwin))
Just follow the instructions on the PLop website.

Note: When you use this method, the files on the USB drive are changed during boot. To use this method more than once, you must delete all files from the USB drive and prepare the USB drive again as described below.

Creating a bootable USB Drive
Check the USB drive for files and back them up if needed, all contents will be destroyed.
A minimum of 1GB space is required for a netbook install. Other install types may require more space.
The Windows utility won't let you select the USB drive if the drive isn't properly formatted and mounted. Booting from a USB drive created with this utility will behave just as if you had booted from the install CD. It will show the language selection and then the install menu, from which you can install Ubuntu onto the computer's hard drive or launch the LiveCD environment.

[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

---

### Post by techxcell on 2010-08-25
Well.. if your system enumerates a USB Pen Drive during boot, it means you "CAN" boot from from it!

In that case you do not need to look further than [UNETBOOTIN]("http://unetbootin.sourceforge.net") . It will install any of your downloaded .ISO images to your USB Drive and make it bootable.

Ubuntu users can install it with "sudo apt-get install unetbootin" if Ubuntu Partner repository is activated.

---

### Post by lechien73 on 2010-08-25
Since you're using Windows, download the Windows version of unetbootin here: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Install it, and then use it to the Ubuntu iso that you have presumably downloaded to your USB stick.

Reboot, and PLoP will allow you to boot from the USB stick and install Ubuntu :)

Before installing, choose the option to test Ubuntu. It would be good to know before you install what hardware compatibility issues you may encounter.

**EDIT:** Or exactly as techxcell said :) this is what happens when I don't refresh the screen before replying :oops:

---

### Post by jamesgreeny on 2010-08-25
thanks so much for the help guys :) 
I've got plop boot loader working and im creating the usb now will keep you updated :)

---

### Post by jamesgreeny on 2010-08-25
Thanks so much guys the USB worked and I'm installing UBUNTU right now. Thanks for the help :)

---

### Post by lechien73 on 2010-08-25
Hope you enjoy Ubuntu :)

If you get chance, please could you go to the **Thread Tools** menu at the top and mark the thread as [Solved]?

Thanks

---

