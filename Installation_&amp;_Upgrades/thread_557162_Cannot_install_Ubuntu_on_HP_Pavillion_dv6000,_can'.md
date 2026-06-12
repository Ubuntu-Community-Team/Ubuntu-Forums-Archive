---
title: "Cannot install Ubuntu on HP Pavillion dv6000, can't access tty job control turned off"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by vzxa1 on 2007-09-22
About three weeks ago I purchased a HP Pavillion dv6000 Notebook PC,
 Processor: Intel(R) Core(TM)2 CPU T7100 @ 1.80GHz 
 Memory(RAM): 1014 MB
When trying to install Ubuntu/Kubuntu, I get the infamous "can't access tty; jog control turned off" message.  I have been to oodles of different web forums, but alas, I'm still not having any joy.

Here are some of the suggestions that I have tried:

1. Pressing F6 at the boot up screen and entering "break = top" at the start of the line,
     then entering "modprobe" or "all_generic_ide" or "modprobe pix"
     and lastly "exit"

    After the "exit" command, the screen just hangs, i.e. nothing happens


2. Pressing F6 at the boot up screen and entering " NOAPIC NOAPCI NOLAPIC NOIRQPOLL NOSMP"
     once again nothing happens


I was able to install OpenSuSe 10.2 (although with no sound and incorrect screen resolution), but frankly I'm not a big SuSe fan and find it clumsy and cumbersome compared to Ubuntu/Kubuntu.  The reason why I chose HP is because of the fact that HP and Dell are said to be more Linux-friendly than their competitors.  I've also noticed some people recommending downloading the alternate cd for installation, but as I'm still using dial-up, this is not a viable option.  I was also considering just waiting until the 18th of October, to try Gutsy, but from what I can gather, Gutsy also has trouble with a second hard drive and is also giving the "can't access tty...." error message during install.

Please, any help will be appreciated, there are so many posts on the web regarding this problem and and so few actual solutions, there must be a simple workaround to fix this.

---

### Post by Pumalite on 2007-09-22
[http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)

---

### Post by vzxa1 on 2007-09-22
Thanks for the link, Pumalite, unfortunately still no luck.  I added "noapic irqpoll noirdebug" at the end of the line after hitting F6, pressed enter, but then I get that familiar black screen saying " can't access tty job control turned off".

I must stress the fact that I am quite the novice, so if there is anything else that I need to do, no matter how simple and logical it may seem, please don't hesitate to mention even the most trivial steps.  

Thanks in advance.

---

### Post by Pumalite on 2007-09-22
Here you go. A mix of fixes, Take your pick (Thanks to dannyboy):

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

Good luck.

---

### Post by vzxa1 on 2007-09-22
Thanks for all your effort Pumalite, really do appreciate it.

I did as you suggested, seleted F6, added "break = top", then entered the commands:

modprobe piix
exit

I then got a blue screen saying:

Failed to start the X Server(Your Graphical Interface).  It is likely that its not set up correctly.  Would you like to view the X Server Output to diagnose the problem?

                        Yes                                                      No

Whether I choose Yes or No, I get the following message:

X Server is now disabled.  Restart GDM when it is configured correctly.

                                               OK

When I select OK it takes me back to the black screen with the command prompt.


Any Suggestions?  Like I mentioned, I am quite the newbie and any help will be appreciated,

Thanks again.

---

### Post by Pumalite on 2007-09-22
Say no to seeing the xserver file.
At the command line try: 
sudo dpkg-reconfigure xserver-xorg, choose most defaults, choose 'vesa' as the driver, then: startx

---

### Post by vzxa1 on 2007-09-22
Thanks for all your help, finally have Ubuntu installed on my laptop.  

Just have a few minor things I still have to work out, no sound, wrong screen resolution and its not recognizing the cd/dvd drive, but I'm sure I'll be able to figure it out.

Thanks again for all the time and effort, its greatly appreciated.

---

### Post by Pumalite on 2007-09-22
You are welcome. Good luck.

---

