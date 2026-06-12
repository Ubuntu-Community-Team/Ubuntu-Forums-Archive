---
title: "Stuck on OEM logo"
date: 2017-12-18
forum: Installation &amp; Upgrades
---

### Post by husin on 2017-12-18
So i used to dual boot my laptop with ubuntu gnome and windows 10 and there was no problem until this problem came up.
i dont really know why but i use UEFI install on both OS and from what i have searched its just telling me to disable UFEI but if i do that i cant boot into windows nor grub.
i use an acer E5-457G laptop and maybe this might be use full but when i tried to install Debian and ubuntu (not both but dual boot it with windows) it wont let me boot into grub cause i have to set the safe boot.

i cant show anylog cause i already formated the ext4 partition cause i cant even boot into windows and i reinstalled my windows to

please help me cause i kinda need to use linux to study programming (not because windows cant, but because it gives me more focus)

---

### Post by yancek on 2017-12-18
You should be able to access the BIOS to change settings.  If you could not do that how did you re-install windows?  You would have needed to change the boot priority to the DVD or usb you were installing from.  Generally, when you boot and see the logo there is a bried (3-5 second) period when you see a message at the bottom of the screen telling which key to press to access setup or BIOS configuration.  Do you have a manual for the Acer.  You might take a look at that for instructions.  If you don't have it, you should be able to find one online by doing a search with the Acer brand name of the computer.

If I understand correctly, you have overwritten your Ubuntu by re-installing windows 10, is that right?.

As far as using UEFI, that is a new standard and is used by default on windows 8/10 and to avoid problems with Ubuntu, you would install Ubuntu UEFI also.

Are you able to boot the Ubuntu install device or any other Linux system?  If so, do that and open a terminal and run this command and post the output here:

```
sudo parted -l
```

That''s a lower case letter L in the command.

---

### Post by husin on 2017-12-18
> **yancek said:**
> You should be able to access the BIOS to change settings.  If you could not do that how did you re-install windows?  You would have needed to change the boot priority to the DVD or usb you were installing from.  Generally, when you boot and see the logo there is a bried (3-5 second) period when you see a message at the bottom of the screen telling which key to press to access setup or BIOS configuration.  Do you have a manual for the Acer.  You might take a look at that for instructions.  If you don't have it, you should be able to find one online by doing a search with the Acer brand name of the computer.

If I understand correctly, you have overwritten your Ubuntu by re-installing windows 10, is that right?.

As far as using UEFI, that is a new standard and is used by default on windows 8/10 and to avoid problems with Ubuntu, you would install Ubuntu UEFI also.

Are you able to boot the Ubuntu install device or any other Linux system?  If so, do that and open a terminal and run this command and post the output here:

```
sudo parted -l
```

That''s a lower case letter L in the command.

Yes i overwrite my windows to reinstall windows but i formated the partition where ubuntu is installed.
I do know how to reinstall windows and going into bios but there is no instruction on the brief 3-5 second.
i can go into other linux device that is using a live usb for trying to fix the boot using boot repair.

>  Are you able to boot the Ubuntu install device or any other Linux  system?  If so, do that and open a terminal and run this command and  post the output here:

```
sudo parted -l
```

That''s a lower case letter L in the command.

i cant really do that right now cause i dont have any installed linux distro cause im to scared, what if the problem happends again and i wont be able to fix it and loss all my date again.

---

