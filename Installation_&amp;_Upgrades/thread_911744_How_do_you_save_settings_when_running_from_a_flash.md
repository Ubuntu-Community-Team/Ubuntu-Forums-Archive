---
title: "How do you save settings when running from a flash drive"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by X_X_loaded_X_X on 2008-09-05
Hey I installed unbuntu 8.04 on a 4GB flash drive to use it at work on different computers. I used this program [http://www.pcmech.com/article/how-to-install-ubuntu-linux-with-no-optical-drive/](http://www.pcmech.com/article/how-to-install-ubuntu-linux-with-no-optical-drive/) It makes it super simple with just an ISO and usb drive. But since its a live session how do I save any settings or installs or updates? Shouldnt there be a way to do this since it is installed on a drive? I looked around and have not found anything. Thanks in advance!

---

### Post by X_X_loaded_X_X on 2008-09-06
bump.

---

### Post by Herman on 2008-09-06
You can't. (At least not easily).
The files from the .iso file are still being booted as a live CD and are running as if they were in a CD.

You can have a live CD running with 'Persistence', but you'll need to do a bit of re-arranging to set that up and get it to work.
First, you'll need to partition your flash drive with another partition and name the file system in that partition 'casper-rw'. Then you will need to edit your syslinux bootloader's configuration file to get your kernel booted in a special mode so that it will recognise the 'casper-rw' partition and set up some files in there where your settings and files will be saved. The Ubuntu partition itself will remain read-only.
If you want to learn how to do that, go to [Pendrive Linux.com]("http://www.pendrivelinux.com/")

An easier way, especially if you have a fast enough flash memory and it's 'ReadyBoost' compliant, or if you're not expecting to be use the USB all the time, is to just install Ubuntu in the USB flash memory as if it was another hard drive. If you have a good quality flash memory with good 'endurance', (over a million read/write cycles), it should last for a fair while before it wears out.
Just make sure you install GRUB to the flash memory's MBR, not your first hard disk's MBR. (It won't damage your hard disk's MBR, but it will mean more work for you to do changing things again if you're not happy with that arrangement).
I prefer this later type of installation myself. I have just finished setting up a flash memory with Ubuntu installed in it and setting it up for an Eee PC 701. It's really neat! There are some tricks in the [Eee Ubuntu]("http://www.ubuntu-eee.com/index.php5?title=User_Guides") website that should be useful also for installing Ubuntu in USB flash memory sticks, [How to: free up space]("http://www.ubuntu-eee.com/index.php5?title=How_to:_free_up_space"), [How to: Reduce Disk Writes to Prolong the Life of your Flash Drive]("http://www.ubuntu-eee.com/index.php5?title=How_to:_Reduce_Disk_Writes_to_Prolong_the_Life_of_your_Flash_Drive")            [How to reduce swappiness]("http://www.ubuntu-eee.com/index.php5?title=How_to:_reduce_swappiness"). Those should be useful.

---

### Post by X_X_loaded_X_X on 2008-09-06
Thanks! Installing it to the flash drive is easier! Also thanks for the grub tip anyone who uses the about for a reference. You have to select the advanced tab right before the actual install to get the option to install grub to the flash drive.

---

