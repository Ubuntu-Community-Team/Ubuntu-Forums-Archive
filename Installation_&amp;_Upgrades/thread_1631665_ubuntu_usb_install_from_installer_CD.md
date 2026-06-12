---
title: "ubuntu usb install from installer CD"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by francois.e on 2010-11-26
[FONT=Arial]I just tried the [/FONT][FONT=Arial][SIZE=1]Method 1: Installing Ubuntu directly to USB drive from installer CD[/SIZE][/FONT] proposed in the hyerlink:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Modifying some cfg file on the usb so that the usb is able to boot has to be done once the system is installed on usb (in my case sdc1). 

Which file is to be modified? 

I can find my way in menu.lst but not in the cfg file of grub2.

When I start the system and select the usb key, I get with a menu from which I select the first choice:
Ubuntu ...

It then tries to boot, with a dash flickering for a while the the error message contains:

Gave up waiting for root device
-Boot args (...
... /dev/sdc1 does not exist.
Droping to a shell.



Some light would be appreciated. Thanks.

---

### Post by C.S.Cameron on 2010-11-27
The link you posted is a bit old I think:
Following is for 16GB pendrive using 10.10:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
(Optional partition for use on Windows machine)
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 4GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 6 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 8 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hybernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB, same size as RAM), Beginning and "Use as" = "swap area" then OK.
(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are woried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

### Post by wet-willy on 2010-11-27
Wow!
Two zig zag routes to achieving a simple task.

1: Boot Ubuntu 10.10 live CD, go to System/administration/startup disk creator.
It will have the CD as the installation source by default, you can browse over to an ISO on the drive if you have one to speed up the process, besides, reading off a hard drive is more accurate than a dirty optical drive.

2: Select your USB key's partition as the distination, select format if required, if there is more than 693MB space, you'll be prompted to move a slider to select the size of the persistence file as persistence will be selected by default. Try not to take all of the space, move the slider slightly back to leave what appears to be 100MB, (every installation I did that had no free space puked during updates, the only one that was seamless was the one I had 75MB free space).

3: Hit "create startup disk".

4: When completed, reboot into the USB and enjoy.

---

### Post by C.S.Cameron on 2010-11-27
> **wet-willy said:**
> Wow!
Two zig zag routes to achieving a simple task.

1: Boot Ubuntu 10.10 live CD, go to System/administration/startup disk creator.
It will have the CD as the installation source by default, you can browse over to an ISO on the drive if you have one to speed up the process, besides, reading off a hard drive is more accurate than a dirty optical drive.

2: Select your USB key's partition as the distination, select format if required, if there is more than 693MB space, you'll be prompted to move a slider to select the size of the persistence file as persistence will be selected by default. Try not to take all of the space, move the slider slightly back to leave what appears to be 100MB, (every installation I did that had no free space puked during updates, the only one that was seamless was the one I had 75MB free space).

3: Hit "create startup disk".

4: When completed, reboot into the USB and enjoy.

Correct me if I am wrong but I think francois.e is looking for a Full install, not a persistent one.

---

### Post by francois.e on 2010-11-27
I am looking for a full install, that is one that will boot directly into the x environment without the use of a password and that will permit the installation of additional software. I have a usb key of 8gig.

With Wet-willy solution, I imagine that I will have the equivalent of the iso on usb, that is that there will be a menu asking me to choose the language at each boot. Correct me if this is not the case or if there is a way to omit that menu by changing some file of some kind.

I wonder if unetbootin from windows would not be the simplest solution to achieve that goal.

---

### Post by wet-willy on 2010-11-27
> **C.S.Cameron said:**
> Correct me if I am wrong but I think francois.e is looking for a Full install, not a persistent one.

> I just tried the Method 1: Installing Ubuntu directly to USB drive from installer CD proposed in the hyerlink:
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)[COLOR="Red"]LiveUsbPendrivePersistent[/COLOR]

Modifying some cfg file on the usb so that the usb is able to boot has to be done once the system is installed on usb (in my case sdc1).

Which file is to be modified? 
The quote above tells me his interested in a persistent live install and is looking for answers to a couple questions.

As for getting rid of the "start Ubuntu, install Ubuntu" menu, one would probably have to modify grub configuration within the ISO before it is used as the image.
 
Keep in mind, a hard drive install may configure certain aspects of the operating system to revolve around specific hardware, where as using Ubuntu in a live environment assures you'll be able to use it dynamically in pretty much any computer supporting USB booting.

---

### Post by Herman on 2010-11-27
> Keep in mind, a hard drive install may configure certain aspects of the  operating system to revolve around specific hardware, where as using  Ubuntu in a live environment assures you'll be able to use it  dynamically in pretty much any computer supporting USB booting.:smile: The hard disk drive type of 'real Ubuntu' installation is just as adaptable as the Live CD 'Persistence' type to all kinds of different hardware. Try it out and see for yourself. 

> Modifying some cfg file on the usb so that the usb is able to boot has  to be done once the system is installed on usb (in my case sdc1). 
Which file is to be modified? That old how-to is obviously ancient history, and was hasn't been updated way back when we still used Legacy GRUB. I think you should ignore it.

C.S.Cameron's installation type of installation in post #2 uses GRUB2 as the boot loader, so it makes the perfect utility/boot disk as well as a portable Ubuntu installation you can carry around with you in your pocket and use in almost any PC.
Since it's a normal Ubuntu installation, you're able to install and software and all updates.
You have the option of installing it with full file encryption for your security if you use the 'Alternate Installation CD', or at least with an encrypted /home in case you loose it and a stranger picks it up. No encryption is simpler and easier and is okay for some people, it's easier to back up your files from.

wet-willy's kind of USB installation in post #3 contains the Ubuntu installer and can be used for installing Ubuntu in almost any computer, but it boots with syslinux and is not quite as useful as a utility disc at least as far as the boot loader is concerned. 
Although it's better than a Live CD because of its capability to save files and added software over a reboot, I don't think it is capable of receiving a kernel update, so it's best not to allow it to receive updates. You also may run into difficulties if you try to follow how-tos with it from the tips and tricks section of Ubuntu web forums or other sites on the internet. The filepaths and files it contains are not the same as a normal installation so you can't just cut and paste commands and it can't do everything a regular install can do.

If you have more than one USB, you might consider making one of each since they're both very useful. :)

---

### Post by C.S.Cameron on 2010-11-27
> I wonder if unetbootin from windows would not be the simplest solution to achieve that goal.

Unetbootin is indeed a simple method of installing to USB however it is not persistent out of the box and it has a startup menu that asks if you want to run Ubuntu or install it. It does not have the language stuff though.

At the end of the post I will tell how to add persistence.

Another option is Universal from pendrivelinux.com. It will install from Windows and has a persistence option.

Unetbootin persistence:

This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1GB FAT32 partition, (on the left side of the bar).
Created a 2GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext2 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Windows, started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, booted thumbdrive.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.

---

### Post by francois.e on 2010-12-10
Sorry for taking so much time to come back.

There are some differences in the setup that I did and the one C.S.Cameron did proposed. Here they are:
1) I work with a 8gig usb key
2) I prefer having the the root and the home on the same partition
3) I did used a swap partition of 500meg
4) I have a laptop, so I do not want to unplug the hdd

So:
1) I have as a first partition a fat32 window partition of 1.54 gig (sdb1)
2) I have a second partition ext2 of 5.5 gig  of on which ubuntu is installed (sdb2)
3) The third partition is linux-swap of 0.558 gig.

I missed the point for the installation of grub on sdb. How do I get the installation of grub on sdb, now that everything is installed on the usb key?

Thanks.

---

### Post by C.S.Cameron on 2010-12-10
> **francois.e said:**
> Sorry for taking so much time to come back.

There are some differences in the setup that I did and the one C.S.Cameron did proposed. Here they are:
1) I work with a 8gig usb key
2) I prefer having the the root and the home on the same partition
3) I did used a swap partition of 500meg
4) I have a laptop, so I do not want to unplug the hdd

So:
1) I have as a first partition a fat32 window partition of 1.54 gig (sdb1)
2) I have a second partition ext2 of 5.5 gig  of on which ubuntu is installed (sdb2)
3) The third partition is linux-swap of 0.558 gig.

I missed the point for the installation of grub on sdb. How do I get the installation of grub on sdb, now that everything is installed on the usb key?

Thanks.
> 
(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.


If you are able to boot the flash drive an update-grub might work.
If not there are lots of posts in the forums explaining how to install grub from the Live CD.
It should be installed to sdb not sdb1, (if sdb is your flash drive.

---

### Post by efflandt on 2010-12-10
If installing to USB, you should select the manual partitioning to partition or select partitions you already set up using gparted.  Then at the bottom of that screen, select where to put grub (on the USB mbr without any partition number).

If you accidentally installed grub to your main drive mbr, you can grub-install to the USB drive per "SIMPLEST - Copy GRUB 2 Files from the LiveCD" way down on [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Then you need to figure out how to fix grub on the mbr of your main internal drive depending upon whether you have Linux on that drive or need to restore it to standard Windows mbr.

BTW which Ubuntu?  I recently had a problem with Kubuntu natty (11.04 development) when the kernel parameter line specified root=/dev/sdc1 instead of a UUID, but sometimes the USB was sdb on my laptop or sdc or sdg on my desktop (depending whether it landed before or after my multi-card reader), and switching to a UUID did not work.  But they fixed that in a Kubuntu natty update, so root=<UUID> works now.

---

### Post by francois.e on 2010-12-11
I am working with ubuntu (gnome) 10.10 maverick.

My question is:

Given that everything is installed, except grub, is it possible to install grub only from ubuntu, without reinstalling the rest?

---

### Post by C.S.Cameron on 2010-12-11
> **francois.e said:**
> I am working with ubuntu (gnome) 10.10 maverick.

My question is:

Given that everything is installed, except grub, is it possible to install grub only from ubuntu, without reinstalling the rest?

Check out this:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by francois.e on 2010-12-13
Many thanks, I am kind of busy right now. But I will for sure try the procedure that you graciously provided.

---

### Post by wet-willy on 2010-12-19
Something to think about:
USB flash drives have a limited 'write' life cycle. If you install Ubuntu onto a USB flash in the same configuration as a hard drive install, the /temp directory will be on the flash rather than in RAM as in a live configuration. Which of course wears out the flash drive prematurally.
Now...
Flash drives are kind of like "a dime a dozen", so...that may seem to not be an issue for some.
But ultimately, a flash drive that hangs where the "chaplet" traditionally hangs is used for data transfer between systems. 
My idea of a nicely configured 8GB USB flash drive has a 5GB NTFS partition marked as the first partition so it's the only one that shows up when plugged into a Windows box, where I can "transfer data".
I also have a 1GB partition allocated high containing my live "read only" Debian image, in between these two partitions is partition #3 which is only 1+GB in size formatted ext4 labeled home-rw, (the persistance partition).

Now...
when an image of Ubuntu live is in that second partition, it don't take long to use up the persistance area (partition #3), when applying updates, and I did update the kernel twice on my live Ubuntu image successfully.

The best configuration I've come up with is to build my own Debian live USB-HDD image with the looks, applications, and settings I want, reducing my need for the persistance angle. My live image is read only, prolonging the life of my flash drive, I set it to boot in single user mode so nobody knows what the **** I'm doing when using my live Debian to recover their system at no less than $300.00 an hour. 
Booting in --persistence mode is rare as the OS is pre-configured to suit my needs and is booted live without persistance over 90 percent of the time.
And it boots so fast, the Ubuntu CD image booting thing is akin to walking a caveman's footsteps compared to booting a Debian Live.
All this is done by installing/using live-build, which is also available in Ubuntu repositories, which means.................
You can build your own customized "live" Ubuntu "read-only" flash drive friendly, "perfectly designed OS".

---

