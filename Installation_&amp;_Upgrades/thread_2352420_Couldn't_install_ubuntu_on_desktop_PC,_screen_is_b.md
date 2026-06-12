---
title: "Couldn't install ubuntu on desktop PC, screen is blank. Please help!"
date: 2017-02-12
forum: Installation &amp; Upgrades
---

### Post by daniele.bosetti on 2017-02-12
Hi all,

I just assembled my new PC, and tried to install Ubuntu.
I downloaded the .iso file for version 16.04.1 LTS, burnt the image onto DVD, then boot.
I am able to see the first screens, where I can select language, keyboard and read the help guide.

But then, when I try "install ubuntu", or "try ubuntu", the screen becomes blank, it somehow doesn't receive output and goes standby, but the DVD drive is spinning.
I am not quite sure on what is going on, after 15 mins. the screen is still blank.

I think this could be related to some driver issue; I have been able to install Windows7 but needed the motherboard's drivers DVD of course.

My build is made of:
Motherboard MSI M3 gaming H270
Processor I5-7500
Samsung Sata SSD 850
WD Sata HDD

I'm using no graphic card, I rely on graphic output of the processor.

Maybe I need to select some special settings just after installing?

Any help is really appreciated!

---

### Post by ubfan1 on 2017-02-12
Tell which graphics card, that is critical.  The usual black screen fix to to try "nomodeset" on the boot line.  Legacy installs have function keys which add such options, but for a UEFI install, you will need to edit the grub boot yourself.  From the grub menu, select the boot you want (usually first line), then type "e" to edit (instructions at bottom of screen).  Edit in the nomodeset, then boot with control X.  If you succeed, you can then add the proprietary drivers from the software updater settings (additional drivers tab).

---

### Post by daniele.bosetti on 2017-02-12
Hi, thank a lot for responding!
Well as I mentioned, I have no graphic card- there is an HDMI output on the motherboard, graphic is handled by the microprocessor, which is intel core I5-7500, I find that processor graphics are [RIGHT][COLOR=#003C71][FONT=intel-clear]Intel® HD Graphics 630[/FONT][/COLOR][/RIGHT] (from ark.intel.com website).

I have been able to set the "nomodeset" option, (not editing the grub; i did as per this post, [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it) ) and the blank screen was solved.

Thanks a lot!

---

### Post by oldfred on 2017-02-12
Did you install Windows in BIOS or UEFI boot mode?
You have a new UEFI system, but Windows 7's DVD is BIOS only. You have to copy to flash drive and move some files around to make it UEFI bootable.
If Windows is BIOS, then you must use the 35 year old MBR(msdos) partitioning with 4 primary partition limit.
If you also added partitions with Windows you may have converted to dynamic, which does not work with Linux.

Does live installer work ok?
May be something in partitions?
Have you partitioned in advance with gparted?
Post this:
sudo parted -l

Update:
See you resolved issue.
You may want to do this.
       Intel Driver updates
[https://ubuntuforums.org/showthread.php?t=2342137&p=13565767#post13565767](https://ubuntuforums.org/showthread.php?t=2342137&p=13565767#post13565767)
Updates often needed for Skylake or Kabylake
[https://01.org/linuxgraphics/intel-linux-graphics-firmwares](https://01.org/linuxgraphics/intel-linux-graphics-firmwares)

---

### Post by daniele.bosetti on 2017-02-12
Hi oldfred,

well I think Win is in bios mode-
my first problem was this blank screen, which is solved by setting that "nomodeset" parameter.
After setting that, I was able to complete the Ubuntu installation-
But I think I made a mess, when Ubuntu asked the boot partition (?) I selected the one labeled windows 7 loader-
I thought that ubuntu would handle this smoothly-
instead, now I am unable to boot windows ;((((
and I think this is very much related with you suggestion.
Alas I have to repeat my windows installation

---

### Post by daniele.bosetti on 2017-02-12
I think this thread is solved now--
I now have other issues, like installing the usb-wifi adapter or having decent graphics performances (driver-related I think); will eventually open another thread.

---

### Post by oldfred on 2017-02-12
You never install grub to a NTFS partition, and almost never install grub to any partition like sda1 or sda2. You should normally install to sda.

I prefer the newer UEFI, but many still like BIOS.
And I greatly prefer gpt over the old MBR, but Windows in BIOS mode only boots from a MBR drive.
Ubuntu can boot in BIOS or UEFI from a gpt partitioned drive, but needs extra partitions for grub to install correctly.

 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

