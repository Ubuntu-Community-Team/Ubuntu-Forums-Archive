---
title: "Killed my computer updating ubuntu"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by laxwrestler on 2008-01-29
well i hadnt updated my system since around thanksgiving, so i finally got around to doing it today when all hell broke loose.  Not really but the update got about half way through before it got some error i guess, i wasn't really paying attention.  i tried to update through the update manager again after that but i find it denies my password.  so i updated through the command line, it still accepts my sudo password.  then i proceeded to restart. now upon starting the system, all i get is some sort of command line that says (initramfs) and waits for input.  no idea whats going on. any help or suggesstions?

---

### Post by erginemr on 2008-01-29
I think your "initrd.img" file, which is responsible from the boot-up process and resides under "/boot/..."  might have been broken during the update process. For a working linux system, running
```
sudo update-initramfs -c -k `uname -r`
```

would rebuild your "/boot/initrd-img-..." file, but since you cannot start it, we have to think of something else. 

There is an advanced technique; after running the Ubuntu Live CD, you may pass onto your installed hard drive by changing your root from the live cd environment to your existing installation with the "chroot" command and then, run the above command thereon to update your corresponding file. But this process is a bit cumbersome and may require mounting several more drivers (such as proc, sys) from your hard drive, so I will try to avoid it.

Second way is to check whether your system has created a back-up of your boot-up file during the update. With respect to the attached screenshot;

In my /boot folder, there are two relevant files:

```
initrd.img-2.6.22-14-generic
initrd.img-2.6.22-14-generic.bak
```

So, I believe your system should also have created a backup file during that process. You can make sure by booting your system with the Ubuntu Live CD, and having a peek at your installed hard drive. Be careful not to confuse it with the contents of the virtual system of the Live CD.

If there is really a back-up of "initrd.img" in your "/boot" folder, then what you need to do is to boot your computer as usual, and when you see Grub menu, to select the item for normal Ubuntu install and press "e" to edit it. Go down to the line with initrd.img-.....-generic, press "e" again to edit it and add ".bak" to the end of the file name. Press "b" to temporarily boot Ubuntu with this setting (do not press Esc or you will lose your edit and will end up with the default options). 

Once (and hopefully) you boot into Ubuntu (provided that you really have a backup file as I do), use the terminal with root privileges (sudo) to go into /boot and replace your initrd file with the backup:
```
cd /boot
sudo mv initrd.img-2.6.22-14-generic.bak initrd.img-2.6.22-14-generic
```

Thereon, you can continue with the update process. 

On the other hand, if changing the grub line accordingly does not give you back your system, then we are on the wrong track and should look elsewhere for the source of the problem.

---

### Post by laxwrestler on 2008-01-29
well i have the ..generic.bak file but thats it

---

### Post by laxwrestler on 2008-01-29
when i boot by changing the init..generic to generic.bak, it actually attempts to boot but i get the error that the X server failed to start and to reboot when the x server is configured correctly

---

### Post by laxwrestler on 2008-01-29
bump

---

### Post by erginemr on 2008-01-30
> **laxwrestler said:**
> when i boot by changing the init..generic to generic.bak, it actually attempts to boot but i get the error that the X server failed to start and to reboot when the x server is configured correctly

Do you mean you can boot in to the terminal this way, but you cannot boot in to the graphical server? If that is the case, then try the following:

1. Replace your broken initrd...whatever file with:
```
cd /boot
sudo mv initrd.img-2.6.22-14-generic.bak initrd.img-2.6.22-14-generic
```
if you haven't done already.

2. Copy your xorg.conf file:
```
cd /etc/X11
sudo cp xorg.conf xorg.conf.bak
```

3. Issue the following command to "automatically" reconfigure four xorg.conf file:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

4. Try to run your X server with:
```
startx
```

5. If it fails, then issue the following command to "manually" reconfigure four xorg.conf file:
```
sudo dpkg-reconfigure xserver-xorg
```
and depending on the brand of your graphics card, select the type of your card as either "vesa" (for all / generic cards), "nv" (for nvidia cards) or "ati" (for ati cards). And rerun:
```
startx
```

Good Luck...

---

### Post by laxwrestler on 2008-01-30
well it starts booting up, doesnt get very far and then gives me the error with x server.  so i don't even boot into the terminal.  i can't do it again right now unfortunately, but tomorrow i will post more details about the error messages it gives.  thanks for all the help erginemr.

---

### Post by erginemr on 2008-01-30
OK, but also try booting into the recovery mode (available as an option under Grub menu) which will (if it works) login to the "root" user and give you a terminal screen to work upon. 

On a side note, in this mode, you are root and don't need to prefix "sudo" to your commands.

---

### Post by boulde on 2008-01-30
hello,

I have the same problem after upgrading from gutsy to hardy: (initramfs)_

I tried the solution with initrd.img-2.6.22-14-generic.bak but it doesn't work

I also tried the recovery mode, but I still fall on the (initramfs)_ command

I have this error message when booting in recovery mode:
```

ALERT! /dev/disk/by-uuid/ c6b2.... does not exist. Dropping to a shell!

```

(for info, I already had this error some month ago after upgrading to gutsy, but I succeeded to boot ubuntu and then I have had to modify my /etc/fstab to replace sda by hda ...)

---

### Post by perixx on 2008-01-30
> it starts booting up, doesnt get very far and then gives me the error with x server. Try pressing ALT+F2 at this point. That should switch to a virtual terminal from which you can log in and enter the necessary commands stated above...

perixx

---

### Post by erginemr on 2008-01-30
> **boulde said:**
> hello,

I have the same problem after upgrading from gutsy to hardy: (initramfs)_

I tried the solution with initrd.img-2.6.22-14-generic.bak but it doesn't work

I also tried the recovery mode, but I still fall on the (initramfs)_ command

I have this error message when booting in recovery mode:
```

ALERT! /dev/disk/by-uuid/ c6b2.... does not exist. Dropping to a shell!

```

(for info, I already had this error some month ago after upgrading to gutsy, but I succeeded to boot ubuntu and then I have had to modify my /etc/fstab to replace sda by hda ...)

It seems the UUID print for your root drive has somehow changed. You need to find out first where your root drive resides as hda1, hdb3, sda2, etc. You can make use of a Live CD to check. Also having a look at your /etc/fstab file (the one in your hard drive) from the Live CD can be useful.

Then, during the booting process, interrupt Grub, edit the menu with "e", find the line with "root=UUID=......", edit that line with "e" again, and replace it with the hard drive ID you have just found such as "root=/dev/hda6", Press "b" to boot and see what happens.

If successful, find the correct UUID's of your hard drives with:
```
ls -l /dev/disk/by-uuid
```
or
```
blkid
```
and reflect the changes in both your "/etc/fstab" and "/boot/grub/menu.lst"

---

### Post by laxwrestler on 2008-01-30
okay when i try to run the command startx with my original xorg.conf file i get the following errors

Failed to laod module "type1" (module does not exist, 0)
Failed to load module "i810" (module does not exist, 0)
No drivers available.

when i try to run start x with the automatically reconfigured or manually reconfigured i get the following errors

Data incomplete in file /etc/X11/xorg.conf    Undefined Device referenced by Screen "Default Screen"
Problem parsing the config file
Error parsing the config file


I tried using my original conf file and replacing the original driver (an intel one) with vesa.  this booted up but i had no mouse control. i also get an error saying there was a problem starting the gnome Settings daemon
Failed to execute program /usr/lib/control-center/gnome-settings-daemon: Success

any suggestions on how to get my mouse back and or get the original intel driver to work?

---

### Post by erginemr on 2008-01-30
You have completed the interrupted update proces from the terminal I guess. So, that is out of question, now.

Here is my xorg.conf file for you to make a comparison. You should focus on the mouse settings.

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"tr"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV17 [GeForce4 MX 440]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Option		"XvmcUsesTextures"	"True"	
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV17 [GeForce4 MX 440]"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Modes	"1024x768_75"	"800x600_75"	"640x480_75"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
    Screen		"Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

Alternatively, booting up from a Live CD and using its xorg.conf file might give you a chance to see your desktop.

---

### Post by boulde on 2008-01-31
> **erginemr said:**
> It seems the UUID print for your root drive has somehow changed. You need to find out first where your root drive resides as hda1, hdb3, sda2, etc. You can make use of a Live CD to check. Also having a look at your /etc/fstab file (the one in your hard drive) from the Live CD can be useful.

Then, during the booting process, interrupt Grub, edit the menu with "e", find the line with "root=UUID=......", edit that line with "e" again, and replace it with the hard drive ID you have just found such as "root=/dev/hda6", Press "b" to boot and see what happens.

If successful, find the correct UUID's of your hard drives with:
```
ls -l /dev/disk/by-uuid
```
or
```
blkid
```
and reflect the changes in both your "/etc/fstab" and "/boot/grub/menu.lst"

thanks for your answer.
I tried with "root=/dev/sda3" which is my system partition, but I still get the same initramfs error ...
I think I will reinstall gutsy ...

---

### Post by erginemr on 2008-01-31
Sorry to hear that. I think Mr. Murphy's rules are in action once again. Do not forget to secure your important data (music, files, etc.) before the install...

---

