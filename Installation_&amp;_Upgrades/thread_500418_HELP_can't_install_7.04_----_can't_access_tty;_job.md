---
title: "HELP can't install 7.04 ---- can't access tty; job control turned off"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by none1 on 2007-07-13
HI!

I am not a big linux hacker, but I have used red hat, fedora, suse and mandrake in the past.  I have not used devian or ubuntu.

I have an older QUAD XEON P3, ibm eserver, with an ide dvd and an ultra 160 scsi drive, 2 gig of ram.

I can not install UBUNTU.  I have a live DVD version of 7.04 that came from a linux pro magazine.  I get to the "choose an install" screen.  It starts to install, then I get kicked out to a busybox console, with an ugly looking message that says something like 

"can't access tty; job control turned off"

I've searched google and here, there seems to be ..... many ? reports of something similar, some folks can get it to work by using "option 3 other driver disk", or hitting F6 and adding break = top and then to continue booting, or by standing on their head when they hit the enter key for the install.

None of the proposed solutions I have seen work for me.

Is there any link / forum discussion / faq that puts all these types of solutions in one spot?

Most of the other distributions I've used have all mostly seemed to work out of the box.  Ubunutu 7.04 apparently can't seem to do the two things I want it for, install on my eserver and use persistency to boot from a usb pendrive. ...... and yet ubuntu has a great reputation and DELL is using it.  So I must be missing something.

So what gives, why can't I get fiesty fawn to work?  Any thoughts or help?

Thanks much!

---

### Post by TheTaylorEffect on 2007-07-13
"can't access tty; job control turned off"  is a frustratingly** ambiguous** error, that could mean almost anything!

(and I've run into it time and time again, especially when using with legacy hardware)

The solution that has worked consistently for me when I've encountered that error has been to:

1) Install [Ubuntu Server Edition]("http://www.ubuntu.com/getubuntu/downloading?release=server-newest&arch=i386&mirror=&debug=%5B%27country_US%27%2C+%27country_UK%27%2C+%27continent_NA%27%5D&download-button=") with the DNS server when prompted (becuase its smaller than the LAMP alternative).

2) Ensure internet connectivity.

3) Reboot.

4) Use the 

```
sudo apt-get install ubuntu-desktop 
```

command to install the rest. I find it's often best to take it a step at a time with older hardware.

---

### Post by 1fl on 2007-07-13
I feel for you, I'm running a amd 1.2ghz 512k ram two hdd 1st xp I ran the ubuntu live cd and it worked great I installed on second hd and got the can't access tty error message, on boot and had to use a boot disk to restart? I tried pc linux same tty error. googled the tty and spent hours reading none of the options worked for me either. But I tried debian and it works well for me, go figure ubuntu and debian are sisters? The only thing debian did not pick up was my printer but its an old hp, and xp doesnt pick it up either. Anyway maybe debian will work for you.

---

### Post by Pumalite on 2007-07-13
Choose the fix that works for you and give it a try:

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

---

### Post by none1 on 2007-07-15
None of those recomended fixes work for me.  Is there a "can't access tty ...... " thread or faq or something official?

Thanks!

---

### Post by TL_Mechanic on 2007-07-16
The "modprobe piix" fix got the live CD to load and run fine for me.  You guys are great, solved my first problem before I even installed.  Before if run the installer I was hoping to learn a bit more on exactly what I'm doing.  In the thread Pumalite wrote:

(snip)
[COLOR="Blue"]If you choose to install from the LiveCD, you must make the following modifications (or else your installed system will not be able to boot, just like the LiveCD)...[/COLOR]
(more steps not shown)

I was hoping some kind soul would elaborate on what the commands are doing so I can figure a bit of this out and adjust if it doesn't quite work on my hardware.

Thanks in advance for the help.

---

### Post by M0rtii on 2007-07-17
So what if I get the "can't access tty; job control turned off" error right after I select to install Xubuntu and I don't have a clue about what you guys are talking about.  Unfortunately I'm not one of those gifted souls who has any competence when it comes to command lines and unknown commands that someone is telling me to enter.

All I need to know is where can I get a working installation package for Xubuntu 7.04?  If this whole Linux OS from Ubuntu is supposed to be so great and easy to use, why can't I even install it?

This is what I'm running:
Dell Power Edge 1400
Dual Intel 667 Ghz Pentium 3 processors
1 GB of RAM
18.2 GB SCSI hard drive with ID set to 0

I've got Ubuntu Server Edition installed (did that yesterday) but did not realize it was all command line.  I need a desktop, I'm a visual person with no prior experience to Linux or trying to find work arounds and hacks to fix a broken OS Installer.

Thanks

---

### Post by bakketti on 2007-07-18
Worked perfect. Thanks!

---

### Post by merlinus on 2007-07-18
> 
I've got Ubuntu Server Edition installed (did that yesterday) but did not realize it was all command line. I need a desktop, I'm a visual person with no prior experience to Linux or trying to find work arounds and hacks to fix a broken OS Installer.
At the command line, enter:

```

sudo aptitude update && sudo aptitude install gnome-desktop

```You will be asked for your password, and after the installation is complete, you can reboot into a GUI.

-merlin

---

### Post by dburnett77 on 2007-10-29
Don't issue this commandedness

'history -c '

---

