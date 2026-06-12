---
title: "How To Move GRUB From sda to sdb Using Boot-Repair-Disk (Boot-Info Linked)"
date: 2023-11-19
forum: Installation &amp; Upgrades
---

### Post by spode2 on 2023-11-19
I have a dual-boot system, sda has Windows7 plus some storage partitions. The other disk sdb, has Xubuntu 23.10 and is the default boot.

The GRUB boot menu has not appeared since I installed Windows 10 as a guest OS in VirtualBox on Xubuntu. I would like to move GRUB from sda to sdb to create a single boot system, and then re-purpose the W7 partition.

I have not used Boot-Repair-Disk before, and would like some advice as to whether this will be a straightforward operation.


[https://pastebin.ubuntu.com/p/skCcmHWPcW/](https://pastebin.ubuntu.com/p/skCcmHWPcW/)

---

### Post by oldfred on 2023-11-19
It looks like the default suggestion by Boot-Repair is reinstall grub to sdb.
Typical to reinstall grub to different drive, you need to use Boot-Repair's advanced mode and choose drive.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Not sure why is dumped a lot of code into report. I only occasionally see that.

You have old BIOS/MBR configuration that uses grub-pc.
The only time you need MBR(msdos) is for Windows drive in very old BIOS boot mode.

Since Microsoft required vendors to install in UEFI boot mode to gpt partitioned drives in 2012, most systems are UEFI. 
And then better to install both Windows & Ubuntu in UEFI mode to gpt partitioned drives.
You can also have Ubuntu in BIOS boot mode on gpt drive, but have to have bios_grub partition.
I started conversion to gpt with old BIOS only systems in 2010.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[gpt Advantages]([http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by spode2 on 2023-11-19
oldfred,

Thank you for the reply. The machine originally came with Windows 7, so the motherboard is quite old. I added another hard disk and installed Xubuntu on the new disk. I want to move GRUB to sdb so, from what you say, it sounds as if the default action will do this.

The important thing is that I do not want to do a new install of Xubuntu. It works fine, and has had many years of customisation. I do want to replace the motherboard at some stage, and that might be UEFI only, so I would like to know how to convert to gpt, if that is possible without a new install.

---

### Post by oldfred on 2023-11-19
If concerned, you must have good backups.
Good backup would allow you to restore system in about an hour. We spend days trying to help some users recovery from various issues that good backup would have allowed easy recovery.

You cannot easily convert from MBR to gpt. Best if new blank drive. That is why I started conversion back in 2010 with every new or totally reformatted drive including larger flash drives. You may want new drive, for backup anyway.

If you use gparted or most other tools to convert to gpt, the drive will be totally erased.
There is gdisk that supposed will convert drive from MBR to gpt, but at minimum you have to add a bios_grub partition for BIOS boot or an ESP - efi system partition for UEFI boot. And then reinstall grub.
 For years when first converting to UEFI, I had both bios_grub & ESP on every drive, but really only needed one or other.

My 2006 laptop had to be pulled out of closet. It last had 12.04 as main install. I had installed 20.04 Kubuntu just to see if it worked. It was ok, but slow as system only has 1.5GB of RAM and old slow HDD. Both batteries are dead, so if I unplug it I have to reset time & some settings in BIOS.
But I was able to boot my full Kubuntu UEFI install on external SSD by adding a boot stanza to laptops internal drive to directly boot install. That worked surprisingly well for old system.
Really recommend SSD for boot or external drives.

---

### Post by spode2 on 2023-11-19
Thanks for all the advice. I intend cloning the drive and then converting the clone. I hope that by the time I get around to it someone will have written an idiot's guide on how to do it with gdisk.

---

### Post by oldfred on 2023-11-19
Best to start with blank drive.
Better to convert data only drives. Its the after conversion of new UUIDs, GUIDs.
If bootable drive, then reinstall of grub and fixes to every entry that uses UUIDs, mostly fstab but some other files that you may not always know about until you have an issue.

Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)
sudo sfdisk -d /dev/sdc > backup_sdc.txt
sudo gdisk /dev/sdc
Used r, l, o, g, p, and w (write) or q to quit

---

### Post by MAFoElffen on 2023-11-19
I was driving by and read this... And am now confused by this statement:
> **spode2 said:**
> The GRUB boot menu has not appeared since I installed Windows 10 as a guest OS in VirtualBox on Xubuntu.
??? I do not understand how install a guest OS, affected the booting of your VM host. This would a big problem if a Virtual Machine is violating it's limits outside of it's sandbox... But that is another problem that needs to be addressed after oldfred gets you going again...

Does you Grub2 menu not appear anymore? What does it do now when it boots? Just goes straight to an OS? Which one? Or does it not boot at all now? I don't see where that was said or described.

If all you wanted to do was to straighten out Grub2, and Win7, and keep them isolated, then what I would do is, with the power turned off, at both the switch and PSU, open the case, unplug the /dev/sdb drive... Boot from a Win7 install disk and repair the boot using startup repair...

Then after that is working... Shut it down plug /dev/sdb in and unplug /dev/sdb. Boot from the Boot Repair Disk and let it reinstall Grub2 on /dev/sdb... After that is working shutdown...

Plug both drives in. Go to the BIOS Setup and point to the /dev/sdb drive so it boots to Ubuntu. After it starts
```

sudoedit /etc/default/grub

```
Change these lines...
```

GRUB_TIMEOUT_STYLE=menu   # Change to this
GRUB_TIMEOUT=2   # Change to this
GRUB_RECORDFAIL_TIMEOUT=2   # Add this
GRUB_DISABLE_OS_PROBER=false   # Change to this

```
Save and exit.
```

sudo update-grub

```
Watch to ensure it see's your Win7 and adds it to the menu...

Then you /dev/sda it unaffected from what it was originally for Win7, as a standalone. Disk /dev/sdb will then include starting Win7 in the Grub2 menu, and the menu is forced to show, for at least 2 seconds... You can adjust that time to whatever you want.

Test that. If that is resulted... Please, lets investigate how an VM Guest install crashed your VM Host.

---

### Post by spode2 on 2023-11-20
I am not sure what happened, but I have limited understanding of how dual booting works in any case. It looks as if Windows installer treats the virtual machine as one thing, but also looks around to see what else it can mess with. I know this is why Windows has to be installed first when creating a dual boot system, but it did not occur to me that it would interfere with grub during a Virtualbox install.

Nothing crashed. It took me a while to realise that the grub menu was not appearing during boot, but it was set to a 1 second timeout anyway, as I rarely used it, and I don't need it now. The menu has been changed radically, but Ubuntu is still the first item on it and that is what it boots to.

I [ATTACH]293091[/ATTACH]

Just for interest, I have tried to attach the Grub Customiser display, as I do not know how to get the same information from the command line.

---

### Post by yancek on 2023-11-20
Dual booting would generally be a situation where you have 2 or more operating systems installed on hardware.  Some people say installing on virtual software is dual booting but the problem with that is if you cannot boot the host system, you cannot have access to the guest .  Installing windows or any other OS in virtual software will not effect the bootloader on the host system.

The image you posted shows an entry for windows 7 and entries for Ubuntu and your boot repair does not show any reference to windows other than 7 so if your Grub menu disappeared, it was for some other reason.

Windows does not need to be installed first but generally it was a good idea to do so on pre-UEFI installs as windows would overwrite the MBR on the dirve without asking or informing the user.  If the other install was a Linux system, it would then be necessary to reinstall Grub or whichever Linux bootloader was being used.  With newer UEFI systems, this isn't a problem as boot files are stored in separate directories in the EFI partition for each OS and not overwritten.  The most likely change a user would need to make would be the drive/OS priority in the BIOS firmware.  If you are not familiar with UEFI, you will need to be when you get a newer computer as manufacturers are selling computers now without the capability to boot in what we refer to as Legacy mode.f

---

### Post by spode2 on 2023-11-20
Dual booting is what I have but, without the grub boot menu showing up, I can't boot to Windows 7. That doesn't matter, because I want to get rid of Windows 7 and re-use the space. Although I thought Boot-Repair-Disk had solved the problem, it hasn't, and the system still boots from the sda drive, even though the BIOS boot order has sdb first. The sdb drive does not show as bootable. I think I am going to have to physically disconnect the sda drive and then try running Boot-Repair again.

---

### Post by MAFoElffen on 2023-11-20
If you make the edits that I suggested to your /etc/default/grub defaults file, that will force the Grub2 menu to show on boot up.

---

### Post by spode2 on 2023-11-20
You are right MaAFoElffen. The reason the Grub Menu was not showing is that GRUB_TIMEOUT_STYLE='menu' had somehow got changed to 'hidden'. It could be connected with the 23.10 upgrade, or it could be because the OS prober was enabled while installing the VM OS. Sorry, that has been a distraction from my main question.

I still have to work out how to convert to a single boot system when the W7 OS I want to delete is on a different disk from the Ubuntu OS and both disks are MBR. It looks to be dead easy when the OS's are both on the same drive, but whatever Grub puts on the Windows drive really does not want to move.

---

### Post by grahammechanical on 2023-11-20
There is something that you can try.

Load Xubuntu on sdb. Open a terminal and run

```
sudo grub-install /dev/sdb
```

and

```
sudo update-grub
```

Watch the printout to see if it detects Windows 7.

That will put Grub on to sdb and with sdb having boot priority should give you a Grub boot menu. Another way to bring up the Grub boot menu is to hold down the shift key during the boot process.

Regards


Regards

---

### Post by oldfred on 2023-11-20
What does this show? Look for drive entry:
sudo debconf-show grub-pc
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short 

you can run this, have to use tab & enter keys.
sudo dpkg-reconfigure grub-pc
sudo update-initramfs -u -k

---

### Post by spode2 on 2023-11-21
Grub-install makes no difference. I think it is the bootloader which needs installing on sdb but, as I still don't fully understand how legacy boot works with multiple drives, I am reluctant to go any further without cloning the drive first. I have another drive on order. It looks as if moving that boot asterisk from one drive to another is not so easy, and I may have to think about a new install with EFI. 

In the meantime, thanks for all the advice.

---

### Post by yancek on 2023-11-21
Your boot repair output shows that you have Xubuntu installed on sdb and that you installed Grub boot code in the MBR of sda.  Linux installations using Grub will give you the option of which drive to select to install the Grub bootloader.  The default is to the MBR of the first drive (/dev/sda) which is what happened in your case.  There would have been an option under device for bootlader installation to select /dev/sdb.  Apparently you did not see this.

Doing a grub-install from Xubuntu to /dev/sdb should have resolved the problem.

> I think it is the bootloader which needs installing on sdb   

Grub is the bootloader.  GRUB is an acronym for Grand Unified Bootloader.   Also, the boot asterisk means a partition is marked as active, something which has always been requred by windows systems for boot partitions but has never been needed with Linux so that doesn't matter if you are not going to use windows.

---

### Post by spode2 on 2023-11-21
This is an old installation. Windows 7 was the original OS, and I added another disk (not at the time a ssd) for the Xubuntu install. The Linux installer chose where and how to install grub, and I went with the defaults.

I assumed that sdb partition would have to show as bootable before I could safely delete the bootable Windows partition. From what you say, that is something else I have misunderstood. I will change the BIOS boot order and see how it goes.

---

### Post by spode2 on 2023-11-21
So it turns out that all I needed to do was install grub on sdb, disable OS prober, and disable sda drive as a boot option in BIOS.

---

