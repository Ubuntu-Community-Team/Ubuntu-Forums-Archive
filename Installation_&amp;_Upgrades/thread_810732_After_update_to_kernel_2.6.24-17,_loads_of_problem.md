---
title: "After update to kernel 2.6.24-17, loads of problems"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by Haiatola on 2008-05-28
Hello.

I updated to the title's kernel version a few hours ago and apparently ubuntu forgot the nvidia driver settings. (Doesn't even show on restricted drivers).

So I set about trying to fix the problems, which landed me here

[http://www.linuxforums.org/forum/ubuntu-help/120492-nvidia-driver-problem-very-weird-ubuntu-8-04-a-2.html](http://www.linuxforums.org/forum/ubuntu-help/120492-nvidia-driver-problem-very-weird-ubuntu-8-04-a-2.html)

and 

[http://www.uluga.ubuntuforums.org/showthread.php?t=717780](http://www.uluga.ubuntuforums.org/showthread.php?t=717780) .

None of it worked, however, and while trying to put it back into the status quo, gdm won't start, all it shows is a black screen... That's what I get for being a newbie :>

Any and all help would be appreciated.

Edit: When the updates were being downloaded, I noticed it downloaded something nvidia related, could be why it all went to hell.

Edit2: I guess I should include more info. I'm running a 8600gs, which was working perfectly out of the box since ubuntu 7.10. After this last update, I rebooted into 800x600, wrong keyboard scheme and didn't detect the restricted nvidia driver. I reconfigured xorg, and it gave me full resolution, but still no 3d. That's when I did what the two links above suggested.

---

### Post by dstew on 2008-05-28
This is what I would do. First, boot in Recovery Mode. Choose **xfix** then resume booting. That should get you a working display. Then, press alt-F2 and enter```
gksudo displayconfig-gtk
```to select your monitor type. After that, you can change your resolution with the System --> Preferences --> Screen Resolution window. Then, check for a restricted driver in System --> Administration --> Hardware Drivers. If one is there, enable it. Restart. If the screen is not good, try displayconfig-gtk again.

---

### Post by Haiatola on 2008-05-28
Thanks for the tips :)

Unfortunately, none of that worked, and gksudo displayconfig-gtk returns the following error:

Gtk-WARNING **: cannot open display:

---

### Post by iaculallad on 2008-05-28
What about issuing the command **sudo apt-get install util-linux** on the recovery mode then recheck the Restricted driver.

---

### Post by Haiatola on 2008-05-28
It returns the message 'util-linux is already the newest version' :/

---

### Post by iaculallad on 2008-05-28
Ty reinstall xserver on Restore Mode

```
sudo apt-get install xserver-xorg
```

or

```
sudo apt-get install –reinstall xserver-xorg
```


The restart:

```
sudo shutdown -r now
```

---

### Post by Haiatola on 2008-05-28
Thanks for the help, but unfortunately, still no go... :(

---

### Post by dstew on 2008-05-29
What happens after you boot in Recovery Mode and choose xfix?

---

### Post by Haiatola on 2008-05-29
Nothing. It will prompt me what to do next, I choose resume and it'll boot to a blank screen.

EDIT:

Progress! I reinstalled gdm after I applied the nvidia driver, wild hunch. I now have a gui, but no acceleration.

---

### Post by dstew on 2008-05-29
What happens if you boot to Recovery Mode, choose root command line, and enter **startx**? Do you get any error messages?

---

### Post by Haiatola on 2008-05-29
Used to get the "No screens found message" but apparently I've already solved it. 

Now I can boot normally up to gdm at 640x480, and the damn thing won't recognize my graphics card :\

EDIT: Too good to be true, after a reboot I'm still getting no screens found.

What the hell... It's working again. Oh well.

EDIT2: The plot thickens... Modprobe nvidia returns the following error:

Could not open /lib/modules/2.6.24-17-generic/kernel/drivers/video/nvidia.ko


EDIT3: After a bit of snooping around, I have concluded something must've broken in the update, since a kernel module for this kernel version was not installed. I booted to the earlier kernel version and all is well (something that I should've tried earlier too...)

Any and all help regarding this would be continually appreciated :)

I checked synaptic and all relevant packages for modules and drivers are installed... but somehow not the nvidia one.

---

### Post by Haiatola on 2008-05-29
Apparently I have the same problem as this fellow [http://ubuntuforums.org/showthread.php?t=779716&page=3](http://ubuntuforums.org/showthread.php?t=779716&page=3) \\:D/

I guess I will continue using the earlier kernel version until this is fixed :) Thanks to everyone for their help

---

### Post by rjdohnert on 2008-05-30
At Grub, enter B to edit the boot options, delete the line VGA 733, boot what will be a console mode, login at the console, sudo nano /etc/X11/xorg.conf
change the driver loaded to the generic 'nv' driver. Ctrl X, save the file, startx, Synaptic, remove nvidia-glx, apply, reinstall nvidia-glx, if you use PC/OS use Envy, when nvidia-glx is reinstalled, reboot.  This should help you, this is what I did on PC/OS 8.04 Beta. 

> **Haiatola said:**
> Apparently I have the same problem as this fellow [http://ubuntuforums.org/showthread.php?t=779716&page=3](http://ubuntuforums.org/showthread.php?t=779716&page=3) \\:D/

I guess I will continue using the earlier kernel version until this is fixed :) Thanks to everyone for their help

---

