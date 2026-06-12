---
title: "Install Troubles"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by Ross M on 2008-01-25
Hello,

I just burned the ISO to a DVD and ran it.  I selected the first install option and my CD drive started to spin.  However, nothing has come up on my screen.  I have also tried this in safe graphics mode with no success.  This is 64bit version and I have a nVidia 8800 GTS vid card.  I downloaded 7.10.

Thanks,
Ross

---

### Post by Partyboi2 on 2008-01-26
Did you check the[ md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") that it matched? Also try burning the iso at a low speed like x4 or lower if you haven't already done so.
If you are getting a black screen straight after making your selection from the menu screen you could try with  adding noapic and nosplash as a boot option. To do that
at the main menu press F6 and at the end of the line add
```
noapic
``` and change ```
splash
``` to ```
nospash
``` then press enter. If that works you will need to add it to grub menu.lst

---

### Post by Ross M on 2008-01-26
It turns out that it wouldn't load due to video drivers (I have an nVidia 8800).  I just burn the alternate disk and its currently installing :)

---

### Post by Ross M on 2008-01-26
Hello again,

I have just completed the install.  However when I boot up, I am getting a blank screen.  It loads the kernel and stops.  I have no way of entering command line interface (that i know of)

---

### Post by PmDematagoda on 2008-01-26
Boot Ubuntu in Recovery Mode and then follow these steps to install the Nvidia driver:-

1) Install the necessary packages to install the Nvidia driver using:-
```
sudo apt-get install build-essential
```

2) Execute:-
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.09/NVIDIA-Linux-x86-169.09-pkg1.run
```

3) Run the installer using:-
```
sh NVIDIA-Linux-x86-169.09-pkg1.run
```

4) Configure the X-Server using:-
```
dpkg-reconfigure xserver-xorg 
```
select Nvidia as the driver and any other options you may need.

5) Execute:-
```
startx
```
to check your settings.

---

### Post by bufsabre666 on 2008-01-26
> **Ross M said:**
> Hello again,

I have just completed the install.  However when I boot up, I am getting a blank screen.  It loads the kernel and stops.  I have no way of entering command line interface (that i know of)

when it loads is it just a blank screen with a  flashing underscore?

if it is, sit back and wait and then install startup manager and change the screen res settings, i had this problem with my old x1600 ((well it was new at the time of said problem))

---

### Post by Ross M on 2008-01-26
@PmDematagoda - I'll try that now and give an update. :)

@bufsabre666 - No underscore.  It's not loading due to the drivers for my nVidia.  I've been reasearching and trying multiple distros all night and that's what it seems to be.  Ubuntu seems to have the best support so I'll try it again.

Red Hat/Fedora/Cent OS ran but put the screen on both of my monitors but when I went to set up two, it couldn't find it....

---

### Post by Ross M on 2008-01-26
Update: I was able to get to the desktop interface by disabling the splash screen.  If anybody else is looking at this: it appears that the error only happens with the 64bit version...

---

### Post by Ross M on 2008-01-26
When I try to run it I get an error that I must be logged in as root to run it.  However, during install there was no root password setup. Must I run this in recovery mode?

---

### Post by Partyboi2 on 2008-01-26
When you installed ubuntu at one point it would have asked you to set up your username and password. That password is also used for root privileges. To do something with root privileges type sudo first  eg
```
sudo apt-get install
``` You can read more [here]("https://help.ubuntu.com/community/RootSudo")

---

