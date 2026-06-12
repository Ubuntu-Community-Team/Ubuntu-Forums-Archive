---
title: "LCD monitor Workaround"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by Aidan1234 on 2007-03-18
Before i start, i am pretty new at this stuff (sorry) so i will need pretty intricate explanations. However, i am not new at all with computers and i know my stuff when it comes to hardware/ windows. its just linux.

I need to know the workaround to getting ubuntu 6.10  to work on my LCD monitor. It is my only monitor, so there is no option of working with a CRT one. Also, i dont know if this makes a difference, but both ports on my monitor are DVI-D ones. I have a converter to analog, but the analog spot on my monitor is being used by my Xbox 360.

I know i read somewhere about some thing you can type somewhere that makes ubuntu work with a LCD monitor. i tried getting the nVidia linux drivers to install during ubuntu's installation in Text mode, but i never saw a point in the installation where i would do that. I have the drivers on a usb flash drive. 

Also, it is not possible to just use 6.06 because i have the Asus p5b deluxe motherboard which is not compatible with 6.06. (something about jmicron)

Thats all.

Thanks,
Aidan

EDIT- I guess i should also mention that my graphics card is a nVidia geForce 7800GT

---

### Post by Scunizi on 2007-03-19
First, if your monitor has two inputs, I would venture to bet that you can only use one at a time.  Try disconnecting the xbox and using the computer to the appropriate port on the monitor and see if you get anything,  it might be just a text prompt like a more elaborate Dos prompt or you might get the GUI. 

 If you don't get anything then while booting you might have to choose "rescue" at the boot prompt.  That will dump you into the terminal mode.  Go ahead and log in like normal (uname/password) then at the prompt type "sudo dpkg-reconfigure -phigh xserver-xorg".  This will ask you a couple of questions which should be easy for you to answer.  When done reboot and with fingers crossed you should be functional on your monitor using the standard generic drivers.

To install the nvidia drivers ..... well.... there's lots of threads on how to install the latest and greatest bleeding edge nvidia stuff.  Personally I use the drivers from Synaptic (the Ubuntu installation utility).  Search for Nvidia-glx.  They are not the most up to date typically but will run in accelerated mode and with glx.  I'm running Dapper 6.06 and I know the drivers there are well behind the power curve but they function fine.  UT2004 and America's Army work.

After installing the drivers you'll need to edit your xorg.conf file to enable them.  Go to your terminal and type:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup <enter> this backups you file
gksudo gedit /etc/X11/xorg.conf <enter> this opens the file in an editor

Now look for a line that begins with "server" (actually "driver")and in quotes on that line you'll typically see either vesa or nv.  Change it to nvidia.  Save the file.  Now give the computer the 3 finger salute CTRL - ALT - Backspace to restart the graphical server.  It should ask you to log in again and put you in the GUI.  Did you see the Nvidia splash screen on the restart?  If you did you're done.  If you didn't the drivers may have still loaded correctly.  I think from the terminal you can type "nvidia-glx info" or "glx info" (forgot the exact command) and it should return if glx is turned on or not.

Edit: Added note after "server"

---

