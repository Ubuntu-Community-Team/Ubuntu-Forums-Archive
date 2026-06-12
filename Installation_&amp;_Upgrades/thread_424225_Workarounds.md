---
title: "Workarounds"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by jerrylamos on 2007-04-26
Some Feisty bugs I've encountered and possible workarounds "that worked for me":

Excessively twitchy laptop mouse/track point/touchpad
[https://bugs.launchpad.net/ubuntu/+bug/84119](https://bugs.launchpad.net/ubuntu/+bug/84119)
James_pic said on 2007-04-22: Apparently the problem is due to the Thinkpad R31 using the same controller (the i8042) for the keyboard, mouse and power management, and occurs every time something polls the battery. The Wrong Solution is to pass i8042.nomux=1 to the kernel - add it to the #defoptions line in /boot/grub/menu.lst, run "sudo update-grub", and reboot (I can vouch for the fact that this works). The Right Solution is to set this as the default in the next release of the kernel.

"Feisty fails to boot"
Some things to try: On boot options, push F6 and change the line ending in:
...quiet splash
to
...quiet splash noapic acpi=off irqpoll
If any/all of these seem to help, they might be needed on an install as well.  Edit /boot/grub/menu.lst (where l is lower case L) the first kernel line to end in the same manner.

"Can't access tty"
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106864)
There was a "fsck failed, see /var/log/checkfs" buried in the middle of the messages that roar up the screen.  My interpretation, the bug came in when hard drive code was changed to support both IDE and SATA.  Along with this came change of device name from hda to sda, complex UUID's, and all that.  fsck failed to process the IDE hard drive.
My fix: put in an extra cable to put the IDE hard drive on IDE2, while the CDROM is on IDE1. Ubuntu booted right up, no "can't access tty" errors.
 Ben Collins  said on 2007-04-18:  (permalink)
The quick workaround for this on an installed system is to add "piix" to /etc/initramfs-tools/modules, and run "sudo update-initramfs -u"
For installing a system, add break=top to the kernel cmdline via the bootgfx menu. Once at a busybox prompt, run "modprobe piix". Then "exit" the shell. Once the system is installed, the above work around will also be needed.

From another post in bug 106864:  Adding piix in /etc/initramfs-tools/modules allowed to advance more in the 
startup but the kernel was not able to finish the startup. I've added this in /etc/initramfs-tools/modules:
piix
i2c_piix4
i2c_core
Now the problem is solved in my system.

Another user report on  [Bug 106864] Re: Feisty boot fail "can't access tty" IDE SATA problem: 
"...then i found this Edgy bugreport:
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256)
thanks to this, edgy booted.  i tried doing the same on feisty:
    $ sudo update-initramfs -u -k 2.6.20-15-generic
and after rebooting everything worked fine!"

"Feisty does not recognise CD burner"
The workaround mentioned in the previous thread (break=top + modprobe piix)
fixed the xfermode error problems described in bug #96826 for me on a
Dell OptiPlex GX100 system. The two problems seems to be connected.

"No network connection" after boot.
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/83143](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/83143)
The ethernet card works fine on Edgy, Dapper, Knoppix, ...  Buried in /var/log/syslog Network Manager decides the card "cannot support carrier detect" and disables it.  The workaround is on every boot, notice the tiny red mark on the network manager icon on the top right, click on it, and click on wired connection.  The connection comes right up.  Network Manager is a default package on Feisty.  Removing the package doesn't help because Network Manager is still active on boot disabling the card, and without the icon I would have to open a terminal, sudo dhclient, enter password.

Xubuntu install partitioning failure
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107259](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/107259)
Xubuntu Feisty couldn't delete, new, or resize partition.  It could however edit target partition to change mountpoint to / and format and then install.  If partitioning is desired, my best bet is standalone CD Gparted: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) 
There is a gparted package on Ubuntu but I didn't try it.

Screen resolution wrong or too low
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/89590](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/89590)
Fix that worked for me: You'll need to know the screen driver, perhaps google the manufacturer to find out.  In my case for Intel 82845G graphics controller it's i810.  
Ctrl-Alt-F1 to get a command line.  Log in.  Ctrl-Alt-F7 to return if you get cold feet.
cp /etc/X11/xorg.conf xorg.conf.save (just in case of goofup.)
sudo dpkg-reconfigure -phigh xserver-xorg
Some screens will ask some questions.  Try to get the driver selected right.  Assuming it goes O.K.,
sudo killall gdm
sudo startx
cross your fingers....
You can safely look at xorg.conf with
less /etc/X11/xorg.conf
which is a browser and can't change the file. Use q to quit.

Persistent on CD Live doesn't work
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591)
With "persistent" option, F6 on CD Live Bootup, files, settings, package installs etc. can be saved to a USB pen drive.  This gives me the luxury of hardware independence since I can take my files and setup with me to any of the 5 computers on the LAN here with just the CD and the pen drive.  This works fine on Edgy and Dapper but not Feisty.  Some Linux's like Knoppix and Puppy have nice menus to set up the pen drive but it's a do it yourself on Ubuntu.  A linux ext3 formatted pen drive with label "casper-rw" is needed.  I'd give a how to but persistent is broken on Feisty.  Development may try to fix for Gutsy Gibbon.
A poor man's solution to saving files (but not settings) from CD Live is to do Applications, Accessories, Terminal.  
ls /media     may show you the USB drive, in my case it's casper-rw.  From home:
sudo cp -au * /media/casper-rw		that will likely get Desktop as well, or
sudo cp -dpu * /media/casper-rw		copies files but not directories.		
enter password
I don't know if this works for default pen drive Window type formats.

"Shutdown" doesn't
This system powers off with Edgy, Dapper, Knoppix, ... but not Feisty.  If I select Shutdown after a while nothing's happening, there's no message on the screen, and the keyboard and mouse are dead.  Someone on some forum (where?) suggested:
Do sudo gedit /etc/modules.  Add the following line, then save:
apm power_off=1
do sudo gedit /boot/grub/menu.lst (where the l is a lower case L).  Find the line that start with "kernel" and add this onto the end, no carriage return, all on the same line which probably wraps over:
acpi=off apm=power_off
then save.  Power off however you can, power back up and on "Shutdown" it should.  Mine did.
Usual cautions apply when changing system files.....

AOL Mail doesn't work on Konqueror
I use mail on AOL and Yahoo so when I go to a different computer or location or country I've got my mail accessible.  Kubuntu Konqueror doesn't do AOL mail; Ubuntu and Xubuntu Firefox does.  For Kubuntu, I did Applications, Add/Remove, searched on firefox and installed it.

Firefox Fonts shrank on May 4 '07 upgrade
Firefox update for Gutsy to fix spell check as you write shrank fonts ~40% example bookmarks etc. etc.
Fix Originally Posted by conjur3r
"To fix the font size: System > Preferences > Font > Details at the bottom right and change the resolution back to 96."


Cheers, Jerry:)

---

### Post by jholsenback on 2007-05-19
Persistance does pay off .... I'm now able to boot the Fiesty LiveCD. I was having the can't access tty error on my Dell 8250. I added break=top to the boot parameters (F6) then when the error shelled out I typed modprobe piix ..... then typed exit. Now I'm feeling froggy. Perhaps I'll attemp a install to my blank HD tomorrow!!!! Thanks you very Much. Ahhhh .... I think I'll step out for a smoke and call it a night.

---

### Post by metra on 2007-06-03
Thank you for posting this;
I just upgaded and was looking for help with a few of the same problems you had.

---

