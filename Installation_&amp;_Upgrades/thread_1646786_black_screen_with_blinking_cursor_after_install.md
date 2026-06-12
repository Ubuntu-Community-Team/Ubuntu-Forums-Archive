---
title: "black screen with blinking cursor after install"
date: 2010-12-16
forum: Installation &amp; Upgrades
---

### Post by cdhauzie on 2010-12-16
I have an Acer Aspire One AOA110 that came with Windows XP. 
 
I created a usb flash drive install for Ubuntu 10.10 netbook edition and went through the install process (wiped disk clean, not a dual boot with WINXP). 
 
Before install, I was able to run Ubunut from the usb key with no problems. 
 
At the end of the install, it told me I needed to restart, so I clicked the "restart" button and the removed the usb drive. Nothing happened and it never restarted and just completley hung for about 20 minutes. I manually shut down the computer by holding the power for 10 seconds and then rebooted the machine. Now all I get after the "acer bios" screen is a black screen with a blinking cursor. If I press any buttons, the computer beeps at me.
 
Anyone have experience with this?

---

### Post by Paul A C on 2010-12-16
I have experienced similar problems a couple of times.
The first thing to try is see if you can boot off the USB in Live distro mode.  I suspect you will be able to.  If that is the case then it could be the disk partitioning  that has gone wrong.  I had the same happen to me today.  It has happened to me a couple of times when re-using old hard disks.

I fixed mine like this:-

I booted from the floppy drive with DOS, and ran FDISK /MBR.

Then I deleted all partitions using fdisk
Then I re-installed Ubuntu without any problems.

Are you able to get hold of a bootable DOS media?  If not, it should be possible to FDISK using a windows install CD I think.

Hope this may be of some help

Paul

---

### Post by sikander3786 on 2010-12-16
Welcome to the forums :-)

Press and hold down Shift key from Bios screen until you see the Grub menu. Highlighting the first entry there, press 'e' to edit it. Navigate to words "quiet splash", delete them and type "nomodeset" in their place (without quotes). Press Ctrl + X to continue boot. Can you see the desktop now?

If not, or if you can't even find the Grub menu by pressing Shift key, boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us what we need to know about your setup ;-)

While posting, click the # icon in post menu and paste your text in between the generated code tags.

And also let us know which graphics card is there?

---

### Post by ac7nj on 2010-12-16
> **cdhauzie said:**
> I have an Acer Aspire One AOA110 that came with Windows XP. 
 
I created a usb flash drive install for Ubuntu 10.10 netbook edition and went through the install process (wiped disk clean, not a dual boot with WINXP). 
 
Before install, I was able to run Ubunut from the usb key with no problems. 
 
At the end of the install, it told me I needed to restart, so I clicked the "restart" button and the removed the usb drive. Nothing happened and it never restarted and just completley hung for about 20 minutes. I manually shut down the computer by holding the power for 10 seconds and then rebooted the machine. Now all I get after the "acer bios" screen is a black screen with a blinking cursor. If I press any buttons, the computer beeps at me.
 
Anyone have experience with this?

I had this same problem trying to upgrade from 10.04 LTS to 10.10 I never did get the live CD to load after that either. My solution was not a pretty one. Re installed 10.04 and lost all of my data (I should have backed up before trying to install the 10.10 my bad)
I thought I had it made because 10.10 worked from 10.04 as a live CD. My best guess is I had a hardware problem with the video.
Randy [email]ac7nj@arrl.net[/email]

---

### Post by revto on 2010-12-16
I have the same problem after up grading from 8.04 to 10.04. I tried the "nomodeset" idea but it doesnt seem to work for me. when ubuntu starts the grub menu I hit escape to enter the menu and then "e" to highlight and edit the kernall and delete the two words "quiet" and "splash" and enter "nomodeset" without quotes in its place, all works great to this point. at the top it says to hit tab to end the command and when I do this it gives me "Error 11 Unrecognized devise string" and if I do as suggested to hit ctrl-x, nothing happens and it doesn't reboot. If I hit escape it exits the kernall without saving.

I would love to give you my boot script info but cannot get it to work because I cannot figure out how to open a terminal in recovery mode in the BusyBox built in shell or how to switch to gnome. when I press ctrl-alt-f2, it gives me a flashing cursor in the top left and I cannot do anything but restart. 

Sorry to jump in here but I wanted to talk to people who know ubuntu as obviously I am still learning. Thanks for any help. Thomas

---

### Post by kansasnoob on 2010-12-16
> **revto said:**
> I have the same problem after up grading from 8.04 to 10.04. I tried the "nomodeset" idea but it doesnt seem to work for me. when ubuntu starts the grub menu I hit escape to enter the menu and then "e" to highlight and edit the kernall and delete the two words "quiet" and "splash" and enter "nomodeset" without quotes in its place, all works great to this point. at the top it says to hit tab to end the command and when I do this it gives me "Error 11 Unrecognized devise string" and if I do as suggested to hit ctrl-x, nothing happens and it doesn't reboot. If I hit escape it exits the kernall without saving.

I would love to give you my boot script info but cannot get it to work because I cannot figure out how to open a terminal in recovery mode in the BusyBox built in shell or how to switch to gnome. when I press ctrl-alt-f2, it gives me a flashing cursor in the top left and I cannot do anything but restart. 

Sorry to jump in here but I wanted to talk to people who know ubuntu as obviously I am still learning. Thanks for any help. Thomas

Your problem sounds a bit different than the OP's.

In your case I'm thinking it's a graphics problem so the first thing I'd try is selecting Recovery Mode from the grub menu, and once it completes you should see the following options:

resume
clean
dpkg
fsck
grub
netroot
root
xfix

I'd first try "xfix" and see if you can then get a working desktop.

Ultimately we may need to know the specific graphics chip info so if you can get to a desktop post the output of this command:

```
lspci | grep VGA
```

Do you have any Ubuntu or Linux Live CD's?

---

### Post by kansasnoob on 2010-12-16
> **sikander3786 said:**
> Welcome to the forums :-)

Press and hold down Shift key from Bios screen until you see the Grub menu. Highlighting the first entry there, press 'e' to edit it. Navigate to words "quiet splash", delete them and type "nomodeset" in their place (without quotes). Press Ctrl + X to continue boot. Can you see the desktop now?

If not, or if you can't even find the Grub menu by pressing Shift key, boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would tell us what we need to know about your setup ;-)

While posting, click the # icon in post menu and paste your text in between the generated code tags.

And also let us know which graphics card is there?

+1! We can't do much without seeing the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternative instructions:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by revto on 2010-12-16
Thank you for replying Kansasnoob,

When I go into the grub menu by hitting escape after bios, I have the option of 2 recovery modes and 2 generic modes and a memtest. When I choose the -32 generic or recovery or the -28 generic I get an attempted startup followed by a black screen then the monitor turns off. When I choose the -28 recovery it drops me into a BusyBox shell. 

Also when I try to find my graphics info it says "/bin/sh: lspci : not found" but I think this is because I am in a BusyBox shell. How do I get to a terminal? I tried ctrl-alt-f2 but it just goes to a black screen with a blinking cursor in the top left and I must restart.

Sorry but I am still new.

---

### Post by kansasnoob on 2010-12-16
> **revto said:**
> Thank you for replying Kansasnoob,

When I go into the grub menu by hitting escape after bios, I have the option of 2 recovery modes and 2 generic modes and a memtest. When I choose the -32 generic or recovery or the -28 generic I get an attempted startup followed by a black screen then the monitor turns off. When I choose the -28 recovery it drops me into a BusyBox shell. 

Also when I try to find my graphics info it says "/bin/sh: lspci : not found" but I think this is because I am in a BusyBox shell. How do I get to a terminal? I tried ctrl-alt-f2 but it just goes to a black screen with a blinking cursor in the top left and I must restart.

Sorry but I am still new.

I think you're going to need some Ubuntu or Linux Live CD to troubleshoot this.

---

### Post by kansasnoob on 2010-12-16
I think the kernel you should be booting is 2.6.35-22. If you don't show that then something went wrong in the upgrade so we would need to see the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

But you'll need some Live CD.

EDIT: Duh! I was thinking 10.10 instead of 10.04 sorry, the kernel should be 2.6.32-something.

---

### Post by revto on 2010-12-16
I have an original 8.04 disk and copies of 10.04 and 10.10 on disk but I  don't know if they are the "live disks". How do I use them if they are  and how do I get "live disks" if they are not the ones

---

### Post by sikander3786 on 2010-12-17
> **revto said:**
> I have an original 8.04 disk and copies of 10.04 and 10.10 on disk but I  don't know if they are the "live disks". How do I use them if they are  and how do I get "live disks" if they are not the ones
Every Ubuntu Desktop CD/USB is a Live Disc ;-)

Just boot from the disc and select the "Try without installing" mode.

---

### Post by cdhauzie on 2010-12-17
Well not sure what exactly fixed my problem but I was able to fix it. I did a couple things different ...
 
1. 
 
--> Created Win98 DOS usb bootable disk. 
--> Booted into DOS, ran FDISK and deleted all partitions on machine
--> FDISK /mbr as well for good measure
 
2.
 
When I re-installed Ubuntu 10.10 ... I kept the USB drive in the machine when it rebooted the first time.
 
So now I'm not sure if by removing the USB drive the first time I installed before rebooting caused the blank screen problem or if needing to fdisk caused the problem.

---

### Post by Paul A C on 2010-12-17
Glad this solution worked, it is what I did...but, after I got the Ubuntu updates, I got a Grub error next reboot.

It appears what is happening, is that the upgrades include a Kernal update, and the process tries to update GRUB to allow you to boot to the old kernal if the new one gives you problems.  However, for me at least this does not seem to go quite right, resulting in a Grub error.  If this happens after running updates, it is probably worth looking at the various forum threads about how to fix grub errors.
I would be interested to know if you get this error again after installing updates, or is it just me?

---

### Post by cdhauzie on 2010-12-17
Do I really need to install 196 updates? That seems excessive!!!

---

### Post by Paul A C on 2010-12-17
It is usually recommended to install all upgrades, for security and stability of the system.  However, since it appears to be the upgrade process that is 'breaking' Grub, it seems that the cure is worse than the disease!  There are certainly some Bugs that talk about the sort of problems we have seen here.  [https://bugs.launchpad.net/wubi/+bug/653134](https://bugs.launchpad.net/wubi/+bug/653134) although describing a 10.4 to 10.10 upgrade seems to describe similar problems, and suggests possible solutions.  However, this is not the sort of thing new users to Ubuntu want to have to deal with.

My gut feel at present is that if you have a working system, it may be best holding off upgrades for now.  See if anyone else comes up with any other suggestions.

**IF** I get the chance tomorrow, I may have yet another go at an install, including upgrades, but leaving out the kernal upgrade.  That would pretty well prove this is the underlying cause of the problem

---

### Post by simon willins on 2011-01-09
> **cdhauzie said:**
> I have an Acer Aspire One AOA110 that came with Windows XP. 
 
I created a usb flash drive install for Ubuntu 10.10 netbook edition and went through the install process (wiped disk clean, not a dual boot with WINXP). 
 
Before install, I was able to run Ubunut from the usb key with no problems. 
 
At the end of the install, it told me I needed to restart, so I clicked the "restart" button and the removed the usb drive. Nothing happened and it never restarted and just completley hung for about 20 minutes. I manually shut down the computer by holding the power for 10 seconds and then rebooted the machine. Now all I get after the "acer bios" screen is a black screen with a blinking cursor. If I press any buttons, the computer beeps at me.
 
Anyone have experience with this?
Hi,
    Had this problem exactly while trying to get rid of linpus lite in exchange for ubuntu10.10. didn't like netbook remix so installed the desktop version on it just fine. it ran from the  flash drive, but on install would go to blank screen and flashing cursor on restart.
 I tried it alongside linpus, and with a complet install over the whole drive, but same outcome.
 
then I copied the ISO image to a CD and ran it from a usb cd drive. it worked first time and no problems.
 
 hope this helps.

---

### Post by simon willins on 2011-01-09
I tried installing 10.10 beside and over linpus lite from usb iso image and with the same result, the flashing cursor and black screen.
 
then I tried installing from a usb cd drive with the iso disk in it and it worked fine first time, just as the live cd on the usb had before install.
 
hope this helps

---

### Post by Paul A C on 2011-01-09
All I can suggest is that you first try running Fdisk on your drive.  I found after the automatic update, Ubuntus's partitioner would not recognise the drive at all.

Thankfully Microsoft's FDisk did manage to clear all partition information on the disk, allowing Ubuntu to re-install.  I am sure there are other partitioners out there that would work too.

Just to re-state how I got a PC back from this sorry state:-

Went into Bios and set the first boot device to floppy drive.
Inserted DOS 6.2 boot floppy, (with utilities on it)
Ran FDisk /MBR This re-writes the Master Boot Record
Ran FDisk and removed all Non-Dos partitions
Now able to run Ubuntu installer again.

If you do not have a floppy drive, you will need to make something else the first boot device, perhaps CD/DVD.  If you do not have a Dos boot medium for that drive, you can use Windows 95 or windows 98.  You can force these to boot to DOS, and run FDISK for there.

I think you may be able to run Fdisk from Windows 2000/XP install CD also.

Hope this helps, let me know if you need further ideas, and let me know what drives you have and what bootable media.

Very frustrating that 10.10 seems to cause this issue with some setups at least, lets hope 11.4 fixes this!

---

