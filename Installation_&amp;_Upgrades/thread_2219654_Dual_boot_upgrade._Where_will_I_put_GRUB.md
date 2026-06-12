---
title: "Dual boot upgrade. Where will I put GRUB?"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by benawhile on 2014-04-24
I have dual boot Ubuntu 12.04 and Windows XP.
I want to choose the "something else" install option as I want to do some resizing of partitions.
I am apprehensive about where to install grub on my machine. I guess I will be asked where to put it by the installation program. I have a partition for it which is not within the extended partition. I can't remember if I made that partition prior to installing ubuntu or if ubuntu made it. Is it the MBR?  I thought the MBR had to be at beginning of the HDD. It is listed as /dev/sda3 but mounted at /boot. Can anyone explain that?
Some sources on the internet talk about installing grub in the extended partition, and some even say install it in two places. I dont want to do that as my system works as it is. What pitfalls will I encounter during installation?

  [ATTACH=CONFIG]252474[/ATTACH]

---

### Post by oldfred on 2014-04-24
Computers only boot from the MBR, so you install grub to the drive that is sda.

From my install where I am creating / in an existing partition with an old install. It shows sda as the location for the grub2 boot loader in the combo box at the bottom.

       Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by Bashing-om on 2014-04-24
benawhile; Hi !

In addition to oldfred's last; consider these venerable sage words:
> 
Sharing /boot is more complex and generally not a good idea, especially as Ubuntu defaults to using no separate boot partition. A separate /boot is something of an anachronism, dating back to limited PC BIOSes that could only handle small disks, so the boot files had to be at the start of the disk. Nowadays, this is no longer applicable and I don't use a boot partition on anything. 
&&

If you want to install GRUB2 to the boot sector of a partition for some strange reason, you may use something like /dev/sda1 or /dev/sda2 for writing GRUB's boot.img to a partition boot sector. The practice of installing GRUB2 to partition boot sectors is not encouraged. It reduces GRUB's reliability and it could be dangerous to other operating systems if users use the grub-install command carelessly or ill-informed and write GRUB to the wrong boot sector.


And besides, taking out that /boot partition saves you a primary partition that perhaps would have better uses .

That only leaves, as oldfred advised, the 1 option, install grub to the MBR of sda. ubuntu's grub will pick up the Window's install and chainload Windows Booting onto grub's boot menu ( 'sudo update-grub' in terminal just to make sure).

[INDENT][INDENT]workie great
[INDENT][INDENT][INDENT]last long time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by benawhile on 2014-04-25
Sorry oldfred, I don't understand. Your screenshot shows you have biosgrub in /dev/sdd2. Also, in my screenshot, the only sda is the 6GB unallocated space. Have attached two more shots with the appropriate partitions highlighted.

NAME   FSTYPE   SIZE MOUNTPOINT        LABEL
sda            74.6G                   
&#9500;&#9472;sda1 ntfs    19.5G /media/sda1       
&#9500;&#9472;sda2 ntfs     4.9G /media/New_Volume New Volume
&#9500;&#9472;sda3 ext3     286M /boot             
&#9500;&#9472;sda4            1K                   
&#9500;&#9472;sda5 swap     2.3G [SWAP]            
&#9500;&#9472;sda6 ext4    18.6G /                 
&#9492;&#9472;sda7 ntfs    23.3G /media/sda7       
sr0           413.6M                   
ben@BENCOMPUTERUBUNTU:~$

---

### Post by carl4926 on 2014-04-25
Just set grub to sda
Like in this image
[https://dl.dropboxusercontent.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png)

---

### Post by carl4926 on 2014-04-25
FYI bios_grub is for gpt partiton tables,which you do not have

---

### Post by benawhile on 2014-04-25
HI, just seen your reply "The practice of installing GRUB2 to partition boot sectors is not encouraged." Fair enough, but I am sure I only did what I was advised from teh web somewhere, and probably didn't understand what I was doing!
"Sharing /boot" Is that what I have done then?:confused:
So should I wipe that partition or delete it?
So when I install I select the unallocated space /dev/sda and grub becomes the MBR somewhere in there? What would I have done if I had allocated all space when I did the original install?
Or does it work that I start out with the empty or wiped extended partition and grub is the first thing to install?

---

### Post by benawhile on 2014-04-25
Thank you carl2496, I think maybe I can follow that. Guess it's time to go ahead and do it!!! Thanks all.

---

### Post by oldfred on 2014-04-25
Sorry to confuse it with my gpt partitioned drive. That is the newer partition scheme required with UEFI or drives over 2TiB. 

But you have MBR(msdos).
Note that sda is the hard drive and the MBR is the very first sector of the hard drive. It is not part of any partition.
BIOS only boots from MBR which is tiny and has just enough boot code to jump somewhere else on drive to continue the boot process.

Drives are sda, sdb, sdc. Each drive has a MBR.
Partitions are sda1, sda1, sdb1 etc with the partition number it is on the drive. You almost never install grub2's boot loader to a partition and never to a NTFS partition.

Shows how Windows boots with BIOS on MBR based computers.
       Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Windows also uses the PBR or partition boot sector to boot. So all NTFS partitions have to have Windows boot code.

---

### Post by benawhile on 2014-04-25
Thanks oldfred. It's coming a bit clearer now. I was lucky then. I don't do much sophisticated stuff on this pc but have done lots of additions to ubuntu 12.04 through the terminal, and apart from a few freezes I have had no trouble at all with my dual boot set up since 2012. 
It's 5.30 am here, been up all night, so please excuse me, will catch up tomorrow.

---

### Post by benawhile on 2014-04-28
Hi
Some things I still would like to understand more fully:
Bearing in mind that I want to keep the original Windows installation on the HDD, and I am going to install GRUB in the MBR, how does the BIOS pick up GRUB if it isn't at the beginning of the HDD, assuming it isn't at the beginning because Windows XP is there in the first active primary partition?
And where will GRUB be installed? In the unallocated space at the end of the HDD?
Generally, what part of my HDD is referred to by /sda?

---

### Post by oldfred on 2014-04-28
If you only have one hard drive, only the boot loader in the MBR controls booting. And Windows is not designed to multi-boot other than other Windows installs. Some have convoluted work arounds.

But grub is designed to multi-boot. And worse case you can use Windows install or repair CD or flash drive to restore a Windows boot loader, or use Boot-Repair to add a Windows type boot loader.

Always best to have a repairCD or flash for the current version of every operating system you have installs. And know it boots.

When you install grub to sda, that is to the MBR of the drive that is seen as sda. The MBR is the first sector of the drive and before the first partition.

---

### Post by Bashing-om on 2014-04-28
benawhile; I give this one a whirl:


Here's an the long version of what happens when you turn the power on after the machine has been shut down for a while:

First, code in the BIOS chip on the motherboard gets loaded into memory automatically and begins running. Next, the Power-On Self Test (POST) code checks all of the hardware to make certain it's working. In the process it clears all of the RAM space except the very small part it's using to run the POST.

When the POST completes, the BIOS code then begins loading the operating system code into memory. 1st stage boot loader (generally located in the hard disk's MBR) is loaded into ram; It's only job is to load stage 1.5 into ram. This becomes a "chicken-or-egg" situation, since loading the code requires code to already be there and the BIOS chip isn't large enough to hold all of the necessary code. The solution, in most Linux distributions, is to create a pseudo-disk in RAM - through stages (1, 1.5 and stage 2), and load it with an abbreviated copy of the system that has all the things needed to load the full system, but nothing else (such as a normal user interface or keyboard drivers). 
 When all the stages are loaded into ram and executing -> linux image and the initial ram disk (Temporary root file system) are loaded into memory. When the images are loaded, the 2nd stage boot loader passes control to the kernel image and the kernel is de-compressed and initialized. At this stage, the 2nd stage boot loader checks the system hardware, inumerates the attached hardware devices, mounts the root device and then loads the necessary kernel modules.
 Once a boot option has been selected (grub's boot menu), grub loads the selected kernel into memory and passes control to the kernel.
Building grub:
GRUB 2 places its files in three core locations:
 /boot/grub/grub.cfg - This is the main configuration file, this file shouldnot be edited by hand!
    00_header is the script that loads GRUB settings from /etc/default/   grub, including timeout, default boot entry, and others.
    05_debian_theme defines the background, colors and themes.
    10_linux loads the menu entries for the installed distribution.
    20_memtest86+ loads the memtest utility.
    30_os-prober is the script that will scan the hard disks for other operating systems and add them to the boot menu.
    40_custom is a template that you can use to create additional entries to be added to the boot menu.

 /etc/grub.d/ - This directory contains GRUB scripts (those listed above). These scripts are building blocks from which the grub.cfg file is built. When the relevant GRUB command is executed, the scripts are read in a certain sequence and grub.cfg is created.
 /etc/default/grub - This file contains the GRUB menu settings that are read by the GRUB scripts and written into grub.cfg. It is the customization part of the GRUB. The grub file is a text file that is parsed by the 00_header script. You can make your changes here, if you want.
------------
GRUB 2 works like this:
/etc/default/grub contains customization; /etc/grub.d/ scripts contain GRUB menu information and operating system boot scripts. When the update-grub command is run, it reads the contents of the grub file and the grub.d scripts and creates the grub.cfg file.
That's all.
To change the grub.cfg file, you need to edit the grub file or the scripts under grub.d.
Scripts are meant to be executed. This means that they have the execute bit turned on. If you turn the execute bit off, they will not run.
see: [http://www.gnu.org/software/grub/manual/grub.html#Command_002dline-and-menu-entry-commands](http://www.gnu.org/software/grub/manual/grub.html#Command_002dline-and-menu-entry-commands) -> for a full list of grub commands.
   update-grub command reads the /etc/grub.d directory and looks for executable scripts inside it. The scripts are read, in the order of their numbering, and written into the grub.cfg file, along with the menu settings read from the /etc/default/grub file.
Boot entries come from several sources - the default that comes with the distribution, other operating systems probed on the connected disks and custom scripts written by the user, following a strict syntax. The scripts are written as shell (sh).
You can add/remove entries by simply chmod-ing the scripts; no need to delete them. GRUB 2 can be reinstalled anytime you want, even while booted in the OS.
   Errors ->
      GRUB Error 11 means the wrong root device is selected or that you're booting devices by ID rather than numbers, in which case you will have to change one of the strings in the config file to make it work.
-----------
Back to the story:
That abbreviated copy is the "initrd.img" file, the INITial RamDisk IMaGe -that was loaded into memory by the stage 2 boot loader; having been copied into ram and mounted. initial RAM disk (initrd) is a temporary root file system that is mounted during system boot to support the two-state boot process. The initrd contains various executables and drivers that permit the real root file system to be mounted, after which the initrd RAM disk is unmounted and its memory freed. 
[[http://en.wikipedia.org/wiki/Initrd]](http://en.wikipedia.org/wiki/Initrd]) Good description.
 The initial RAM disk (initrd) is an initial root file system that is mounted prior to when the real root file system is available. The initrd is bound to the kernel and loaded as part of the kernel boot procedure. The kernel then mounts this initrd as part of the two-stage boot process to load the modules to make the real file systems available and get at the real root file system.
 The initrd contains a minimal set of directories and executables to achieve this, such as the insmod tool to install kernel modules into the kernel.
 In the case of desktop or server Linux systems, the initrd is a transient file system. Its lifetime is short, only serving as a bridge to the real root file system.
Once it's loaded, control goes over to it, and it begins loading the actual full system from the "vmlinuz" file. While all this is going on, you see only the splash screen (but you can edit GRUB's actions to see play-by-play reports of it all, if you want to).

When the full system is all loaded, and all complete,  control goes to the "init" process, which sets up the console and virtual terminals, loads the window manager and display code, and completes the high level initialization, and lets you log in. It is init's job to get everything running the way it should be. It checks that the file systems are ok and mounts them. It starts up ``daemons'' to log system messages, do networking, serve web pages, listen to your mouse and so on. It also starts the getty processes that put the login prompts on your virtual terminals. The init process continues to run in the background until you shut down the machine, allowing the system to do its work more or less invisibly.

You can view the log of all this by firing up a text editor and looking at /var/log/syslog. This file records each significant event -- and gets huge in a hurry.

I hope this helps answer your question, but it will probably prompt many more. Welcome to this wild and wonderful world!
More info:
[http://www.ibm.com/developerworks/aix/library/au-speakingunix_unixboot/index.html](http://www.ibm.com/developerworks/aix/library/au-speakingunix_unixboot/index.html) <-Speaking UNIX: Booting up

//

Finally; 'sda' is that whole disk drive that the operating system first recogmizes.
sd = Serial Device 
a= 1st recognized
b= 2nd recognized
c= 3rd recognized
and the partitions on the hard drives are referred to by number
sda1 is the 1st harddrive, 1st partition
sdb3 is 2nd harddrive 3rd partition
sdc9 is 3rd harddrive 9th partition.

[INDENT][INDENT]be careful what you ask
[INDENT][INDENT][INDENT]you may get it [/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by benawhile on 2014-04-28
Ah, so the MBR is a reserved section of the HDD that can't get overwritten by partitioning?

---

### Post by oldfred on 2014-04-28
Yes & no.

The very first part of the MBR is the boot code, but the last part of the MBR is the partition table. If you use some tool to totally erase the first sector then both boot & partition table are erased.

But normally you install boot loaders separate from updates to partition tables.

---

