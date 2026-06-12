---
title: "Fresh reinstall without touching GRUB"
date: 2014-09-07
forum: Installation &amp; Upgrades
---

### Post by satnelav on 2014-09-07
My latest Ubuntu dist upgrade failed my system is broken and I need to do a clean reinstall. However I don't want to touch grub (since each time in the past i had serious problems with autodetection of entries for other OS'es).
what options do I have? 
I would prefer a solution like installation from a usb image but there does not appear to be an option to keep the boot loader intact..

---

### Post by yancek on 2014-09-07
You would need to explain in a little more detail what "my system is broken" means.  If that means it is unbootable then keeping the boot files from the old install isn't going to help.
You mention other OSs so which OS has its boot files in the master boot record.  If it is Ubuntu then you need to reinstall Grub with the OS installation.  If it is some other distribution which has its boot files in the mbr, when you re-install Ubuntu, install Grub to its partition and then reboot to the primary system with Grub in the mbr and run suod update-grub.  You're a little short on details on your system.

---

### Post by satnelav on 2014-09-07
My system is  bootable. I can access the ubuntu terminal. As I understand Grub is in the MBR and it has entries to ubuntu, windows 7 and a samsung recovery partition. Are you saying it is not possible to reinstall ubuntu without reinstalling grub in this case(I know it wont autodetect the last two ones correctly)? Is it easy to manually save the grub configuration?

---

### Post by nerdtron on 2014-09-07
What were your previous problems in GRUB? In the latest ubuntu grub has a very good chance of detecting the OSes installed on other partitions.
And to make it clear, this isn't a wubi install right?

---

### Post by yancek on 2014-09-07
> As I understand Grub is in the MBR and it has entries to ubuntu, windows 7 and a samsung recovery partition

The mbr is one sector, 512 bytes, the Grub files needed are much more than that.  The Grub boot menu and all the scripts used to create Grub and boot the system are on your Ubuntu partition.  The standard method is to install Grub to the mbr of the primary drive which puts a minimal amount of code there pointing to the boot files on the Ubuntu system partition.  From your last post, does that mean you have Ubuntu and windows 7 as the only operating systems?  There must be some other complication because Grub rarely has a problem detecting windows 7.  I have Ubuntu and windows 7 and 7 as well as its recovery partition have entries in Grub and boot no problem.  Since you don't have any other bootloader except for windows which doesn't boot a Linux system there doesn't seem to be an alternative to either repairing your current Ubuntu or reinstalling.  You never mentioned what your problems are?

---

### Post by kansasnoob on 2014-09-08
If this is a simple Win 7 and Ubuntu dual-boot then grub will have to be reinstalled, but there is a greater concern. There is a bug in the installer that can unexpectedly cause the loss of existing operating systems and data during reinstallation:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

So the only safe way to reinstall is to back up any existing data in your Ubuntu install and then use the ***Something else*** option to reuse and/or create partitions for your Ubuntu reinstallation. But it's not as scary as it sounds, it just requires a bit of planning and preparation. If you need any help or clarification regarding the steps below please ask.

Step #1 is deciding which version and flavor of Ubuntu you wish to reinstall. I'd think most users would want 14.04.1 which is the first point release of Trusty. Do you need help deciding which image to use or locating your preferred download?

Step #2 is actually downloading the .iso, verifying the md5sum of the download, creating either a live DVD or USB, then booting the new live media, and finally entering the [Advanced boot options]("https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options") and selecting Check disc for defects. Do you need additional help with any of that?

Step #3 is to actually provide some info to us here at the forums so we can both have a look at your existing grub configuration and also recommend a detailed reinstallation procedure. One way of providing a lot of the needed info in one easy step is to supply the boot info link created by [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair"). **[COLOR="#FF0000"]DO NOT actually run the recommended repair![/COLOR]** We only need to see the boot info to be able to help you.

Clear as mud so far?

---

