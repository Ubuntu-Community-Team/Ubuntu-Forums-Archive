---
title: "Mounting of drives &amp;  1680x1050 display driver"
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by SegueImaging on 2007-03-16
Unable to mount drives and/or partitions therein.  Error msg: ...cannot execute pmount.

Where did I go wrong?

I would like to open existing Excel, PowerPoint and Doc files directly under OO.  Only way now is to copy to a CD.  That 2nd disk drive works fine.

BTW, using LiveCD.   

Also:

Cannot display at 1680 x 1050 (though machine is doing so fine under XP).   Do I need a Ubuntu driver?  If so, obtained how/where?

Tks!
WayneD

---

### Post by bulldog on 2007-03-16
To mount a drive,can you tell me how you did this?

Install the driver for your graphics.
The command depends on which graphics you've got.

After that ```
sudo dpkg-reconfigure xserver-xorg
``` and choose the right resolution.
This should be enough.

---

### Post by SegueImaging on 2007-03-17
Don't laugh too loudly ~~ I did, have done nothing.  (BTW, I am using Live CD.)  When I GoTo 'Computer', the drives and respective partitions are shown.  Clicking on Properties on any one of them brings up a list, one referring to Mounting.  I click on this - error msg says I cannot mount due to no access to pmount. 

As for the 1650x1080 (Nvidia card and driver in XP-MCE handles this) do I need to dwnld a Linux driver from Nvidia?  Likewise for any device, peripheral, like an HP printer?

---

### Post by bulldog on 2007-03-17
Okay,to mount a partition you'll have to make a mountpoint and you need administrator rights.
I'll give you the commands with a virtual partition,you have to replace the name with the one you actual want to mount.
This method works from a live cd session,as well when you have ubuntu installed.
But after installation ubuntu should recognize your partitions and list them in a file called ' fstab' which you can modify if you want.
Your graphics however,you can only install them when you have installed ubuntu to your hdd,not in a live session.

Create a mountpoint,
```
sudo mkdir /mnt/windows
```
To mount the partition,
```
sudo mount -t ntfs /dev/hda /mnt/windows
```
Now you can find the mounted partition in your /mnt/windows folder in the file system.

To install your graphics driver,you need to know which kernel you use,
```
uname -a
```
gives your kernel like 2.6.20-11-generic.

Install the restricted modules,
```
sudo aptitude install linux-restricted-modules-2.6.20-11-generic
```
After that install your graphics driver,
```
sudo aptitude install nvidia-glx
```

Now your graphics driver will be installed.
To configure your graphics,
```
sudo nvidia-settings
```

You can use```
sudo dpkg-reconfigure xserver-xorg
``` and choose the right resolution for your monitor.
Take a look at your xorg.conf,to see if the driver is changed from "nv" to "nvidia" if not do it manually.
```
gksudo gedit /etc/X11/xorg.conf
```
Change the driver if necessary and save the file and exit.

At last reboot and see if things are working correct.

Your printer should be recognized by ubuntu,but if not,go to System-->Preferences-->Printers, and choose your printer and its driver from a list.
Set is as the default and you should be good to go.

---

