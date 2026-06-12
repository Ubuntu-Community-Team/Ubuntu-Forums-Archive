---
title: "Installing on 1 TB USB Hard Drive. Have a few questions."
date: 2014-03-03
forum: Installation &amp; Upgrades
---

### Post by TrolliOlli on 2014-03-03
Hi all, 

So I recently purchased a [My Passport Ultra 1 TB USB 3.0 HD]("http://www.amazon.com/Passport-Ultra-Portable-External-Backup/dp/B00E055H5O/ref=sr_1_1?ie=UTF8&qid=1393831352&sr=8-1&keywords=my+passport+ultra")  and my intention is to partition ~200g of it as simple space to store and swap files between Windows 7 and Ubuntu, and then use the rest of the space to install Ubuntu.

This hard drive will almost entirely be booted off of my desktop computer, but there is the chance that I'll carry it around and boot it off other machines.  This is where I am in a bit of a dilemma   I know I can install a live USB version of ubuntu to make it easy to run off any machine I plug the HD into, but don't these live versions run quite a bit slower than normal installs?  

If I were to install ubuntu on this drive just like I would on an internal drive, would I run into issues trying to boot it off machines other than the one I originally had it connected to when ubuntu was installed?  My knowledge here is lacking but from the research I've done, this would cause issues as the HD would have all the drivers from my original machine, and thus this would cause issues when it was connected to different hardware.


In the end, I am a C.S. student and I already do a lot of programming work on my laptop (currently running fedora), and I simply want this HD to be a linux system I can run on my desktop.  Ideally I want to get the best performance out of this HD, so if it's not really possible to have this be a portable copy of linux while still maintaining performance, I'd be fine leaving this as a "permanent" external hard drive to my desktop.

Thanks for the help, and I appreciate your time.

---

### Post by fdrake on 2014-03-03
linux is very good with drivers . Even if you install linux into an usb hdd from machine-1 and then plug the usb to machine-2 linux should be able to get the right driver for your hardware at boot time. This is not suggested because it may happen that you have to correctly install manually the video card  from your console, or your Ethernet /wifi adapter.  Linux recognizes most of the hardware pretty easily but it doesn't do it of everything. That is why we have live cd . If you plane to use the USB hdd only on specific machines (2 or 3 pcs) you can try how it works directly from the installed linux partition. If you plan to use it on a wide range of hardware the live version is a better suggestion.

---

### Post by oldfred on 2014-03-03
The issue is often video drivers or Wireless drivers. You can avoid some video driver issues by not installing any proprietary drivers, or when booting on a different system boot in recovery mode and either change driver or in effect turn off proprietary driver.
I have nVidia and until I install the nVidia proprietary drivers have to use nomodeset boot parameter. And I have to do that with both live installer and first boot after installed.

Some systems support USB3 better than others. But USB is not as fast as hard drive or SSD. But once an application is loaded into RAM system runs well. And if you have a fair amount of RAM, Linux caches recent programs in RAM so if you do not change large apps a lot you may still be very quick.

You can also boot ISO directly from a hard drive with grub and that is how I install to another hard drive now. And I have multiple ISO on my larger flash drives to be both installer and repair ISOs.

This is older, so not sure still current.
 [http://ubuntuforums.org/showthread.php?t=1714456](http://ubuntuforums.org/showthread.php?t=1714456)
Boot using recovery mode & 'Reconfigure graphics' or
Create Portable Ubuntu for 2 different Video Cards - script
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)
There is a application named switchconf that lets you choose between xorg.conf files at boot.
[http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/](http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/)

---

### Post by sudodus on 2014-03-03
> **TrolliOlli said:**
> Hi all, 

So I recently purchased a [My Passport Ultra 1 TB USB 3.0 HD]("http://www.amazon.com/Passport-Ultra-Portable-External-Backup/dp/B00E055H5O/ref=sr_1_1?ie=UTF8&qid=1393831352&sr=8-1&keywords=my+passport+ultra")  and my intention is to partition ~200g of it as simple space to store and swap files between Windows 7 and Ubuntu, and then use the rest of the space to install Ubuntu.

This hard drive will almost entirely be booted off of my desktop computer, but there is the chance that I'll carry it around and boot it off other machines.  This is where I am in a bit of a dilemma   I know I can install a live USB version of ubuntu to make it easy to run off any machine I plug the HD into, but don't these live versions run quite a bit slower than normal installs?  

If I were to install ubuntu on this drive just like I would on an internal drive, would I run into issues trying to boot it off machines other than the one I originally had it connected to when ubuntu was installed?  My knowledge here is lacking but from the research I've done, this would cause issues as the HD would have all the drivers from my original machine, and thus this would cause issues when it was connected to different hardware.


In the end, I am a C.S. student and I already do a lot of programming work on my laptop (currently running fedora), and I simply want this HD to be a linux system I can run on my desktop.  Ideally I want to get the best performance out of this HD, so if it's not really possible to have this be a portable copy of linux while still maintaining performance, I'd be fine leaving this as a "permanent" external hard drive to my desktop.

Thanks for the help, and I appreciate your time.

I suggest that you try the One Button Installer (at the advanced OBI level) to install one of the systems from a tarball. See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)
[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)[URL="https://help.ubuntu.com/community/OBI"]
[/URL][the OBI quick start manual file]("http://ubuntuone.com/42AIgmpo9lsz7YNfXKCROV")




[URL="https://help.ubuntu.com/community/OBI"]

[/URL]

---

