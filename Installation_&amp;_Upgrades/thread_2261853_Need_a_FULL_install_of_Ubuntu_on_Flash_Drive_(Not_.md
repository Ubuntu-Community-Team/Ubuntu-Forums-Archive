---
title: "Need a FULL install of Ubuntu on Flash Drive (Not Live CD, Not Persistence)"
date: 2015-01-21
forum: Installation &amp; Upgrades
---

### Post by vas2 on 2015-01-21
I don't care if Ubuntu is gonna run a little slower on a flash drive or if it is going to somehow damage the flash drive through writing a lot.  I need a full total install of Ubuntu on a flash drive, and every time I try to look up how to do this, everyone says use persistence, which I DO NOT WANT.  My net is in extremely severe condition, and I only have 2 days to figure this out before I have to send my laptop away for 4 weeks to get repaired because Asus blows at repairing things fast.  4 weeks to replace a damaged fan.  Good god they are slow.

I'd like to be able to put Ubuntu onto a 64GB flash drive, a full install.  No persistence file, no Live CD mode.  I would search the forum more, but at this point I am getting 80% page failures when I try to search.  It'll likely even take me 10 tries to post this thread, hopefully it'll go through first try though.  I really need help with this as quickly as possible.  Every time I tried to get Ubuntu to install from the Live CD mode to the flash drive, it refused.  :/

---

### Post by oldfred on 2015-01-21
It is a standard Something Else install. The main reason for Something Else is that is the only option that lets you control which drive the boot loader is installed into.

Is system BIOS or UEFI?

 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

I installed to my 16GB flash drive with only 8GB for / (root) and 8 GB for data. But that is for emergency boot with my laptop.
With my 32GB flash drive it made it gpt partitioned and added both an efi partition for UEFI boot and a bios_grub partition for BIOS boot.  Again about 16GB for / and rest for data. No swap as I have a fair amount of RAM.

 Flash drive to boot in UEFI or BIOS - sudodus
Note that there may be issues, if you try booting both ways. But shows install to flash drive.
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/](http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/)
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)

You do want to change a few settings to reduce writes. You want to use a  USB3 flash drive even if you have only USB2 ports. And some flash drives are faster than others.
 pendrive speed tests USB2 & USB3 various brands - user sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)
Includes links to speed tests and lists some that do not work well.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

### Post by vas2 on 2015-01-21
I don't have any USB 3.0 drives and they are way too expensive for me to get.  I assume my system is BOIS, but then, this flash drive will need to work in any computer I go to, not just the one I install Linux with.  If Persistence wasn't maxed at 4GB, I wouldn't mind it so much, I want at least 16GB persistence with the other 47GB (1GB for OS) for data like steam games, if i do the live CD thing, but the tool I used (UUI) can't do more than 4GB persistence.

I'm only considering Live CD in case you can't make a full linux install that is also portable and works on any machine.  However, if I do Live CD mode, if we can figure out how to get more than 4GB Persist, how do I change the download directory for all apps and such that install?  Would be nice if I could do the Live CD thing and not need more than 4GB persist, but I haven't found a way to make apps like Skype install to the other partition of the flash drive.

I'm not much of a Linux user.  I've only ever used Ubuntu to repair my laptop and recover data and as something to use while my HDD was dead for 2 weeks.  So I really don't know that much about it, the only linux related command I learned is Sudo apt-get install blah.  Which I really hate.  I prefer double clicking an exe file like I do in Windows to install something and having the wizard let me choose where to install and such.

---

### Post by sudodus on 2015-01-21
A big +1 to oldfred's advice.

I might add, that you can make it easier by removing the internal drive and have only the 64 GB pendrive (the target drive) and a DVD disk or USB pendrive with the Ubuntu desktop installer system. This way you can probably use the default method to install into the whole drive. Without an internal drive, the target drive should be selected for the partitions as well as for the bootloader.

---

### Post by sudodus on 2015-01-21
> **vas2 said:**
> I don't have any USB 3.0 drives and they are way too expensive for me to get.  I assume my system is BOIS, but then, this flash drive will need to work in any computer I go to, not just the one I install Linux with.  If Persistence wasn't maxed at 4GB, I wouldn't mind it so much, I want at least 16GB persistence with the other 47GB (1GB for OS) for data like steam games, if i do the live CD thing, but the tool I used (UUI) can't do more than 4GB persistence.

Avoid proprietary drivers (typical for graphics and or wifi) in order to keep the system portable to other computers.

If you use a partition with the label casper-rw (instead of a file with the name casper-rw) you will have persistence that way. And then you can use most of the drive for that partition :-)
> 
I'm only considering Live CD in case you can't make a full linux install that is also portable and works on any machine.  However, if I do Live CD mode, if we can figure out how to get more than 4GB Persist, how do I change the download directory for all apps and such that install?  Would be nice if I could do the Live CD thing and not need more than 4GB persist, but I haven't found a way to make apps like Skype install to the other partition of the flash drive.

See these links, which discuss persistence
[One pendrive for all PC (Intel/AMD) computers]("http://ubuntuforums.org/showthread.php?t=2259682")[URL="http://ubuntuforums.org/showthread.php?t=2260697"]
Multiboot flash drive with second partition[/URL]
> 

I'm not much of a Linux user.  I've only ever used Ubuntu to repair my laptop and recover data and as something to use while my HDD was dead for 2 weeks.  So I really don't know that much about it, the only linux related command I learned is Sudo apt-get install blah.  Which I really hate.  I prefer double clicking an exe file like I do in Windows to install something and having the wizard let me choose where to install and such.

Sorry, you will need a few command lines here, but we are here to help you :-)

*Edit*: I'm sorry but I fear that gaming will be too slow with a USB 2 pendrive unless you have so much RAM, that you can run from a ram-disk.

---

### Post by yancek on 2015-01-21
> this flash drive will need to work in any computer I go to, not just the one I install Linux with

If you don't install proprietary drivers, it will probably work on different computers.  I've done this and tested it and it worked but only tried it on a few different computers.

You're using UUI which is windows software and if I remember correctly, it requires FAT32 filesystems on which to create the bootable flash drive.  The 4GB limit is only on FAT32 formatted systems and doesn't apply if you use a Linux filesystem.  Of course, you can't create a Linux filesystem from windows.

If you create a persistent partition with a Linux filesystem, you don't need to change the Downloads directory.

You don't need to use a terminal to install software, that's what the Software Center does.
More information on creating persistence with Ubuntu at the site below:

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

---

### Post by vas2 on 2015-01-21
> **sudodus said:**
> *Edit*: I'm sorry but I fear that gaming will be too slow with a USB 2 pendrive unless you have so much RAM, that you can run from a ram-disk.

I don't need to worry about that.  I was able to run Kerbal Space Program from my USB 2.0 drive perfectly fine with Ubuntu before.  However, my laptop won't be around, and I'll have a machine so crappy, it couldn't possibly load any game at all, not even likely Pong.  >.>

Another funny thing I've noticed, is you can't install Linux from Windows.  Every tutorial I've seen so far, says to get linux onto a DVD or flash drive, then run it, then install it to the drive you want.  :P

As for the tips given, I believe I might try Live CD again, since i was given some suggestions on how to make a persist partition instead of the previous thing I was stuck with.  I am trying to keep this as simple as possible so I don't end up wasting several hours trying to get a portable full Linux install and end up having it not work right.  I only need it for the time that my laptop is gone after all.  I can't go 4 weeks without a computer.  :/  I hate that they can't just mail me a new fan and let me install it myself.

---

### Post by sudodus on 2015-01-21
It depends what you mean by installing. When you make a DVD or USB boot drive you are actually installing linux (to that drive) with for example Unetbootin. In a slightly different way you can flash a portable installed system to a flash drive or even to an internal hard disk drive or solid state drive using Win32 Disk Imager from Windows.

See these links for more details

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)[URL="https://wiki.ubuntu.com/Win32DiskImager/iso2usb"]
[/URL]
*Edit*: For example this 'installed system' is installed from a compressed image file:

[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

-o-

Anyway, it seems like you go for a persistent live system with a casper-rw partition. It should work well for you. Good luck :-)

---

### Post by vas2 on 2015-01-22
I tried the casper-rw partition method, it failed.  :/  Not sure why.  Unetbootin annoys me with it's big boot screen and delaying me from getting into the system.  I mean it's nice to skip the "try ubuntu" screen but it's also slower.  However, once I got in, I tried fiddling with some settings, added a program, then shut down properly, then tried loading it up again and all my settings were reverted.  This is what I did to the drive before loading it up with the new partition.
[https://www.dropbox.com/s/2utb46p6yyg33ex/Screenshot%202015-01-21%2020.05.42.png](https://www.dropbox.com/s/2utb46p6yyg33ex/Screenshot%202015-01-21%2020.05.42.png)
And then my flash drive died, the one I was running Ubuntu off of that is.  A 4GB Sandisk that is extremely old.  I've never before seen a hard drive die.  Kind of odd.  it loads up in Windows disk manager, shows up as healthy, but doesn't show up under my computer, the light flashes at a slow pace for a while on it, then starts flashing wildly several minutes later and turns to either black unpartitioned space or shows up as no media on that same disk manager.  I assume that means it is a dead one, right?  Not sure how else to detect what's wrong with it.

---

### Post by sudodus on 2015-01-22
> **vas2 said:**
> I tried the casper-rw partition method, it failed.  :/  Not sure why. 
- Did you also add the boot option persistent?

- Did you click the green tick icon to really create the casper-rw partition?
>  Unetbootin annoys me with it's big boot screen and delaying me from getting into the system.  I mean it's nice to skip the "try ubuntu" screen but it's also slower.  However, once I got in, I tried fiddling with some settings, added a program, then shut down properly, then tried loading it up again and all my settings were reverted.  This is what I did to the drive before loading it up with the new partition.
[https://www.dropbox.com/s/2utb46p6yyg33ex/Screenshot%202015-01-21%2020.05.42.png](https://www.dropbox.com/s/2utb46p6yyg33ex/Screenshot%202015-01-21%2020.05.42.png)
And then my flash drive died, the one I was running Ubuntu off of that is.  A 4GB Sandisk that is extremely old.  I've never before seen a hard drive die.  Kind of odd.  it loads up in Windows disk manager, shows up as healthy, but doesn't show up under my computer, the light flashes at a slow pace for a while on it, then starts flashing wildly several minutes later and turns to either black unpartitioned space or shows up as no media on that same disk manager.  I assume that means it is a dead one, right?  Not sure how else to detect what's wrong with it.
[URL="http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297"]
See this link (and links from it) concerning pendrive lifetime and ways keep it alive[/URL]

---

### Post by vas2 on 2015-01-28
Well, I delayed my mailing back the machine for a while, so now I have more time to look into getting Linux set up properly on a flash drive.  However, I have to get a new flash drive and some high speed net access so I can have someone help me set it up via teamviewer.  Too difficult to figure all this out myself.  I at least figured out how to get Ubuntu to run in VirtualBox so now I don't have to use two computers to do it.

---

### Post by sudodus on 2015-01-28
VirtualBox has many advantages, but it cannot boot from USB. It boots directly from the iso file, which is enough in most cases.

A virtual machine made with KVM + VirtManager can boot from USB (but maybe it is a little bit harder to get started using it).

---

### Post by MAFoElffen on 2015-01-28
One issue I can see that may or may not be valid for this... It depends on the device.

Most hand-help devices will boot from a memory card. But these days, since memory cards have been around for a while, laptops, tablets and convertibles have a card reader-- but their BIOS will not boot from the internal card reader. They have them there to "expand" storage and to add a compatible interface to. (There are ways to hack around that, but not suggested for the average user.)

I have installed to an external card reader as it shows up to most devices just as usb external mass storage devices.

So my two questions to the OP ares: 
-What device are trying to install this to?
-If an internal card reader, does the device's BIOS support booting from an internal card reader?

Edit-- (I don't know if I should mention this.) On VirtualBox, VMWare player, etc... you can store your Guest virtual disks to a user defined area they have user-right permissions to... so he can store a virtual disk logically where-ever. The VM Guest XML define file ties that all together. But they vary on virtual USB appliance support after that VM is booted. Is "possible," but does not "always" turn out well.

---

### Post by vas2 on 2015-01-29
Oh, I'm using Virtual Box and I got it to boot from Ubuntu off a flash drive perfectly fine.  Took a while to get the partitions right and get persistence to work off a partition but I finally did it.

And the flash drive I'm complaining about that is broken, is a 4GB SanDisk that died when it either ran out of writes or the laptop I was using it on overheated and did something bad to the drive at the same time.  Not really sure.  Nothing seems to be able to load it, I might have to load it into a machine that is already on Ubuntu, rather than running it in a virtual box.  Can't get VB to mount the device to Ubuntu because Windows won't stop poking the dead hardware when I plug it in so it's constantly busy.

Anyway, I managed to get Ubuntu running and such.
[https://www.dropbox.com/s/wo2vhoh1oedieoq/Screenshot%202015-01-29%2001.54.49.png](https://www.dropbox.com/s/wo2vhoh1oedieoq/Screenshot%202015-01-29%2001.54.49.png)
[https://www.dropbox.com/s/abvsxup8efvsdf1/Screenshot%202015-01-29%2001.55.15.png](https://www.dropbox.com/s/abvsxup8efvsdf1/Screenshot%202015-01-29%2001.55.15.png)

Now I just wish I could get rid of that obnoxious install ubuntu icon that keeps popping back up every time I start the system.  And need to figure out how to get sound when running it in Virtual Box.  Still also trying to figure out how to install missing dependencies for skype and teamviewer because the installs no longer work with Ubuntu 14 when they were made for Ubuntu 12.

---

