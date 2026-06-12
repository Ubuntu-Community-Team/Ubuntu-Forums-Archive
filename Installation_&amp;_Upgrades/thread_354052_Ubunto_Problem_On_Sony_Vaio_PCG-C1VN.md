---
title: "Ubunto Problem On Sony Vaio PCG-C1VN"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by Religion on 2007-02-05
Hey Guys 
I have tried to install ubuntu on my sony vaio picturebook since its the only linux system that can be used on this computer.
and i have little problem i allready have been search in the fourm for an answers and nothing seems to be working.
i cancled the splash option on setup and still got with the problem it sais
/bin/sh: can`t access tty : job control tunred off

* i am talking about ubuntu 6.06 

any one can help ?

---

### Post by stanbriggs on 2007-07-17
did anyone ever respond to this post? i'm having the same issue with 7.04.

---

### Post by Pumalite on 2007-07-17
Choose the fix that works for you and give it a try:



when I boot, the screen shows

Starting up

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


f you are getting this error (and you have a SATA harddrive); this is the fix:

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
-- if you choose to install the '/boot' mount from a different partition make note of it as well (this would be done from the manual partition selection); just a side note -- if you do this, make sure the boot partition is at least 50MB or the install will error at grub setup
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
__________________

---

### Post by stanbriggs on 2008-03-05
all,

an even simpler answer is to use the 'alternate CD' that is available for download. i tried both 6.06 and 7.10 and both installed flawlessly. this website ([http://www.swampgas.com/linux/vaio.html](http://www.swampgas.com/linux/vaio.html)) has some good follow up instructions to get things like X-windows working properly.

life is good,
stan

p.s. the 7.10 alternate CD link is broken. i had to use the 6.06 link and wget (with appropriate changes made to the path, of course).

---

