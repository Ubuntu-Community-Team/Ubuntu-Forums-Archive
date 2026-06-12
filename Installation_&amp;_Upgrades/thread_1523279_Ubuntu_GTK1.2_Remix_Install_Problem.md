---
title: "Ubuntu GTK1.2 Remix Install Problem"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by Logos Asectic on 2010-07-03
I have a Dell Inspirion 3500 laptop with the following specs
[FONT=times new roman][SIZE=3]pentium II 266mhz processor
floppy drive (registers in BIOS, attached to serial port in back)
CD-ROM drive (doesn't registers in BIOS, although is displayed in system intialization prior to boot)
4 GB hard drive (wiped with Darik's Nuke and BOOT floppy disk)

I have tried to boot from all sorts of Windows CD's and Linux CD's. None will boot. So I choose to boot from USB. Since It is such an old laptop I needed to load the USB drivers before booting. SMART BOOT MANAGER failed. PLOP BOOT MANAGER booted to its own menu. It still would not boot to CD. So I tried putting an exact copy of the remix ISO onto a USB and loading it. This failed so I used UNETBOOTIN to extract the ISO to USB. PLOP finally recognized it and loaded the UNETBOOTIN MENU. From there I load the Graphical environment (since the dev said it wont load any other) Then UNETBOOTIN loads the REMIX into the "LIVE ENVIRONMENT" from USB. Once I was in the "LIVE ENVIRONMENT" I right clicked and opened a "TERMINAL EMULATOR" and from there I ran the “sudo ./install.sh” command to install it from the USB stick (dev's instructions). From there it says it can only install to a single blank hard drive of at least 500mb, but it makes no allowance for alternative hardware or software changes. Is it possible that since I have a floppy,cdrom,and usb stick installed during the install that it is causing an error? I choose yes.I enter username , then click yes.Then I choose hostname , and click yes.

Now for the final step It says that the drive has partitions or filesystems in place. Here is what  it displays

Checking....
disk /dev/sda doesn't contain a valid partion table
disk /dev/sda: 40099 mb, 4099866624 btyes
disk /dev/sdb: 1012   mb, 1012924416 bytes
/dev/sbb1    ?    1651315    1777688    123339962    78    unknown
/dev/sdb2    ?     221758      619137     387841909+  10    OPUS
/dev/sdb3    ?     399394     403658        4161539       8b    unknown
/dev/sdb4    ?    399394    403658         4161539         a     OS/2 boot manager

do you wish to continue and destroy any partitions?

So I click yes,and this is displayed

checking for active swap, if any on /dev/sdba /dev/sdbb......

making a valid label....
expr: non-numeric argument

partitioning /dev/sda /dev/sdb......

it appears that the partitioning step has failed. exiting.

SO you can see where Im stuck. Any suggestions?[/SIZE]
[/FONT]

---

### Post by Ibidem on 2010-07-20
I'm guessing you know the command line somewhat, if you plan to use that remix...

OK, which is your hard drive--/dev/sda or /dev/sdb?
It looks like /dev/sda.

Try running "sudo cfdisk" if you are ready to partition manually--it will be sort of like DOS fdisk, if you've used that.
Or (my own suggestion) "sudo parted -a optimal /dev/sda"
At the prompt, run:
mklabel msdos                                         #Create a DOS partition table; advised for BIOS reasons
mkpartfs primary fat16 1 20                     #A little DOS partition, for any utilities/BIOS updates...
mkpartfs primary ext2 21 3048
mkpartfs primary linux-swap 3050 3500
print
quit

Reboot (sometimes helpful with a changed partition table), and see how it installs afterwards.

If that fails, what I'd do is:
sudo gtkedit install.sh
(open up the installer in the text editor)
Try to figure out the problem, or install manually.

Perhaps a better bet, if you have DSL, would be using the netboot ISO...but that is complex and slow.

What type of CD--IDE or SATA?

---

### Post by Logos Asectic on 2010-07-21
well The author of the remix stated on his blog that the installation had problems with anything other than a cd and blank hard drive. I just put the hard drive in another laptop, installed it from disk.Then put that hard drive into the original computer. I would liek to try your method just to see if it works. But now when I get past the partitioning and get to the part where it asks to set up a username and password. It lets me put a user name, host name, but it automatically skips past the password setup. So I had to log on as root in terminal and create a new user in order to log on. It might be a bug. Im not sure

---

