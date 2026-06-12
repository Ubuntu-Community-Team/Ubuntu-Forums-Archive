---
title: "Feisty Installation Problem"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by Sadi on 2007-06-18
I've downloaded & burned the Fiesty distro. On boot up I get the commonly reported error **"/bin/sh:can't access tty; job control turned off"**

I have tried the following fixes but to no avail :(

- On F6 (more options) I have deleted splash, quiet and --  and added break=top
- I have also tried 'add_generic_ide' instead of break=top
- On some forums on the net, I have found people suggesting that putting a floppy in the floppy drive works!....I tried that but I get this error message:
                                              **end_request: I/O error, dev fd0, sector0**

I know this has been a common error discussed on this forum but I would really appreciate if someone can help me out here, I'm sick of Microsoft and would really like to start using Ubuntu. I'm a noob in linux so easy to follow instructions will be greatly welcomed.

---

### Post by merlinus on 2007-06-18
The Search feature works great!

[http://ubuntuforums.org/showthread.php?t=415009&highlight=can%27t+access+tty](http://ubuntuforums.org/showthread.php?t=415009&highlight=can%27t+access+tty)

Or this:

SOLUTION TO /bin/sh: can't access tty; job control turned off
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

-merlin

---

### Post by Sadi on 2007-06-18
I have tries the steps that you mentioned
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

BUT even after that I'm getting the same error!!!

Is there something that I'm doing wrong??

---

### Post by merlinus on 2007-06-18
You can try this:

At the command prompt: type:
```

 sudo dpkg-reconfigure -phigh xsever-xorg

```
Then select vesa as your video driver and use the space bar to select the resolutions.

Have you tried Safe (Video) Mode?

If all that still fails, you might try the Alternate Desktop install cd at:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Check the box just below the green Start Download graphic.

-merlin

---

