---
title: "Stall on (initramfs) -"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by maldonna on 2007-12-13
Please excuse my ignorance on this but I`m completely new to Ubuntu. I have a computer which a friend gave me that had a fried hard drive. It had been running Win XP Pro prior to its demise. I wanted to play around with Ubuntu so have installed a new hard drive and fired it up. I checked out my install  disc on my main computer and found it to be OK. When I try to install on the computer with the new hard drive I can get through the Ubuntu flashing bars and a "Busy Box"  line, a "Enter `help` " line, then a line (inittramfs) with the flashing (-)  waiting for an order. If I enter "help" I get a list of orders and then the (initramfs)- again waiting for an order. What do I do to get past this to continue installation?

---

### Post by Pumalite on 2007-12-13
Post the entire error message.

---

### Post by maldonna on 2007-12-13
After the sliding bar stops this is what appears: 

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)

Enter `help` for a list of built-in commands.

(initramfls)_ (Dash is flashing

I just found out that after sittting for some time that last line now shows:
(initramfls) ide_media (2398): main: unable to read from `/proc/ide/ideo/hda/media
`

Then if I hit enter the next line again reads:
(initramfls) with the flashing _
This has remained for ten minutes with no change

---

### Post by Pumalite on 2007-12-13
Try this first:
At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

You will now boot into the LiveCD normally.(cross your fingers)

---

### Post by Pumalite on 2007-12-14
If the above did not work; try the Alternate CD

---

### Post by maldonna on 2007-12-14
That didn`t work. What is the Alternate CD and where do I get it?

---

### Post by maldonna on 2007-12-14
I found it. Please ignore last post.

---

### Post by maldonna on 2007-12-14
I am trying to install now with the alternate CD. I`v tried twice now with the same results. I get to the window "Detecting hardware to find CD ROM drives". It stalls at 86% and reads "Loading module`ide-floppy` for `Linux IDE floppy`...". What can I try next?

---

### Post by Pumalite on 2007-12-14
If you have a floppy drive; stick a floppy in there.

---

### Post by maldonna on 2007-12-14
Tried to no avail. Also tried a USB floppy drive with and without a floppy installed. Nothing worked. Can that step be bypassed somehow?

---

### Post by Pumalite on 2007-12-14
Could you post your specs please?

---

### Post by maldonna on 2007-12-16
I`m not sure of specs as I was given the computer without any accompanying info. This is what appears on the startup splash screen:
AGP8K
Gb 100mbps
      LAN
DDR400
(PC3200)
A7V8X
Serial ATA 

I replaced the defective hard drive with an 80 GB Western Digital hard drive. 

I do think the floppy drive may be defective. Removing it only produces a verbal notification "No floppy drive detected" Everything else remains the same.

---

### Post by maldonna on 2007-12-16
That should be 1000 Mbps

---

### Post by Pumalite on 2007-12-16
Just a side note -- if you do this, make sure the boot partition is at least 50MB or the install will error at grub setup
When the install is complete do not reboot -- stay in the LiveCD
Open a terminal (Applications->Accessories->Terminal)
You must now mount the installed partitions by typing the following (assuming the install was to /dev/hda1; otherwise replace '/dev/hda1' with the install partition) commands:

mkdir target
sudo mount /dev/hda1 target

If you also created a boot partition issue (replace /dev/hda2 with the boot partition) the command:
sudo mount /dev/hda2 target/boot

sudo chroot target

You will now be in a 'chroot' command prompt for your new ubuntu system (be careful here, you are editing with root access!)
You must edit the /etc/initramfs-tools/modules file; adding a line with the word: piix
You should do this with your favorite unix editor; or simply type the command:
echo piix >> /etc/initramfs-tools/modules
After modifying the file you must update the system with the command
update-initramfs -u
When complete, type 'exit' to exit the chroot env; you can now close the Terminal and reset your system.

Now when you boot you will be in your new shinny Ubuntu system!

---

### Post by Recovering from MS. on 2007-12-17
You could try disabling the floppy in the bios, not just the drive, you'll want to disable the floppy controller... hope it helps...

---

### Post by maldonna on 2007-12-17
Since my problems seem to be related to the floppy drive I`ve ordered a new one. I`ll wait until it arrives to do any further work on this. I`ll try again after the installation of the new floppy drive and see if I can get any further. Thanks for your assistance. I`ll be back later.

---

### Post by maldonna on 2007-12-29
After breaking for Christmas I`m now back to my project. I`ve installed a new floppy disk drive but come up to the same point as before. I,e., with the regular install disk the stall is after command  ":unable to read from `/ proc/ide//ideo/hda/media" and with the text install disk the install bar stalls at 86% saying "Loading module `ide-floppy` for `Linux IDE floppy`..." The problem with following the last suggestions is that the install is never completed. This computer has a brand new drive with no partitions installed. I wanted to establish a Microsoft and Mac  free computer. Any more suggestions on how to continue will be appreciated.

---

### Post by Pumalite on 2007-12-29
Format your drive with Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn the image to a disk and boot from it. Tell me what you see.

---

### Post by maldonna on 2007-12-30
I`ll just show the last few lines (there are many).
"The graphical environmental configuration should have been done automatically. Unfortunately it did not since you are back to the bash!
So run Forcevideo script and you will be asked for video driver and resolution.
Vesa driver should always work, and 1024x768 resolution too.
If needed you can kill X by using ctrl+alt+backspace combination !
gparted ~ * - (dash is flashing for prompt)   "
 Hitting enter repeats :
gparted ~ * -
The text is in multiple colors if that means anything.

---

### Post by Pumalite on 2007-12-30
You probably have several options in the menu. Try all of them. One is bound to work.

---

### Post by maldonna on 2007-12-31
Well, I guess I`m on but I`m unable to do anything with what`s here. I essentially have a yellow desk top with six icons and a GParted toolbar. When it started up a GParted window opened. This is apparently where I can partition the hard drive. Since I don`t want any partitions I just clicked out of that and am left with the yellow desktop with the icons and the GParted toolbar. Some of the icons are semifunctional but do nothing that I want to do - except for the Exit icon which doesn`t work at all. (I can`t shut down from there. I have to hard boot to turn off.) Also I can only boot from the CD. What I really wanted was to have a Linux operating system installed on my hard drive. Everything here seems to assume that Linux is going to be a secondary OS and the hard drive needs to be partitioned to accommodate this setup. Is what I want to do possible, i.e. to have a computer set up with only a Linux (Ubuntu) OS  installed on the hard drive?

---

### Post by Pumalite on 2007-12-31
If you want Ubuntu alone, once in Gparted, delete everything in your hard drive, make a new large partition of your whole drive partition ext3 if you want (you can choose any format, because the Ubuntu installer is going to reformat anyway), and install Ubuntu.

---

### Post by maldonna on 2007-12-31
The hard drive is new and I assume a blank slate to install Ubuntu on. I`ve been trying several types of Linux to install (Freespire and the various Ubuntus). They all stalll out even after running GParted. That`s the whole problem, I can`t  install Ubuntu on my new hard drive. Are there other Linux programs that you would recommend that do not  incorporate Ubuntu? (Or is that heresy :-) )

---

### Post by Pumalite on 2007-12-31
I have the suspicion that your hard drive is not formatted. (??)

---

### Post by maldonna on 2007-12-31
I see that I`ve posted no thanks. I certainly appreciate your efforts on my behalf. I  may not be a candidate for using Ubuntu as I probably am not as computer literate as I should be to do this. I`ve been reading various articles on Linux and was lead to believe that it was nearly ready for general use. I probably need to hang it up for awhile and see if something comes along later. Thanks again for your help.

---

### Post by Pumalite on 2007-12-31
Sorry to hear that. Here are some links for future use:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)
[http://www.geekgirls.com/](http://www.geekgirls.com/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)

---

