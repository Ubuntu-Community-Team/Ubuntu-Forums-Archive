---
title: "Format from GRUB"
date: 2016-06-23
forum: Installation &amp; Upgrades
---

### Post by angel mike on 2016-06-23
Can I format the hardrive from  Grub? 

Cannot get into the Terminal and have no Screen.  Thanks

---

### Post by howefield on 2016-06-23
If you have grub, you probably have Recovery mode ?

In any event, if your intent is to format the drive or partitions, easier to boot a Live media and use gparted.

---

### Post by angel mike on 2016-06-23
Thanks - have a live USB of 14.04 which I have used but and have got into the Terminal but that seems to have been blocked. Can you explain how I can use gparted from the Grub2. Yes can get the Recovery Mode from the list in Grub.

---

### Post by angel mike on 2016-06-23
Just to add - there is no screen because the graphics card is not regonised being old but Nvidia 304.125 driver will work it. I managed this before setting nomodeset in grub but this route seems to habeen blocked as well.

---

### Post by yancek on 2016-06-23
Grub is a bootloader.  You can not format anything from Grub nor can you use GParted from Grub.  You need to boot into your recovery mode or use the nomodeset option on the Ubuntu usb.  Maybe a little more info on what happened that led to this problem would poin someone in a direction to suggest some help.  Can you boot a CD/DVD, anything?

---

### Post by grahammechanical on 2016-06-23
Please tell us how far you get into the Ubuntu loading process. An open source video driver is used by default and it will recognise older video adapters even when the newest proprietary video drivers have dropped support for that video adapter.

You can use recovery mode and select Resume. That may load to a working desktop environment using an open source video driver as a fall back. Then you can use System Settings>Software & Updates> Additional Drivers to active the nvidia 304 driver. Or,

You can use recovery mode and first select Network to establish an internet connection and also to put the file system (Ubuntu partition) into read/write mode. Then you can select Root shell prompt and run

```
ubuntu-drivers devices
```

Allow time for the command to work and you will see something like this

> graham@sdb7-Dev:~$ ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00000A20sv00001043sd0000830Fbc03sc00i00
model    : GT216 [GeForce GT 220]
vendor   : NVIDIA Corporation
driver   : nvidia-340 - distro non-free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-304-updates - distro non-free
driver   : nvidia-304 - distro non-free

== cpu-microcode.py ==
driver   : intel-microcode - distro non-free

That will give you information about your video adapter and the drivers available for it. To install the latest Nvidia driver for the video adapter from that list, run

```
ubuntu-drivers autoinstall
```

When you are finished type exit to get back to the recovery menu and then select Resume. Then, shut down and restart Ubuntu to use the installed proprietary video driver.

Regards

---

### Post by angel mike on 2016-06-23
Thanks Yancek and Graham for the helpful suggestions - will give it another try.
The problem started when I just had a grey screen on bootup. I had Lubutu loaded and did see the logo on closing down but that has gone now. 
I then tried to install ubuntu 14.04 with a usb ( have used it ok on another computer) but I know from when I did this last time I had to use nomodeset in grub and I did get a degraded screen so could use the software depositary and get the list of available Nvidia drivers. 
Now I could get into the Terminal and it was headed Ubuntu 14.04 so I know the usb has loaded ok I think - but for some reason cannot get back in.
I am intending to change the graphics card and power supply to avoid all this. the present one on Gateway Desktop GM5066b is very low ended.
Regards

---

### Post by angel mike on 2016-06-23
[B]I took your suggestion yaneck and tried loading with a CD and it worked ! Now all I have to do is install a graphics driver.
Thanks for your help.Problem solved. Thanks 
[/B]

---

