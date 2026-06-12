---
title: "Ubuntu install on Dell M6700 with M5000M Nvidia using 18.04, 20.04.6, 22.04 - UGH"
date: 2024-04-18
forum: Installation &amp; Upgrades
---

### Post by casiobearing on 2024-04-18
Hi,
Short story - Trying to leave Windows behind which I only need for my Solidworks,
Luckily I use Clonezilla Live CD regularly for bare metal backups so I had that close to hand. Aiming to put Ubuntu on 2nd drive.
I dedicate this post to the demise of three DVDs and 18 hours of time.

My system, Fully loaded Dell M6700, Optimus enabled, triple hard drives, was UEFI boot but now using BIOS multiboot - Win 10 on 1st drive, Win 11 on 2nd drive.

Attempt #1 - Try out 22.04 as a Live install - total failure, fails to launch live and just hangs.

Attempt #2 - Started with DVD install of 22.04 - total failure - 99.9% of the time the screen is black, occasionally a mouse cursor appears for 30 seconds or so but the hard drive and DVD drive just go bananas with a dead system.

Attempt #3 - Started with a DVD I have of 18.04 - excellent, installs perfectly no issue once I got past a bug (use of incorrect keyboard layout for initial username\password entry) that prevented me logging on using a # character. Decided to do an online upgrade to 20.04 - perfect no issue. Decided to do further online upgrade to 22.04 - failed - same result as the 22.04 DVD install with a black screen doing ziltch.

Attempt #4 - Grubbed into the 22.04 recovery with safe graphics. Then using the terminal tried the following I found in the internet -
sudo apt purge ~nvidia
sudo apt autoremove
sudo apt clean
sudo apt update
sudo apt full-upgrade
sudo reboot

Success! I ended up with a dual boot Win 10 and Ubuntu 22.04 - So Clonezilla'd everything before further experimenting.

Experiment #1 Created DVD of 20.04 - DVD install appeared to be working from the start showing the Ubuntu screen (unlike 22.04) but right at the end of the install process 20.04 totally destroy my boot partition, taking out absolutely everything including my Win10 installation - Not good :o( thank god for Clonezilla!
Restored my 1st drive containin the Win10 and boot partition - system still dead!
Restored 2nd drive with backup of 22.04 that I installed earlier - woohoo I'm back up and running.

Experiment #2 Installed Nvidia other driver for M5000M - seems to be working fine.

In summary, 18.04 is the only DVD I can install without anything breaking. 20.04 seems to destroy booting somehow not yet determined, and 22.04 just doesn't work at all with the graphics subsystem during install.
 
So for now I'm good, with Clonezilla backups of everything just in case :o)
I hope this is of help for other Dell users.

---

### Post by MAFoElffen on 2024-04-21
That Dell Laptop came with an NVidia GPU and Intel iGPU:
> 
NVIDIA® Quadro® K3000M 2 GB Intel® HD Graphics 4000

Ubuntu's ISO image is oversized and is meant to install via an installer LiveUSB media. It will have a challenge installing via DVD. That lapptop will boot via USB.

Because of the NVidia Graphics, boot from the Grub Menu using the "Safe Graphics" option. Select the "install 3rd party drivers" checkbox during the install to try to install the driver for NVidia. If not, then reinstall it after the first boot, by addig the "nomodeset" boot parameter to te Grub2 boot line, then installing the driver in the Alternate dDrivers tab of the "Software & Updates" application.

For my laptops that came with a DVD drive, I remove them and add a SATA drive bay caddy in place of the DVD drive... You have the option to have 2 SATA drives, and a 3rd mSATA drive (in the WAN card slot). I value those kinds of storage these days over DVD storage.

---

