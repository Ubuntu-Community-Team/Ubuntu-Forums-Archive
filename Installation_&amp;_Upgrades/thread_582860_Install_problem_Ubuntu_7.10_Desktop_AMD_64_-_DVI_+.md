---
title: "Install problem Ubuntu 7.10 Desktop AMD 64 - DVI + LCD"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by bruban on 2007-10-20
I'm unable to install 7.10 on a system with a Samsung 931C LCD monitor and an NVIDIA GeForce 8800GTS card. 

I suspect that the problem relates to the graphics card being connected to the monitor with a DVI connection.

Symptoms:

The same PC worked OK with Ubuntu 7.04 connected to a CRT monitor. The only change to the system has been to add the LCD connected via DVI. 

This system works OK with 7.04 and the LCD monitor connected with a VGA DSUB connection.

This PC, video card and monitor connected via DVI works OK with WinXP.


I've tried installing 7.10 from the AMD64 live CD. The PC boots into the Live CD and presents the initial menu. 

From this menu I selected the install option. The screen goes blank and the hard disk / CD process for several minutes before activity ceases. No image is displayed on the monitor.

I tried the same unsuccessfully with the safe graphics boot option.

On both occasions I was not able to to access the virtual terminals via CTL-ALT-Fn.

The PC appeared to hang, even after being left for 15 minutes.

I've noticed a number of posts on the forum re: LCD/DVI problems with a number of video cards.


Does anyone have any ideas?


Bruce

---

### Post by slante9 on 2007-10-21
I had virtually the same problem with 7.04.   I was able to install from the alternate cd, but now installed Ubuntu boots, doesn't display anything and just dies with a black screen.

HELP!     :(

---

### Post by Therion on 2007-10-21
**bruban/Bruce**:

I have an LCD/DVI connection and an 8800GTS as well.  

What solved the problem for me was installing from the LiveCD and then booting from the hard drive.  
Go into the GRUB menu and select "Recovery Mode".
This should bring you to a command prompt.
Now, edit menu.lst:
```
nano /boot/grub/menu.lst
```
Find the first kernel entry down near the bottom of the file (It's a loooong line of code) and remove "splash".
The default line looks like this:
```
kernel   /boot/vmlinuz-2.6.22-14-generic root= (blah, blah, blah) ro **splash** quiet
```
Change it to look like this ("splash" removed):
```
kernel  /boot/vmlinuz-2.6.22-14-generic root= (blah, blah, blah) ro quiet
```
^X to save, Y to accept the changes, etc.

Immediately install Envy and use it to install the nVidia driver.

---

### Post by bruban on 2007-10-21
Thanks for the replies Therion and Slante9,


Therion, I was unable to get the LiveCD to boot using DVI. Once I had 7.10 installed, I tried your suggestion of removing splash from the boot option, however my PC would still not boot (or rather I could not get an image displayed on my LCD monitor when using the DVI connection).


I now have my system running under Ubuntu 7.10, by not using a DVI connection and switching back to the DSUB/VGA connection.

I've included what I did below to help others in a similar boat and to help debug the DVI / LCD problem.

btw, I was not able to use the Ubuntu provided NVIDIA GeForce 8 series drivers for the GeForce 8800 GTS.



In the end, as I was not able to boot from the 7.10 LiveCD using the DVI connection to the LCD.



_My steps to getting 7.10 installed_

I switched to using the DSUB / VGA connection.

Booted into Ubuntu 7.04 and upgraded using the System>Administration>Update Manager tool.

(I have since found that the 7.10 LiveCD would also have worked)

Ubuntu then upgraded to 7.10 without a hitch.



NB: Take care with the NVIDIA drivers. After I had 7.10 installed I activated the Restricted NVIDIA GeForce 8 series drivers. After reboot, NO image was displayed on screen.


_Steps I used to recover display_

- press CTL-ALT-F1 to get a virtual terminal

- edit /etc/X11/xorg.conf, change the video card's driver from nvidia to vesa

- reboot

- using  System>Administration>Restricted Drivers Manager activated the NVIDIA drivers and then immediately deactivated the NVIDIA drivers with no reboot in between.

- after reboot display was again usable.



I hope this helps someone.

Bruce

---

### Post by slante9 on 2007-10-24
Looks like I have this working with 7.10 now, with my Samsung, DVI and AMD64 system.

Installed using the alternative CD.

In recovery mode, edited xorg.conf, per release note that seemed like it might apply, adding following to driver section for nVidia card:

Option "LVDSBiosNativeMode" "false"

Adventure may not be over yet, though.

I also change splash to startx in the grub entry, but that may not have been necessary.

---

