---
title: "Installing new graphics card driver."
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by Syroco on 2008-05-16
I downloaded the new beta driver that supports my card, and I found a website to help me install it. It gives me these steps, but I have no idea what he's talking about. I tried his commands in terminal and they didn't do anything, invalid commands, or not found, etc.

Can someone give me a bit more detailed walkthrough? Thanks

1) Make sure that you don't have any of the following packages installed on the system: nvidia-glx or nvidia-glx-new
2) If any of these files exist, delete them: /etc/init.d/nvidia-glx, /etc/init.d/nvidia-kernel, and /lib/linux-restricted-modules/.nvidia_new_installed
2) Install the packages for some of the more common development tools if they aren't already: gcc, linux-headers, pkg-config, and xserver-xorg-dev
3) Modify the /etc/default/linux-restricted-modules file and add the following line to the bottom of it: DISABLED_MODULES="nv nvidia_new"
4) Download the latest driver from NVIDIA. I had to click on the "Beta and Archived Drivers" link to find version 173.08, which said that it added support for the GeForce 9600 GT GPU. Later version will likely work too.
5) From a root console window (CTRL-ALT-F1), run "/etc/init.d/kdm stop" if you are using KDE, or "/etc/init.d/gdm stop" if you are running GNOME.
6) Execute the binary driver that you downloaded from step 4 above. It will walk you through a few screens necessary for setting up the driver on the system. When it asks if you want it to auto configure your xserver, choose "yes."
7) If everything was successful, you might want to edit your /etc/X11/xorg.conf file and check the "Device" section. If you don't see any mention of "AddARGBVisuals" or "AddARGBGLXVisuals", add the following lines to that section:
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
You can start up your xserver again. Run "/etc/init.d/kdm start" if you are using KDE or "/etc/init.d/gdm start" if you are running GNOME.

---

### Post by chewearn on 2008-05-17
> **Syroco said:**
> I downloaded the new beta driver that supports my card, and I found a website to help me install it. It gives me these steps, but I have no idea what he's talking about. I tried his commands in terminal and they didn't do anything, invalid commands, or not found, etc.

Can someone give me a bit more detailed walkthrough? Thanks

[B]First, a disclaimer: I haven't done these steps myself.  I'm simply interpreting your post verbatim.  So, I'm not responsible for breakage due to error in your post or the instructions in the original website. :mrgreen:
[/B] 
Second, open a terminal window; it located under:
Applications > Accessories > Terminal

Run the commands I give below in the terminal.  When prompted for password, enter your user's password.


[I][B]1) Make sure that you don't have any of the following packages installed on the system: nvidia-glx or nvidia-glx-new
[/B][/I] 
```
sudo apt-get purge nvidia-glx nvidia-glx-new
```[I][B].


2) If any of these files exist, delete them: /etc/init.d/nvidia-glx, /etc/init.d/nvidia-kernel, and /lib/linux-restricted-modules/.nvidia_new_installed
[/B][/I] 
```
sudo rm /etc/init.d/nvidia-glx
sudo rm /etc/init.d/nvidia-kernel
sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
```.


[B]2) Install the packages for some of the more common development tools if they aren't already: gcc, linux-headers, pkg-config, and xserver-xorg-dev
[/B]
```
sudo apt-get install gcc linux-headers pkg-config xserver-xorg-dev
```[I][B].


3) Modify the /etc/default/linux-restricted-modules file and add the following line to the bottom of it: DISABLED_MODULES="nv nvidia_new"
[/B][/I]
```
echo DISABLED_MODULES="nv nvidia_new" | sudo tee -a /etc/default/linux-restricted-modules
```.


[I][B]4) Download the latest driver from NVIDIA. I had to click on the "Beta and Archived Drivers" link to find version 173.08, which said that it added support for the GeForce 9600 GT GPU. Later version will likely work too.
[/B][/I]
Seems you know what to do here.  Move the binary file you download from nvidia to your home directory (if it's not there already).  If it's in compressed archive format, uncompress it (right click > Extract Here).


[B][I]5) From a root console window (CTRL-ALT-F1), run "/etc/init.d/kdm stop" if you are using KDE, or "/etc/init.d/gdm stop" if you are running GNOME.
[/I][/B]
From now on, things will be scary.  You will go off the GUI into the console, and there is a chance you might not get GUI back, so be very prepared.

Press CTRL+ALT+F1.  Type in your username and password when prompted.

If you have KDE:
```
sudo /etc/init.d/kdm stop
```If you have Gnome:
```
sudo /etc/init.d/gdm stop
```.


[I][B]6) Execute the binary driver that you downloaded from step 4 above. It will walk you through a few screens necessary for setting up the driver on the system. When it asks if you want it to auto configure your xserver, choose "yes."
[/B][/I] 
```
sudo ./<filename>
```Replace <filename> with the actual filename.


[I][B]7) If everything was successful, you might want to edit your /etc/X11/xorg.conf file and check the "Device" section. If you don't see any mention of "AddARGBVisuals" or "AddARGBGLXVisuals", add the following lines to that section:
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
You can start up your xserver again. Run "/etc/init.d/kdm start" if you are using KDE or "/etc/init.d/gdm start" if you are running GNOME.
[/B][/I] 
To edit the file:
```
sudo nano /etc/X11/xorg.conf
```Then, if you have KDE:
```
sudo /etc/init.d/kdm start
```If you have KDE:
```
sudo /etc/init.d/gdm start
```That's it, good luck!  :mrgreen:

.

---

