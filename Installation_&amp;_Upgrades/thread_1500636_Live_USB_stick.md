---
title: "Live USB stick"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by cpplinux on 2010-06-03
Anyone use Ubuntu 10.04 from a USB stick? I know the loading time would be longer than from the harddrive. But is it as fast after the system is up? Does the system write to USB drive frequently -- for caching/buffering etc -- so that it would wear out the USB drive quickly?

---

### Post by frostschutz on 2010-06-03
I have the 10.4 live cd on USB, boots faster than from CD and doesn't write at all (doesn't write on CD either does it). But of course you can't store any data this way. ;) I only use it for rescue purposes (and unfortunately it does not have smartctl installed by default which makes me oh so very sad). :(

If you're thinking of installing Ubuntu on USB, no problem, but do make backups. USB Sticks can fail like any other storage media. Also consider using ext2, or something that doesn't have to write a journal all the time.

---

### Post by cpplinux on 2010-06-03
> **frostschutz said:**
> But of course you can't store any data this way. 

Can I install applications or save personal preferences? Or it is like a live CD that one can change absolutely nothing.

---

### Post by howefield on 2010-06-03
> **cpplinux said:**
> Can I install applications or save personal preferences?

Yes, you can use it like it was installed on the hard drive, complete with your favourite applications and save data/settings to the stick.

Some sticks are better than others when it comes to life expectancy but sticks are so cheap these days, is it really a problem ?

I have been using a stick for about 18 months now and seems just as good as it was when it was new.

---

### Post by C.S.Cameron on 2010-06-03
There are several ways to run Ubuntu from a USB stick.
Full install is just like installing to an internal hard drive but runs a bit slower. 

Non-persistent disk image install, is like running off of the Live CD. Use the built in usb-creator or UNetbootin to make the bootable USB.

Persistent disk image installs will save changes and downloaded aplications. usb-creator will make a persistent install using a casper-rw file, max size of this file is 4GB. You can make a non-persistent install persistent by creating a casper-rw partition.

Bootable iso image, grub2 will boot some Live CD iso images. Some can be made persistent with a casper-rw partition.

Speed of these installs is about the same as the Full install to flash drive.

I understand that you can also make a flash drive install of Ubuntu that runs fully in RAM, (just like Puppy Linux). This should be much faster than running off hard disk.

I agree with howefield, It would take the average user many years to brick a flash drive running Ubuntu in normal use.

---

### Post by jimmers on 2010-06-03
Hi All,

I did a full install of Lucid to my 16 GB Kingston Data Traveller and it works good:-

Boot time from restart 1 minute 7 seconds.

I also installed the following Gimp, Inkscape, Scribus, Xsane, Firestarter, Vodafone Mobile Connect, Adobe Reader, Homebank, RedNoteBook, Task Coach, Gxine.K3B, K9 Copy, Kaffeine, Bitdefender, Ubuntu Tweak

This is above the apps normally installed, I have also installed various Fonts in OO0.
 
I only installed it, for when I go away for Weekends to friends, (To lazy to carry Laptop).

I still have 8.7GB free space to save anything I want.  I am using it now as I write this.

I hope this information will be of some help to others, obviously I cant guarantee that it will work for your system, but it works for me.

BTW I have disabled updates in Software Sources, after reading various other posts, regarding installing to usb.

Luck

---

### Post by C.S.Cameron on 2010-06-03
Jimmers: 
I don't see any need to disable updates on a full install, I've upgraded versions without any problem. One of the main reasons to do a full install is so that you can update, me thinks.

---

### Post by wilee-nilee on 2010-06-03
> **jimmers said:**
> Hi All,

I did a full install of Lucid to my 16 GB Kingston Data Traveller and it works good:-

Boot time from restart 1 minute 7 seconds.

I also installed the following Gimp, Inkscape, Scribus, Xsane, Firestarter, Vodafone Mobile Connect, Adobe Reader, Homebank, RedNoteBook, Task Coach, Gxine.K3B, K9 Copy, Kaffeine, Bitdefender, Ubuntu Tweak

This is above the apps normally installed, I have also installed various Fonts in OO0.
 
I only installed it, for when I go away for Weekends to friends, (To lazy to carry Laptop).

I still have 8.7GB free space to save anything I want.  I am using it now as I write this.

I hope this information will be of some help to others, obviously I cant guarantee that it will work for your system, but it works for me.

BTW I have disabled updates in Software Sources, after reading various other posts, regarding installing to usb.

Luck

I have the same thumb half lucid half maverick both full installs.

---

### Post by silvervein on 2010-06-03
I made my 8 gig USB drive with 9.10 and I even upgraded it to 10.04 no problems. Just leave some room for packages/updates and save some space for personal files.

---

### Post by cpplinux on 2010-06-04
Thanks to all.

What is the easiest way to do a full installation? I think it is not from menu System|Administration|Startup Disk Creator.

---

### Post by C.S.Cameron on 2010-06-05
Turn off and unplug the computer.
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu 10.04.
Fill in "Time Zone" and "Keyboard layout".
At "Prepare disk space" select "Specify partitions manually (advanced)".
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext4, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning, Ext4, and "Use as" = "swap area" then OK.
Click "Forward".
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Select Install.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

---

### Post by efflandt on 2010-06-05
For full install on USB, just make sure that you pay attention to the **Advanced** button in step 7 or 8, to put grub on the mbr of USB, instead of default to your main hard drive.  As long as you have enough room, you should not have a problem doing updates.  You might want to use tempfs for /tmp like the live iso does, it it just uses RAM for small tmp files.

However, if you put the live iso on USB, with persistent data, you can add programs, but should avoid doing updates, because initial boot is from the original (compressed) iso, before persistent data is mounted.  So things like kernel updates or other things during initial boot would not work.

---

### Post by cmommsen on 2010-06-06
> Turn off and unplug the computer.
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.

And how would I do this if the computer is a laptop...?

---

### Post by C.S.Cameron on 2010-06-06
With a laptop you would have to remove the HDD, on some laptops this is not too hard.

Some people suggest that after setting up the partitions selecting the advanced tab and making sure grub is installed to the flash drive.

If your laptop is running Windows I would suggest making sure you know where the install CD is in case you need to do a fixmbr from the recovery console if things go bad.

---

### Post by wilee-nilee on 2010-06-06
> **cmommsen said:**
> And how would I do this if the computer is a laptop...?

Removing or unplugging the HD is not needed unless you want to learn a method that is not always applicable. As another post suggested it is where grub goes that is important, check the advanced tab on the last install screen and make sure that grub is pointed at the mbr of the device your installing to.


If we show methods that you don't learn some key things like grub placement it is not a good way to help.

---

### Post by C.S.Cameron on 2010-06-06
> Removing or unplugging the HD is not needed unless you want to learn a method that is not always applicable.
wilee-nilee:
Have you tried this from a Windows only machine?
I've tried it four times and had to fixmbr each time.
It was a long time ago though.

---

### Post by wilee-nilee on 2010-06-06
> **C.S.Cameron said:**
> wilee-nilee:
Have you tried this from a Windows only machine?
I've tried it four times and had to fixmbr each time.
It was a long time ago though.

Yes, the biggest problem generally with a bootloader is not making sure they go to the right place to begin with. When you do a full install to a external device, grub defaults to the HD on the computer your doing it with, so I suspect that was what happened, if you check that advanced tab in the install, grub will go where you tell it to, unless there is a unknown bug. 

Sometimes people just can't remove the HD I can't on my netbook so I have to know whats going on to have a workable computer. I could remove it but I would have to tear it apart then put it together without the HD then tear it apart to put it back in. My netbook came with XP the first thing I did was shrink that and install Karmic with no problems.

---

### Post by oldfred on 2010-06-07
I have a 16GB flash but it has data and a unetbootin install. I plan on converting it to this:

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

I like the added encryption as flash drives do tend to get lost.

---

### Post by cpplinux on 2010-06-10
> **efflandt said:**
> However, if you put the live iso on USB, with persistent data, you can add programs, but should avoid doing updates, because initial boot is from the original (compressed) iso, before persistent data is mounted.  So things like kernel updates or other things during initial boot would not work.

I can understand kernel updates would not work. But would applications (such as Firefox) updates work?

---

### Post by spitnllama on 2010-06-11
i am having a bit of truble with the install of ubuntu from a flash  drive to my mac. i only have CD-R that have space of 700MB and the iso  of ubuntu is 733 plus. so iam using my 8G usb flash drive. the  instructions ([http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)) that  are for mac are vary clear but i am getting an error at step 3. every  time i try to conert the iso to a .dmg i get (Permission denied) and  thats were i am stuck.

---

### Post by spitnllama on 2010-06-11
i am having a bit of trouble with the install of ubuntu from a flash  drive to my mac. i only have CD-R that have space of 700MB and the iso  of ubuntu is 733 plus. so iam using my 8G usb flash drive. the  instructions ([http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)) that  are for mac are vary clear but i am getting an error at step 3. every  time i try to convert the iso to a .dmg i get (Permission denied) and  thats were i am stuck.

---

