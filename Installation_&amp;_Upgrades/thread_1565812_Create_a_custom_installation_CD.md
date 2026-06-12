---
title: "Create a custom installation CD"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by GeoMX on 2010-09-01
At work, we use custom Ubuntu installations, I create them by plugging the new hard drive to my computer and running some installation scripts, basically, these scripts debootstrap the hard drive and later install some additional packages and files. It works great for our needs.

But now, I think a CD or USB installation method could be a better option, and would like to get some advice on how and what tools could be of use for this.

I'm reading the Install CD Customization guide at [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization), and I think I can use it, but would have to remove a lot of packages (we use only the ones supplied by the "normal" debootstrap process and some other packages, mainly the X server and optionally FluxBox).

Are there other alternatives? Is there a tool that I could execute inside one of the already created systems that would allow me to package the whole system as an installation CD? Remastersys perhaps?

Thanks in advance for any comments/help/suggestions.

---

### Post by oldfred on 2010-09-01
I have not done it.

I would suggest starting with 
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Then you can install all your apps to that. I use this to list my apps from my previous install to have a list of what I want in my new install:
 dpkg --get-selections > ubuntu-files

Then you may want to use remastersys or clonezilla.

Make live CD or DVD
[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by GeoMX on 2010-09-03
I tried remastersys within my custom installation but if failed, I still have to try to fix it.

I've thought of another option: I already have my scripts for creating the installation, I think I could place them into a Live CD and run them from there. The only thing I need to know is hot to set the new hard disk to use the Live system as source repository for packages for running deboostrap and then install additional packages (which I would add to the CD).

Note: I'm referring to Live CD, but I'm thinking on using a Live USB.

---

### Post by oldfred on 2010-09-03
These are all links to somewhat related info:
 How to make a live CD/DVD from your harddisk installation 
[http://ubuntuforums.org/showthread.php?t=688872](http://ubuntuforums.org/showthread.php?t=688872)

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[https://help.ubuntu.com/8.04/add-applications/C/install-file.html](https://help.ubuntu.com/8.04/add-applications/C/install-file.html)

To install a .deb  file, double-click on it. If you prefer using the Terminal, enter:
sudo dpkg -i package_file.deb

Location of downloaded debs
/var/cache/apt/archives/

You can use your package manager to uninstall a .deb file once it has been installed. Alternatively, enter the following in a Terminal:
sudo dpkg -r package_name

More info I saved:
With Debian Installer(Which is text/ncurses based) ,it asks to Mount Ubuntu CD when booted from hard disk iso. What I did was ,to symlink(symbolic Linking) Lucid Alternate cd ISO to /dev/sr0(Which is the device file for dvd drive) .Then If I ask debian-installer to retry to mount cd ,it got mounted!

ln -sf /yourubuntuisodirectory/ubuntu.iso /dev/sr0

One advantage of using grub2 to boot the ISO on the USB flash drive is that the rest of the ISO is available for data. I have several ISOs and space for additional data and my scripts that I use to configure my system. But I install everything from the Internet. I did use my ISO boot flash to do a full install on another flash drive.

I think you can convert you base install to a install and then add in the .debs to add them if you want.

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by GeoMX on 2010-09-04
That's a lot of information, and it seems to be useful for my purposes :).

I'll let you know of my results, thank you so much for your help :).

---

### Post by GeoMX on 2010-09-10
I've just made the first test and it works :). I decided to do it this way:

[LIST=1]
[*]Back a current installation to a compressed file.
[*]Create a minimal LiveCD that includes the compressed backup and some scripts.
[*]Run the LiveCD in the target system with the new empty hard drive.
[*]The scripts create needed partitions on the hard drive, unpack the backup to the new hard drive, set correct boot options and do some other minor adjustments for the new system.
[*]That's it.
[/LIST]

I've just finished creating a new installation, it seems to work fine, I'm happy with the results, I just need to make some adjustments and add options to the installation scripts :).

Thanks a lot for your help.

---

### Post by oldfred on 2010-09-10
Glad you got it working.:)

---

### Post by GeoMX on 2010-09-11
Thanks again, marking as solved.

PS. For the record, a LiveCD can not be used as package source for debootstrap: [https://bugs.launchpad.net/ubuntu/+source/debootstrap/+bug/77589](https://bugs.launchpad.net/ubuntu/+source/debootstrap/+bug/77589)

---

