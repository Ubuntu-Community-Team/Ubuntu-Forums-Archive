---
title: "Ubuntu 13.10 install on 64gb flash drive"
date: 2014-01-19
forum: Installation &amp; Upgrades
---

### Post by joshua14 on 2014-01-19
Hello all, I am rather new to Linux but would like to get my feet wet. I don't want to install Ubuntu on my laptop yet however I want it on my flash drive so it is portable and easy to use on any computer that allows usb boot. I want to install the OS using the encryption method but I also want to partition the flash drive do Ubuntu gets 30Gb of space and the remaining 34 can be used as normal storage. I have watched a few YouTube videos but none of them have helped me figure out how to proceed. I also read the Ubuntu install guid with no luck. Is there a good way to accomplish this.


Some of you are probably wondering why I want the OS encrypted, well I don't want any data or personal information getting into the wrong hands and if the OS is encrypted it will be harder for some one to obtain this information.

---

### Post by jp734 on 2014-01-19
I don't think it will work the way you want it. Once you installed the OS, it will be only tailored for the hardware on that system. It works differently than the live version.

---

### Post by jp734 on 2014-01-19
.

---

### Post by oldfred on 2014-01-19
As long as you do not install proprietary drivers it should work. Issues can be video or wireless drivers and different systems may need different drivers. But it usually works.

Is system BIOS or UEFI. Not sure if possible to configure for both like live install is, but since live installer can be both there may be a way but do not know.

I have full install on 16GB flash with 8GB for install and 8GB for data. But Windows will only read NTFS (or FAT) on first partition, so if you want to also read data from Windows the first partition must be NTFS.

I do not (yet) have UEFI, but configured a new 32GB flash drive with gpt partitioning and both an efi partition and a bios_grub partition. I hope to configure to boot either BIOS or UEFI from that one, but have not been able to test.

Even on my USB2 ports I find my new USB3 flash drives are about 10% faster. But some systems will not boot from USB3 ports or have other issues. Depends on hardware and UEFI/BIOS.

Install to flash drive is just like any install to another drive or external hard drive, just better to make some settings to reduce writes for better life and a bit more speed. Writes are slow. If you have a fair amount of RAM once you load applications and do not use too many RAM caches recent activity, so not reloaded from flash and it is just as fast as any drive.

I now use gpt partitioning for all new drives including flash drives. But gpt will not work with XP. Newer Windows can read data partitions on gpt partitioned drives.

        I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

      
 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

      
 Full install of 12.04 to 64GB USB device C.S.Cameron post #3
[http://ubuntuforums.org/showthread.php?t=2092077](http://ubuntuforums.org/showthread.php?t=2092077)

      
```
 Disk /dev/sdb: 31.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

   Number  Start   End     Size    File system  Name        Flags
 1      20.5kB  500MB   500MB   fat32        EFI System  boot
 2      500MB   501MB   1049kB                           bios_grub
 3      501MB   15.2GB  14.7GB  ext4         sys
 4      15.2GB  31.0GB  15.8GB  ext4         sys


```           
 
With SSD or Flash (trim does not work on flash) drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.

I do not use Unity, laptop barely runs with it, but use fallback. If you want  even lighter/faster consider Lubuntu. My flash boots both desktop with nVidia and laptop with Intel video. But I have no proprietary drivers.

I have not used encryption. You have two choices, full drive or /home. Full drive is LVM and separate /boot, you cannot use gparted with LVM.

---

### Post by joshua14 on 2014-01-19
ok thanks for the responses, is there something else you guys recommend?  I need it to boot on every computer possible so I have a portable OS.

---

### Post by Herman on 2014-01-20
> is there something else you guys recommend?  I need it to boot on every computer possible so I have a portable OS. Don't worry, you'll be able to boot, just try it.

Ubuntu is not Windows. Some proprietary operating systems which come in new computers are only intended for running in one computer and are even designed to self destruct if they detect too many hardware changes. The idea is to try to prevent piracy.
Gnu/Linux operating systems like Ubuntu have the exact opposite motives. The operating systems are free in more ways than one. We are more than welcome to use as many copies of the operating system as we like and the operating system is not just designed to boot and run in almost any hardware, in most cases it can configure itself automatically on boot-up. 

In the early days, only the Ubuntu Live CD was capable of automatically configuring for all kinds of hardware automatically during boot-up. The first version of Ubuntu to have a Live CD was 'Dapper Drake', (June 2006), and before that Knoppix was the only  well known Gnu/Linux distro I can remember running a full GUI from a Live CD.
Not quite two years later, Ubuntu 8.04 'Hardy Heron came out featuring the Xorg 7.3  Xwindow system from X.Org Foundation. From then on hard disk installed (or flash installed) Ubuntu has been able to set itself up automatically for most different  computers hardware silently during boot-up. 
Ubuntu Intrepid Ibex, (Oct 2008) was the version which introduced booting using file system uuid numbers rather than /dev/sdx,y type device numbering. 
After those changes it became simple to unplug a hard drive (or flash memory stick or SSD), and move it from one computer to another no matter if it's connected by IDE, SATA or USB.
Over the years since then a lot of new hardware has come out and there have been a lot of improvements in the software and operating system too. Over time Ubuntu has just been getting steadily better and better and better. Now it's 2014 and Ubuntu can even set itself up for dual monitors by itself.

EDIT: One exception is the CPU architecture,  if you want to be able to use your portable USB installation in as many different computers as possible, it is better to choose the i386 32-bit versions of your Ubuntu download. The i386 32-bit versions should boot up okay if the CPU only has a single core or if has multiple cores, but the amd 64-bit Ubuntu can only boot in dual core or multi core computers, not in a PC with a single core CPU. 

You may find most USB flash memory drives a little slow and jerky since most of them are really only designed by the manufacturers to be used for file storage and transfer and most consumers tend to buy the cheapest ones. Performance will vary greatly between brands and models. You may find the operating system will run in fits and starts, especially in cheaper USB sticks. It wasn't so noticable in older hardware a few years a back. Now that most of us are spoilt with fast drives we expect smooth and snappy performance all the time. Tweaking the operating system settings goes some way towards improving the performance when running in flash. A hard drive or an SSD in an external USB Hard drive case or a more upmarket flash memory stick with some cache memory and some kind of RAID setup (similar to a SSD) would be best if you can buy one. I was against running an OS in a USB HDD for a long time, due to risk of it being dropped or jarred while spinning, but many new hard drives now come with motion detection systems that can park the heads very quickly to protect the drive when they sense they are falling. Hard drives tend to run more smoothly than flash.

Encryption will further slow the operating system down, but it would be better than leaving yourself exposed in the case of a USB flash drive being lost or stolen. Only another Gnu/Linux user would likely be able to access your files. The average Windows user would plug it in and Windows wouldn't recognise the file system (even unencrypted) and helpfully offer to format it. You can't be too safe though and encryption will only slow the operating system down a little.

It's great to have Ubuntu in any kind of drive, and all Ubuntu installations are portable these days. Ubuntu in a removable drive is extremely useful. You can do a multitude of tasks with it whether you are primarily a Gnu/Linux user or even is you are primarily a Windows user. If your portable Ubuntu boots in a computer when the regular operating system won't you immediately know there is an operating system problem, not hardware that's the source of the trouble. You can use it for working on your regular installed operating systems. Ubuntu is unaffected by Windows viruses and you can use it for file rescues and you can even use it to modify the Windows registry if you install the right programs. For Gnu/Linux installations, the regular Ubuntu install in a USB boots with GRUB2 and can be used to easily boot an other Gnu/Linux with bootloader problems. If your business involves repairing other people's computers there are terminal commands for identifying hardware too, so you can find out exactly what make and model numbers are for the replacement parts you'll need to hunt for. You can also carry your operating system around in your pocket and access all your internet accounts easily from anywhere in the world as long as there's a computer around that you can get the use of which can boot your USB. Being able to do things like that can save you a lot of time and are more than worth tolerating any slowness of the auxilliary Ubuntu operating system running in flash memory.

Mon Feb 9th 2014 - EDIT: I have just found out that trying to boot an older (pre-UEFI) version of Ubuntu, (previous to 13.10 amd 64-bit) can cause the new secure boot programs in some new computers, (at least the one I tried)  into lock mode and they will block all subsequent attempts to boot any Ubuntu until the settings are corrected. In the one I worked on I had to set a password before I could gain access to those settings, and then I had to re-register shim, grub and Ubuntu in the EUFI's database of approved bootable programs. After that everything was okay again.
Also it turns out that so far anyway, (I haven't had time to try very hard yet), the UEFI installation of Ubuntu I made in a USB flash memory doesn't seem to boot in my older computer with a traditional BIOS. So it seems like it will be a good idea to put stickers or some masking tape on our Ubuntu USB installations and mark them as 32-bit or 64-bit, and EUFI or non-EUFI ones and only boot them in the appropriate machines. Sorry, I was wrong, or partially wrong at least. I'm just beginning to get access to the newer hardware and my experience is limited to at this point in time. I'm used to the older BIOS type computers.

---

### Post by Topsiho on 2014-01-20
To Herman:

Wow! If all this is true, another Wow!
I copied this answer just to show this to my friends.

Topsiho

---

### Post by Zhivargo on 2014-01-20
cant you format it to fat anymore? that should be fine.

if your problem is actually making the usb stick bootable you can use mkfs and set a boot flag IIRC....
or you can install you boot loader with syslinux 

```
sudo apt-get install syslinux
```

---

### Post by oldfred on 2014-01-20
FAT formatted with syslinux boot loader is the live installer version, which you would add persistence. 

But with large flash drive a full install is much better.

Even with my 16GB full install I copied several repair ISO into data partition and directly boot those from grub2. Then I have a multi-tool repair and emergency boot drive.

---

### Post by joshua14 on 2014-01-20
I am using s Kingston 64gb data traveler. I would like to install the ubuntu onto the flash drve using the install ubuntu option the OS provides. however I am having little luck accomplishing the task. has any one accomplished this?

---

### Post by joshua14 on 2014-01-20
I'll be booted into ubuntu on my laptop amd I want to install ubuntu to rtf he flash drive using ubuntu install option and I want f2f he drive split into to partitions one with encrypted ubuntu and one formatted to ntfs for normal storage use.

---

### Post by Jason_Gibson on 2014-01-20
> [COLOR=#000000]Even with my 16GB full install I copied several repair ISO into data partition and directly boot those from grub2. Then I have a multi-tool repair and emergency boot drive.[/COLOR]

If possible could you point to a guide that works on google. I have been trying to do this for awhile but none of them seem to work for me.

---

### Post by Herman on 2014-01-20
I don't think the brand of flash memory you're using is the problem. I happen to have 8 Kingston DataTraveller 16GB G2 flash memory sticks here. I'm not saying they are the best or anything, but they are mostly okay.

One has an encypted installation of Lucid Lynx (in a single partition / installation and /boot). 

Another one has a multiple partition encrypted installation with the operating system spread out over a number of separate partitions, I did that as an experiment because some Arch Linux folks thought splitting the operaing system into many partitions with different file systems optimized for whatever their particualr role in running things is, would make the OS work faster. 

Another four x 16GB Kingston Data Travellers I have are attached to four ports around a USB hub and I have one Ubuntu operating system stretched across all four USB drives by using LVM, (Linux Logical Volume Management.

One Kingston USB stick I have seems to be defective and after repeated attempts to format it with ext4 and install Ubuntu failed, I gave up and reverted it to FAT32 and still use it for file storage and transfer, although it is still problematic and doesn't show up in Windows computers, and sometimes it doesn't even show in in Ubuntu machines either.

I have one more with a normal installation of Ubuntu 12.04 LTS in it and that's my old faithful auxilliary Ubuntu operating system which I use quite often for all kinds of purposes, a few of which I already mentioned.

It could be that trying to make a separate NTFS data partition is a problem.
I have not tried the encrypted installation options from the Live CDs yet, I used to use the old Ubuntu 'Alternate Installation' CDs for that but those are discontinued now.
With the 'Alternate' CD you had no choice for an encryped installation than to format the entire drive, you could not make any extra data partitions. The default was to let the installer use the entire disk and install Ubuntu in an encrypted / with a non-encrypted separate /boot partition, and it installed in LVM automatically.  The LVM part of it might be the problem, because the installer's partitioner will stick an LVM flag in the partition table. Try letting the installer have the entire disk.

---

### Post by Herman on 2014-01-20
> If possible could you point to a guide that works on google. I have been  trying to do this for awhile but none of them seem to work for me.

Okay, I'll find some links for you.  As I said before, I have not tried out an encrypted installation myself since the 'Alternate Installation' CD was discontinued, so my information and opinions may be out of date. 

Here's the first link I found:[ How to Install Ubuntu 13.04 Raring Ringtail]("http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.Ut3N0PgRXRY")  Installing 13.10 probably will be similar.

A quick look at that web page reveals they show how to install an encrypted installation alongside another OS, so obviously it doesn't use LVM now. LVM has never been a requirement for an encrypted operating system, it was just the default for the old 'Alternate Installation CD'.

Here's an interesting link comparing the file system speeds between non-encrypted, encrypted /home and the fully encrypted installation, [The Cost Of Ubuntu Disk Encryption]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_1304_encryption&num=1")

Here's a thread that agrees with my idea that you might need to set aside the entire disk and also claims the recent (13.04) Ubuntu installer may lack the ability to do the things it pretends to be able to do: [Manual LVM encryption setup with Ubuntu 13.04]("http://askubuntu.com/questions/289793/manual-lvm-encryption-setup-with-ubuntu-13-04")

Here's a guide to how to accomplish a dual boot with 13;10 encrytped but it involves some command - line work which not all of us find appealing, [How can I install Ubuntu encrypted with LUKS with dual-boot?]("http://askubuntu.com/questions/293028/how-can-i-install-ubuntu-encrypted-with-luks-with-dual-boot") Looks like it would probably work though.

---

### Post by Herman on 2014-01-21
Okay, here is an update:

I decided to try out a simulation of the kind of installation you (joshua14) described in post #1 in this thread and I have successfully installed Ubuntu 13.10 Saucy Salamander in an 8 GB Toshiba USB flash memory stick. It did not require any command line work, and any person with average computer skills should be able to do it. 
At first I went through a brief period of trials and errors before I worked out what to do. I will leave out the things I tried that didn't work for the purposes of clarity and brevity and just describe what worked.

First I used use GParted to create a small partition in the USB drive formatted NTFS and labelled 'DATA' . That is partition number 1 in the USB stick, so Windows will readily recognize it and mount it. In my case I have only a small drive so I only made the DATA partition around 256 MiB. This is just for a test example, yours can be any size providing more than enough room is left to install the operating system.

Second, I created a small partiition 256 MiB formatted ext2 and labelled it 'BOOT', and that was automatically given the partition number of 2. The size for a separate /boot partition needs to be large enough to contain kernels and initrd.img files to be received in future updates. I think 256 MiB is a generous size for /boot.

Third, the number 3 partition occupies the remaining space in the disk, formatted ext4. The / (or 'Root') partition needs to be large enough to install the OS in plus added software and files, leaving at least 20% breathing space for the file system, plus with mine I will install 'dynamic swap space manager', more on that later.

After preparing the above partitions in advance I started the installer and chose 'something else', and then I selected the BOOT partition and let the installer know it is intended to be for /boot. I then selected the partition I created for / (or 'Root'), and chose the 'encryption' option from the bottom of the file systen list.
That resulted in two new entries near the top of the installer's partitions list.
Here comes the part where a new user might not know what to do, I chose the second new item down from the top, which was called ' /dev/mapper/sde3_crypt and set that as the / (or 'Root) file system, ext4.

EDIT: Also I selected to have GRUB installed to /dev/sde because that's the MBR of the disk I'm installing in. It's important to install GRUB to the disk we're installing in and not some other disk if we want to be able to boot this USB install in other computers, and besides we do not affect the boot loaders for other operating systems that may be in other disks in the host computer. 

On proceeding with the install, I received an error message to remind me I had not created a swap area and I chose to ignore it and continue anyway.
The rest of the installation was just the same as any other normal installation.

Afterwards I test booted it in the same computer it was made in and it booted up just fine, and I left a plain text file in the DATA partition.
Then I tested in a Windows 7 laptop and Windows 7 mounted the ntfs partition (after installing drivers for the USB), and read the text file no problems.
Finally I shut down Windows 7 and booted the new Ubuntu encrypted USB installation in the laptop and it booted up just fine and I was able to access files in Windows. 

The performance and 'feel' of the new flash installed operating sytem is a little bit slower than I'm used to with the kind of hardware I normally use, but it's tolerable for an auxilliary installation.

---

### Post by Herman on 2014-01-21
There are a few reasons why I chose not to create a swap partition.
One reason is for not creating a separate swap partition is for security. This is an encrypted installation and I have read that it's theoretically possible for another person with physical assess to the disk to retrieve files from a swap area outside of the encrypted partition. If they happen to be sensitive files the idea of having an encrypted operating system could be negated. 
Another reason is to make the best use of precious disk space. Most of the time swap areas tend to be much larger than really needed, and space in most flash memory drives is an issue. Instead, I just install [Dynamic Swap Space Manager]("http://pqxx.org/development/swapspace/"), and reboot.

Here are a few more links to information about swap, [Swap FAQ]("https://help.ubuntu.com/community/SwapFaq") - Ubuntu Community Docs, [Linux Performance tuning - vm.swappiness]("http://unixfoo.blogspot.com/2007/11/linux-performance-tuning.html") - unixfoo.blogspot.com, 
       [What Is the Linux Kernel Parameter vm.swappiness?]("http://www.linuxvox.com/2009/10/what-is-the-linux-kernel-parameter-vm-swappiness/") - Linux Open Source Blog

What I have found by trial and error is a swappiness setting of 10 seems to be best for me. So I append the line: vm.swappiness=10 to the end of my /etc/sysctl.conf file.
You don't really need to do that unless you want to but in my opinion it helps a little. It means my operating system will prefer to use RAM most of the time and will only use swap as a last resort if it really has to.

---

### Post by oldfred on 2014-01-21
Thanks for update Herman.
Much better to follow Herman's instructions on manual install with encryption.

The new GUI installer has an auto install full encryption and another LVM install option. With Alternative installer it said full drive/disk install. They left that note out with GUI version, but added "easy" partitioning for LVM. But it still is full drive install and users have overwritten entire drive when they did not want to.

---

### Post by joshua14 on 2014-01-22
Thank you this worked very well.

---

### Post by joshua14 on 2014-01-22
I am curious about one thing though, I installed 64bit ubuntu so if I try to boot it on a 32bit computer will it work? I ask because I am always asked to remove viruses from people's computers and I know that a few of them are 32bit. also do you recommend any specific software for linux that is good at removing viruses and fixig problems? I know I can fo a search for this stuff but a search doesn't compare to the knowledge of a person with experience.

---

### Post by westie457 on 2014-01-22
> **joshua14 said:**
> I am curious about one thing though, I installed 64bit ubuntu so if I try to boot it on a 32bit computer will it work? I ask because I am always asked to remove viruses from people's computers and I know that a few of them are 32bit. also do you recommend any specific software for linux that is good at removing viruses and fixig problems? I know I can fo a search for this stuff but a search doesn't compare to the knowledge of a person with experience.

No it will not work. A 64bit OS will not run on 32bit architecture at all. However a 32bit OS will run happily on 64bit machines.

---

### Post by oldfred on 2014-01-22
A lot of 32 bit Vista and even XP have 64bit hardware underneath. So on those systems it will work. Most hardware in the last 6 or 7 years is really 64 bit.

For the very old systems you can have another flash drive or put repair ISO on the same one.

I copy many ISOs and directly boot from grub menu with loopmount. So I have several repair ISO in the data partition on my flash drive.

 This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

### Post by Herman on 2014-01-22
I edited post #6 about 16 hours ago after I realised I had failed to mention about the 32-bit vs 64-bit architecture, looks like I was too late, sorry about that. 
My new 13.10 USB installation is 64 bits too, because I used the same file I already downloaded for my main computer, which has a quad core CPU. 
The 64-bits versions can utilise more than 2GB of RAM. Mine sure does run nicely too, it seems to have much better performance than I was expecting.

It might be time to re-think the idea of recommending only to use only the 32-bit versions of Ubuntu for portable installations now. Dual, quad and multiple core CPUs, (i7), and computers with more than 2GB of RAM are getting quite plentiful these days, or so it seems to me. To chroot into an installed Ubuntu operating system we need the  auxilliary system of the same architecture as the installed sysytem. Maybe we should start recommending two USB flash memory installtions now, one for each architecture, or a setup similar to oldfred's.

I'm going to keep my old 32-bit 12.04 USB auxilliary installation and upgrade it to 14.04 when that comes out, and I'll keep my new 13.10 USB 64-bits install or maybe make a new one in a larger memory stick.

Again, sorry for any inconvenience, I just didn't think of that until later.

---

### Post by oldfred on 2014-01-22
Flash drives do make a difference. I find a USB3 flash drive about 10% faster on my USB2 ports.

See various tests in post #6
  Installation/FromUSBStick - with lots of details on various USB drive issues by  sudodus
[http://ubuntuforums.org/showthread.php?t=2196858](http://ubuntuforums.org/showthread.php?t=2196858)
Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)
Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208)

---

### Post by Herman on 2014-01-22
> also do you recommend any specific software for linux that is good at removing viruses and fixig problems?
Yes, the last time I was doing that kind of work I used [clamav]("http://www.clamav.net/lang/en/download/packages/packages-linux/") to scan the Windows for viruses and identify the viruses.

The program I was using for editing the registry is called chntpwd.
Link to chntpwd's home page: [Offline NT Password and Registry Editor]("http://pogostick.net/%7Epnh/ntpasswd/") 
It would be a good idea to practice on a Windows installation you don't care about until you get used to using chntpwd first.

Sometimes it only takes a little change to overcome a problem in Windows, for example  [Change drive letter on a boot device]("http://www.leghumped.com/blog/2007/01/09/change-drive-letter-on-a-boot-device/") - LegHump. Other times, it's more complicated than that. There are web pages you can find on the internet with specific instructions about how to remove the particular virusesand edit the registry to fix the daamge done. To be honest, most of the time it's probably quicker to do a file rescue to a backup drive and re-install Windows as editing the registry can be time consuming and you can never be sure you got all the viruses and malware. SInce Gnu/Linx operating systems aren't affected by Windows viruses, you can safely copy all the users files out to a backup drive without risking contamination of your own operating system.

Most Gnu/Linux operating system problems are self inflicted, as we like to mess around a lot trying to tweak our systems and customize them to our heart's desires. Sometimes we make mistakes. Usually, the Gnu/Linux users remembers what they just did and what to undo to fix it again. With boot loader problems, we only need to boot the USB auxilliary and run 'update-grub', then reboot it and the PC's internal installed operating system's operating systems will be listed in the USB stick's Grub boot menu, (including Windows).  From there we can boot a previously unbootable operating system inside the computer and then fix it.
It it still won't boot properly, we can mount the OS's file system and restore from backup or edit certain configuration files to fix the operating system.
With some kinds of problems, we need to [chroot into it]("http://ubuntuforums.org/showthread.php?t=1156240") and repair the stricken operating system from within by  running commands to fix the problems, such as apt-get clean, apt-get update and apt-get upgrade and whatever else is needed.

---

### Post by Herman on 2014-01-22
Hardware

For testing RAM, we have memtest 86+ available from the GRUB boot menu, look for it while your computer is booting up.  [http://www.memtest.org](http://www.memtest.org)

Available from the Ubuntu Dash, Disk Utility is the name of the application we use for looking at the hard disks and it contains a smaller program called smartmontools for looking inside and reading the hard disk's error logs. It's generally pretty good but hard disk manufacturers like to keep some information to themselves. Sometimes the results need to be taken with a grain of salt. Most of the time it's pretty good though, and it alwasy does return a lot of interesting information, like the number of power-on hours, temperatures the disk has been run at and so on. Often we're simply seeking to confirm what we already suspect.
A better way to tell if a HDD is on it's last legs is to run badblocks on a partition. The badblocks command can be run from the command line in a Ubuntu terminal.

Just a couple of useful hardware detection commands are [FONT=Bitstream Vera Sans Mono]sudo lshw and [/FONT][FONT=Bitstream Vera Sans Mono]sudo dmidecode[/FONT][FONT=Bitstream Vera Sans Mono].[/FONT] Those will give you a lot of useful information about your hardware.
There are many more Gnu/Linux hardware detection commands which are more specialised, they are too numerous to list them all.

Another trick to diagnose computer problems is to try to boot the computer and then issue the command [FONT=Bitstream Vera Sans Mono]dmesg > boot.messages.[/FONT] The dmesg program helps users to print out their bootup messages  - possibly useful to identify a hardware issue which may be causing problems during boot-up

If your computer shuts down suddenly and unexpectedly you should check your logs  to see if  a hardware problem was the cause: cat /var/log/syslog | less , cat /var/log/messages | less , cat /var/log/kern.log | less

For diagnosing xserver problems for your video display: cat /var/log/Xorg.0.log  | less

Those are just a few examples, there are lots more.

---

### Post by Herman on 2014-01-22
> Flash drives do make a difference. I find a USB3 flash drive about 10% faster on my USB2 ports.Thanks oldfred, I might try a USB3 flash memory stick sometime soon then. :)

---

