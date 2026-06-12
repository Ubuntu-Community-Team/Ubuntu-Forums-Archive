---
title: "Nvidia graphics card resloution"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by eekfonky on 2008-10-26
Can anyone help me up the resolution? My monitor is capable of 1280x1024 but currently won't go higher than 640x480 which is no use. Please help

---

### Post by mrjohnston on 2008-10-26
First of all it sounds like your system is defaulting to low resolution from an X related error.  I doubt your nvidia drivers are installed right.  I would uninstall all Nvidia stuff, reboot and then reinstall via hardware drivers.  

Once you reboot you should get at least 800x600, but if you aren't getting your full resolution at this point, it means your monitors EDID if wrong likely, from being old or having any adapter between your monitor and graphics card.  So at that point you have to either remove the adapter or find the monitors info for xorf.conf manually.  I got mine from an old installation xorg.conf file I always keep around.

---

### Post by eekfonky on 2008-10-26
How do i reinstall via hardware drivers? I don't want to end up with a black screen, a blinking cursor and no clue? lol
Thanks

---

### Post by mrjohnston on 2008-10-26
Let me ask something first.  Have you actually installed the Nvidia drivers via either envy or hardware drivers (under system-> Administration menu)?  If you haven't then you need to go to hardware drivers and select to install the Nvidia drivers (I think 1.77 is what you want IIRC).  Then it will install and you should reboot once that is done and all should be well.  

If you have already installed via hardware drivers the drivers, you can also uninstall from hardware drivers or from envy if you used that instead.  Worst case scenario you can uninstall the nvidia driver by searching for nvidia in synaptic.  I would completely remove them if you do this route (its an option in synaptic to remove or completely remove).  Then reinstall via hardware drivers as I have had that work flawless each time I have used it with intrepid thus far.

---

### Post by David D. on 2008-10-26
I had a similar or the same problem.  It was diagnosed and fixed with expert help.  The details are at [http://ubuntuforums.org/showthread.php?t=957529](http://ubuntuforums.org/showthread.php?t=957529).

---

### Post by Iowa Dave on 2008-10-26
Try the nvidia-settings utility. It is a dedicated utility for managing NVIDIA graphics in the X window environment.

For users who are not techno-whizzes, I'll give the steps I followed.

Go to System > Administration > Synaptic Package Manager. Check the box next to "nvidia-settings" and then click "Apply" to install it. 

Open a terminal window (Applications > Accessories > Terminal) and type "sudo nvidia-settings"
Enter your login password when requested.
The NVIDIA X Server Settings window will open.
Click on "X Server Display Configuration"
Choose the screen resolution you want, then click "Save to X Configuration File".

That's what got 'er done for me. By the way, you need to include that word "sudo" in front of the program name when you run nvidia-settings. Otherwise the settings won't get saved to the configuration file.

---

### Post by eekfonky on 2008-10-27
I have tried all of what has been suggested to no avail. I believe the EDID is wrong.
```
~$ sudo get-edid | parse-edid
parse-edid: parse-edid version 1.4.1
get-edid: get-edid version 1.4.1

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
	Function supported
	Call successful

	VBE version 300
	VBE string at 0x11110 "NVIDIA"

VBE/DDC service about to be called
	Report DDC capabilities

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
	Function supported
	Call successful

	Monitor and video card combination does not support DDC1 transfers
	Monitor and video card combination does not support DDC2 transfers
	0 seconds per 128 byte EDID block transfer
	Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
	Read EDID

	Performing real mode VBE call
	Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
	Function supported
	Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
parse-edid: IO error reading EDID
```
Does this help?

---

