---
title: "Problem While booting/installing from USB"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by reedip on 2010-02-03
Hi,
First and foremost I hope every1 is in their good health.
My hard disk is going to crash(it failed to boot for some time now...I guess GOD is giving me time to back up before he Pulls the PLUG), meaning the boot sector would be gone too.
I bought a new hard disk, but was not able to create a Master Boot Record on it(lucky??).
The old hard disk has Windows XP SP2 Intsalled on it. Since I have been using Windows for some time now, I thought of using Unix(Ubuntu 9.10 Live). By the way, my CD Drive doesn't work
 I Tried using the Unetbootin (ver 377)manager to create a live USB.

The main obstacle comes up when I reboot.The PC boots up from the USB, but immediately after that shows the error
    "COULD NOT FIND KERNEL IMAGE:LINUX"
    "BOOT:"

I am using Ubuntu 9.10.
The syslinux.cfg file is as thus :

default vesamenu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel ubnkern
append initrd=ubninit file=/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel ubnkern
append initrd=ubninit

label ubnentry1
menu label oem=OEM install (for manufacturers)
kernel ubnkern
append initrd=ubninit oem=oem-config/enable=true

Could someone let me know WHY I CANNOT BOOT FROM UNETBOOTIN, or any other way to INSTALL UBUNTU on my HDD via USB(since the CD DRIVE is broken) ?
Awaiting your responses


(Also, I did not search on this forum regarding this issue(although I did it in the Ubuntu Documentation), since Unetbootin and XP have already eaten half of my brains, and my company requires the other half, so if some one sends a link to a previous answer , then that's fine.but a proper explanation would be just GREAT!)

---

### Post by darkod on 2010-02-03
Unetbootin replaces the main ubuntu menu with a menu of its own. I always enable the main ubuntu menu because it's better and has more options (like Try Ubuntu without chaging anything on your computer). Open the usb stick and do:

1. In the root folder rename syslinux.cfg to syslinux.old
2. In the folder isolinux find and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
3. Go back and rename the whole folder isolinux to syslinux

This should enable the main ubuntu menu. See if it works better.

---

### Post by reedip on 2010-02-03
I will get back to you on that as soon as possible!!! :)

---

### Post by reedip on 2010-02-04
Hi,
I did the following editing, but to no use....
Still the error:

Could not find Kernel Image :Linux
Boot:



It seems that the kernel is not visible to the menu.....
I found vmlinuz and initrd.gz in some of the folders.Should I link them up as my defualt initrd and kernel in the syslinux.cfg?

---

### Post by darkod on 2010-02-04
> **reedip said:**
> Hi,
I did the following editing, but to no use....
Still the error:

Could not find Kernel Image :Linux
Boot:



It seems that the kernel is not visible to the menu.....
I found vmlinuz and initrd.gz in some of the folders.Should I link them up as my defualt initrd and kernel in the syslinux.cfg?

I would suggest start from scratch and also be careful which options you use in unetbootin. First format the stick as FAT32 in windows. Then start unetbootin and use the Disk option I think it was called, specify the ISO, and in the bottom specify the stick letter in windows.
Then click on OK and let it finish. Ignore the question to reboot, just close unetbootin.
After that do the procedure to enable the ubuntu menu and it should be fine.
In case you are interested to check, vmlinuz and initrd should be in the casper folder after you create the stick with unetbootin.

---

### Post by SoFl W on 2010-02-04
I am joining this thread with a question about usb boot sticks.  Is there a way to access the stick after booting from it?  If I place files I want on the stick how do I access those once ubuntu boots from the usb drive?  I tried mnt, and mount directories but there was nothing there.

I want to access my bookmark.html file.

Did I read somewhere that you can write to the bootstick and retrieve files and settings?  If I could take my desktop Firefox settings (bookmarks, passwords, settings, addons) and import them to the stick when it boots each time that would help.

---

### Post by darkod on 2010-02-04
> **SoFl W said:**
> I am joining this thread with a question about usb boot sticks.  Is there a way to access the stick after booting from it?  If I place files I want on the stick how do I access those once ubuntu boots from the usb drive?  I tried mnt, and mount directories but there was nothing there.

I want to access my bookmark.html file.

Did I read somewhere that you can write to the bootstick and retrieve files and settings?  If I could take my desktop Firefox settings (bookmarks, passwords, settings, addons) and import them to the stick when it boots each time that would help.

If we are talking about a stick you used to boot the live desktop (and not a full installation of ubuntu running from a usb stick/hdd), then after the live desktop loads you should see the stick in Places. It might say like 2GB Filesystem, click on it and it will offer to mount it.
You should be able to open it that way and access any files you put there. Although I haven't tried that myself.

---

### Post by reedip on 2010-02-05
Did what you said darkod.....
But to no avail :(

I read the syslinux doc, [http://syslinux.zytor.com/wiki/index.php/SYSLINUX#What_is_SYSLINUX.3F](http://syslinux.zytor.com/wiki/index.php/SYSLINUX#What_is_SYSLINUX.3F)


I now understand (i think) why it always says Could not find disk image:Linux.
But still not able to figure out HOW to fix the cfg file???

---

### Post by reedip on 2010-02-05
The problem is, the Syslinux could not find the syslinux.cfg


COuld someone let me know where should I keep this file, for it to be visible??
I have tried it in the root directory of the USB , as well as in the syslinux directory.
the syslinux.cfg is ver 3.84, therefore I need to check the paths in text.cfg for the kernel and initrd.BOTH are Correct(/Casper/vmlinuz and /casper/initrd.lz)
I hve deleted the isolinux.cfg file from the syslinux directory(no differnce though)
I have tried the LiveUsb Creator as well(Lili ver 2.4) With the Same result.....Everything though, seems to be correct

And my motherboard can boot from the USB


If everything is in place, then why is the error too in place??    :( :( :(

---

### Post by javierfh on 2010-05-19
hi did you ever got an answer for that.
im in similar situation as you are.
my live cd(in fact two that i recorded in two different computers) wont work. my motherboard seems not to boot from usb..so im hoping i can fix it with unetbootin, but i get the missing kernel error.

Any ideas how to fix that?

javier

---

### Post by Jessfarnsworth on 2013-03-31
> **darkod said:**
> Unetbootin replaces the main ubuntu menu with a menu of its own. I always enable the main ubuntu menu because it's better and has more options (like Try Ubuntu without chaging anything on your computer). Open the usb stick and do:

1. In the root folder rename syslinux.cfg to syslinux.old
2. In the folder isolinux find and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
3. Go back and rename the whole folder isolinux to syslinux

This should enable the main ubuntu menu. See if it works better.

I had a similar problem, only I was getting the unetbootin menu with the word default, and it would say booting in 10 seconds and count down, and start over.  I tried this, that gave me some clue, aqlthough I was trying to run a linimint package.  I took the umuntu 12.1 iso image and extracted the casper and isolinux folders, renamed, and I am on the way.  Now I am unpacking the entire ISO without replacing existing files.....hopefully this will work.  (I did have it up briefly earlier, but not installed.  If this works, Ill do a full install this morning.  This has been an unsolable problem for over 4 months, so this is great.

---

### Post by oldos2er on 2013-03-31
Old thread closed.

---

