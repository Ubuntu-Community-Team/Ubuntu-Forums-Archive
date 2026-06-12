---
title: "Install Ubuntu/Win7 dualboot to new hard drive"
date: 2014-12-01
forum: Installation &amp; Upgrades
---

### Post by snoz_re on 2014-12-01
Hi

I have searched for this and checked previous posts with no luck, so appoligies if this is answered elsewhere already.  There is info about, but I am unsure on the best way to go about what I want to do without a fresh install of Ubuntu.  I want to keep my current installation of Ubuntu as I have it set up nicely to my needs/wants, but just want it on a bigger hard drive with Win7 avaliable just in case I need it. Soooo......

**I have** an existing Ubuntu 14.04 installation on my Samsung NC110 with old 250GB hard drive.
**I want** a dualboot Ubuntu/Win7 system (just in case Wine doesn't do the job) on my Samsung NC110 with new 1GB hard drive.
**To hand** are a Win7 .iso (with legal codes, etc) file from microsoft, 2TB external hard drive, 32GB usb drive, 1TB new hard drive, 250GB old hard drive with Ubuntu 14.04, Samsung NC110 and a desktop PC running Win7.

I had planned (in very simplistic terms) to muddle my way through:

Clone the 250GB to the 1TB hard drive (and 2TB just in case I mess it up!! ;) ).
Fit the 1TB drive to Samsung and see if all works.
Make a 750GB partition.
Install Win7 to the 750GB partition.
Hope for the best that it works!!
Adjust the partitions to allow Ubuntu most of the space.

OR

Fit 1TB to Samsung.
Install Win7 to 1TB (from a usb).
Clone Ubuntu across to 1TB.
Hope for the best.
Adjust the partitions to allow Ubuntu most of the space.

Any advice, better ways of doing it, simple walkthroughs, etc would be greatly appreciated please. 

Thanks
Tim

---

### Post by fantab on 2014-12-01
The following might help:
[http://askubuntu.com/questions/106527/how-to-move-ubuntu-installation-from-one-hdd-to-another](http://askubuntu.com/questions/106527/how-to-move-ubuntu-installation-from-one-hdd-to-another)
[http://askubuntu.com/questions/20460/move-installation-to-new-disk](http://askubuntu.com/questions/20460/move-installation-to-new-disk)

---

### Post by oldfred on 2014-12-01
I am more of a fan of new installs.
But in your case a clone should work as the main issue of a clone that is not for recovery to the same partition/drive is duplicate UUIDs which then require editing of UUID, fstab, reinstall of grub and a few other fixes.

Also with a clean install you can repartition if desired, so you have smaller system partitions & large shared data partitions and/or a separate /home. Windows requires a primary partition to boot from if BIOS system.

All your user setting are in /home. And standard installs have all your data in /home. And if you export a list of installed applications then you can easily reinstall those. All those applications settings will still be in your /home.

Also a new install is a major houseclean. You have accumulated packages, log files and various other data. If you have been good about housecleaning then that is less of an advantage. And if you do clone be sure to thoroughly houseclean before hand.

Windows does like to be the first partition so I would install it to sda1, and if a BIOS system it will use 2 of the 4 available primary partitions.

My backup is to make a new install easy to replicate current system, but not backup Ubuntu system as that is easily downloaded and reinstalled.

       Oldfred's list of stuff to backup May 2011 (still current):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

---

### Post by snoz_re on 2014-12-03
Fantab, thanks for the links.

Oldfred, Thanks for the reply.  You are convincing me to do a back up of my system, fit the new drive and then Win7 install followed by a fresh Ubuntu install.  Will give it a go this weekend and see what happens!!

---

### Post by oldfred on 2014-12-03
Since you will have more than just / & swap, you do have to use something Else.
If only one drive, you just specify the drive (usually default sda) to install grub2's boot loader into. Examples below discuss multiple drive installs where you do choose another drive. Only in a few cases is flash drive used for installing seen as sda by BIOS and then grub may want to install in the wrong drive.

       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

I prefer to partition in advance using gparted for Linux partitions.

When you install Windows to a blank drive it will take over entire drive. Use Windows own partition tools to shrink Windows and leave lots of unused space. Reboot immediately so it can run chkdsk and make repairs for its new size.
 But I prefer smaller system partitions for both Windows & Ubuntu (/) and larger data partitions or /home. If using Windows a fair amount make a shared NTFS data partition also.

---

### Post by snoz_re on 2014-12-04
Oldfred,

Cracking, many thanks!!  Am doing backups as we speak and hopefully going to start the drive swap and dualboot installation tonight.  One quick question for you though please, where you linked to this thread:

Oldfred's list of stuff to backup May 2011 (still current):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

And advised the backup of these:

[I]I include these also:
cp /etc/apt/sources.list ~/sources.list.backup
apt-key exportall > ~/repositories.key
Various hardware listings/configurations
dpkg --get-selections > ubuntu-files
bash ~/Documents/LinuxDocs/CurrentSys/boot_info_script055.sh
lshw -html > ~/hardware_info.html
udevadm info --export-db > file.txt
dmidecode > bios.txt[/I]

I have put each of these commands into terminal and got the intended output, I will back these up and keep them safe, but what do I do with them please?  What's the reverse command/script to make use of them?

Thanks
Tim

---

### Post by oldfred on 2014-12-04
Most of it is just documentation of system. Or reference info if needed to know details.
In Windows I used to run Belarc to get similar info.

The sources list is just so you know any ppa you have. Occasionally someone deletes that, but you can get new copy created with on line sources of all but any you have manually added.
Keys may be something you need.
I just like having documentation of hardware, internal settings, and various configurations. More for reference if I get into trouble, but I have had to use them.

The dpkg list is all installed apps to make it easy to reinstall. Sometimes editing is requried if changing to a newer Ubuntu. Sometimes newer apps replace old. Or old kernels may be listed and should be removed.

I now run this version of script as it has been forked due to lack of updates in original.
 Updated fork  as bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)

---

### Post by snoz_re on 2014-12-14
Oldfred,

Many thanks for all the help here.  Got there in the end, but took a little longer as restoring the back-ups proved to be problematic and ended up just doing a clone after the win7 install, the only hassle being having to sort the boot options afterwards, but Boot-repair sorted it with minimal hassle.

Thanks again
Tim

---

### Post by oldfred on 2014-12-14
Glad it is working.

Boot-Repair has been updated so it is easy to install in all current versions of Ubuntu.

---

