---
title: "Ubuntu 12.04.1 - USB Install Stick Shows Text During Boot But Doesn't Launch GUI"
date: 2013-03-06
forum: Installation &amp; Upgrades
---

### Post by svet-am on 2013-03-06
I just set up a new machine based around the Intel DX48BT2 and some other hardware I have laying around. My video card is an EVGA 560 Ti.

Previously, I had all of my hardware on an EVGA 780i until it died so I know that all of _that_ hardware is fine/Ubuntu compatible.

What I'm seeing is that when I boot from the USB stick, I see all of the normal boot-time console messages such as hardware detection and the like but the GUI never launches.

In the background I can hear the tribal drum signifying that Ubuntu has booted but I don't have a GUI. I also cannot switch to a different terminal so I can muck around at the command line (but my keyboard is still responsive since I can toggle CAPS lock and NumLock just fine).

This is the first time I've run into this kind of issue so I don't know what to make of it (but it smells like a video card / chipset issue...)..

As an additional note, Windows works 100% on this hardware configuration so I know the hardware is all okay (even together).

thanks in advance for any help.

---

### Post by svet-am on 2013-03-07
after researching, I found that I need to interrupt the USB stick boot and apply "nomodeset" to prevent the kernel from automatically grabbing the modes (apparently incorrectly).  I don't know why I had to do this now when I never had to before -- I suppose the new mainboard is involved somehow.

That allowed me to boot the USB stick and get Ubuntu booting but now I am in _exactly_ the same spot when rebooting the machine into my newly installed Ubuntu.  I would like to apply "nomodeset" to my Grub bootargs but I cannot figure out how to get to just a Grub menu.  I found an online article that said that holding "Shift" during boot should do it but it doesn't appear to for me.

---

### Post by oldfred on 2013-03-07
If you only have one operating system, grub menu does not show. But holding shift from BIOS until menu appears should work. 
Then you can use e on grub menu and change quiet splash to nomodeset. I have had to do this will all new installs since 10.04 or there abouts. That was when they changed to make some video part of the kernel and nVidia and some AMD need nomodeset until drivers are installed.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

Last resort, if you cannot get shift to work, you can edit the grub file we are not supposed to ever edit. :)

Use liveCD/Flash and mount install, and edit /boot/grub/grub.cfg. You only have to edit first entry and any sudo update-grub will overwrite it. It is write protected also, so you may have to change that. Example if install is sda5.


 mount /dev/sda5 /mnt
gksu gedit /mnt/boot/grub/grub.cfg
#May have to do this first as it is write protected also:
sudo chmod +w /mnt/boot/grub/grub.cfg
#Or even this first:
sudo chmod 777 /mnt/boot/grub/grub.cfg

---

