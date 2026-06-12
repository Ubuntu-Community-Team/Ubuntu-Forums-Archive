---
title: "Nvidia Kernel Conflict"
date: 2012-10-08
forum: Installation &amp; Upgrades
---

### Post by mansonmedia on 2012-10-08
[FONT=Courier New]I'm a Newbie in the Ubuntu Linux and I'm having a problem...[/FONT]

[FONT=Courier New]I updated my nvidia driver to 304.51 and and then everytime I boot up my pc I'm always brought to the place where you will go if you pressed Ctrl+Alt+F1... and if I type startx I get this error(or atleast a part of it...):[/FONT]

[FONT=Courier New]______________________________________________________[/FONT]

[FONT=Courier New]Using config file: "/var/log/Xorg.0.log," Time:[/FONT]
[FONT=Courier New]config file: "etc/X11/Xorg.conf"[/FONT]

[FONT=Courier New]API mismatch: The NVIDIA kernel module has version 304.51, but this NVIDIA driver component has version 295.49. Please make sure that the kernel module and all NVIDIA driver components have the same version.[/FONT]
[FONT=Courier New]Fatal server error:[/FONT]
[FONT=Courier New]no screens found[/FONT]


[FONT=Courier New]Please consult the The Xorg Foundation support at [http://wiki.x.org](http://wiki.x.org) for help[/FONT]

[FONT=Courier New]Please also check the log file at /usr/log/Xorg.0.log for additional information[/FONT]

[FONT=Courier New]ddxSlqGiveUp: closing log[/FONT]
[FONT=Courier New]Server terminated with error(1). Closing log file.[/FONT]
[FONT=Courier New]xinit: giving up[/FONT]
[FONT=Courier New]xinit unable to connect to server: no such file or directory[/FONT]
[FONT=Courier New]xinit: server error[/FONT]

[FONT=Courier New]_________________________________________________[/FONT]

[FONT=Courier New]Please help... so this can be fixed or if cannot be fixed I can understand what is actually happening... ;)[/FONT]

---

### Post by bogan on 2012-10-09
Hi!, **mansonmedia,**

When an update nvidia driver is installed, all previous driver elements have first to be removed [or at least deactivated ].

If the downloaded nvidia-installer is used, this is done as part of the installation, but not necessarily so if the Ubuntu nvidia-current driver is installed by dpkg or jockey, from 'Additional Drivers'.

To cure it you need to shut down the graphics xserver; remove --purge all nvidia* components; reinstall the later driver and reboot.
 How you do the last depends on how you got the 304.51 driver; either use "apt-get install nvidia-current", if you got it from the x-swat ppa, or run the downloaded nvidia '.run', file if that is what you did before.

If you are in doubt, run ```
sudo apt-cache policy nvidia-current
```to confirm if nvidia-current is installed.

So, assuming you are using ubuntu 12.04 or 12.04.1, from the tty [ '[FONT=Courier New]Ctrl+Alt+F1'] login and run: [/FONT]```
sudo service lightdm stop # to stop the xserver
sudo apt-get remove --purge nvidia* # to remove all driver elements
# then either: 
sudo apt-get update
sudo apt-get install nvidia-current
sudo reboot
# or:
cd /home/user/Downloads # put your username in place of 'user',
 # and the folder where the nvidia '.run' file is, if not 'Downloads'
ls # to check you are in the right place and the spelling of the file name
sudo sh NVIDIA- # Press 'Tab' to complete the name and press 'Return'
``` You may get a script failed message and other options, accept them, navigating with the 'Tab' key & pressing 'Return' to accept.

When complete run' sudo reboot'.

You should then be AOK. Please Post how you get on, or with any queries.

Chao!,** bogan**.

---

### Post by BicyclerBoy on 2012-10-09
"or run the downloaded nvidia '.run', file if that is what you did before."

If you used that method then you need to have the kernel headers package that matches your current kernel (& other dependencies).

There is a "generic" meta package for kernel headers that matches the generic "meta" package for kernel image..
So as kernel updates roll over, your headers changes to match..

But with every kernel change you must re-build the nVidia driver.

---

### Post by Bobhuber on 2012-10-09
> **BicyclerBoy said:**
> "or run the downloaded nvidia '.run', file if that is what you did before."

If you used that method then you need to have the kernel headers package that matches your current kernel (& other dependencies).

There is a "generic" meta package for kernel headers that matches the generic "meta" package for kernel image..
So as kernel updates roll over, your headers changes to match..

But with every kernel change you must re-build the nVidia driver.
The newer drivers (304.xx) now support DKMS and will update without rebuilding the driver every time the kernel changes.

---

### Post by mansonmedia on 2012-10-10
> **bogan said:**
> Hi!, **mansonmedia,**

When an update nvidia driver is installed, all previous driver elements have first to be removed [or at least deactivated ].

If the downloaded nvidia-installer is used, this is done as part of the installation, but not necessarily so if the Ubuntu nvidia-current driver is installed by dpkg or jockey, from 'Additional Drivers'.

To cure it you need to shut down the graphics xserver; remove --purge all nvidia* components; reinstall the later driver and reboot.
 How you do the last depends on how you got the 304.51 driver; either use "apt-get install nvidia-current", if you got it from the x-swat ppa, or run the downloaded nvidia '.run', file if that is what you did before.

If you are in doubt, run ```
sudo apt-cache policy nvidia-current
```to confirm if nvidia-current is installed.

So, assuming you are using ubuntu 12.04 or 12.04.1, from the tty [ '[FONT=Courier New]Ctrl+Alt+F1'] login and run: [/FONT]```
sudo service lightdm stop # to stop the xserver
sudo apt-get remove --purge nvidia* # to remove all driver elements
# then either: 
sudo apt-get update
sudo apt-get install nvidia-current
sudo reboot
# or:
cd /home/user/Downloads # put your username in place of 'user',
 # and the folder where the nvidia '.run' file is, if not 'Downloads'
ls # to check you are in the right place and the spelling of the file name
sudo sh NVIDIA- # Press 'Tab' to complete the name and press 'Return'
``` You may get a script failed message and other options, accept them, navigating with the 'Tab' key & pressing 'Return' to accept.

When complete run' sudo reboot'.

You should then be AOK. Please Post how you get on, or with any queries.

Chao!,** bogan**.


well thanks for all the reply... well I've just decided to reinstall Ubuntu along with the driver... but the new problem is that I'm stuck at a lower resolution than what I'm actually enjoying at my (dual boot) windows...

---

### Post by BicyclerBoy on 2012-10-10
If the nVidia installer (>304) now uses DKMS that is good news.
But novice users should not be advised to go to nVidia drivers webpage..
 
The ppa packaged nVidia drivers from X-swat xorg-edgers etc have always used DKMS.

@OP
What is in the log file /var/log/Xorg.0.log ?
run:
sudo nvidia-xconfig
check the log file again..

---

