---
title: "Worst Experience Ever, Need help"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by dreadlocks1221 on 2007-09-18
At first I couldnt get the regular installer to work it would either freeze up or not load, I finally got the alternate cd to install, now when I try to boot up Ubuntu it stops when it tries to start bluetooth services, it then will try to load start x and then itll say no screens found. Then it goes back to the blue tooth thing and I can type stuff in but nothing happens. 

I can load ubuntu in recovery mode and get a command line but I still can load startx because of the no screens found reason. So far I haven't had any success with anything 

I've looked all around these forums, googled many things, but found no help

My computer Specs are

HP
Core 2 T7300
4 GB DDR2 Ram
200 GB Hard Drive
GeForce 8400M GS
Wireless N and Bluetooth
Vista Ultimate (I Dual Boot, but this problem still happened when I wasnt)

Thanks in advance for any help

---

### Post by Pumalite on 2007-09-18
Install while wired to a LAN or such. Later configure your wireless.

---

### Post by dreadlocks1221 on 2007-09-18
I dont see how that will help since my boot hangs when it tries to start bluetooth and gnome wont start either

---

### Post by Zenham on 2007-09-18
If you're using the restricted drivers for Nvidia, I had an issue a couple days ago because th ere were API version mismatches between the X.org nvidia driverand the nvidia kernel module.

If you check the extended output for your X server, look at the lines starting with "EE", those are the errors. If you can post more information from there to us here, people may be able to give you a bit more help.

Regards-

---

### Post by dreadlocks1221 on 2007-09-18
what it says is : (EE) NV(0): No Display Devices Found
and                    (EE) Screen (s) found, but none have usable configuration

---

### Post by Pumalite on 2007-09-18
If you have installed your system and you end up with a blank screen, Ctrl+Alt+F1 to get a command line. If you can get a command line through 'Safe Graphics Mode', even better; then:
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx

---

### Post by Zenham on 2007-09-18
If you look at the detailed X server output, there will be more information. Those two lines are just the "Hi, your display is broken" message.... hate to make you go back again, but if you would... :)

The errors you've described have everything to do with X configuration, and nothing to do with Bluetooth. This isn't to say Bluetooth isn't the problem, but just that the issues you're describing have to do with your video configuration for X.

---

### Post by Zenham on 2007-09-18
As an aside, the suggestion Pumalite made just above my post is worth saving, if you won't remember it offhand... it's the way to get your system to reconfigure X.org automatically. If that still does not work, however, a more specific error message would be helpful.

Cheers-

---

### Post by dreadlocks1221 on 2007-09-18
it said xserver-xorg is not installed and no info is avalable

---

### Post by Pumalite on 2007-09-18
It means you have not installed your system yet. We can help you if you give us more step by step details of your problem.

---

### Post by dreadlocks1221 on 2007-09-18
they way I instlled my system was with the alternate cd because the regular one wouldnt load up If I have to reinstall then thats fine, but I have to go to class soon so Ill post all the errors I get when I use the regular one when I get back, I do remember it had to do with startx as well though

---

### Post by Pumalite on 2007-09-18
Ok.

---

### Post by dreadlocks1221 on 2007-09-18
Ok I put in the instalation cd, I get the failed to allocate mem resources error (which I read was harmless) 

Then I get the Busy Box info and it says /bin/sh: ttyl job control turned off 

(initramfs) _ [Blinking underscore]

I get the same thing when I try to run it in safe graphics mode

---

### Post by Pumalite on 2007-09-18
I think this is your problem:
GeForce 8400M GS
If you are adventurous, you might try Tribe 4 (it worked for me). Cannot recommended it for people that depends on their OS as it's in testing.
Or you might try a collection of fixes I have picked up from other threads:

Credit to this goes to
hbjason as these are his exact words. It appears as though it's a combination of some of my suggestions that I found on the internet etc etc.
ust a side note -- if you do this, make sure the boot partition is at least 50MB or the install will error at grub setup
o When the install is complete do not reboot -- stay in the LiveCD
o Open a terminal (Applications->Accessories->Terminal)
o You must now mount the installed partitions by typing the following (assuming the install was to /dev/hda1; otherwise replace '/dev/hda1' with the install partition) commands:

mkdir target
sudo mount /dev/hda1 target

*if you also created a boot partition issue (replace /dev/hda2 with the boot partition) the command:
sudo mount /dev/hda2 target/boot

sudo chroot target

o You will now be in a 'chroot' command prompt for your new ubuntu system (be careful here, you are editing with root access!)
o You must edit the /etc/initramfs-tools/modules file; adding a line with the word: piix
-- you should do this with your favorite unix editor; or simply type the command:
echo piix >> /etc/initramfs-tools/modules
o After modifying the file you must update the system with the command
update-initramfs -u
o When complete, type 'exit' to exit the chroot env; you can now close the Terminal and reset your system.

Now when you boot you will be in your new shinny Ubuntu system!

---

### Post by dreadlocks1221 on 2007-09-18
should I do that while booting what I already have installed or while trying to reinstal? Im kinda a noob so its best to give me more detailed instructions

---

### Post by Pumalite on 2007-09-18
'When the install is complete do not reboot -- stay in the LiveCD'

---

### Post by dreadlocks1221 on 2007-09-18
But thats the thing, I can't install with the regular install cd, I get the Job contron turned off thing, sorry about all this, and from what I read the alternate doesnt have a live from cd thing

---

### Post by Pumalite on 2007-09-18
Try this:

At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

---

### Post by dreadlocks1221 on 2007-09-18
I did all that and I got the xserver thing again and then it threw me into the same kind of command line thing as when I tried to boot what I already had installed

---

