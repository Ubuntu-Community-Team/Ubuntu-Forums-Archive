---
title: "Lubuntu Install Problems - Partitioning, Freezing, Failed Install, AMD 64bit"
date: 2016-02-09
forum: Installation &amp; Upgrades
---

### Post by FaultedGeologist on 2016-02-09
Linux N00b here, trying my best to get some old junk computers to function for the kids.  I have pieced together some scrap computers that people put out to the curb.  This particular comp is an old HP that ran XP, 64bit AMD processor, SATA HD, two sticks of stock memory.  I successfully installed Ubuntu 15 on the drive, wiping XP since it is unsupported and unsafe, but it runs soooo slow.  It began to boot to a DOS like command screen that asks for login.  Between install and insanity, I added an old pci graphics card to reduce mobo/process strain, an old wifi card, and two other sticks of faster ram (that should behave like slower ram, right?)  My buddy said I should remove the hardware one at a time to see if it functions again.  My error searches seem to point to the graphics card.

Next, I put a second 200GB SATA HD in and attempted to do an install of Lubuntu.  I used Unetbootin to create a live drive; it loads, but will not let me initiate the install from the loaded OS.  Rebooting to do the install has created a number of failures:
Some where the mouse freezes, no response.  No partitioning, just get through it and work the rest out later.
Some where the partitioning creates an error.  OS loads, but no OS on reboot.
L>  I created a 20GB root / ext4, a 7GB swap, and a 173GB /Home ext4, in that order.

Needless to say, this is a little frustrating.  When I boot to the live version via USB, I was unable to setup the network.  I would like to get one functional version working so I can take a few steps, then run.  Melp!

>I went back to the Ubuntu 15.10 HD, boot froze at a psychadelic purple and dashed screen.  
>Pulled the nice dual monitor graphics card with DVI cable from circa 2006, replaced the VGA cable to the mobo, got locked in a DOS screen:
   [  OK  ] Started Light Display Manager.  
>Pulled the wifi card circa 2006, made it to a different DOS like screen with the 
   [  OK  ] Started Light Display Manager
   [   47.645754] [drm:drm_crtc_helper_set_config [drm_kms_helper]] *ERROR* failed to set mode on [CRTC:27]
>Pulled the two faster RAM chips, leaving the two original RAM in place (2x 512MB, PC2-4200), and it went to the login screen...  I was able to log in.  Now the screen shows the purple background with ubuntu 15.10 at the bottom left, but moving the mouse makes it flash between black screen/purple/black/seizure.  No icons, menu buttons, etc.  Bunk.
>Replaced the spiffy Raedon 7k 64MB V/D/VO VT-RAD7k 64P video card.
>Went to get another beer... I work the night shift, so right now it is nighttime for me!

Mini-Conclusion:  The RAM mismatch was pissing the system off.  The big X223w ACER monitor would not work with the onboard VGA cable, and required the nice oldskool graphics card with the DVI cable.

I still need to figure out the Lubuntu install.  Will do so with a full mug.  Any help on the partitioning?  Did my above partition scheme seem appropriate?  TIA.

---

### Post by sudodus on 2016-02-09
Welcome to the Ubuntu Forums :-)

The two original RAM in place (2x 512MB, PC2-4200) is good for Lubuntu, but not for standard Ubuntu.

Please tell us also about the ***CPU*** and if possible also details about the ***graphics*** chip(s) :-)

-o-

I think you can try some versions of ***Lubuntu*** *live*, booted from the DVD or USB drive. I suggest that you start with Lubuntu ***14.04.1 LTS***, and then ***14.04.2, 14.04.3, 15.10***. Go ahead and install what works best for you.

If no Lubuntu version works well, you can try a 'light-weight' community re-spin based on Ubuntu 12.04 LTS, for example ***Bento, Bodhi, LXLE***.

If still no luck, you can try ***Knoppix, Wary Puppy*** and ***TahrPup***.

You find more details in the following links

[Old hardware brought back to life](http://ubuntuforums.org/showthread.php?t=2130640)

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by FaultedGeologist on 2016-02-09
Ubuntu 15 AMD64 is slower than Windows 3.1 on a 386 machine from the 80s. 

Connected the other 200GB HD, attempting the install of Lubuntu AMD64 again.  I only have the original two RAM chips in (2x 512MB), and the graphics card.  The install is going forward.  No partitioning selected, but I can do that later (right?).  Ubuntu + LXDE = LUBUNTU !!  Eat a byte of some bits!  Macho LibreOffice!  This is Audacious!  

Hopefully this will at least allow some NES emulation.  WTFrack else can I do with Lubuntu?!?

Again, the problem was shoving a couple newer ram chips in the extra two sockets.  I still need to partition the drive, so some suggestions would be great.  Did I get the best partition scheme started like listed above in the OP?

> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

The two original RAM in place (2x 512MB, PC2-4200) is good for Lubuntu, but not for standard Ubuntu.

Please tell us also about the ***CPU*** and if possible also details about the ***graphics*** chip(s) :-)



Thanks for the welcome and the reply!  
Processor:  AMD Athalon 64 X2 Dual Core
Graphics:  Onboard VGA, PCI card: [COLOR=#000000]Raedon 7k 64MB V/D/VO VT-RAD7k 64P

As per my latest reply, the comp works now with both installs.  Lubuntu is noticeably fast.  Ubuntu will have to wait for a newer setup.
Now I need to partition the drive to have a swap file and a home dir, then install the D-Link Air DWL-520, and then get some games for the kids to play with.[/COLOR]

---

### Post by sudodus on 2016-02-09
7 GB looks like wasting drive space to me. With 1 GiB (gibibyte, base 2) RAM you need slightly more (in GiB) for hibernation. If you really think you need it, you can have 2xRAM (in your case 2 GiB). When swapping starts, the computer will be very slow, so you don't want to run it like that anyway. Therefore it is usually no point in having more swap. (Get more RAM (of the same grade as you have already), it makes a difference.)

Otherwise the partitioning is good.

An alternative is to have a root partition and a ***data*** partition instead of the home partition (and /home as a directory in the root partition), but a separate home partition is preferred by many people.

> **FaultedGeologist said:**
> Thanks for the welcome and the reply!  
Processor:  AMD Athalon 64 X2 Dual Core
Graphics:  Onboard VGA, PCI card: [COLOR=#000000]Raedon 7k 64MB V/D/VO VT-RAD7k 64P

As per my latest reply, the comp works now with both installs.  Lubuntu is noticeably fast.  Ubuntu will have to wait for a newer setup.
Now I need to partition the drive to have a swap file and a home dir, then install the D-Link Air DWL-520, and then get some games for the kids to play with.[/COLOR]

I have a similar processor in an old 'cube' desktop: specified as 4400+, and 2 GiB RAM.

I have nvidia on-board graphics in that computer, and with a proprietary driver it works well with the flavours with light-weight desktop environments, ***Lubuntu***, ***Ubuntu MATE*** and ***Xubuntu***, and it works with standard Ubuntu too. But without a better graphics chip, I think you can forget about standard Ubuntu.

You can probably run Lubuntu 14.04.1 LTS with the Trusty kernel. Try it live, install it and upgrade the software. Do not upgrade it to newer versions, if it works well.

***Edit:*** If you have only 1 GiB RAM, it might work better with a 32-bit version of Lubuntu, Ubuntu MATE or Xubuntu. The reason is that 64-bit versions use more RAM for the same tasks, and 1 GiB RAM is a bottleneck.

---

### Post by FaultedGeologist on 2016-02-09
I attempted to install Lubuntu over the Ubuntu install on the original 200GB HD with partitions of 20GB for /, 2GB for swap, and the rest for /home.  It crashed again.  
Problem in ubiquity
The problem cannot be reported:

Your system partition has less than 0.0 MB of free space available, which leads to problems using applications and installing updates.  Please free some space.

Can you recommend a good partition scheme for a 200GB disc in full detail of name, size, format type, and if I need a 'free space' partition?  This will be a single boot Lubuntu install with nothing else going on.  Thanks.

---

### Post by sudodus on 2016-02-09
I suggest that you start with a new partition table. The simplest method is to simply let Lubuntu's installer use the whole drive.

If you want a separate home partition, you can format the ext4 partitions you have already, and then select **Something else**.

Select the root partition, /, and home partition, /home. I think the swap and bootloader will problably be automatically.


20GB root / ext4, and the rest of the drive as an extended partition. In that extended partition you make two logical partitions: 2.2 GB swap, and the balance /home ext4, in that order, should be OK.

---

### Post by FaultedGeologist on 2016-02-09
> **sudodus said:**
> I have a similar processor in an old 'cube' desktop: specified as 4400+, and 2 GiB RAM.

I have nvidia on-board graphics in that computer, and with a proprietary driver it works well with the flavours with light-weight desktop environments, ***Lubuntu***, ***Ubuntu MATE*** and ***Xubuntu***, and it works with standard Ubuntu too. But without a better graphics chip, I think you can forget about standard Ubuntu.

You can probably run Lubuntu 14.04.1 LTS with the Trusty kernel. Try it live, install it and upgrade the software. Do not upgrade it to newer versions, if it works well.

***Edit:*** If you have only 1 GiB RAM, it might work better with a 32-bit version of Lubuntu, Ubuntu MATE or Xubuntu. The reason is that 64-bit versions use more RAM for the same tasks, and 1 GiB RAM is a bottleneck.

I am now trying the other RAM chips that are a little faster than the stock.  As I understand RAM speed, it is like amps or mA in electrical transformers:  the computer (or device) will only pull what it can (or is needed); thus, my computer will only use the faster RAM at the speed of mobo build (or the mA of the device trying to draw power).  Adding a Kingston KVR800D2N5/2G (2GB PC6400) and a Mushkin Enhanced PC2-6400 2GB.  **THE UNPARTITIONED LUBUNTU OS LOADED USING THE TWO FASTER RAM CHIPS!!  NOW I HAVE 4GB OF RAM RUNNING AT THE 4200 SPEED.**  

I added the wifi network to the network preferences page, but methinks the WIFI card is not active.  Under the tab in the bottom right by the time it has no wifi devices ready.  

Step by step...

---

### Post by sudodus on 2016-02-09
Great that it works with 4 GiB RAM :-) Now you have a wider choice of Ubuntu flavours. You should have at least 4GiB swap (~4.4 GB) if you intend to hibernate. Otherwise 1 GB is probably enough.

-o-

In Lubuntu you can run ***hardinfo*** alias 'System Profiler and Benchmark' to find out about the wifi chip. You can probably find information about the ***network controller***. Maybe you need a proprietary driver for it (depending on the brand name and model).

-o-

It is a good idea to start a new thread with a good descriptive title in the [network subforum](http://ubuntuforums.org/forumdisplay.php?f=336). That way our wifi experts will find your thread.

---

### Post by FaultedGeologist on 2016-02-09
> **sudodus said:**
> Great that it works with 4 GiB RAM :-) Now you have a wider choice of Ubuntu flavours. You should have at least 4GiB swap (~4.4 GB) if you intend to hibernate. Otherwise 1 GB is probably enough.

-o-

In Lubuntu you can run ***hardinfo*** alias 'System Profiler and Benchmark' to find out about the wifi chip. You can probably find information about the ***network controller***. Maybe you need a proprietary driver for it (depending on the brand name and model).

-o-

It is a good idea to start a new thread with a good descriptive title in the [network subforum]("http://ubuntuforums.org/forumdisplay.php?f=336"). That way our wifi experts will find your thread.

Sudodus, Thanks for all the help.  I had some rest, and now back at it before the nightshift.  I think I wiped the Ubuntu 15.1 install when trying to do a Lubuntu with a Swap partition, the root /, and a home.  I had partitioned it using the available space, but it said there wasn't enough space to do what I attempted.  This doesn't make sense to me.

As for the graphics chip, I am not seeing that it is connected under the System Profiler and Benchmark program in System Tools.  It should show up in PCI Devices, right?  Under Computer - Display it doesn't say anything about the graphics card.  As per my previous post, I have a Raedon 64 VT-RAD7k.  Should I try what is listed in this post?  [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I will start the wifi thread after tackling the partitioning and video card.  Thanks again.

As I understand from other threads, the drive looks like this, with the center at (O):  (building on how I partitioned my XP installs over a decade ago;-)
(START or Beginning of this space - outside of the disc     (End of this space  (O)  End of this space)                                           START)
So I want to have my Swap at the Start, then my Lubuntu install space, then my extra drive space.  I think this time I will do this:

sda5  Swap  - 5064MB,  Logical, Beginning
sda2  ext4 / - 19999MB, Primary, continued beginning.  Will install Lubuntu
sda3  ext4 /boot - 19999MB, Primary, continued beginning.  Will probably try Ubuntu or other distros here to see what works best.
sda4  ext4 /home - 154986MB, Logical, continued beginning.  Extra space for storage, right?
Device for boot loader installation:  /dev/sda ATA ST.... (200GB) - I left this as-is.

Is this looking right?  What can you advise about how to proceed?  So far, it looks like the install is golden, or purple-blue, or whatever.

How will I go about installing Ubuntu on the extra partition?  Do I have to make any special magic happen at that point, or will it just give me the choice of which OS to boot up?

Thanks.

---

### Post by sudodus on 2016-02-10
I suggest that you do *not* use a separate boot partition. 20 GB as you suggest is a waste of drive space. A smaller one, for example 300 MB or 500 MB, will work, but makes it necessary to remove old kernels often (otherwise it will get full, and you will not be able to install new kernels). It is better to share the drive space with other system files, in other words, let the system create /boot as a directory in the root partition, which is the standard way of installing modern linux systems.

Otherwise your partition table looks OK.

---

### Post by FaultedGeologist on 2016-02-10
> **sudodus said:**
> I suggest that you do *not* use a separate boot partition. 20 GB as you suggest is a waste of drive space. A smaller one, for example 300 MB or 500 MB, will work, but makes it necessary to remove old kernels often (otherwise it will get full, and you will not be able to install new kernels). It is better to share the drive space with other system files, in other words, let the system create /boot as a directory in the root partition, which is the standard way of installing modern linux systems.

Interesting.  I guess in all my searches there were no explanations of what /boot and the other options are used for.  It would not allow two root / partitions, so I just selected one of the next options in hope that I could put an OS there in the future.  Can I put the install usb for Ubuntu in, then tell it to format that /boot drive to do the Ubuntu install on?  How would I go about that?  When I boot up each OS, it should then create its own /boot on the install drive to run kernels from?  Do I need to move any files from /boot to the root partition first?  Thanks again.

Wow, I am just lovin' this!  I was prompted to do an update since I was connected to the interwebs.  After reboot I was left with a black screen of death.  I hard-killed it after a few minutes of nothingness, and on restarting got hit with a screen:
GNU GRUB asking if I wan to boot Ubuntu, Advanced Options for Ubuntu, or memory tester...  That install should be wiped, and Lubuntu should boot.  Now the screen has a bunch of 
[ 10.192896] [<fffffffff810...>]
going down the whole screen that suggests it needs a reboot (what I just did!) and the last one says 
[ 10.192896] ---[ end trace 9737f2d51258bdcd ]---
Grumble, grumble...

Reinstall?  The startup has a constant message of a Bios Bug.
On booting to reinstall, Installation type:
This computer currently has Ubuntu 15.04 on it.  What would you like to do?  --  This OS should have been wiped when I did the last re-partitioning and installed Lubuntu.
Options:
O Reinstall Ubuntu 15.04
O Erase Ubuntu 15.04 and reinstall
O Erase disk and instlal Lubuntu
O Something Else

To me, this means it is still trying to boot in to a now-defunct Ubuntu.  Under the Something Else option (nothing noted for Mount point, see previous posts):
Device-----Type---Size----Used-----System
/dev/sda
 /dev/sda5 swap 5062MB unknown
 /dev/sda2 ext4 1999MB 5331MB Ubuntu 15.04
 /dev/sda3 ext4 1999MB 567MB
 /dev/sda4 ext4 154986mB 2629MB

I think I'll wait to see what to do.  Should I tell it to delete Ubuntu on the previous page?  **This is the Lubuntu installer.**

---

### Post by sudodus on 2016-02-11
> **FaultedGeologist said:**
> Interesting.  I guess in all my searches there were no explanations of what /boot and the other options are used for.  It would not allow two root / partitions, so I just selected one of the next options in hope that I could put an OS there in the future.  Can I put the install usb for Ubuntu in, then tell it to format that /boot drive to do the Ubuntu install on?  How would I go about that?  When I boot up each OS, it should then create its own /boot on the install drive to run kernels from?  Do I need to move any files from /boot to the root partition first?  Thanks again.

An operating system will have only one root file system, /.

You can have partitions, which are not used directly by the operating system, but can be mounted (more or less) manually and used for storage of data. Partitions can also be used for another operating system (in a dual boot or multi-boot setup).

You need a /boot partition only if your root partition is encrypted. Otherwise it is a good idea to have /boot as a directory inside the root partition.

-o-

At this stage it is better to get the partitioning correct and after that make a fresh install. It is easier and faster than to try to repair a system with a cumbersome partition table.

> **FaultedGeologist said:**
> Wow, I am just lovin' this!  I was prompted to do an update since I was connected to the interwebs.  After reboot I was left with a black screen of death.  I hard-killed it after a few minutes of nothingness, and on restarting got hit with a screen:
GNU GRUB asking if I wan to boot Ubuntu, Advanced Options for Ubuntu, or memory tester...  That install should be wiped, and Lubuntu should boot.  Now the screen has a bunch of 
[ 10.192896] [<fffffffff810...>]
going down the whole screen that suggests it needs a reboot (what I just did!) and the last one says 
[ 10.192896] ---[ end trace 9737f2d51258bdcd ]---
Grumble, grumble...

Reinstall?  The startup has a constant message of a Bios Bug.

Yes :-)
> 
On booting to reinstall, Installation type:
This computer currently has Ubuntu 15.04 on it.  What would you like to do?  --  This OS should have been wiped when I did the last re-partitioning and installed Lubuntu.
Options:
O Reinstall Ubuntu 15.04
O Erase Ubuntu 15.04 and reinstall
O Erase disk and instlal Lubuntu
O Something Else

[SIZE=3]A. If you want the simplest solution, select *Erase disk and install Lubuntu*[/SIZE]

[SIZE=3]B. If you want to create your own partition table, select *Something Else*[/SIZE]
> 
To me, this means it is still trying to boot in to a now-defunct Ubuntu.  Under the Something Else option (nothing noted for Mount point, see previous posts):
Device-----Type---Size----Used-----System
/dev/sda
 /dev/sda5 swap 5062MB unknown
 /dev/sda2 ext4 1999MB 5331MB Ubuntu 15.04
 /dev/sda3 ext4 1999MB 567MB
 /dev/sda4 ext4 154986mB 2629MB

I think I'll wait to see what to do.  Should I tell it to delete Ubuntu on the previous page?  **This is the Lubuntu installer.**

If you want to create your own partition table, I suggest that you ***boot into the Lubuntu install drive*** again,

- run ***gparted***, unmount the mounted partitions in the internal drive and remove all those partitions.

- After that you create new partitions according to what you want.

- After that you run the installer and select *Something Else* at the partitioning window.

- Select the root partition and the home partition.

- The swap partition will be selected automatically (if you have created one with gparted).

- The bootloader will be installed into /dev/sda (the [first] internal drive) by default. It is probably correct. Change it only if you know what you are doing.

---

### Post by FaultedGeologist on 2016-02-12
> **sudodus said:**
> Yes :-)  [SIZE=3]A. If you want the simplest solution, select *Erase disk and install Lubuntu*[/SIZE]  [SIZE=3]B. If you want to create your own partition table, select *Something Else*[/SIZE]   If you want to create your own partition table, I suggest that you ***boot into the Lubuntu install drive*** again,  - run ***gparted***, unmount the mounted partitions in the internal drive and remove all those partitions.  - After that you create new partitions according to what you want.  - After that you run the installer and select *Something Else* at the partitioning window.  - Select the root partition and the home partition.  - The swap partition will be selected automatically (if you have created one with gparted).  - The bootloader will be installed into /dev/sda (the [first] internal drive) by default. It is probably correct. Change it only if you know what you are doing.  K.  Thanks for your eternal patience and numerous replies.  I do want O Something Else...  the eternal grass is greener struggle.  I think maybe the thing I am missing is checking the [ ] Format box in the O Something Else options for each drive that I create.  Would checking the Format box erase the old Ubuntu install when I do this?  I almost swear on my ol' motherboard's case that I did check the Format box.  I am going to switch back over to that drive and try once more.  I verified the Raedon 7k video card via Terminal, ran some updates, and added G-Parted.  Hopefully I can repeat that process on the other install.

Fraggle Rock!  I just did attempt number 234,089,456 going for 5GB swap, 30GB / ext4, the rest /home ext4.  The following message appeared over the Where Are You? world map:
Partition(s) 2 on /dev/sda have been written, but we have been unable to inform the kernel of the change, probably because it/they are in use.  As a result, the old partition(s) will remain in use. You should reboot now before making further changes.  [Ignore] [Cancel]

What a stupid message.  Ignore or cancel?  How about a reboot option?

Do I need to plug the drive in on the SATA 2 spot, boot to the functioning and unpartitioned drive, then use GParted to partition this drive, then come back in and try to do this elusive install?!?  STUFF!! FRACK!!  BOB SAGAT!!

Momentary lapse of time...  I had to swap the power supply with another that would power two SATA drives.  Now the Lubuntu straight install is running, with the totally botched drive that is the subject of this thread plugged in SATA2.  Here are the three screens I can see in GParted...

/dev/sda, /dev/sdb, and /dev/sdc, respectively:

[ATTACH=CONFIG]267250[/ATTACH][ATTACH=CONFIG]267251[/ATTACH][ATTACH=CONFIG]267252[/ATTACH]

I am unsure what I am seeing here, but I think **sdb** is the SATA2 drive that is all botched.  What is **sdc**?

---

### Post by FaultedGeologist on 2016-02-12
> **sudodus said:**
> If you want to create your own partition table, I suggest that you ***boot into the Lubuntu install drive*** again,

- run ***gparted***, unmount the mounted partitions in the internal drive and remove all those partitions.

- After that you create new partitions according to what you want.

- After that you run the installer and select *Something Else* at the partitioning window.

- Select the root partition and the home partition.

- The swap partition will be selected automatically (if you have created one with gparted).

- The bootloader will be installed into /dev/sda (the [first] internal drive) by default. It is probably correct. Change it only if you know what you are doing.

Methinks this makes sense now.  I booted the live USB, but have no GParted natively.  In the other OS, I had to run a script in Terminal to get GParted to install.  This Lubuntu has a program called Disks under Accessories.  **In it, the assessment is that the Disk is OK, 20 bad sectors (42C/108F)** - I didn't know the drive had a thermometer in it.  I removed all the partitions.  In this program, it gives me the option to overwrite with zeros!  Woo hoo!  This should allow me to wipe the slate clean.  I am creating 5GB unnamed ext4 (no swap options here) that will become swap, then a 30GB ext4, then the rest ext4.  Next, running the installer using O Something Else as planned.  Hopefully this solves the problem and I can close this nasty book.

---

### Post by sudodus on 2016-02-12
> **FaultedGeologist said:**
> Would checking the Format box erase the old Ubuntu install when I do this?
Yes
> 
.  Here are the three screens I can see in GParted...

/dev/sda, /dev/sdb, and /dev/sdc, respectively:

[ATTACH=CONFIG]267250[/ATTACH][ATTACH=CONFIG]267251[/ATTACH][ATTACH=CONFIG]267252[/ATTACH]

I am unsure what I am seeing here, but I think **sdb** is the SATA2 drive that is all botched.  What is **sdc**?

It is the USB pendrive

---

### Post by FaultedGeologist on 2016-02-12
[B]I owe everyone a beer.  Let me know if you are passing through Kansas.  Marking the thread as SOLVED!!  

[/B]It seems that writing the zeros over the drive did the trick using Disks in Lubuntu Live USB mode to reformat and partition.  Next, I ran the installer, reassigned the partitions to swap, /, and /home.  

I am still wondering what is going to happen with 20 bad sectors on the HD.  Can this thread still receive posts after SOLVED is marked?  If not, PM me.

Bon weekend!

---

### Post by sudodus on 2016-02-12
> **FaultedGeologist said:**
> Methinks this makes sense now.  I booted the live USB, but have no GParted natively. 

If I remember correctly, all Ubuntu flavour desktop iso files contain gparted. I know Lubuntu does, so you should find it via the menu in the live system running from the CD/DVD/USB drive. It is one of the System Tools. But it is not present in the installed system, because normally you run it from 'another drive' (not the drive that you intend to edit, and normally you edit the internal drive).
> 
In the other OS, I had to run a script in Terminal to get GParted to install.  This Lubuntu has a program called Disks under Accessories.  **In it, the assessment is that the Disk is OK, 20 bad sectors (42C/108F)** - I didn't know the drive had a thermometer in it.  I removed all the partitions.  In this program, it gives me the option to overwrite with zeros!  Woo hoo!  This should allow me to wipe the slate clean.  I am creating 5GB unnamed ext4 (no swap options here) that will become swap, then a 30GB ext4, then the rest ext4.  Next, running the installer using O Something Else as planned.  Hopefully this solves the problem and I can close this nasty book.

Good luck :-)

---

### Post by sudodus on 2016-02-12
> **FaultedGeologist said:**
> [B]I owe everyone a beer.  Let me know if you are passing through Kansas.  Marking the thread as SOLVED!!  

[/B]It seems that writing the zeros over the drive did the trick using Disks in Lubuntu Live USB mode to reformat and partition.  Next, I ran the installer, reassigned the partitions to swap, /, and /home.  

I am still wondering what is going to happen with 20 bad sectors on the HD.  Can this thread still receive posts after SOLVED is marked?  If not, PM me.

Bon weekend!

Congratulations and thanks for marking the thread as solved :KS

You can continue to post here, but it is much better to start a new thread with a good descriptive title and more details in the first post alias 'opening post'. This will attract people who know about your next problem and you will get better help (in this case from people who know about troubleshooting disks with bad sectors).

---

