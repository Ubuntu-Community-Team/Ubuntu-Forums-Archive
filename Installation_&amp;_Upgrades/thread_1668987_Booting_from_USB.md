---
title: "Booting from USB"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by Hyperreal_Logic on 2011-01-17
I understand that it is possible to boot Ubuntu from USB and use it on other computers after configuring the BIOS.  I read in *Linux Journal* that you can use Startup Disk Creator on Ubuntu, which makes the USB bootable.  I have been successful in installing it on the USB and getting it to boot on other computers; however, I cannot install apps or otherwise write to the disk.  In *Linux Journal*, Rick Rogers wrote an article titled 'Create Your Own Linux Desktop', in which he described the method of obtaining a bootable Ubuntu USB flash drive.  He also mentions that you could "install applications using sudo apt-get install, and do pretty much anything you would do on your desktop, limited only by the available storage on the USB stick."  Needless to say, I could install applications from neither the software manager nor sudo apt-get install. 

If anyone can help me with this I would be very grateful.  It would certainly be nice to have a portable Linux USB to use wherever I go.

---

### Post by mikewhatever on 2011-01-17
To be able to install applications etc, you'll need to go through the process of the proper installation to the USB stick. The programs like Startup disk creator or Unetbootin don't install. They simply copy the iso and make the stick bootable, which is great for evaluation and hardware testing.

---

### Post by Hyperreal_Logic on 2011-01-17
Ah, I understand now.  I was apparently misled by Rick Rogers in his article then.  He said to use Startup Disk Creator to make the disk bootable and to be able to use it like an ordinary Ubuntu installation capable of storing and creating files rather than simply testing and installing Ubuntu.

So if I install Ubuntu onto the USB stick, will it also be bootable?  Or would I have to install extra boot files and configure yaboot?

Thank you for the advice!

---

### Post by mikewhatever on 2011-01-17
I think yaboot is Open Suse's boot loader, Ubuntu uses Grub. When installing to a usb stick, you'll have to make sure Grub is installed to the MBR of the stick and not the hard drive.

Can you post a link to the article you keep referring to.

---

### Post by Hyperreal_Logic on 2011-01-17
> **mikewhatever said:**
> I think yaboot is Open Suse's boot loader, Ubuntu uses Grub. When installing to a usb stick, you'll have to make sure Grub is installed to the MBR of the stick and not the hard drive.

Can you post a link to the article you keep referring to.

Could you please tell me how I could install GRUB onto the MBR, or perhaps refer me to a post that has clear directions?  By "not the hard drive," are you referring to the USB hard drive, or internal?

In order to view the article I mentioned in the previous posts, you'll have to purchase the February 2011 edition of *Linux Journal*.  The article is called 'Create Your Own Linux Desktop, and Take it With You' by Rick Rogers.  It is on pages 60-61.  You can purchase the magazine from a local Borders or Barnes & Noble, or buy a downloadable .pdf version online at [http://www.linuxjournalstore.com/products/Linux-Journal-February-2011,-%23202-(Digital).html](http://www.linuxjournalstore.com/products/Linux-Journal-February-2011,-%23202-(Digital).html)

I understand your desire to see for yourself, and I would recommend it in any situation, but I can save you $5.99 by assuring you that Rick Rogers describes how to "run a desktop distro from a USB stick" using the "Startup Disk Creator from the Ubuntu menu."  He says, "select the download .iso and the target USB device," and that "when you click Make Startup Disk, Ubuntu copies all the needed files to the stick and makes it bootable."  In the next paragraph, he says, "You'll get a confirmation box, and then you've got your portable Ubuntu.  If that meets your needs, you're all set.  You can boot it on another machine, install applications using sudo apt-get install, and do pretty much anything you would do on your desktop, limited only by the available storage on the USB stick."

---

### Post by mikewhatever on 2011-01-17
Interesting. What happened when you tried installing applications as suggested in the article?
To change the default boot loader location, you'll have to select the manual partitioning option, and down the bottom of the partitioner window, there is a dropdown menu to select where to install grub (see the pic).
[http://www.dedoimedo.com/images/computers_years/2010_2/maverick-partitions.jpg](http://www.dedoimedo.com/images/computers_years/2010_2/maverick-partitions.jpg)

---

### Post by oldfred on 2011-01-17
If a small flash drive of 2 or 4GB you can add persistence and save files but not install applications. 
Added "persistent" as shown below in syslinux.cfg:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent

Benefits of persistent install over direct install to flashdrives 
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

If your flash drive is 8GB or larger you can do a full install and run it just like any other install. The only issue with different systems is usually video drivers, so do not install proprietary drivers.

With details on some of the caveats, std install.
[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

With grub2 persistant C.S.Cameron post#5 10.10:
[http://ubuntuforums.org/showthread.php?t=1643791](http://ubuntuforums.org/showthread.php?t=1643791)
With grub2 persistant 10.04 C.S.Cameron post#15:
[http://ubuntuforums.org/showthread.php?t=1593656](http://ubuntuforums.org/showthread.php?t=1593656)

See post #19 C.S.Cameron - recommends disconnection sda so grub can only install to flash drive.
Maverick now only gives combo box on grub location if you use manual install.
Lucid:
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)

---

### Post by C.S.Cameron on 2011-01-17
Applications are saved in a persistent install ok, video drivers arn't.
Desktop Effects become persistent if you add to Startup items.
I have vbox installed on a persistent disk image flash drive.

---

