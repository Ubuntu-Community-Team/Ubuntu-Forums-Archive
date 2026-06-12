---
title: "Dual boot question..."
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by scb0825 on 2007-08-24
Hello! 

I am rather new to linux; I have been using Feisty as a primary OS now for about month (I know that may not seem like a lot) and I intend to keep using it as a primary OS; however, I would like to keep Windows just in case. ;)

My machine is set up like this...

HD Primary - 150GB Windows
HD Secondary - 80GB Ubuntu
HD (IDE Raid Controller) Primary - 80GB Storage
HD (IDE Raid Controller) Secondary - 80GB Storage

Currently, I use my computers BIOS boot menu to select which drive I boot. I would like to make the Ubuntu drive the primary and the Windows the secondary. When I installed Ubuntu onto the secondary drive it found windows on the primary and added it to the Grub boot loader. I have not tried to load Windows from Grub since I haven't been booting from it directly. 

I would like to know how difficult it will be to swap the two so that the drive Ubuntu is on is the primary and the drive Windows is on is the secondary, and what steps I should take to do this. Any and all help is appreciated!

:mrgreen:

---

### Post by forestpixie on 2007-08-24
Does grub actually work properly? If it does why do you want to change drives about - you could edit your menu so's it boots Ubuntu quicker - ie you won't get the choice for long, or so you don't get a choice and have to press esc to get the choice.

That was how I had my dualboot working.

---

### Post by scb0825 on 2007-08-24
> **forestpixie said:**
> Does grub actually work properly? If it does why do you want to change drives about - you could edit your menu so's it boots Ubuntu quicker - ie you won't get the choice for long, or so you don't get a choice and have to press esc to get the choice.

That was how I had my dualboot working.

I probably didn't do a very good job of explaining my issue. I installed ubuntu on a secondary drive, windows is on my primary drive. To boot from the secondary drive I use my machines BIOS boot menu... which requires a key stroke at boot up and at times I'm too lazy ;)

Anyway, I do not want to reinstall anything... I just want to know if I can swap the two making the ubuntu drive primary and the windows drive secondary and use grub as the boot loader. I also want to know what I may have to change in grub so that it knows that the windows drive is now the secondary drive.

---

### Post by wudsta on 2007-08-24
Just change the boot order of your drives in your BIOS?

---

### Post by confused57 on 2007-08-24
> **scb0825 said:**
> I probably didn't do a very good job of explaining my issue. I installed ubuntu on a secondary drive, windows is on my primary drive. To boot from the secondary drive I use my machines BIOS boot menu... which requires a key stroke at boot up and at times I'm too lazy ;)

Anyway, I do not want to reinstall anything... I just want to know if I can swap the two making the ubuntu drive primary and the windows drive secondary and use grub as the boot loader. I also want to know what I may have to change in grub so that it knows that the windows drive is now the secondary drive.
With Feisty, you "might" be able to just switch the drives(primary & secondary) without doing anything else to reconfigure grub...I don't think it would do any harm to just try it.

Added:  If you're able to boot Feisty after changing the position of the hard drives, you may need to change your device.map in order to boot Windows, e.g.
(hd0) /dev/sda
(hd1) /dev/sdb

You might want to open a terminal(Applications---Accessories---Terminal), and see how your Ubuntu & Windows drives are designated:
```
sudo fdisk -l
```
-l is a lowercase "L"

---

### Post by fumduck on 2007-08-24
whats your motherboard?? You should be able to just change boot order

---

### Post by Jeff4 on 2007-08-24
I think that I have the exact same problem as scb0825. I installed Ubuntu on a spare HDD with my Win2K drive removed. Then I installed both drives in the PC, and used the BIOS setup screen to dual boot.  Can I now reconfigure GRUB on the Ubutu drive to be able to choose either drive to boot?  My Win2K drive is formated NTFS, would that be a problem? 
Thanks in advance, -Jeff.

---

### Post by scb0825 on 2007-08-24
> **confused57 said:**
> With Feisty, you "might" be able to just switch the drives(primary & secondary) without doing anything else to reconfigure grub...I don't think it would do any harm to just try it.

Added:  If you're able to boot Feisty after changing the position of the hard drives, you may need to change your device.map in order to boot Windows, e.g.
(hd0) /dev/sda
(hd1) /dev/sdb

You might want to open a terminal(Applications---Accessories---Terminal), and see how your Ubuntu & Windows drives are designated:
```
sudo fdisk -l
```
-l is a lowercase "L"

I will try just swapping the drives this weekend. I will report back with the results. If it doesn't just "work" after swapping, I am just going to reinstall Ubuntu after swapping the drives. I have been dicking around with it, especially with Compiz Fusion, and I finally think I have a handle on things... but I have a feeling that I may have mucked things up in the process of dicking :) Today after fixing my Cf, I was installing and removing some applications... when I rebooted I got a "Panel already running, I'm closing" type of error... and Gnome pretty much just crapped on itself. I got it back by doing a killall gnome-panel in terminal... I have a feeling that some stupid KDE auto updates caused this panel problem, because it didn't occur until after the updates. Anyway, with that being said I think I'm going to start fresh. I will report back on Sunday.):P

---

