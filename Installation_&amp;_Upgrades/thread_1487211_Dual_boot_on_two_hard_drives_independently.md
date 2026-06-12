---
title: "Dual boot on two hard drives independently"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by dulwichdik on 2010-05-18
[SIZE=4]Dual boot on two hard drives independently[/SIZE]
[SIZE=3]Another newbie!
Hello can anyone advise me ? 
My current set up has two sata drives. Vista 32 on one and win 7 64 on the other, both were installed in the 1st slot separately and are independent  of each other, I change drives in BIOS. 
I do not want Vista anymore and will replace it with Ubuntu 32, I would like to keep the drives independent. I guess I should disconnect the win 7 , then install Ubuntu in the 1st slot. this is how I did it for the above. I want to know how I would instruct Grub2 to have windows as the 1st option in the boot order and how to adjust the time out. would I be right in believing that the windows MBR would be left untouched? 
After I have made the adjustments to Grub I would then power down and connect the windows disc to a spare slot and grub should pick up the drive and have it as an option in the boot menu, am I correct in the above assumptions? 
I would like to do it this way as I am pretty new to computing and I want to keep all the options open and, above all to keep it as simple as possible, this way methinks there would never be any conflicts between O/S's nor possible errors in the MBR? 
I have little knowledge of terminal (or command prompt) and require the commands so I can copy and paste them in, hopefully with time, study and practice I'll be able to delve in with confidence, windows doesn't promote tampering or tweaking and until recently made it over-difficult.
Any suggestions would be greatly appreciated
[/SIZE]

---

### Post by darkod on 2010-05-18
Disconnecting the win7 disk does help with confidence, but it can sometimes create confusion when you plug it back in. It's better if ubuntu during installation knows there is another disk too, and win7 is on it.

The process is not difficult, and if you pay attention there should be no problems.

Are both disks the same size, can you tell them apart by size or manufacturer?

---

### Post by dulwichdik on 2010-05-18
Hello darkdod, thanks for info, the disks are both 320gb and of different manufacturer, what confusion can it create? (sometimes)!

---

### Post by darkod on 2010-05-18
For booting purposes grub labels the disks as hd0 (first), hd1 (second), etc. When you install with only the ubuntu hdd, it will be hd0, no other option because there is one disk.
When you add the win7 disk, it may become hd0, and the ubuntu disk hd1, so grub will not work properly because it will be looking at the wrong disk all the time.

But you can try and install with the win7 disconnected, and often it works out OK.

Once you connect it back, ubuntu will not know win7 is there (because it didn't detect it during installation) until you open terminal in Applications-Accessories and run:

sudo update-grub

That should detect win7 and update the boot menu.

For controlling default OS and timeout, when you are not familiar with commands in terminal yet, it's easy to install the package startupmanager which can manage it for you with graphical interface. You do it in terminal with:

sudo apt-get install startupmanager

Note: when you use the sudo in front of a command, it will usually ask you for your ubuntu password to enter it again. This is for confirmation before executing commands as administrator (super user).

PS. I don't use startupmanager so I don't know where exactly it will show in the menu after you install it, but it will either be in System-Administration, or Applications-System Tools... Look around.

---

### Post by dulwichdik on 2010-05-20
Darkod, Thanks for your help, I have done a bit more research and looked up your suggestions, having a start up manager would work for me I think that maybe I was being a tad paranoid about screwing with the MBR, but it looks as if Linux is a lot more flexable than windows and changes made are are a short fix away. this sudo update- grub is what I would need if I added another drive, another question answered, Thanks again D/D

---

