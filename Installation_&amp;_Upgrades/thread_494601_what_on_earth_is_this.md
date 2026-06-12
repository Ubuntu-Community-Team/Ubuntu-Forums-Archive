---
title: "what on earth is this?"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by speedingbullet on 2007-07-07
On one of my pcs I tried installing xubuntu.... but I got a weird message that was from some program that went by busy box or something....

up close:
[IMG]http://img354.imageshack.us/img354/7117/problem1it9.jpg[/IMG]


away (dont ask, the monitor was dirty like that when i got it):

[IMG]http://img479.imageshack.us/img479/1660/problem2dl6.jpg[/IMG]

I noticed it said ata2.... does this mean somethings wrong with my hard drive?

---

### Post by regomodo on 2007-07-07
can't really read it tbh. has this cd worked in other computers before?

---

### Post by speedingbullet on 2007-07-07
yes it has... lemme boot it up again so I can type what it says:



/bin/sh: Cant access tty; job control turned off
(initrans)  [     71.0966251 ata2.01: exception Enask 0x0 action
0x2 frozen

do I need to type the whole thing?

---

### Post by s_raghu20 on 2007-07-07
I am having the same problem. The same Live CD worked on my other Dell Laptop, but on this new compaq 6710b it flashes the same message.

BusyBox v1.1.3 (Debian...so on and on...)

/bin/sh: can't access tty: job control turned off
(initramfs)

Afterwords, this **(initramfs)** becomes the prompt.

Help...

regards
raghav..

---

### Post by speedingbullet on 2007-07-07
tommarow im going to try downloading an alternate CD of xubuntu, but before I do that, ill check for more replies to this thread

As for my model... there apparently is no model... as it seems the company who made it, perpetual systems, makes custom builds.

---

### Post by s_raghu20 on 2007-07-07
I tried searching more and found a diff thread on the same topic.

However, that did not do the final trick as well... Here is the thread
[http://ubuntuforums.org/showthread.php?t=421588]("http://ubuntuforums.org/showthread.php?t=421588")

Good luck to all attempts..

---

### Post by speedingbullet on 2007-07-07
A hard drive problem eh? Well if thats the case, i might as well just replace the hard drive with another one, as im planning to simply give the computer away to a random, person, and I dont want them to go through that if they try reinstalling linux.

---

### Post by Pumalite on 2007-07-07
I found this:

/bin/sh:can't access tty;job control turnedoff

Describe your new note here.

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

I don't know, but it might be of help.

---

