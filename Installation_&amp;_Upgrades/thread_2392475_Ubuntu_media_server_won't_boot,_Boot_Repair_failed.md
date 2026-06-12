---
title: "Ubuntu media server won't boot, Boot Repair failed to fix - please help!"
date: 2018-05-21
forum: Installation &amp; Upgrades
---

### Post by daves00 on 2018-05-21
Hi All,

My first time I've needed to post, and am hoping someone can assist and save me losing 2 TB of media :(

I used synaptics to apply a couple of minor application level updates to my Ubuntu 14.04 - its the only version of Ubuntu that has driver support in quiet mode for my HP Microserver smart array coontroller
I tried to stream a movie via an xbox to my TV. This locked, and so reboot xbone, reboot Ubuntu - then disaster
The ubuntu booted, failed to fidn the network (dodgy cable) and auto reconfigured the network from Eth0 to em0 (?), carried on booting services, but never showed a login prompt.
The ubuntu runs no graphical interface on the local machine, but does run a VNC server, which no longer responded due to the network auto-reconfigure I presume
Unable to shutdown I had to hit the big red button and force shutdown, restart, rinse , repeat.
I booted into recovery mode and that came up ok, shut the system down.
Today on boot I get a grub error - unable to boot. After googling I grab a copy of Boot Repair, push the ISO to a pen drive, boot to pen drive and run, up comes Boot Repair.
Under advanced I backup the partition info and save to /tmp - this works ok
I then let it auto repair - and failure, the same grub error "unknown file system" and the grub rescue prompt

I'm hoping someone out there can help - although i work in IT its Microsoft stack (i know, boo hiss!) and with linux this is over my head!

pastebin is [https://paste.ubuntu.com/p/rzrxvWXfvQ/](https://paste.ubuntu.com/p/rzrxvWXfvQ/)

The Linux is pretty basic - nothing fancy other than the HP drvier for the smart array. Minimal GUI installed.
Other items installed:
Samba 
Mediatomb
Plex
Grub coinfig tweaked for screen resolution, otherwise left at system generated values.

Installer recommended partitioning used. The main media drive is of course the 3.7 TB partition. 
If all else fails to resolve the boot issue,  simply gaining access to the media partition and backing up would be great!

Thanks in advance for any assistance
Dave

---

### Post by oldfred on 2018-05-21
Something really wrong with drives, were they always mis-configured?

MBR(msdos) partitioning goes back to the 1980's when MB was large, GB unheard of with a PC. So MBR has a hard limit of 2TiB way beyond any drive considered.

But you have two 4TiB drives. And with those you need to be using gpt(GUID) partitioning. 
Some may have a proprietary driver to make use a large drive. That often was for compatibility with XP, but does not really work with Linux.
Some have just used MBR, and not noticed drives were really on 2TiB in size.

       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[URL="http://en.wikipedia.org/wiki/GUID_Partition_Table"]http://en.wikipedia.org/wiki/GUID_Partition_Table
      [/URL]
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT) 
    
If you save to /tmp it is erased on reboot. Best to save data to an external drive.

With gpt partitioning you need either an ESP - efi system partition for UEFI boot or if older system, you need a bios_grub partition for BIOS boot. Grub will not correctly install without one or the other supporting partitions to match boot mode.

       [https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/](https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/)
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html) 
    

[URL="http://en.wikipedia.org/wiki/GUID_Partition_Table"]
[/URL]

---

### Post by daves00 on 2018-05-22
Hi Oldfred,

Thanks for the info.

Are they misconfigured or just mis-labelled? The  microserver is circa 2012 when i built it, and pretty much accepted the  default partition layout therefore it must have used GPT surely? - I did  have to build it 3 times before i got the HP smart array driver to work  - but wiped it between each of those builds.

/tmp - thanks for  letting me know .. I didn't have a spare usb slot to plug a drive into.  As the machine won't boot - only to grub (and i used "boot repair" to  try and fix it) perhaps the partition info backup hasn't been cleared  from /tmp? I'll boot a linux distro from USB again and see if the folder  has been wiped.

With the messed partitioning sounds like a  rebuild. Is there any utility that is likely to be able to copy data  from the 3 TB partition or is that going to be doomed?

Thanks
Dave

---

### Post by oldfred on 2018-05-22
Does testdisk show anything? If deeper search shows files that would be better.
If not perhaps photorec, but with your large drives it may take days to scan a drive.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
       [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step) 
    
I have used photorec. I accidentally deleted a folder. I had backups, but a bit older. It took all night on my 640GB drive for photorec to scan it. And it only recovers files by type, not full name. It took me weeks to find & compare recovered files with backups. And same file was saved/replaced many times & photorec found every old copy, so difficult to know which was newer.

Back in 2012 a lot of partitioning tools were not gpt aware. You had to use gdisk. Newer copies of gparted/parted worked, but fdisk has only been updated in the last year or so to know & use gpt drives. Windows 8 was released in 2012 and required UEFI with gpt partitioning, so many tools were updated.

---

