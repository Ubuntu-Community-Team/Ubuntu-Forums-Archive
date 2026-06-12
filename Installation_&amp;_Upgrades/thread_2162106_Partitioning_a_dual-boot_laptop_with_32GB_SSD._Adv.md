---
title: "Partitioning a dual-boot laptop with 32GB SSD. Advice requested"
date: 2013-07-13
forum: Installation &amp; Upgrades
---

### Post by skamarla on 2013-07-13
Hi,

I just bought an HP envy 6-1050ss. It's got a 500 GB disk + a 32 GB SSD. It comes with Windows 7 preinstalled (not 8, yay!), and I intend to keep it as a dual-boot, although my primary OS will be Kubuntu. I still depend on Windows for a few things. The current partitioning is as follows:

/dev/sda1 199 MiB  name:SYSTEM (bootable)
/dev/sda2 446 GiB  name:OS
/dev/sda3 19,47 GiB  name:Recovery
/dev/sda4 108 MiB name:HP_TOOLS

/dev/sdb1   6 GiB allocated
/dev/sdb has 23,82 unassigned GiB.

From what I've seen, Windows is using just 6 GiB of the SSD as a hibernation partition. The rest goes unused.
I think I'd better not mess up with all the tools, recovery and system partitions, because I've had problems in the past moving these OEM setups; they tend to want the same things in the same place.
On the other hand, this 32GB SSD is screaming for a more optimal use. An SSD just for hibernation????

So, my plan right now is:
- move the Windows hibernation file to C:\ or create a new hibernation partition on /dev/sda
- resize /dev/sda2 and make room for Kubuntu /home
- use /dev/sdb1 as kubuntu root.

Now, for the questions:
- any drawbacks to the plan?
- how will Windows react to Grub taking up boot control?
- can you suggest a partition plan? I intend to leave some 150 GB for Windows, and the rest will be for Ubuntu /home, /tmp, and whatever is not advised to be in SSD.
- I have 6 GB of RAM. Do I really need to reserve 12 GB for swap?

Thanks in advance,

---

### Post by Mark Phelps on 2013-07-13
My guess is you are using MBR BIOS, not UEFI -- in which case you can NOT create any more partitions on the HDD. The four there already max out the limit.

You could move the HP_TOOLS stuff into an existing partition and remove that -- but that is so small as to be all but useless.

IF you plan to shrink down the Win7 OS partition to make room, be sure to use the Win7 Disk Management tool --NOT the Ubuntu installer or any Linux filesystem utility.

IF you don't feel comfortable using the Win 7 Disk Management tool, then download the MiniTool Partition Wizard Boot CD, burn a CD from that ISO file, and boot from that.  That is a full-feature Windows partitioning tool.

Also, BEFORE you mess around with installing Ubuntu, do yourself a favor, download and install the free version of Macrium Reflect (MR), burn the MR Linux Boot CD, and image off Win7 (including the boot partition) to an external drive.  That way, if anything goes wrong during the dual-boot setup, you will have a way to restore Win7.

---

### Post by oldfred on 2013-07-13
+1 on Mark Phelps suggestions.

I have seen the Intel SRT mostly with the new UEFI systems. Is your also an UltraBook with dual video? 
The link in my signature is on UEFI systems, but also has some info on Intel SRT.
I thought the SSD was not just hibernation but to speed up some Windows activity also. Some have installed Ubuntu to the SSD, others have installed to hard drive and re-enabled SRT.
Intel SRT uses RAID somehow which you have to turn off.

Since you are still BIOS you will need to delete one partition on hard drive to make a new extended partition. Most delete HP tools.

       Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

    
  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

      
 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by skamarla on 2013-07-13
Good point on the four partition problem. I have found this [ posting]("http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/Delete-HP-Tools-Partition/td-p/479927") that gives instructions on deleting the HP_TOOLS primary partition, and then put it back as a logical partition.

I have already shrunk the C: partition from within Windows. It didn't shrink enough on first try, so I followed [this guy's suggestions]("http://www.brandonchecketts.com/archives/how-to-shrink-a-partition-with-unmovable-files-in-windows-7").

I'll take your advice and take the image off Win 7, just in case. The only problem is that the machine doesn't have a DVD; I'll have to get a USB DVD drive.

I am not sure that this has Intel SRT. It's an Ultrabook (15,6" screen, but it's got an Ultrabook sticker) and it's got a discrete Radeon card.

From some of your links, it seems that Intel SRT needs a proper partition to do its cache thing, but this one only has a 6 GB hibernation partition. Is there any way to make sure? That would be one less hurdle.

---

### Post by oldfred on 2013-07-13
You can image to flash drive. I now use flash drives for some backup, but still like to have a (more) permanent backup to DVD.

Because the Intel SRT uses the RAID, the liveCD does not see the partitions correctly. I think if you install the RAID driver dmraid it may show it. Gparted did not work with RAID at all, but the very newest works with some RAID types, but you have to download the very newest gparted liveCD as that verson is not in the Ubuntu live installer yet and would not be in any of the older verisons of Ubuntu.

       [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

### Post by windows2003 on 2013-07-13
Hi, 

You can also work on different way like I do with mine notebooks and stand alone computers.

Place your windows completely on 1 hard-disk and place your linux on the second hard-disk.

1. First go into your BIOS, go to Tab Main and enable Boot Menu option.
2. Just put for installation the empty HD into computer and install your favorite linux OS.
3. After installation, you put back your Windows HD into computer together with your Linux HD.
4. If you start computer, press the key so you can choose by bios wich HD you want to start. (for mine Acer I need to press F12)

This  is a handy way to install a second OS into your laptop...The linux  installation will never affect the windows & the windows never the  linux installation.
You don't need to worry about the bootloader from  linux neither the loader from windows, the bios does do the work for  you. If you've a 3th HD for laptop, you just put one out, work the same  way...
So, you can always change from Operating Systems. For mine  work I use Windows & ubuntu, but when I"m on holiday, I want the  same notebook but with a harddisk debian and ubuntu...this is possible  if you work like that.
If you do a complete upgrade, don't be scarry..it is one notebook with complete shielded HD's if you not make references to it!

The  hard-disk you put on sata sleeve 0 will be the first started if you not  interrupt the computer with F12 (for other computers this can be other  F-key), so I suggest you put there the one you most use, the other OS  you put then into sleeve1.

Positive:
1. If you have 2 - 3 - 4  -....harddisk and you work like that, then you can install on each hd an  OS and you can always choose wich OS you want, if you go on travel...
2. Don't be scare about Windows bootloader or Linux Grub loader, the Bios let you chose wich HD you want to start!
3. If Linux crashes or windows, don't be scare it affect an other HD.

Negative:
1.  In most notebooks you can place 2 HD, so if you want to put an other HD  into it, you need to open your notebook, and replace a HD.
2. When  notebook start, you need to press the F-key so you get the BIOS bootmenu  option for chose wich HD you want to start...by default he starts the  one on sleeve0

I work no already some years like this and I did  configure 3 HD for mine notebook Windows7 - Ubuntu 12.04 - Debian. I can  always put 2 from them into mine system...and I've also a 4th HD wich I  also did install, but this is for testing things....

Hopes mine english is good enough to explain,how I did do it!

---

### Post by skamarla on 2013-07-14
I am attaching two screenshots of how Gparted 1.16.1.1 sees both disks. I see no sign of RAID, here. The warning sign on sdb (the SSD) is because Gparted doesn't recognize the partition type (hibernation).

However, looking at the BIOS, it does say "Intel Rapid Start Technology" is <Enabled>.

As for UEFI, the BIOS seems to suport it, but Legacy Support is enabled. According to the inline help, this mean that the BIOS will load Compatibility Support Module to support Legacy OS such as Windows 7, ... If Legacy Support is disabled, BIOS will boot in UEFI Mode without CSM to support Windows 8.

UEFI, being disabled by default, doesn't seem to be a problem. Will RST be?

---

### Post by oldfred on 2013-07-14
The newest versions of Ubuntu seem to install to systems with Intel SRT(older versions did not), but often grub then still does not work with RAID with standard desktop installer. Grub sees RAID on the hard drive and does not know whether to install to a MBR or to the root of the RAID. If really standard RAID it does not install to MBR, but you need it installed to the MBR. The drmraid commands posted above to remove the RAID meta-data will let you then correctly install grub2's boot loader to the MBR.

Be sure to boot Ubuntu in legacy mode. You should get accessiblity screen (tiny icons of person & keyboard) at very begining. If you get grub menu at startup you are in UEFI mode. It installs it the mode you boot installer.

---

### Post by skamarla on 2013-07-14
After some more research, it *is* using Intel RST, with RAID and everything. [This link]("http://h30434.www3.hp.com/t5/Notebook-Hardware-e-g-Windows-8/Brand-new-Envy-dv7-7212nr-missing-SW-or-config-for-SSD/td-p/2270455") explains the setup. The part of the SSD used for raid doesn't show as a partition, but the Intel RST driver is using it. I am attaching a screen capture of the setup: 6 GB for hibernation, 24 GB for RST.
[ATTACH=CONFIG]244719[/ATTACH]

So, after reading everybody's advice and links, let me see if I have got right. I have three options:
[LIST]
[*]adding a new hard disk, just for Linux. Sorry, it's a new computer, and I really don't need that much disk space.
[*]keep Intel RST, leave the SSD to it, and install Ubuntu in the mechanical hard drive as if the SSD didn't exist. This has a caveat, since that RAID setup may fool Grub, so I need to disable Intel RST temporarily, use the drmraid commands oldfred posted to disable RAID, install Ubuntu, and then re-enable it.
[*]disable Intel RST, disable Windows hibernation (and re-enable it after installing Ubuntu), and install Ubuntu in the SSD. I'm inclined to do that. After all, the goal is having a fast computer, that's why I'm installing Ubuntu, after all.
[/LIST]

Whatever I do, I have to remove at least one of the four partitions that HP creates in new systems; I plan to remove the HP_TOOLS and create it back as a logical partition. Thanks for the pointers for disk image tools; I'll see if I can use them from a USB hard drive I have around.

As for the rest: the computer is certainly booting in Legacy mode; I got the person and keyboard icon; I had to set acpi=off, by the way, but that will be another issue.

Thanks a lot, I'll keep you posted

---

### Post by oldfred on 2013-07-14
If you are primarily a Windows user then I would keep the Intel SRT. But if primarily an Ubuntu user then installing / (root) to the SSD and not re-enabling SRT make make more sense.

I typically install Ubuntu into a 25GB / on my stand alone SSD and have all data on my hard drives. But I keep /home inside / as I link all the standard folders back into /home so /home is tiny. That is a bit more advanced, so a separate /home on rotating drive is easier to configure and use for newer users.

---

### Post by skamarla on 2013-08-02
I took up the installation again yesterday, and it's still a work in progress. I think my experience may be useful to someone else, so I'm going to give you an update:

I have to say that this installation is being a real pain. I installed Ubuntu two weeks ago in a Windows 8 Lenovo and everything worked on first try, despite all the UEFI stuff. Installing it in a Windows 7 was supposed to be easier but HP is making it really really hard.

About repartitioning: I found [a well-documented posting]("http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019") in an HP forum, and I followed this guy's advice to remove the System partition, instead of HP_TOOLS. I had to waste a 32 GB pendrive for the Windows repair disk, but so far it's getting heavy use...

So I created this repair disk (BTW, you only get to create one, you know, that wonderful copy-protection scheme and whatnot), deleted the system partition, and, sure enough, Windows didn't boot. The next step was to run the "startup repair".

But HP has changed the look and feel of its "Recovery manager" (what you get when you create a repair disk ), and "startup repair" just isn't there. It does give you the option of "doing maintenance" and opening a command line. After some searching, I found  bootrec /rebuildbcd. That fixed Windows. I now had a three partition system where I could install Ubuntu.

Then I started the kubuntu installation, but the installer didn't find the SSD. gparted and fdisk saw it, but the installer didn't. I remembered that I had to disable Inter SRT from the BIOS, but it still didn't work. After some more fiddling, I saw [this thread]("http://ubuntuforums.org/showthread.php?t=1484448"), and sure enough, it seems that RAID had left some metadata on the SSD. After running [FONT=courier new]sudo dmraid -r -E /dev/sdb[/FONT] (sda is the traditional HDD, sdb is the SSD), the installer recognized the SSD.

The installation worked just fine, with root on /dev/sdb, and swap and home on /dev/sda, but now I just can't boot Kubuntu. I know it's there, but the computer is always booting Windows. Kubuntu installation gives you the option of installing the bootloader in /dev/sda or /dev/sdb, and I've tried both, but it still doesn't work. The BIOS only gives you the option of booting from the "netbook HDD", not the SSD.

I'll try to post another question in this forum and see how it goes. I'll keep updating this thread until it's solved.

---

### Post by oldfred on 2013-08-02
If you install grub to sda, you cannot be booting Windows as it will overwrite the Windows boot loader in the MBR. Not sure if the RAID will resync sda boot and sdb boot sectors as I do not fully understand how that Intel SRT works.

---

### Post by skamarla on 2013-08-02
I don't think it was RAID; I had disabled Intel RST and removed the RAID metadata before.

Finally, the winning stroke was [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). I booted into the Live CD, and, instead of reinstalling for the umpteenth time, I installed Boot-Repair's apt-repository, and boot-repair itself, as explained in the "second option" of the [previous link]("https://help.ubuntu.com/community/Boot-Repair"). Then, it was just a matter of launching it, answering a couple of easy questions (is /dev/sdb internal or external?), and letting it do its magic.

I think the problem is in the Kubuntu installer. It's probably fooled by the root folder being in a secondary disk, which must remain secondary, because even the BIOS can't consider booting from it. Kudos to the authors of boot-repair, and grub2, for being flexible enough to detect and correct the situation.

Now I have a very fast netbook. Windows is OK, there is no noticeable slowdown from its losing the SSD cache, and Kubuntu is lightning-fast. Not just boot; even Libreoffice pops up surprisingly fast. The 32 GB are more than enough for the root partition, and most of the HDD has been assigned to /home.

Thanks everybody

---

