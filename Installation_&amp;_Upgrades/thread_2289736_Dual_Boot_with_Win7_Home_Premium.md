---
title: "Dual Boot with Win7 Home Premium"
date: 2015-08-06
forum: Installation &amp; Upgrades
---

### Post by Iflana on 2015-08-06
I want to setup my system to dual boot either Win7 Home Premium OR Ubuntu.  Each OS would have a separate partition.  When reading the installation instructions I see that you have to disable fast boot if you plan on using Windows again.  Basically all mentions are of Win8+ for this, but I wanted to confirm... do I need to do this with Win7 as well?

---

### Post by oldfred on 2015-08-06
With Windows 7 it is just hibernation. In Windows 8, fast start up is always on hibernation. 

But most Windows 7 systems have used all 4 primary partitions. 
Post this from Ubuntu live system installer booted in live mode and then in terminal.
sudo parted -l

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by Iflana on 2015-08-06
Thank you very much for clarifying on the fast start.

I have two physical hard disks in my computer.  One is 500GB for the Win7OS and applications.  The other is 1TB partitioned into 150GB for my files, 250GB for someone else's files, 500GB for shared files, and 100GB intended for ubuntu OS.  I'm thinking since I could run ubuntu off of a DVD that should be enough space for the OS and applications... right?

---

### Post by oldfred on 2015-08-06
I normally use 25GB for / (root), but have all other user files normally in /home inside data partition(s).

Is system UEFI or BIOS.
Post this from live installer in live mode, terminal:
sudo parted -l

---

### Post by Iflana on 2015-08-06
Should be EFI.  I am running am Asus Sabertooth P67 motherboard on a system that I custom built.  Here's some more info from MMC (where I created the partitions) on my system.  The **bold drive** is where I intend on having ubuntu.  Before shrinking, the J:/ was 250GB.  I chose to shrink this drive for two reasons: keep it physically separate from Windows, and prevent Windows from running out of space as I've had happen before.

C:/, NTFS file system, System/Boot/Page File/Active/Crash Dump/Primary Partition, 500GB

J:/, NTFS file system,  Active/Primary Partition, 150GB
**L:/, NTFS file system, Logical Drive, 100GB**
R:/, NTFS file system,  Primary Partition, 250GB
T:/, NTFS file system,  Primary Partition, 500GB

I haven't tried the auto installer yet, because I'm still reading to ensure everything will "be ok" & prepare some backups.  Can you explain what the command you've given will do exactly?  I'm very confused about whether it's even safe for me to try to install ubuntu.

---

### Post by yancek on 2015-08-06
You forgot to post the output of the parted command suggested by oldfred.  Also, the partition you indicate you want to install Ubuntu to is formatted ntfs.  That won't work but you can easily format it with a Linux filesystem during the install.

---

### Post by oldfred on 2015-08-06
While parted and gparted (GUI) are partitioning tools the -l parameter is a command line list of your partitions.
If confused about any command you can always ask Ubuntu's man pages.
man parted

If you have logical partitions, you are not booting Windows in UEFI.
Windows only boots in UEFI from gpt partitioned drives.
Windows only boots in BIOS from MBR partitioned drives.

MBR uses 4 primary partitions. Or one primary can be converted to the extended partition and then hold any number of logical partitions.
Gpt only has one type of partition and a soft limit (user can change) of 128 partitions.

---

### Post by Iflana on 2015-08-07
> **yancek said:**
> You forgot to post the output of the parted command suggested by oldfred.  Also, the partition you indicate you want to install Ubuntu to is formatted ntfs.  That won't work but you can easily format it with a Linux filesystem during the install.

I haven't done it yet, because I am unsure what this command does & still need to determine that I can install the OS properly to the partition I've set aside for it. ;) I am new to Linux and trying to be cautious since I see so many incidents of problems when people don't know what they're doing - like me!

---

### Post by Iflana on 2015-08-07
> **oldfred said:**
> While parted and gparted (GUI) are partitioning tools the -l parameter is a command line list of your partitions.
If confused about any command you can always ask Ubuntu's man pages.
man parted

I have been reading some, but I find a lot of the pages confusing.  I am new to Linux.  Hopefully I can keep posting here, and learn more from talking with others.

> If you have logical partitions, you are not booting Windows in UEFI.
Windows only boots in UEFI from gpt partitioned drives.
Windows only boots in BIOS from MBR partitioned drives.

MBR uses 4 primary partitions. Or one primary can be converted to the extended partition and then hold any number of logical partitions.
Gpt only has one type of partition and a soft limit (user can change) of 128 partitions.

OK, so it sounds like what I have then is Windows that uses BIOS to boot from MBR.  The logical drive was created when I did that last partition, because I already have the 4 primary partitions.  Sorry, if it sounds like I'm just repeating what you stated.  It helps me to put it in my own words and confirm to ensure I am understanding correctly.  So, I shouldn't have any troubles installing ubuntu as is?  No concerns with being able to boot ubuntu from an extended logical drive?

---

### Post by oldfred on 2015-08-07
We need to see your partitions to confirm what you have.
Linux will not install to NTFS formatted partitions. You have to use Linux format and many formats are supported, but ext4 is the standard. You cannot create an ext4 formatted partition from Windows. And often creating partitions in Windows converts to Windows dynamic partitions instead of basic partitions. But if you have an extended partition your are ok. Again need to review your structure to determine if ok or not.

Linux will read & write NTFS & FAT formatted partitions, but cannot have system files or settings. 
On of the advantages of Linux is that it has ownership & permissions in the file structure. Only authorized users & then with permissions can read, write or excute files. Greatly helps prevent virus from auto installing as in Windows NTFS all users have all permissions.

---

### Post by yancek on 2015-08-07
The parted command suggested above by oldfred does not "do" anything but outputs text in the terminal which will show information on your hard drives/partitions and will help someone to help you.

---

### Post by Iflana on 2015-08-07
I ran the installer from the disk, and no where did I find opportunity to use the command line given in order to determine the drive structure.

Since I was 100% that I was putting ubuntu on an extended logical drive I just went for it.  It does appear that I've somewhat successfully installed the OS at this point.  I used the partition options from the ubuntu dvd installer in order to delete the NTFS partition I created as L:/ for 100GB turning it into "free space".  From there I made a logical extension of 16GB for "/swap", then another logical extension as ext4 84GB for "/" like the install guide suggested.  I opted not to attempt to split it any further until my knowledge increases on actually using Linux.  Anyhow, I restarted and was able to boot ubuntu.  I restarted again, and was able to boot Win7.  Yay!

Please let me know if I should start a thread for the following somewhere else.  As far as I'm concerned it still relates to installation, so I'm just going to continue for the time being.

I went into the system settings, so that I could finish setting up ubuntu.  Unfortunately, this is where my good luck stops for now.  Once I open system settings my mouse disappears and everything comes to a stop.  No error message displays after letting it sit for like 15 minutes, so I just restarted the computer myself.  Tried several times with no luck accessing this area.

If I stay out of system settings then after a short while, no matter what I'm doing, I get error messages related to the xOrg nouveau driver.  I anticipated needing to install a driver for my video card, nVidia GeForce GTX 550 Ti, and I have downloaded it ahead of time onto my J:/ drive. The file I downloaded is from here [NVIDIA-Linux-x86_64-352.30.run]("http://www.nvidia.com/download/driverResults.aspx/87650/en-us") and I want to be using this particular driver as it is the most current driver available - released JUL28/15, from the manufacturer, and is designed for Linux.  Was reading the nVidia instructions, again lots of command lines I will have to try after I finish reading.  Also, when I look for some of the files I don't see them.  For example, neither "usr/local/modprob.d" nor "ect/modprobe.d" appear at those locations.  For the time being I've managed to set an old nVidia driver 340.76 that is found automatically, but I can't seem to search any other locations.  I don't want to continue using this old driver!  Note: at this point, not using the nouveau driver, I still can't access system settings.

---

### Post by oldfred on 2015-08-07
Do not install the .run file from nVidia.
Your card is old enough that the newest in the Ubuntu repository should work. The very new drivers from nVidia are really to support the very new cards particularly the Maxwell based 970/980/750 series. At some point they stop updating the driver for older cards and make the last version a Legacy version. There are several Legacy version.

If you install one nVidia driver, you must totally purge the old one before installing a new one or you have conflicts and neither work.

If you really want the newest driver, you can add a ppa or private archive that works just like Ubuntu's repository.

Mouse issue may be settings in UEFI/BIOS or video driver.

 The GTX 970/980 Maxwell GPUs Light Up With Nouveau On Linux 3.19
[http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg](http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg)
NVIDIA GeForce GTX 970/980: Windows vs. Ubuntu Linux Performance 2015 note versions ppas used to update
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1)
Install with Asrock Z97 & nVidia 970
[http://ubuntuforums.org/showthread.php?t=2257406](http://ubuntuforums.org/showthread.php?t=2257406)
[http://ubuntuforums.org/showthread.php?t=2259210](http://ubuntuforums.org/showthread.php?t=2259210)

The ppa's have all the newest drivers, so any instructions for an older one should work with most current.
      
 Install Nvidia 340.24 from ppa:xorg-edgers/ppa
[http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/](http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/)
14.04 drivers for Nvidia GeForce GT 730 desktop board - 
[http://ubuntuforums.org/showthread.php?t=2240702](http://ubuntuforums.org/showthread.php?t=2240702)
PPA for nVidia mamarley pps
[http://ubuntuforums.org/showthread.php?t=2256437&p=13185945#post13185945](http://ubuntuforums.org/showthread.php?t=2256437&p=13185945#post13185945)
[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)
All the current drivers xorg-edgers PPA
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages)
Oibaf PPA discusion
 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1)

---

### Post by Iflana on 2015-08-07
I understand you feel it isn't necessary given the age of my video card to have a recent driver, but is that the only reason you're saying not to use the nVidia download?

---

### Post by oldfred on 2015-08-07
If you download the nVidia driver from nVidia, you have to reinstall it with every kernel download. The version in repository or a ppa is automatically reintegrated into a new kernel.

---

### Post by Iflana on 2015-08-08
I see.  So if that becomes obsolete every time a system update is done, then can I set ubuntu to only update when I want it to be done?  With Windows you have the option.  With ubuntu I just assumed it would be manual!

I have had far too many bad experiences running old graphics drivers, or alternative drivers not from the card manufacturer in the past.  I do want to use the current driver from nVidia for sure, at least for now.  I mean, it's not like any of the ones provided with ubuntu seem to work anyhow.  The one that's allowing me to access areas other than system settings is the fifth one I tried in ubuntus prepackaged driver list... and I'm still having problems possibly related to the graphics driver to resolve.

---

### Post by oldfred on 2015-08-08
If you have installed more than one nVidia driver without totally purging the old one, you will have major problems.
You should only install the most current version that applies to your card in repository. If legacy card then you have to install the correct legacy version and no other.

If you want the very newest driver and that is still valid for your model, then you should add one of the ppas, that has all the nvidia drivers in them and install the correct one only. Not sure if one is better than the other. Did you look at the links on ppas?

---

### Post by Iflana on 2015-08-08
I was browsing the links in your last post while I was waiting to see just that.  I believe I found the driver version I'm looking for in a PPA on LaunchPad.  Not sure how to make it an option in the "additional drivers" tab though.  I know I can go to the "other software" tab, click on "add", and enter an "APT line".

[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages?field.name_filter=352&field.status_filter=published&field.series_filter=](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages?field.name_filter=352&field.status_filter=published&field.series_filter=)

Of the 3 results there I think the one in the Trusty series would be what I need, because my system info says ubuntu 14.04 LTS.  If that's the case, what do I input for the APT line?

---

### Post by oldfred on 2015-08-08
The only ppa I have used is Boot-Repair and it gives specific commands.

But this one has the generic link on using ppa, just change instructions to the one you want.
Click on -  read about installing.

[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

That looks like you are installing the experimental or development version. 
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)
Says 355.06 is correct version.

---

### Post by Iflana on 2015-08-08
The 355.06 version is a beta according to nVidia, while the 352.30 isn't.  I had to double check to make sure I didn't note the wrong number.

I'm glad the APT line wasn't somewhere terribly obvious on the page I was looking at.  :D  I've got this PPA location added, now I just have to work out why it's only updated with the 355.06 driver.  I was even able to find the proper APT for the page I found after knowing what I was looking for!  Thanks a bunch for pointing me in the right direction.  Here's hoping one of them has drivers that will let me access my system settings!  Will update another day.

---

### Post by oldfred on 2015-08-09
If you have already installed any nVidia driver, be sure to totally purge before installing from the new ppa source.

 Lists installed version, in/with your kernel:
dkms status
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
If new version of Ubuntu with systemd it does not use X11 anymore, so you will get error and can ignore it.

---

### Post by Iflana on 2015-08-09
I'm using the GUI to make changes whenever possible instead of the terminal.  I don't know what <nvidiadriverpackagename> would be here, so using that command would be hard.  I am assuming that the GUI would do the purge before switching to the new driver I've clicked, no?  I tried the command **dkms status** and it looks like there is two lines that say installed.  The 340.76 was the last version I had clicked on.  I have no idea what bbswitch is.  See below.

> bbswitch, 0.7, 3.16.0-30-generic, x86_64: installed
nvidia-340, 340.76, 3.16.0-30-generic, x86_64: installed

---

### Post by oldfred on 2015-08-09
Is yours an optimus laptop?

I use synatic to know package names and details of a package.

> bbswitch is a kernel module which automatically detects the required ACPI
calls for two kinds of Optimus laptops

I do not know if this means you have two versions or is just a detail on the version?
nvidia-340, 340.76,
If two versions then an issue.

---

### Post by Iflana on 2015-08-09
OK, so everything was working including system settings until I ran the ubuntu software update after it prompted me there was new stuff.  It gave an error about the graphics driver as it was a PPA.  I figured it just couldn't update it, and I wasn't worried given I just set it.  Now, I can't even login.  I think it's using one of the bad drivers that were packaged with ubuntu instead.

---

### Post by oldfred on 2015-08-09
The ppa will automatically update. Or if ppa gets obsolete then it will give an error.
And newest version from ppa or Ubuntu will normally be what is installed.

Then did you have both 340 from Ubuntu and 340.76 from ppa?
And if not Optimus that may be an issue.

 # only reason to purge is there are several versions, if you know you have different nVidia use that:
Also must make sure parts of old install or persistence issue are not presevered as they are in use.
#To see available versions:
dpkg -l | grep -i nvidia*
#see details for version installed
sudo apt-cache policy nvidia*
dkms status

      
 sudo apt-get purge nvidia*

---

### Post by Iflana on 2015-08-09
Yes I recall there being several & I tried 5 drivers that came packaged with ubuntu.  Some open source, some proprietary, and the nouveau.  They were versions 346 through 340.  After that, the one from the PPA that allowed me access to system settings.  I added the PPA source for the xOrg driver I originally found/wanted, as well as the Marley one you pointed out with the beta driver.  I figured they'd both be good sources to have for the future & I could just select from there the best one.

I'm feeling confident this is from ubuntu reverting back to one of it's original graphic drivers.  How do I change back to a working driver if I can't load the OS past the login screen?  Also will need to find a way to avoid it reverting back to the ubuntu drivers in the future.

---

### Post by oldfred on 2015-08-09
I think I mentioned that you must purge a previous nVidia driver before installing a new one.

You may be able to boot in recovery mode, it uses nomodeset automatically. 
It should give terminal and if you also enable networking you can run updates.

---

### Post by Iflana on 2015-08-10
> **oldfred said:**
> Is yours an optimus laptop?

I use synatic to know package names and details of a package.



I do not know if this means you have two versions or is just a detail on the version?
nvidia-340, 340.76,
If two versions then an issue.

I am not using a laptop. I am using a custom built desktop.

---

### Post by oldfred on 2015-08-10
Then you should not need bbswitch. Not sure if installed by default with new nVidia drivers. But better without it.

---

### Post by Iflana on 2015-08-10
> **oldfred said:**
> I think I mentioned that you must purge a previous nVidia driver before installing a new one.

You may be able to boot in recovery mode, it uses nomodeset automatically. 
It should give terminal and if you also enable networking you can run updates.

Yes, you did; however, I'd explained that I'm not knowledgeable enough to do this unassisted.  Since I was using the GUI, I was under the impression that something like this would be completed in the background without my direct input.  I'm unsure what the package names are, which is a requirement to using the command.  I see you said to use synatic to find out package names & details.  I am a new user to Linux, so I do need help that is geared towards someone that's never used Linux before in their life.  A name isn't enough for me to figure it out.  I don't know if this is something I should be trying to get after Linux is fixed, if I can get it from using the terminal - if so how to do that & how to use synatic to accomplish my goal.  Step by step instructions would really help infinitely more than a list of links to other pages or commands.  I do greatly appreciate your assistance, I'm just having a very hard time taking advantage of it as I don't have the knowledge you do!

For example, another place I read that it's possible my user didn't have the appropriate permissions in order to complete the login process & it would get stuck in a loop.  The solution was the set the appropriate permissions for my user using the terminal.  If I'd been given just that I'd be just as stuck as when I started, because I don't have the knowledge.  What helped me accomplish that was these step by step instructions:


[LIST=1]
[*]start up ubuntu 
[*]press CTRL + ALT + F1 to access text mode 
[*]login at prompt 
[*]use this command to see who owns the directory **ls -l /home** 
[*]if not owned by your user then use this command to change permissions **sudo chmod -R u+w /home/user** (where user is your username for ubuntu) 
[/LIST]

I hope that helps explain why I'm having a hard time.  I'm really trying to do my due dilligence, and read the links & manuals.  It's just the ones I'm finding for the most part aren't geared at individuals who are new to Linux.

-----

When I use your command **sudo apt-cache policy nvidia*** I get pages upon pages of information.  It seems like the important part is that each set of information says "Installed: none".  This seems to conflict with the **dkms status** command doesn't it?  I am so confused. :(

When I select advanced ubuntu boot options at startup I'm given four options: a regular startup for version 1, a recovery startup for version 1, a regular startup for version 2, and a recovery startup for version 2.  Regular startup doesn't seem to work.  Recovery startup does, but then I don't know what I'm supposed to do from there.  Step by step instructions would help.

---

### Post by oldfred on 2015-08-10
The recovery startup uses nomodeset by default.
You may be able to boot into gui with nomodeset on first boot option.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If using recovery mode it gives a text screen with various options. You will need network to be able to run updates.

If you were the user who installed Ubuntu, you should have all the correct ownership & permission in /home. And those should not be changed.
      
 Ubuntu /home is permissive:
[https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access](https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access)
sudo chown -R $USER:$USER /home/$USER
sudo chmod -R a+rwX,o-w /home/$USER
Where this shows the user:
echo $USER
fred@trusy-ar:~$ echo $USER
fred

Do not run any commands to change ownership or permissions on any system partitions except your own /home or your data partitions if separate partition(s). And -R is recursion, or all folders below also are changed. If run on a system partition the only way to fix it, is a reinstall. 

The apt-cache shows all the available nVidia versions that apt can find to install and give details. If you add a ppa it will show even more alternatives.
The dkms status shows what is installed. If more than one copy then best to uninstall everything, reboot using nomodeset to get low quality gui or recovery mode for terminal and install correct version.
      
 Lists installed version, in/with your kernel:
dkms status
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
May not have this if newer system with systemd:
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
I would also purge this:
sudo apt-get purge bbswitch-dkms 

then you can install the version you want. Installing from the gui using system settings is the only way a new user should install as it is easy. But if you have to have the newest version which really only is required with newest nVidia cards like the Maxwell series 970/980/750, then you have to add one of the ppa and install the newest version ppa has with terminal.

These were the commands I used in terminal to update with my older system. Back then 319 updates was the newest in Ubuntu repository. Line numbers are just from listing commands in history with history command.


 1995  sudo apt-get remove --purge nvidia*
 1996  apt-cache search nvidia
 1997  sudo apt-get install nvidia-319-updates
 1998  sudo reboot

---

### Post by Iflana on 2015-08-10
> **oldfred said:**
> The recovery startup uses nomodeset by default.
You may be able to boot into gui with nomodeset on first boot option.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I was reading that thread while waiting for your next reply.  :D  I managed to edit the file and tried two different things.  First I tried putting NOMODESET at the end of the linux /boot line like the original thread, used CTRL+X to reboot, and still couldn't login to the OS.  Second I tried putting NOMODESET in place of QUIET SPLASH, used CTRL+X to reboot, and still couldn't login to the OS.

> If using recovery mode it gives a text screen with various options. You will need network to be able to run updates.

Yes, when I enter either recovery option it is a text screen with a number of choices.  What steps should I take once in there in order to update, apart from enabling network?

> If you were the user who installed Ubuntu, you should have all the correct ownership & permission in /home. And those should not be changed.
      
 Ubuntu /home is permissive:
[https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access](https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access)
sudo chown -R $USER:$USER /home/$USER
sudo chmod -R a+rwX,o-w /home/$USER
Where this shows the user:
echo $USER
fred@trusy-ar:~$ echo $USER
fred

Do not run any commands to change ownership or permissions on any system partitions except your own /home or your data partitions if separate partition(s). And -R is recursion, or all folders below also are changed. If run on a system partition the only way to fix it, is a reinstall. 

It looks like my user is the owner, so that sounds good.

> The apt-cache shows all the available nVidia versions that apt can find to install and give details. If you add a ppa it will show even more alternatives.
The dkms status shows what is installed. If more than one copy then best to uninstall everything, reboot using nomodeset to get low quality gui or recovery mode for terminal and install correct version.
      
 Lists installed version, in/with your kernel:
dkms status
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
May not have this if newer system with systemd:
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
I would also purge this:
sudo apt-get purge bbswitch-dkms 

then you can install the version you want. Installing from the gui using system settings is the only way a new user should install as it is easy. But if you have to have the newest version which really only is required with newest nVidia cards like the Maxwell series 970/980/750, then you have to add one of the ppa and install the newest version ppa has with terminal.

These were the commands I used in terminal to update with my older system. Back then 319 updates was the newest in Ubuntu repository. Line numbers are just from listing commands in history with history command.


 1995  sudo apt-get remove --purge nvidia*
 1996  apt-cache search nvidia
 1997  sudo apt-get install nvidia-319-updates
 1998  sudo reboot

Would it be worth while to try **sudo apt-get purge bbswitch-dkms** first?  I'll have to figure out all those nVidia package names, because that's what is holding me back now.  What I'm going to do is see if I can run that list, write down a few sections, post it back here, and then see if what I'm guessing is the package name is the package name.

---

### Post by oldfred on 2015-08-10
I have always used synaptic. It was standard before Software Center.
But it shows packaged details.
The only ppa I have added is Boot-Repair and in synaptic it shows the ppa.
So if you enable a ppa and use synaptic you can see all the nVidia packages from there and also install from there. A bit easier than terminal.

sudo apt-get synaptic

The do a search for nvidia.

---

### Post by Iflana on 2015-08-12
That command doesn't work for me.  Here is what the terminal returns.

> E: Invalid operation synaptic

[ATTACH=CONFIG]263800[/ATTACH]

---

### Post by oldfred on 2015-08-12
You can just copy & paste text from terminal. If long, then include code tags which also preserves formatting of some output. Easy to add code tags with # in Forum advanced editor.

I left off install. 
sudo apt-get install synaptic

---

### Post by Iflana on 2015-08-12
> **oldfred said:**
> You can just copy & paste text from terminal. If long, then include code tags which also preserves formatting of some output. Easy to add code tags with # in Forum advanced editor.

I only have one computer box, so I'm not sure how I can accomplish that without being able to get into Ubuntu.  What I have to do right now is boot in Linux, run any commands, take pictures with my cell, reboot into Windows, and then I can post results in the forums here.  If there is any easier way I'm all ears!

These pictures are the results of the install.

[ATTACH=CONFIG]263807[/ATTACH][ATTACH=CONFIG]263806[/ATTACH][ATTACH=CONFIG]263805[/ATTACH][ATTACH=CONFIG]263804[/ATTACH][ATTACH=CONFIG]263803[/ATTACH]

---

### Post by oldfred on 2015-08-12
If you can boot into Linux with nomodeset, cannot you not get Internet & use Firefox?

The nvidia uvm packages are shown in synaptic as this:
> This is a transitional package for nvidia-340-uvm, and can be
safely removed after the installation is complete.

---

### Post by Iflana on 2015-08-12
When I put the NOMODESET option in it didn't make any difference - I still couldn't load the GUI OS.  I've just been doing CTRL+ALT+F1 to access a terminal screen.

So my next step is then to remove the nVidia package by putting **sudo apt-get purge nvidia nvidia-340-uvm** into the terminal?

---

### Post by oldfred on 2015-08-12
I have seen this posted.
 sudo apt-get purge nvidia-*

Or list exactly what is installed and purge each:
      
 Lists installed version, in/with your kernel:
dkms status
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

If newer Ubuntu using systemd you may not have xorg.conf, so an error is ok then.

---

### Post by Iflana on 2015-08-13
> **oldfred said:**
> I have seen this posted.
 sudo apt-get purge nvidia-*

This is the command I ran, and here's what happened.

[LIST=1]
[*]Command appeared to run ok in the F1 screen terminal.
[*]Switched to the F7 screen to try and login.
[*]Tried first to reconfigure graphics, but I couldn't do this as I had no backup & selecting the default option didn't do anything.
[*]Tried second to run in low graphics mode for this session only.  It let me login, and then it was just a blank screen with the blinking cursor.
[*]Rebooted the system, and logged in ok with the GUI.
[*]Went into additional drivers and see that the system is using the Nouveau driver that causes the system to crash.  Thought I'd wait and make sure that's what was going to happen.
[*]Opened Launchpad and started the "tour" to take up some time.  Then ubuntu reports an internal error.  When I tried to send the report the system crashed.
[*]Rebooted the system again, and logged in ok with the GUI.
[*]Internal errors show up after logging in, and I had to enter my password/authenticate a few times.
[*]Went into additional drivers, and selected the 355.06 as this is the newest version from the mamarley PPA.  I am missing some of the versions that the xOrg-edgers PPA added here before.  All original versions that came with ubuntu still show up.
[/LIST]

[ATTACH=CONFIG]263835[/ATTACH][ATTACH=CONFIG]263834[/ATTACH]

So now I'm a bit scared to turn off my computer or restart.  Is it possible to do something to prevent the system from loading the Nouveau drivers, or other ones that I know don't work for me from the ubuntu repository?  Or is this something I'm going to have to contend with every system software update?  Also, should I be concerned about those errors?

---

### Post by oldfred on 2015-08-13
If you have installed nVidia driver then it should always use that. And if from a ppa, then a kernel update will also integrate it into the newer kernel. You should not be using nouveau driver.

I see kernel 3.16, so you did not use the newest 14.04.3?
       Ubuntu 14.04.3 LTS Released Aug 6, 2015
[https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/ChangeSummary/14.04.3](https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/ChangeSummary/14.04.3)
Ubuntu 14.04.2 (Trusty Tahr) Uses 3.16 kernel

I do not know about  HWE - Hardware Enablement Stack.
I have original 14.04 which still has old kernel 3.13.
But as I understand if you use HWE, you have to keep updating to  newest HWE release or you do not get the 5 year support. Then with last HWE you get the rest of the support.
The HWE is so those with newer systems get the newer kernels & support software. Otherwise original kernel after 4 years may not work with any new hardware.

---

### Post by Iflana on 2015-08-13
I downloaded the latest LTS version when installing the system about a week ago.  Looking at the calendar, seems like that may have been right before the new one was released.  Isn't that something that should have updated when I ran the system software update?

I had installed an nVidia driver from a PPA, but after I ran the system software update that's when the OS changed to a different graphics driver and became unusable.  Then I purged with the command you gave me, and it went back to the Nouveau driver that only worked for a few minutes before crashing the system.  That's why I was asking about preventing it from going back to another driver.

---

### Post by oldfred on 2015-08-13
Not sure what you are seeing then, or which driver may be causing the issue.

It does not automatically update to the next HWE.

 Confused about HWE - Hardware Enablement Stack 12.04
[http://ubuntuforums.org/showthread.php?t=2238876](http://ubuntuforums.org/showthread.php?t=2238876)
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

