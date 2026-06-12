---
title: "Installation keeps freezing on a particular programming line"
date: 2015-03-05
forum: Installation &amp; Upgrades
---

### Post by stuart16 on 2015-03-05
Hello. I'm hoping someone will take pity on a newbie and suggest something before I get really cheesed off and throw my new build out of the window.

Just completed a new build and am trying to install Ubuntu 14.04 onto the SSD from a USB flash drive. I followed all of the on screen prompts including a guided partition. Was then told to remove the installation media (USB flash drive) and reboot, which I did. Now I'm faced with a load of fast moving programming code that stops dead and refuses to go any further when it gets to the following line.


[B]3.323635] Adding 8245244k swap on /dev/sda5. Priority: -1 extents: 1 across 8245244k SSFS

[/B]
It would appear to be attempting to add the swap partition but I can't work out why it doesn't want to proceed any further. This installation is now becoming tiresome and I'm beginning to think that Bill Gates isn't such a bad chap after all. Can anyone help please?

---

### Post by MAFoElffen on 2015-03-06
That is the boot messages (not programming code).

So I gather that yon installed 14.10 and during the install, it did not say there were any errors. Then on the first boot after the install, it stopped with that message as the last line before_______________________ <-- It just froze up there?

That could mean that it had problems at the "point it time"... Which means that it might have had problems with the swap, but not as likely as that it had other problems about that time or after that step in the boot process.

I'm on my way out the door so I can't get int much detail in the next few minutes, but--
Please post a little info about what the hardware is (make & model). Please tell me if it boots into a "try" live image succesffuly.

I'll check on this thread later and tell you would I would need from running in a Live image...

(Bill Gates lives near here... My little brother used to work for him... No comment...)

---

### Post by stuart16 on 2015-03-06
Hi, and thanks for responding. I'm using LinuxLive USB Creator to place a bootable *.iso for Ubuntu 14.04 onto a Sandisk Extreme 32Gb USB 3.0 flash drive. As part of that process, it's formatting the stick as FAT32 which, I presume, is the correct thing to do. Then I'm plugging that into a USB 3.0 port on the new build, accessing bios and selecting the Sandisk flash drive as 1st boot device. So far so good. Installation begins and appears to go through the entire process with no indication of error. At the end, the on screen message says that installation is complete and tells me to remove the installation media and then reboot. I take out the Sandisk and press reset. Then, on restart, the boot messages begin to appear but stop at that point I mentioned before. As far as I can tell, the installation process appears to run as it should until I get to the reboot and these boot messages.

I'm assuming that by 'live image' you mean the try without installing option. Yes, I've had a go at that one too but that will not work either. I'm at a loss to know whether there is something wrong with my build, or a faulty flash drive device, or some corruption in the OS software. Perhaps I should also say that the attempted installation is to a totally blank SSD with no Windows on it at all.

Hardware wise, I'm using ~

CPU: Intel i5-4460
motherboard: Gigabyte Z97X - Gaming 5
ram: Kingston HyperX fury ( 2 x 4Gb) so 8Gb of ram altogether
graphics card: EVGA Geoforce GTX750ti SC

Any useful suggestions for a fix are welcome because if I can't sort this out soon I'll be forced to abandon Linux and install Windows 7 instead.

Cheers! Stuart.

---

### Post by MAFoElffen on 2015-03-06
Did it install or just on reboot that you got this? I'm thinking if it installed normally without know the below, you were lucky... High-end nVidia graphics cards need a few specifics to help get through the hurdles...

On a LiveUSB, you get a Grub type menu at the first part of the boot process. 

If, at that menu, you press <E> to get into an edit mode, then press the <down arrow> until you get the start of the kernel boot line. That line starts with the word "linux". Do the install

Go the end of that line and appnd it with "nomodeset". Press <X> and boot. Install.

After the install, you have to repeat the above again... just until you get the nVidia drivers installed.

After it boots, go to: System Setting > [COLOR=#333333][FONT=UbuntuRegular]Alternative Drivers... then install the recommended driver for your nVidia card.

Tell me how it goes.[/FONT][/COLOR]

---

### Post by oldfred on 2015-03-06
Two know issues.
Gigabyte boards seem to need IOMMU setting in UEFI.
And nVidia 750 series is new and needs the very newest kernel, support software & nVidia drive from a ppa.

 Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)

      
 Maxwell 750 - kernel 3.15 required
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)
[http://ubuntuforums.org/showthread.php?t=2265505](http://ubuntuforums.org/showthread.php?t=2265505)
Usually better to use PPA.
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)
[http://ubuntuforums.org/showthread.php?t=2257506](http://ubuntuforums.org/showthread.php?t=2257506)
[http://ubuntuforums.org/showthread.php?t=2261714](http://ubuntuforums.org/showthread.php?t=2261714)
[http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1](http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1)
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1)
 open-source driver support for Maxwell, there's none right now, at least not mainline.  Feb 2014

---

### Post by stuart16 on 2015-03-07
Thanks for trying to help chaps but I can't be bothered with this anymore. I don't understand much of this computer speak and to be perfectly honest I have no interest in learning, what to me is, another foreign language. I'm one of those people that expects to install something and then it just works. I didn't expect to have to do major tweaking to get it to work properly and I just don't have the patience for this. There seem to be an awful lot of people on here asking for help because they can't get this thing to run properly, which suggests to me that it's more problematic than it's worth so I've now loaded and installed windows 7 and it works straight out of the box. Thanks again for trying to help but plan to switch to Linux now abandoned.

---

