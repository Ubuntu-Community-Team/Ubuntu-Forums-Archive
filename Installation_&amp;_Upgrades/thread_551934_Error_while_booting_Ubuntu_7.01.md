---
title: "Error while booting Ubuntu 7.01"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by Navery on 2007-09-15
I just installed Ubuntu 7.01 (Fiesty Fawn) on a computer with 512 MB RAM, an Intel Pentium 4 Processor, and a 9GB hd that I installed it too. But I have another 40GB slave drive in the computer.


It is giving me this after a long stall on the boot screen:

udevd-event[1931]: run_program: '/sbin/modprobe' abnormal exit


BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)

/bin/sh: can't access tty; job contral turned off
(initramfs) 

Not sure what is going wrong brand new to linux so I need as much information without being to technical. 

Thanks,

Navery

---

### Post by Navery on 2007-09-15
I installed with Live CD could that have anything to do with it? I do not want to but I am willing to try installing again with Alternative CD would this make any difference?

---

### Post by Pumalite on 2007-09-15
Maybe; maybe not. Here is a mix of fixes for your problem:

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

### Post by Navery on 2007-09-15
Thanks I will try this! The only thing is Ubuntu is already installed it comes to the splash screen without the live CD but after sitting there forever it takes me to the before metioned error. Sorry to sound a little unexperienced but this is my first time ever loading any kind of Linux. I think I will like it I just wished I could get it working lol! Have to go to bed now but will try tomorrow afternoon. I hope this works :)! I LOVE UBUNTU!!!!!!

---

### Post by Pumalite on 2007-09-15
Post your specs.

---

### Post by Navery on 2007-09-16
Here are the specs:
2 GHz Intel Pentium 4 processor
512 MB DDR (Have some extra may add more later)
49GB (2 drives one 40 and the other 9)

Not sure on which motherboard graphics card sorry

1 DVD - RW Drive
1 CD Drive
1 Floppy Drive 
 Not sure of the makers of any of this or any more specs on this computer. My Dad bought this computer and the previous HDD went bad so he told me since we are not using it anymore if I could get a HDD for it he would let me install Ubuntu. We also had another computer not being used in the attic. It had windows 98 so i took out the drive and do not want to keep windows 98 so I partioned the HDD using Gparted and wiped out the OS. So I installed Ubuntu(with problems) but I will try this afternoon to reinstall or fix install.

---

### Post by Pumalite on 2007-09-16
Have you tried the fixes?.

---

### Post by Navery on 2007-09-17
Sorry it took so long to repost. But I have tried the fixes and this is what happened. It looked well with the installation thing in the terminal. 

Then I got it reinstalled and got the same error.

I tried the fix but ended up with this error:

FATAL: Could not load /lib/modules/2.6.20-15-generic/modules.dep: No such file or directory.

Not sure what to do now. Please let me know. I am soooooooo close I can taste it! I want Ubuntu really bad! Right now I have a computer (which thankfully did not work originally) with no OS and nothing to be able to do! I will be bringing this computer into school tomorrow to see if someone there can help me.

Please let me know if you know any fixes! Thanks I cannot tell you how much I appreciate this! 

Thanks again!

---

### Post by Pumalite on 2007-09-17
Trying to load the kernel. Graphics would help.

---

### Post by Navery on 2007-09-17
Not sure what you mean. Do you want to know what kind of Graphics card I have? or something else? Gotta go to bed will check for your reply tommorrow! Thanks!

---

### Post by Navery on 2007-09-18
What did you want to know Pumalite? My type of graphics card? if I have one or what?

---

### Post by Pumalite on 2007-09-18
Both.

---

### Post by Navery on 2007-09-18
I tried the thing with the terminal and it gave me a segmentation fault (core dumped) over and over until it finally stopped. hmmmm... not sure what to do now. Any suggestion on what could be wrong???

---

### Post by Pumalite on 2007-09-18
I still don't know what graphics do you have.

---

### Post by Navery on 2007-09-18
I am not sure on the kind of graphics but I did get the install to finally WORK!!!! WOOT!!! I had to just follow the fix in order LOL! Did not know this! Thanks SO MUCH Pumalite for your help! I am so happy now if I could figure out how to install my wireless USB Network Adapter it would be the best I have ever had! Again thanks alot I will be framing the fix and hanging over my bed so it is the last thing I see at night LOL! J/K! But I cannot tell you how much I apperciate this THANKS!!!!!!!!:popcorn::guitar::lolflag::):KS:popcorn::):guitar:

---

### Post by Pumalite on 2007-09-18
You are welcome. Glad it worked for you!. For your wireless you might want to try Networking & Wireless.

---

