---
title: "How to upgrade kernel and initrd in a LiveUSB?"
date: 2020-08-11
forum: Installation &amp; Upgrades
---

### Post by ping-wu on 2020-08-11
I have upgraded all the installed packages in my Ubuntu 20.04 LiveUSB (now 20.04.1).  However, the kernel and the initrd are never upgraded.  

How to upgrade the kernel and initrd in a LiveUSB?

---

### Post by ajgreeny on 2020-08-11
You can't do that, I'm  afraid as all changes to the OS itself are lost on rebooting and to run a new kernel you have installed requires a reboot.

You say you have upgraded all packages in your live OS; are you sure about that?  As far as I'm aware only changes you make within your live user home are retained after rebooting; everything else is lost, and all the changes in home demand the live OS must be using persistence.

---

### Post by ActionParsnip on 2020-08-11
You can use persistence on the live USB but you'll find it easier to install to the USB stick and run the OS there, just as you would install to an internal drive.

---

### Post by sudodus on 2020-08-11
[SIZE=4][Persistent] live drive[/SIZE]

The kernel and hardware drivers, that belong to the kernel are activated early, when a live drive is booted. This happens before the overlay structure for persistence is activated. For this reason it is not possible to use upgrades of the kernel and its drivers.

If you want to upgrade a [persistent] live system, you can [backup the content of the /home directory](https://help.ubuntu.com/community/mkusb/persistent#Backup_.26_restore_of_the_home_directory_in_a_casper-rw_partition) and create a new persistent live drive from the latest version of the iso file. The iso files of LTS versions are upgraded for years. See for example

- [this link to the iso testing tracker for Bionic](http://iso.qa.ubuntu.com/qatracker/milestones/384/builds) and
- [this link to the iso testing tracker for Focal](http://iso.qa.ubuntu.com/qatracker/milestones/408/builds)

Select standard Ubuntu or the flavour you want and then get to the download files.

[SIZE=4]Portable installed system[/SIZE]

An alternative, that might be more difficult is to create a portable installed system in a USB drive (installed like into an internal drive, but into a USB drive). **Such a system can be updated and upgraded without restrictions** just like any installed system. There are different ways to create such a system. See [this link *and links from it*](https://askubuntu.com/questions/1263746/ubuntu-doesnt-boot-from-usb-stick/1263749#1263749) for more details.

---

### Post by ping-wu on 2020-08-11
Using persistent LiveUSB has many advantages, most importantly in that it is pretty much independent of the hardware.  I have found out that a persistent (i.e., my own remix) LiveUSB, is the best tool to encourage a Windows user to try Ubuntu.  I have experienced a lot of problems trying to run an installed USB, created from my own machine, on an unknown machine.  A persistent LiveUSB also allows a user to install Ubuntu into his/her computer.  An installed USB stick does not have this option.  Also a persistent LiveUSB allows a user to boot into various locales, similar to what the official iso offers.

For a relatively older computer with mechanical harddrive, running a LiveUSB (on USB 3.0) is actually substantially faster than from an installed system.  It does everything that I would expect from an installed system, except updating the Linux kernel and the initrd.

---

### Post by ping-wu on 2020-08-11
BTW, making a persistent (remix) LiveUSB is extremely easy ***and totally transparent***--no need to use any script--in Ubuntu.  Actually I think this is one of the best selling points of Ubuntu (aside from its LTS feature).

The first step is to (as a recommendation) use gparted to create at least two partitions in a USB 3.0 stick:

1.  A fat32 first partition, 4GB, (optionally) labelled FAT;
2.  An ext4 second partition, 16GB (or whatever you can afford), labelled "casper-rw".

The second step is copy the content of the Ubuntu 20.04.1 iso into the first (FAT) partition of the USB stick:

1.  Re-insert the USB stick into the computer, open the FAT partition on the launcher; this will open a Nautilus ("Files") window.
2.  Right-click on the Ubuntu 20.04.1 iso file, and open it in a new window; click on "select all" then copy the entire content into the FAT partition.  (Since fat partition does not allow links, ignore the warnings.)
3.  In the FAT partition, go to "boot", "grub", double click on grub.cfg and edit the first line that contains the following statement:

    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed maybe-ubiquity quiet splash ---

 4.  Change this line to read:

       linux /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed maybe-ubiquity [COLOR=#ff0000]fsck.mode=skip persistent[/COLOR] quiet splash ---

Voila! You've got yourself a persistent Ubuntu 20.04.1 LiveUSB ready to be customized.  You can use this USB stick (or disk) as a functional backup, which can double as an installation disk, or as an alternative to your installed system.  But most importantly, please use this LiveUSB to promote Ubuntu!

---

### Post by pbear42 on 2020-08-11
Persistence is a good way to try an OS, but it's a crappy way to run one.  Anyway, did you notice?  *sudodus* answered your question.  You can't upgrade the kernel.  You can recycle the /home directory.

---

### Post by ping-wu on 2020-08-11
Actually I am running a persistent LiveUSB on one of my machines, and it is quite snappy.  The key is to use a relatively high speed USB (mine has a "nominal" write speed of ~400MB/s).  Yes, you're exactly right, the performance can be very crappy if I use cheap USB sticks.  For me, the main reason to use a persistent LiveUSB is not only to recycle the /home directory, but to preserve the additional packages (e.g., Chinese input method such as ibus-rime, etc.) as well as optimized config files. 
[COLOR=#000000]
As per [/COLOR]*sudodus, *[COLOR=#000000]the kernel and drivers are loaded before the overlay structure for persistence is activated; thus, the only way to update the kernel and the initrd is to *manually* replace the same in the casper folder with updated versions.  I was wondering if anyone has tried that???[/COLOR]

---

### Post by sudodus on 2020-08-12
> **ping-wu said:**
> ...
As per sudodus, the kernel and drivers are loaded before the overlay structure for persistence is activated; thus, the only way to update the kernel and the initrd is to *manually* replace the same in the casper folder with updated versions.  I was wondering if anyone has tried that???

I have not tried that, and I have not read any report about it, but it is an interesting idea. Linux is very flexible, you can do almost everything with it. Some tasks are easy, some tasks are more difficult :-)

---

### Post by ping-wu on 2020-08-12
I think I can manually download the most recent kernel and rename it as /casper/vmlinuz.  But any suggestions or suggested readings as to how to recompile the initrd for the LiveUSB based on the new kernel?

---

