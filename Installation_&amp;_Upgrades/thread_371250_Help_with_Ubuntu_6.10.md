---
title: "Help with Ubuntu 6.10"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by DoughBoi on 2007-02-26
Hi, this was my original post at another forum.  i had the problem installing it, but then i tried the 32bit installed and it worked.  but now, same problem occurs as i cannot log in.

problem
> i'm trying to install Ubuntu 6.10.

but i'm getting this:

"Failed to start X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

How should i tackle this problem?


suggestion at computerforum.com
> Do you have it installed on the machine in your signature?

Are you trying to run the install CD or have you completed the install?

If you are trying to run the CD to install then please try the text based installer:

32bit text based installer

64bit text based installer

If you have completed the install and are trying to run Ubuntu then:

Boot your machine.
When it says starting grub and gives the countown, hit ESC
Choose the option that says (single user mode)
When it's finished booting you will be at a command prompt.

Type this and make a note of it.


Code:
uname -rNow type this:


Code:
sudo apt-get install xorg-driver-fglrxEnter your password when prompted - it will appear as though you are not typing, don't worry this is normal)

Once that has finished downloading and installing, type this:


Code:
sudo apt-get install linux-restricted-modules-(uname -r)Where (uname -r) is, add the result you got from typing that command in earlier - without the brackets.

Once that has downloaded and installed, type this:


Code:
sudo dpkg-reconfigure xserver-xorgYou will need to select the fglrx driver.

Once that is all done, just press CTRL ALT DEL to reboot.

Hopefully you will now be able to login!

If not then please post on [http://www.ubuntuforums.org](http://www.ubuntuforums.org) with the steps I have asked you to take above.

please bare with me, this my first time using linux.  Thought it would be easy...sheesh.  Anyways, only the last code worked: sudo dpkg-configure xserver-xorg and it went into the setup screen, but then after the setting up, it still didn't work.

please help! thanks.

---

### Post by johnc4510 on 2007-02-26
If you click yes after you get this:"Failed to start X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?" It will give us an idea of where your problem is. Do that and then post the results you get as the problem back here. Someone will then have a better idea of the problem.

---

### Post by DoughBoi on 2007-02-26
that error message was the one i got before i actually got it installed and i don't really know how to get to it again.  Also, the information it gave me was huge.

So when linux boots up, and it gets to the end of the bar, the images just screw up.  Sorry for the limited information.  Any suggestions?

---

### Post by johnc4510 on 2007-02-26
reboot your computer, when the first text comes up, hit escape quickly. It will take you to a terminal. Type in this: startx   It will then give you that screen with the error msg. Choose yes and post the results back here please.

---

### Post by mikewhatever on 2007-02-26
Can you please tell us what video card you have? If you close the error messages you'll see the black screen with an option to log in. Log in and type the password, then type

> sudo nano /etc/X11/xorg.conf

a text file will open. Locate the following section
> Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

and change the driver to "vesa", then save and exit. Look for save and exit options at the bottom of the screen.
Then type startx.
Then tell us what happened.:)

---

### Post by benson444 on 2007-02-26
Yeah, what graphics card do you have? The answer from the other forum seems to assume you have an ATI.

When asked if you want to view the X server output select no. You may end up with a _ flashing in the corner. If so press Ctrl+Alt+F1 which should allow you to log in. Enter the command:

sudo dpkg-reconfigure xserver-xorg

and select the default settings except for graphics drivers. For this select vesa. When you're back at the command prompt enter startx. Hopefully this will get X server up, then you can install the correct drivers for your system.

---

### Post by DoughBoi on 2007-02-27
the only command prompt i can access right now is the "recovery mode" boot when i press esc during start up.  when i type in startx, i get this error message at the bottom:

Fatal server error
No screens found
XIO: fatal IO error 104 (connection reset by peer) on x server ":O.O"
after 0 requests (0 known processed) with 0 events remaining

---

### Post by DoughBoi on 2007-02-27
ok, i tried to type in "sudo dpkg-reconfigure xserver-xorg" in recovery mode and found "vesa" you guys were talking about.  change "ati" to "vesa" and it worked.  i did startx and finally accessed the graphical interface.

thanks for everyone's help so far.

how can i set up my video card driver?  the videocard i'm using is Sapphire ATI x800gt/se

---

### Post by masteryurez on 2007-02-27
Do you have an ATI or nVidia grafic card in your computer?
If you have nVidia I don't know but if you have an ATI-card you can do like this. Works for me very well..

> 
This might be to do with the CD being a dodgy copy, as it&#347; doing the same on both PCs. On the first menu scroll down to "Check CD". If this is OK then try the following:

I think it could be having difficulty loading the graphics drivers, try reverting to the "**vesa**" bog-standard drivers by doing the following:

at the startup screen press F6, which will bring up the boot line.  Delete the "**quite - splash**"  part and enter in "**break=bottom**" instead. Save this and carry on booting. 

Instead of the fancy looking Ubuntu splash screen you'll get a few messages (if they are errors don't worry too much right now) and then, after a wile, you will get a command prompt.

Type in "**chroot /root /nano /etc/X11/xorg.conf**". This will bring up the "**xorg.conf**" file which is the configuration file for the graphics. Scroll down to the heading "**Device**" under which will be a sub-heading called "**Driver**". 

Change whatever is to the right of the driver (e.g. ATI if it's an ATI card or otherwise) to "**vesa**". (**vesa** is the name of the ATI-driver). Now press ctrl+O and ctrl+X to save and exit the text file. 

This will bring you back to the Command line, type exit in to this and, hopefully, Ubuntu should boot propertly.
I hope this guide will help you to solve your problem.. 

Have a nice day :)

---

