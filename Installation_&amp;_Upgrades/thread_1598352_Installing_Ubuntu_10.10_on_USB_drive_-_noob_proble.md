---
title: "Installing Ubuntu 10.10 on USB drive - noob problem"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by PearlChoco on 2010-10-16
Hello,
i'm a Windows user trying out Ubuntu for the first time. Since I want to keep my regular Windows install on my main hard drive, I want to install Ubuntu 10.10 on an external USB disk drive.

I started my PC with the Ubuntu Live CD, and selected "Install Ubuntu". During install I formatted my USB drive and made a swap (512MB) and /.. (8GB) partition on it. I created a username and password and after installation was completed I restarted my PC.

I selected the USB drive on the boot menu ( F8 ) and Ubuntu started, but then I arrived again on the menu where I have to choose between testing or installing Ubuntu! So I couldn't boot in the real Ubuntu installation.

Did I do anything wrong? Help please!

---

### Post by thebarisaxkid on 2010-10-16
If you placed the ISO image that you downloaded on the USB, then that is a problem.

You need to erase the ISO and any other files found on the USB.  You will then need to burn the ISO file to a cd.  Pop the cd in and go through the installation steps.  When it asks how/where to install, select Advanced, then select the usb drive, select the non-swap partition, and select install.

---

### Post by C.S.Cameron on 2010-10-16
You need to remove the Live CD from the optical drive first.

---

### Post by C.S.Cameron on 2010-10-16
Oops, double post.

---

### Post by PearlChoco on 2010-10-17
> **thebarisaxkid said:**
> If you placed the ISO image that you downloaded on the USB, then that is a problem.

You need to erase the ISO and any other files found on the USB.  You will then need to burn the ISO file to a cd.  Pop the cd in and go through the installation steps.  When it asks how/where to install, select Advanced, then select the usb drive, select the non-swap partition, and select install.

Thanks, that's it.

But it's still not working; I reformatted the USB drive, did a clean and succesfull install of Unbuntu and booted the PC with the USB drive (using F8 during startup) but now it shows the message "Operating System not found"... Same thing when I try it on my laptop.

Could I have chosen the wrong filesystem during install (ext4)?

---

### Post by luftbahnfahrer on 2010-11-09
I also am having trouble installing Ubuntu.  My computer is a Dell optiplex 760 and currently has Windows xp.  I've burned the cd and tried rebooting.  Directly after the Dell logo flashes, this messages shows up for about half of a second:
[IMG]https://mail.google.com/mail/?ui=2&ik=eb82f66024&view=att&th=12c3020853e5921a&attid=0.1&disp=inline&zw[/IMG]
Then the screen turns a purplish color for about a second, wish some Ubuntu logos at the bottom:
[IMG]https://mail.google.com/mail/?ui=2&ik=eb82f66024&view=att&th=12c301fd32bf9e82&attid=0.1&disp=inline&zw[/IMG]
Then the screen turns completely black and I get a single flashing cursor at the top.  I've tried redownloading the iso file and making new disks, but the same thing happens every time!  I also tried putting the installer on a formatted flash drive. The exact same process happens, except that instead of getting a completely black screen at the end, I get a bunch of messages I don't understand:
[IMG]https://mail.google.com/mail/?ui=2&ik=eb82f66024&view=att&th=12c301c52ab0773b&attid=0.1&disp=inline&zw[/IMG]

Thanks for any help in advance!

---

### Post by mr_Loki on 2010-11-09
Put out the cd from drive.

---

### Post by luftbahnfahrer on 2010-11-09
The cd is not in the drive.

---

### Post by mr_Loki on 2010-11-09
> **luftbahnfahrer said:**
> The cd is not in the drive.
1) That`s for OP
2) Can`t see images

---

### Post by SL0ltMJGyh on 2012-10-16
Is ur processor 32 or 64 bit? i have a 32 so i downloaded the 32 and it worx. Look for hardware :D

NO BILL GATES!:guitar:

---

### Post by oldos2er on 2012-10-16
Old thread closed, please don't bump old threads.

---

