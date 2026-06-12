---
title: "8800 GTX problem.  Can't load desktop, still get black screen"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by kntgsp on 2007-12-06
I have read and googled every possible scenario for this and there is not a working solution in existence.

Here is the setup:

ASUS P5N32-E SLI
Q6600
4GB RAM
150GB 10k Raptor
2x8800 GTX in SLI

I can't boot up the LiveCD, keep getting the black screen, which is apparently a common problem.  Ok fine, so I run the regular install.  I use the text based installer that I burned to a second CD, everything goes fine, ejects the CD and prompts for reboot to start new OS.

I reboot and it initializes everything but I just get a black screen.  I can hear the boot up african drums, so it's booting fine, and I can switch to command line with ***-alt-f1, so it's booting fine, it's just the desktop that isn't displaying.  I've tried every resolution under the sun, i've tried it without quite and all the other F6 options on install.

I've tried every option listed in the forum posts to no avail.  I would very much like to run Ubuntu, if it would just let me get to the damn desktop.  I try to install the nvidia drivers with the "sudo apt-get install nvidia-glx-new" but that doesn't work.

I'm a complete n00b to Linux, but I'd really like to make the switch.  However if i can't get this working, obviously there's no reason for me to switch.  I downloaded the nVidia drivers from their website and burned them to a CD.  Is there some way to install that manuallly in recovery mode?

---

### Post by JangMunho on 2007-12-06
Either Live CD or an installed system will use an open source driver instead of nvidia's official driver. And the open source driver won't work on GrForce 8 series.
All you have to do is install nividia's driver through apt ( I don't know if the driver there support GeForce 8, since they are often out of date), or download a new driver on [www.nvidia.com](www.nvidia.com) (I recommend this). Install the driver and you can start x.

By the way, you should notice something during the installing process ( your card module is too new some way...), like edit linux-re*****modules**(sorry the name of the file is too long, I can't remember) to "nvidia new" instead of "nv" (which will work on old cards).

I can remember the commands by detail, try to get something on wiki...

Good luck!

---

### Post by kntgsp on 2007-12-06
I already have downloaded the Linux driver from the Nvidia site.  But how do I install it if I can't boot into the desktop?  I burned the driver to a CD, but how do I load it into Linux using the command interface in recovery mode?

I pop the CD into the drive and then is there some command to type in to run that .run app from the CD?  If so, what is it?

Haven't been able to boot into the desktop once.

---

### Post by JangMunho on 2007-12-07
A brief description of the installing process is:
1. switch to the command line (quit x server):
Using Ctrl+Alt+F2 to login on tty2, since your card cannot load X, this step has been automaticly done by the system.
2. stop any appicaitons contains in gnome:
Though x cannot be loaded, this step should be done to make sure any appications based on x have been terminated.
Try: sudo /etc/init.d/gdm stop
3. Modify some files, otherwise the driver won't work:
Try: sudo pico /etc/default/linux-restricted-modules-common
modify DISABLED_MODULES="" to DISABLED_MODULES="nv nvidia_new".
pico is an easy-to-use editor. You can use Ctrl+o to saved the file, and Ctrl+x to quit the program.
4. Install build-essential:
This package can install all the compiler that the installer needs, such as gcc. You must have a active network connection.
Try: sudo apt-get install build-essential
5. Ready to install the driver:
Either a CD or a flash disk won't be auto mount when they are inserted with no GUI loaded. You must use mount command.
For a flash disk, when it's inserted, a message will appear to tell you new disk found. Try to find which device it is from the message (like sdb1, most of the new systems will be this).
Then try: sudo mkdir /media/usb
and: sudo mount -t vfat /dev/sdb1 /media/usb

Then you can read the files on /media/usb

Now use: sudo sh NV*.run
to start the installer.
One thing should be noticed is that when the installer ask you weither to download a module, you should choose 'no'; when it ask you weither to auto update xorg.conf, you should choose 'yes'.
after finished the installation, try this command to unmount your flash disk: sudo umount /dev/sdb1

6.Now start X:
sudo /etc/init.d/gdm start

7. Enjoy. 
More tuning features can be found in nvidia-settings.

---

### Post by Ilias83 on 2007-12-07
I followed these steps to install latest nvidia drivers, but now I can't see effect at all and my system run slower...

---

### Post by Ilias83 on 2007-12-07
Try to use Envy [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) to install NVIDIA Drivers.
I just made it work.
It was very easy...

---

### Post by Sicundercover on 2007-12-07
How did you get this "Envy" to work?

Im looking on their site and Im not seeing instructions anywhere. I must not be seeing something.

---

### Post by Ilias83 on 2007-12-07
You just download a file named envy_0.9.9-0ubuntu1_all.deb from the link I just wrote in my previous post.
Doulbe click it starts installation.
It will install Envy.
You'll run Envy from Application->System Tools->Envy
You'll just following its instructions.
CATION: You'll have to disable Restricted Drivers before running Envy

I hope this will help.
I'm totaly amateur on Linux.

---

### Post by Sicundercover on 2007-12-07
Ohh I thought you were saying it could be done from recovery. 

Ohh well back to start.

---

