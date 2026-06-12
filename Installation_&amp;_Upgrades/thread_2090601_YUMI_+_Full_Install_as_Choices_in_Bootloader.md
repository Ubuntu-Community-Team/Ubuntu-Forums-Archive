---
title: "YUMI + Full Install as Choices in Bootloader"
date: 2012-12-02
forum: Installation &amp; Upgrades
---

### Post by 1nxr0x on 2012-12-02
First of all I'm somewhat of a noob, but not a total noob, and then only when it comes to using Linux and not anything else computer related.

I have studied Linux from reading online articles, forums, and tutorials and such, I just haven't actually used it much at all yet, but I really want to now.

I'm very good at learning and following directions if they are good, properly descriptive, and detailed.

For me I've found the best way to learn, play with, and use Linux for now is from a bootable USB pen-drive.

I used YUMI to install Ubuntu, Mint, and a few others on my pen-drive. Now, from what I can tell, booting into and using a distro from YUMI has me in a "Live CD" mode, without persistence, at least with system changes. So what I've done is used Unetbootin to install Ubuntu on the drive with persistence set during the install to test it out there.

Here's my question:
When I boot from the drive now, I'm no longer getting the YUMI installed bootloader, but rather the standard bootloader installed with Ubuntu from Unetbootin. So I no longer have any of my YUMI installs coming up as boot options.

What I'd like to have is both my full Ubuntu install AND my YUMI installs come up as option choices in my bootloader.

Is this possible, and if so, how can I do this?

---

### Post by oldfred on 2012-12-04
I thought unetbootin reformated flash when it installed? Do you still have your other ISOs?

I have not used yumi, but created my own with grub2. But the installers usually use syslinux to boot. I have not manually attempted to edit syslinux menus.

this uses syslinux for multi-booting:
       multicd.sh - combine Linux ISOS into one - syslinux boot loader or isolinux.cfg 
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)

    
       These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

    
       MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

    
       This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

### Post by 1nxr0x on 2012-12-05
Thank you so much for your reply. You have posted so much great info for me to study and learn from!

Unetbootin does not reformat your drive, but only installs one bootable distro to your drive and leaves all other directories and files untouched as far as I can tell. However, from what I can tell so far, it appears as though YUMI stores the syslinux bootfiles/bootloader in its own directory rather than in root, whereas Unetbootin is installing them in root. I'm now thinking that because of this, the bootloader that Unetbootin is installing is being read first because it is in root, and that is why the distro that is installed by Unetboootin is coming up, and not those installed by YUMI. I suppose there may be a way to unify them so that you would be able to choose among them at boot.

So far the only main differences I can see between YUMI and Untebootin is where the bootloader files are placed upon install, that YUMI offers to reformat your drive if wanted, allows the installation and removal of more than one distro and manages them through its own interface, but does not have an option to set a persistence directory for the distros. Unetbootin on the other hand does not offer reformatting as an option and does not allow the installation of more than one distro, but it does provide the option upon installation to create a persistence directory.

YUMI does have an option to reformat the drive prior to installation of distros, but it is not required. Note that one of the listed requirements for YUMI is that your drive be formatted as either FAT32 or NTFS; of course NTFS is preferred if possible.


Here are the listed requirements for YUMI,

"Basic Essentials to create a MultiSystem Bootable USB Drive

Fat32 or *NTFS Formatted USB Flash or USB Hard Drive
PC that can boot from USB
Windows XP/Vista/7 or WINE to create the Bootable USB
YUMI-0.0.8.0.exe
Your selection of ISO Files"

I believe these requirements are essentially the same for Unetbootin. It is said that if your drive is not being recognized formatted as NTFS, then you should try Fat32, being mindful of the limitations of Fat32.

I have gotten to run a few different distros now on my drive, and they are lightning fast! I am now going to do a full version install on my fastest pendrive, which is a Patriot Memory - Supersonic Magnum 64GB "USB 3.0", which is one of the fastest, if not the very fastest pendrive currently on the market. This pendrive is testing as faster than many dedicated SSDs! That being said, such high levels of performance are not really necessary.

I have another older USB 2.0 drive that I'm going to use YUMI to install distros on for additional fun, testing, and learning purposes, but I will likely also install several Rescue type distros on it as well!

I see so many fantastic uses for these pendrive installs! Not the least of which is that they will provide an opportunity for newbies like myself to be able to install several distros at will, and be able to use them in full functionality, and without even having to install them on your system drive at all if you can&#8217;t or simply don&#8217;t want to.

---

### Post by oldfred on 2012-12-05
I have a full install of Ubuntu in my 16GB flash in a 8GB partition more for testing with my laptop. Then I installed a few ISO in the 8GB data partition and added a couple of boot entries as backups to boot my hard drives. So my grub 40_custom has lots of entries.

I now have changed to use a config file in grub on my hard drive. That way I do not have to run sudo update-grub but just edit config file as all grub does to load it.

---

### Post by 1nxr0x on 2012-12-05
> **oldfred said:**
> I have a full install of Ubuntu in my 16GB flash in a 8GB partition more for testing with my laptop. Then I installed a few ISO in the 8GB data partition and added a couple of boot entries as backups to boot my hard drives. So my grub 40_custom has lots of entries.

I now have changed to use a config file in grub on my hard drive. That way I do not have to run sudo update-grub but just edit config file as all grub does to load it.

Sounds good!

---

### Post by sytheii on 2013-01-19
I have just made a usb with a bunch of distributions of linux as well as windou ws xp and 7, and yumi was the tool I used to put them on the stick. 

I have booted successfully into the "live cd" function of ubuntu desktop 32bit....but the normal txt screen I am used to has been  replaced with something different by yumi, with many of the options of how to use the image missing and or changed. 

This is exemplified by the fact that when you start a live session, you should have root privileges, but you don't.  Which sorta sucks. I guess using yumi is only good if you want to install an os or run a command line utility?  I am now wondering if installations will work properly.

You said.....

> **1nxr0x said:**
> it appears as though YUMI stores the syslinux  bootfiles/bootloader in its own directory rather than in root, whereas  Unetbootin is installing them in root. I'm now thinking that because of  this, the bootloader that Unetbootin is installing is being read first  because it is in root, and that is why the distro that is installed by  Unetboootin is coming up, and not those installed by YUMI. I suppose  there may be a way to unify them so that you would be able to choose  among them at boot.


Which makes sense, because after booting up from YUMI, and then choosing live session for ubuntu desktop 32, i was not able to make any changes to ANYTHING on /dev/sda, which sorta defeats the purpose of running a live cd, neh?

Ideally I would like to be able to have a multiboot usb that has the exact same functionality of each distribution iso, as it would normally have if you burned it soley onto optical media or onto a usb.


Also when you do a live session from said ubuntu desktop, the standard "Install Ubuntu" shortcut that is on the destop normally is replaced with "install this."

---

### Post by oldfred on 2013-01-19
Then use one of the multi-boot scripts posted above. I did it manually with grub2's loopmount  before scripts became available. Most but not all distributions will work with the loop mount. The issue is finding the correct boot parameters. The scripts generally have the parameters and if I have issues now I often look at the script and find what it uses.

The general instructions for manually doing it and the hard drive instructions are really the same, it just is the path you use.

---

### Post by sytheii on 2013-01-19
> **oldfred said:**
> Then use one of the multi-boot scripts posted above. I did it manually with grub2's loopmount  before scripts became available. Most but not all distributions will work with the loop mount. The issue is finding the correct boot parameters. The scripts generally have the parameters and if I have issues now I often look at the script and find what it uses.

The general instructions for manually doing it and the hard drive instructions are really the same, it just is the path you use.

Could you recommend the simplest one to use? I am replying before actually having a chance to browse through those...and i am new to linux relatively.

---

### Post by sytheii on 2013-01-19
> **oldfred said:**
> Then use one of the multi-boot scripts posted above. I did it manually with grub2's loopmount  before scripts became available. Most but not all distributions will work with the loop mount. The issue is finding the correct boot parameters. The scripts generally have the parameters and if I have issues now I often look at the script and find what it uses.

The general instructions for manually doing it and the hard drive instructions are really the same, it just is the path you use.

Srry, my brain wasnt working, so you reccomend grub2s loop mount? since it works with most distros?

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/sh....php?t=1535864]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864")
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/....html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")

---

### Post by oldfred on 2013-01-20
I have not actually used any of the scripts. They probably are the easiest as they automate everything. 
Manual install is not particularly difficult and you learn more about how grub works. But I even had issues with some distributions on exactly what options are required in the boot stanza for different ISO. Several of the threads above have many examples. And a few ISO do not loop mount. Those you have to exact kernel & init and boot those, then boot.
If you want to try manual just use Ubuntu as it loop mounts easily.

---

