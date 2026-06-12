---
title: "installation problem with laptop..."
date: 2007-09-21
forum: Installation &amp; Upgrades
---

### Post by Neapix on 2007-09-21
heya 

before i installed the ubuntu, i made special room for ubuntu in the hard disk using Partition Magic (windows has no connection to that free room).
i have problem when i install ubuntu on my laptop.. (from live CD)
my laptop is:
LG LE50 Express
1.73 Ghz
2024 Mb RAM DDR2 533mhz 
graphic card i think its - ATI RadeonTM Xpress 200M 128MB

when i put the live CD and start installing.. i get wierd window that says:

[ 149.452000] Buffer I/0 error on device hdc, logical block 0
[ 149.452000] Buffer I/0 error on device hdc, logical block 1
[ 149.452000] Buffer I/0 error on device hdc, logical block 2
[ 149.452000] Buffer I/0 error on device hdc, logical block 3
[ 149.452000] Buffer I/0 error on device hdc, logical block 0

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off

i really dont know what to do and i dont know much about linux this is first time trying using =]

tnx for helpers,

neap.

---

### Post by Pumalite on 2007-09-21
Try Alternate CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below green sign 'Start Download'

---

### Post by Neapix on 2007-09-21
i have problem with that.. i'm not at home right now and for the next two weeks.. im using my mobile as a modem for internet and i can't download...
but someone told me that this error can be fixed.. (not using the Alternate CD, diffrent way...)

---

### Post by Pumalite on 2007-09-21
I'll give you a mix of fixes. Choose what applies to you:(thanks to dannyboy):

At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

You will now boot into the LiveCD normally.

If you choose to install from the LiveCD, you must make the following modifications (or else your installed system will not be able to boot, just like the LiveCD):
o Make note of the device id of the partitions that were used to install (such as /dev/hda1)
-- if you choose to install the '/boot' mount from a different partition make note of it as well (this would be done from the manual partition selection); jStarting up

then boots to the following:

/bin/sh: cant access tty; job control turned off.
(initramfs)

so, i try the following command as suggested:


/bin/sh: cant access tty; job control turned off.
(initramfs)modprobe piix
(initramfs)exit


This does the trick, Ubuntu starts up fine, and smoothly.

> Just to simplify a little, however, after the command (in the chroot env):
> sudo echo piix >> /etc/initramfs-tools/modules
> all I needed to do is issue the command
> sudo update-initramfs -u
> to update the initramfs (thus correcting the system) and then
> exit
>

UPDATED FIX!!! I removed the old suggestion that I had written and pasted the new fix from the main thread of this problem...... Credit to this goes to
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

