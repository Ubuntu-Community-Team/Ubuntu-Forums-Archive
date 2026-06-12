---
title: "Installing Ubuntu 10.10 on a second hard drive"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by kyral210 on 2010-12-17
Ok, sorry to disapoint everyone, but I love Windows 7 and I want to keep it as my main OS. But, I also want a copy of Linux as an alternative OS to play with and maybe use for more. My PC has four hard drives and I want to keep the main hard drive (C) as my Windows HD, and install Ubuntu on one of my other drives, say D.
 
Do I need to do anything special configuring the HD's before installation, or can I just go and install onto the D hard drive? Do I have to configure Windows at all?
 
Just so you know, HD: D is currently empty and unused, but small with around 69 Gb free space.

---

### Post by kansasnoob on 2010-12-17
You're very wise to plan in advance :D

You might find some of the info I posted here useful:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

I've been collaborating with Herman to bring this tutorial up to date:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

I'd particularly point out how Ubuntu identifies discs and partitions:

> In case you're new from Windows I want to explain about the Linux way of numbering disks and partitions before you get too confused and upset.  There's no such thing as a 'C: drive' in Linux or any other drive letter for that matter. I hope you'll see why the Linux partition naming system makes a lot more sense.

In Linux the word 'disk' means an entire disk, such as a hard disk drive, SSD or flash memory drive.
Disks are numbered with letters, starting with 'a' for the first disk and 'b' for the second and so on.

Partitions have numbers.
Only primary partitions including the extended partition if there is one can have the numbers 1, 2, 3 or 4.
Logical partitions (inside the extended) are always numbered counting from 5 upwards.
If you're not sure what I'm talking about here and you're curious you may use this link, Help on Partitioning.

If you look in the screencap below, you'll see a spinbox over in the top right-hand corner for changing between one hard disk and another, including and USB drives you may have plugged in.
My first disk is called /dev/sda in Linux speak.
My second disk is called /dev/sdb.
My third disk will be called '/dev/sdc', and so on ...
The first part, '/dev/' stands for 'device', and the second part, 'sda', means hard drive 'a', for the first hard drive.
It used to be 'hda' in the old days, for 'hard drive a', but they changed the 'h' to an 's' for reasons that are outside the scope of this how-to.

The first partition in my /dev/sda disk is /dev/sda1.
The second partition is called /dev/sda2.
If I had more partitions they'd be numbered /dev/sda3, and /dev/sda4.
Partitions don't necessarily need to appear on the disk arranged in numerical order.

---

### Post by kyral210 on 2010-12-17
Thanks for the info, but I dont really want to partition my C drive since I only have 100 Gb left...

Is installing Ubuntu on a second hard drive a really bad idea?

---

### Post by b_w on 2010-12-17
I just did it with my desktop and it is working perfectly. The only thing that I had to do differently was select the drive with Ubuntu on it as the primary boot drive.

---

### Post by kyral210 on 2010-12-17
and how do I select that? Would it be a BIOS thing? Would I be able to use Windows 'startup and recovery' to put up a 'chose your OS' screen at startup?

---

### Post by kyral210 on 2010-12-19
Any further advice for me before I take the plunge? I dont want to screw up my PC...

---

### Post by Rebelli0us on 2010-12-19
> **kyral210 said:**
> Any further advice for me before I take the plunge? I dont want to screw up my PC...

You're wise to worry, Ubuntu installer can easily destroy windows. I'd temporarily disable or disconnect your 1st Windows "C" disk, and do a default Linux install on the 2nd disk. Then use BIOS to boot the OS of your choice, or reconfigure windows bootloader to boot either OS.

---

### Post by kyral210 on 2010-12-19
If I don't unhook the C drive and just install Ubuntu onto my D drive (telling the installer to install on d ONLY), will it cause problems?

---

### Post by Rebelli0us on 2010-12-19
> **kyral210 said:**
> If I don't unhook the C drive and just install Ubuntu onto my D drive (telling the installer to install on d ONLY), will it cause problems?

Yes you can but you have to make sure that Ubu puts the bootloader (Grub) on D as well. There is an obscure setting during the install that accomplishes this but it's easy to overlook. It also uses techno-gibberish terms to identify partitions, like hd0, sdb2, etc., so it's very easy to inadvertently trash your Windows.

---

### Post by Pillars of Creation on 2010-12-19
Get Grub2 to boot OS on second drive issue


ran update-grub.

[http://ubuntuforums.org/showthread.php?t=1264354](http://ubuntuforums.org/showthread.php?t=1264354)


&#8220;I added "(hd1) /dev/sdb" to /boot/grub/device.map and ran update-grub.
This adds to operating systems on the second drive to GRUB, which works just as well.&#8221;

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1558804](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1558804)

---

### Post by oldfred on 2010-12-19
Many here recommend unplugging the windows drive, but if you also have other drives you still have to make sure that whatever drive is sda is where you install as  that is where grub will default to unless you use manual install.

kansasnoob gave you a good link to installing in dual drives. Most install instructions do not discuss that.

If you disconnect a drive:
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)

---

### Post by Pillars of Creation on 2010-12-19
kyral210, 

&#8220;Ok, sorry to disappoint everyone, but I love Windows 7 and I want to keep it as my main OS. But, I also want a copy of Linux as an alternative OS to play with and maybe use for more. My PC has four hard drives and I want to keep the main hard drive (C) as my Windows HD, and install Ubuntu on one of my other drives, say D.

Do I need to do anything special configuring the HD's before installation, or can I just go and install onto the D hard drive? Do I have to configure Windows at all?

Just so you know, HD: D is currently empty and unused, but small with around 69 GB free space.&#8221;

I haven&#8217;t actually tried dual booting Windows 7 and Ubuntu across two drives but here&#8217;s what I suggest. As long as you have the Windows 7 install disc, and I suggest you make a copy because you might be using it frequently, you can easily repair the Windows 7 installation. It&#8217;s really quite easy to do so.

What I suggest you do is boot Ubuntu in life CD mode and run the GParted partition utility. Use it to make two partitions on the second hard drive. The main one is for Ubuntu and the second one is a swap file which should be approximately twice the size of memory in case you want to put Ubuntu into sleep mode. Note the size of the Ubuntu partition. Then reboot and install Ubuntu into that partition on the second hard drive.

Then I suggest you boot into Windows 7 and  download and install a free third-party boot loader called EasyBCD 2.0.2 and install it. it will modify the Windows 7 boot loader and allow you to add other OS&#8217;s to it. You can then configure it to automatically start Windows 7 if you don&#8217;t do anything or if you touch space bar you can boot into other OS&#8217;s.

EasyBCD 2.0.2

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)


[http://neosmart.net/wiki/display/EBCD/Windows+XP](http://neosmart.net/wiki/display/EBCD/Windows+XP)


Dual-Booting Ubuntu Linux and Windows 7/Windows Vista (with the Windows bootloader)

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Note 1: when you do the Ubuntu install let it do its normal thing regarding grub2. Ubuntu will install its own grub2 boot loader. After you get the Ubuntu installed do the repair procedure with a Windows 7 disc to get the Windows 7 boot loader back up and running. Then boot into Windows 7 and start EasyBCD 2.0.2 and add the Ubuntu entry to the boot loader menu.

You now effectively going to have two separate boot loaders on the system. Slightly annoying but tolerable. Later on you can go into Ubuntu and edit the grub2 boot loader to time to load equal zero.

Note 2: for the scenario you&#8217;re talking about what I am about to mention is irrelevant. A hard drive can have up to four primary  partitions or three primary partitions and a extended partition which can contain many logical partitions.

On a system with more than one hard drive the lettering scheme in terms of drive letters can get complicated. For example if a system has one hard drive with four primary partitions, they will in order be lettered C, D, E, F. 

On the other hand if a system with two hard drives has four primary partitions on each hard drive the letter will go this way. The first partition on the first hard drive  will be C. the first partition on the second hard drive will be D. The second partition on the first hard drive will be E. This means that if someone sets up Two Windows OS&#8217;s on the first hard drive in primary partitions, adding a second hard drive with a primary partition will screw up the second windows on the first hard drive. Windows can&#8217;t deal with having its drive letter changed once it&#8217;s installed.

So while it&#8217;s perfectly fine to install Ubuntu using primary partitions is important to note that it can also be installed into logical extended partitions. Adding logical extended partitions to a second hard drive would not affect the drive letter ordering on the first hard drive.

Good luck with your dual operating system two hard drive multi-booting setup.

---

### Post by irockonguitar on 2010-12-19
I would like to do this same thing with my new laptop which has two hard drives. It currently runs Windows 7 which I know almost nothing about, as I have used Ubuntu exclusively on my older laptop. I'm not the most computer literate person out there though, so I don't understand what you guys are talking about with Grub and BIOS and disconnecting drives and all that, so is there a step-by-step how-to for this anywhere?

Thanks :)

---

### Post by oldfred on 2010-12-19
irockonguitar, if you look thru the posts in this thread you will see a lot of links each is slightly different but they all go over more details than we can post.

---

### Post by C.S.Cameron on 2010-12-20
I recommend unplugging all hard drives except the one you are installing to. If you do that you can't go wrong.

If you choose not to unplug all hard drives except the one you are installing to:

1) When you get to partitioning make sure you are installing to the correct drive.
2) Use manual partitioning.
3) Select the correct drive for bootloader installation.

In BIOS choose the new HDD as first HDD, you should be able to select drives with other O/S's from grub at boot.

If you unplugged the other HDD's during install you may need to do an update-grub to add the other drive to the startup grub menu.

---

### Post by Rebelli0us on 2010-12-22
> **oldfred said:**
> Many here recommend unplugging the windows drive, but if you also have other drives you still have to make sure that whatever drive is sda is where you install as  that is where grub will default to unless you use manual install.

kansasnoob gave you a good link to installing in dual drives. Most install instructions do not discuss that.

If you disconnect a drive:
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)

Thanks Fred, the 1st link is very useful.

For most new users, Linux fails at the install stage, because they're asked to set a "mount point", an unknown concept, so most users simply quit here.

---

### Post by kansasnoob on 2010-12-23
> **kyral210 said:**
> Thanks for the info, but I dont really want to partition my C drive since I only have 100 Gb left...

Is installing Ubuntu on a second hard drive a really bad idea?

No.

---

### Post by kansasnoob on 2010-12-23
> **kyral210 said:**
> If I don't unhook the C drive and just install Ubuntu onto my D drive (telling the installer to install on d ONLY), will it cause problems?

Arrgh, this is exactly why I posted the info I did in post #2. You're still talking about drive C and drive D, but what you really need to understand is how Ubuntu recognizes your drives and partitions :)

A common command for identifying drives and partitions is "sudo fdisk -l" (BTW that's a lower case L at the end), just as an example:

```
lance@lance-desktop:~$ sudo fdisk -l
[sudo] password for lance: 

**[COLOR="Red"]Disk /dev/sdb: 80.0 GB[/COLOR]**, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eeefe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9730    78149632   83  Linux

**[COLOR="Red"]Disk /dev/sda: 500.1 GB[/COLOR]**, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a6391

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2610    20964793+  83  Linux
/dev/sda2            2611        5219    20956792+  83  Linux
/dev/sda3            5220       18363   105579180   83  Linux
/dev/sda4           18364       60801   340883173    5  Extended
/dev/sda5           39292       45992    53825751   83  Linux
/dev/sda6           45993       52514    52387933+  83  Linux
/dev/sda7           52515       59192    53641003+  83  Linux
/dev/sda8           59193       60495    10466316   83  Linux
/dev/sda9           60496       60801     2457913+  82  Linux swap / Solaris
/dev/sda10          36642       39291    21286093+  83  Linux
/dev/sda11          33998       36641    21237898+  83  Linux
/dev/sda12          31366       33997    21141508+  83  Linux
/dev/sda13          28691       31365    21486906   83  Linux
/dev/sda14          18364       20924    20571169+  83  Linux
/dev/sda15          20925       23487    20587266   83  Linux
/dev/sda16          23488       26089    20900533+  83  Linux
/dev/sda17          26090       28690    20892501   83  Linux

Partition table entries are not in disk order

```

From that you can see I have a lot of partitions on /dev/sda which is a 500 GB drive, and only one partition on /dev/sdb which is an 80 GB drive. If I wanted to install Ubuntu 10.10 to /dev/sdb I'd first boot the Ubuntu 10.10 Live CD choosing "Try Ubuntu" rather than "Install Ubuntu".

That would give you a chance to see just how well Ubuntu is going to run on your hardware, and you can then find out just how Ubuntu identifies your drives and partitions using Gparted, which you'll find in System > Administration. That's something you should know regardless of what installation procedure you decide to follow.

Obviously you would not want to use the "Install alongside" option because you don't want to resize any of your Windows partitions (that option is also riddled with bugs), and if you choose "Erase and use entire disc" you'll have no option for choosing where to install the Grub bootloader :(

Therefore I can personally only recommend using the "Specify partitions manually (advanced)". Yes, that does somewhat complicate matters, and I have filed bug reports in an attempt to make things easier.

---

### Post by kyral210 on 2011-01-06
Ok, please let me know if I have this right.
 
[LIST]
[*]My main boot loader & windows 7 is loaded on drive C. I leave that 100% alone
[*]I install Ubuntu onto drive D being VERY careful to tell it to install Grub & ubuntu onto D drive.
[/LIST]If I do that Ubuntu wont screw up Windows?
 
Ok, so what then? How do I get the option to boot into Windows or Ubuntu working, so is it automatic?
 
Really sorry I am a little helpless here, still getting to grips with Ubuntu. I think Windows 7 is better, but I like Ubuntu on the work laptop so much I want a copy of it on my home PC.

---

### Post by Sylos on 2011-01-06
> **kyral210 said:**
> Ok, please let me know if I have this right.
 
[LIST]
[*]My main boot loader & windows 7 is loaded on drive C. I leave that 100% alone
[*]I install Ubuntu onto drive D being VERY careful to tell it to install Grub & ubuntu onto D drive.
[/LIST]If I do that Ubuntu wont screw up Windows?
 
Ok, so what then? How do I get the option to boot into Windows or Ubuntu working, so is it automatic?
 
Really sorry I am a little helpless here, still getting to grips with Ubuntu. I think Windows 7 is better, but I like Ubuntu on the work laptop so much I want a copy of it on my home PC.


If you do that as suggested by others then theoretically nothing should be harmed. If you manualy specify the installation to your unused HDD then everything should be fine BUT things can always go wrong with any installation on any system. If you have valuable data on your existing drives back it up before you embark on this.

With regard to your question about booting into windows - the GRUB bootloader will search for other OS's when it is installed and will add a windows entry to the boot loader screen for each additional OS it finds. This wont happen if you disconnect your windows HDD before installation but it can easily be updated once the install is complete and you have plugged your windows drive back in.

As for my opinion - I have never removed any of my HDDs when installing Ubuntu and havent yet had any problems (is saying that a curse?). I would look very carefully in windows before you start the installer and take notes of the sizes of each drive and the sizes of each partition on the drive. Remeber that (as already mentioned by other more knowledgable people than me) the drives wont be labeled D E etc so you need to be able to identify them by their size and number and size of partitions. This will help you ensure that you dont select the wrong drive or Partition when the time comes. And also, when you come to install, if you suddenly feel unsure that you are selecting the correct drive/partition - bail out and recheck everything.

Hope that helps.

---

### Post by Rebelli0us on 2011-01-06
> **kyral210 said:**
> Ok, please let me know if I have this right.
 
[LIST]
[*]My main boot loader & windows 7 is loaded on drive C. I leave that 100% alone
[*]I install Ubuntu onto drive D being VERY careful to tell it to install Grub & ubuntu onto D drive.
[/LIST]If I do that Ubuntu wont screw up Windows?
 
Ok, so what then? How do I get the option to boot into Windows or Ubuntu working, so is it automatic?
 
Really sorry I am a little helpless here, still getting to grips with Ubuntu. I think Windows 7 is better, but I like Ubuntu on the work laptop so much I want a copy of it on my home PC.

Yep, you can have the 2 OS completely independent and boot each with the BIOS boot menu -- F8, F12.

Linux doesn't use letters, your C: drive will probably be shown as /dev/sda and your D: as /dev/sdb and the installer should also show the volume label on your Windows NTFS disk which will help you make sure to install Linux on the OTHER disk. So if you install on /dev/sdb and put the boot loader on /dev/sdb as well, your windows disk will be untouched. Also since the 2 disks will have their own boot loader, you could remove either one and the other will still boot ok.

---

### Post by oldfred on 2011-01-06
kyral210,

As Kansasnoob posted before run this so we can see your exact drive layout. I am concerned if you really have a second hard drive or just a partition. Windows calls both drives & partitions as drives, so D: can be either a drive or a partition.

From liveCD:

```
sudo fdisk -lu
```

---

### Post by Rebelli0us on 2011-01-06
> **oldfred said:**
> kyral210,

As Kansasnoob posted before run this so we can see your exact drive layout. I am concerned if you really have a second hard drive or just a partition. Windows calls both drives & partitions as drives, so D: can be either a drive or a partition.

From liveCD:

```
sudo fdisk -lu
```

Good idea, although he said in the OP that "PC has four hard drives". And since he said he's new to Linux he's more comfortable using Windows so he could also use Windows' "Disk Management" to see how many drives & partitions are available.... right-click My Computer > Manage > Disk management.

---

### Post by edwardalmost on 2011-01-22
[COLOR="Black"]_**re: **[[COLOR="Black"]**richard petty experience in las vegas[/COLOR]**](http://www.racingadventure.com/)_[/COLOR]



Has any one tried it?

---

