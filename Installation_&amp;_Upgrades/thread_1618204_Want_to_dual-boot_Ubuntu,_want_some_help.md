---
title: "Want to dual-boot Ubuntu, want some help"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by erikvduyn on 2010-11-10
After messing around with booting Ubuntu from my USB drive, I decided a dual-boot wouldn't be a bad idea. Problem is, I don't really know how to go about doing it. I consulted the wiki but I found it a bit confusing.

Can somebody give me a good step-by-step guide on how to do it?

---

### Post by sikander3786 on 2010-11-10
Hi and Welcome to Ubuntu :popcorn:

It would be better if you go through this guide and then post specific queries for the issues you can't understand in there. We would be able to better answer then :-)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by candtalan on 2010-11-10
Welcome!

> **sikander3786 said:**
> Hi and Welcome to Ubuntu :popcorn:
It would be better if you go through this guide and then post specific queries for the issues you can't understand in there. We would be able to better answer then :-)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Yes, good strategy.

Installing Ubuntu is fast. 

However, it is the Windows side of things which really takes up a LOT of time. If you intend to continue using Windows, as you might, then take a lot of care and patience with the possible recovery information and tools, and of course, any of your own data in Windows.

---

### Post by erikvduyn on 2010-11-10
Okay, here goes.

The wiki mentions something about resizing the windows partition beforehand, followed by partitioning using the Ubuntu installer. That confuses me a bit. Do I need to make a separate empty partition to install Ubuntu on or can the installer create it?

The wiki also says to use a CD to install it. I assume I can also install Ubuntu by booting the ISO from a USB drive?

And as stupid as this is gonna sound (but I'd rather know for sure), when I've installed it, how do I choose which OS to boot into when I start my laptop?

---

### Post by sikander3786 on 2010-11-10
> The wiki also says to use a CD to install it. I assume I can also install Ubuntu by booting the ISO from a USB drive?

But you'll properly need to extract the iso to the USB before you can boot from it.

I use unetbootin to serve the purpose.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

> Do I need to make a separate empty partition to install Ubuntu on or can the installer create it?

The installer can create it for you. But we need some info. Please burn a Live USB, boot from it and then from Terminal (Applications > Accessories > Terminal), post the output of

```
sudo fdisk -l
```


Edit:

> how do I choose which OS to boot into when I start my laptop?

A default Ubuntu installation should let you dual boot Windows. Grub (the Ubuntu bootloader) should pick up Windows itself and add an entry to the menu which is shown when you boot.

Some people run into troubles. No promises that it will dual boot that easily. But those problems are easily solve-able. I am not trying to frighten you at all. Please understand. We'll be happy to assist you.

---

### Post by Mercfrog on 2010-11-10
I'm new to Ubuntu/Linux but not to computers (15 years webmaster).
I want to have a dual boot for XP & Ubuntu on 1 disk with separate partitions.
I made 2 partitions (2x250GB)
Here's the problem: When installing (U10.10) I am asked "side by side", "Wipe entire disk" & "Specify partitions manually".

I believe* Manually was the one I wanted but keep getting a "No root file system is defined" message while trying it this way.
* Sideby side" sounds like on the same partition, "wipe entire disk" did not sound like a good idea either as I want to keep my XP working.

Question: What is the best route in order to install it on a separate partition?
(XP is currently installed and running, but I would like the Ubuntu to also be "really" installed- nothing virtual or within windows)

---

### Post by erikvduyn on 2010-11-10
> **sikander3786 said:**
> 
The installer can create it for you. But we need some info. Please burn a Live USB, boot from it and then from Terminal (Applications > Accessories > Terminal), post the output of

```
sudo fdisk -l
```

```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6d401907

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1567    12586896   27  Unknown
/dev/sda2   *        1568        1580      104422+   7  HPFS/NTFS
/dev/sda3            1581       71248   559608210    7  HPFS/NTFS
/dev/sda4           71249       77825    52829752+   f  W95 Ext'd (LBA)
/dev/sda5           71249       77825    52829721    7  HPFS/NTFS

Disk /dev/sdb: 16.0 GB, 16001269760 bytes
255 heads, 63 sectors/track, 1945 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1946    15626208+   c  W95 FAT32 (LBA)

```
It may be worth to mention that my HDD is currently split into 2 partitions. One that's roughly 50 gigs and the rest is in the other.

> Some people run into troubles. No promises that it will dual boot that easily. But those problems are easily solve-able. I am not trying to frighten you at all. Please understand. We'll be happy to assist you.
Why do you think I came here rather than asking somebody who may or may not know? I've heard lots of praise about the Ubuntu community when it comes to tech support so I figured it was my best bet.

---

### Post by sikander3786 on 2010-11-10
You didn't metion which drives are useless for you? Where do you want to install Ubuntu?

---

### Post by erikvduyn on 2010-11-10
> **sikander3786 said:**
> You didn't metion which drives are useless for you? Where do you want to install Ubuntu?

The only drive I currently have is a 640 gig drive divided in 2 partitions.
The other one that's at the bottom is the USB stick I'm booting from.

Why, did something **** up with my HDD or something?

---

### Post by oldfred on 2010-11-10
If using Vista or 7 it is better to use the windows MMC to modify the windows partition and reboot windows several times as it will want to run chkdsk or other repairs to update itself to its new size.

If specifying partitions manually you have to create a / (root) and  a swap partition. One advantage of manual install is you can also add a /home partition but you do not have to. I prefer to have data separate from system installs. So I also like to have most of my windows data in another NTFS partition also.

Some examples of installs:
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by erikvduyn on 2010-11-10
> **oldfred said:**
> If using Vista or 7 it is better to use the windows MMC to modify the windows partition and reboot windows several times as it will want to run chkdsk or other repairs to update itself to its new size.

If specifying partitions manually you have to create a / (root) and  a swap partition. One advantage of manual install is you can also add a /home partition but you do not have to. I prefer to have data separate from system installs. So I also like to have most of my windows data in another NTFS partition also.

Some examples of installs:
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

So basically:
1. Clear up a partition with plenty of free space in Windows.
2. Boot Ubuntu setup through either USB or CD.
3. Create a / partition of at least 4 gigs and a /home partition with the rest.
4. Install

That's pretty much it?

Okay, I know you don't have to have seperate partitions for / and /home, but the idea of being able to re-install and keep all my data sounds rather appealing.

---

### Post by Mercfrog on 2010-11-10
Oldfred: Thankyou !!! This seems to be what I'm looking for. I have been trying for over a week to get this working and have completely nuked my PC 4 times- but I refused to give in :)
I tried finding this in forums and Co. but with all the variables out there I never had an example with the U10.10 version and many videos were not "readable" from the quality. I did try though, before I asked for help. I will leave windows as soon as they make a "Call of Duty" game version for the Linux :) I'll let you know tomorrow how it turned out and mark my thread accordingly. Thanks again!!

---

### Post by candtalan on 2010-11-10
> **Mercfrog said:**
> I'm new to Ubuntu/Linux but not to computers (15 years webmaster).
I want to have a dual boot for XP & Ubuntu on 1 disk with separate partitions.
I made 2 partitions (2x250GB)
Here's the problem: When installing (U10.10) I am asked "side by side", "Wipe entire disk" & "Specify partitions manually".

I believe* Manually was the one I wanted but keep getting a "No root file system is defined" message while trying it this way.
* Sideby side" sounds like on the same partition, "wipe entire disk" did not sound like a good idea either as I want to keep my XP working.

Question: What is the best route in order to install it on a separate partition?
(XP is currently installed and running, but I would like the Ubuntu to also be "really" installed- nothing virtual or within windows)

Be careful with 10.10 Desktop edition installer, although if you accept a resize option that will work ok afaik. But one of the in depth options has given grief
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/659106)

(Ubuntu 10.04.1 installer is less problematic).

'Side by side' is expecting to take one of your existing partitions, (experience suggests it takes the largest one, or maybe with the biggest space in it) and offers to resize it. You do not get the opportunity to choose *which *partition in this option. Although for many Windows users this will provide a serviceable situation.

If you intend to choose the advanced option it is easiest to first (using the live CD or live USB) create a partition for the system to go into (format ext4) and a partition for swap (format as swap). (Swap size - I use between 500 MB and 2 GB depending....)

[edit]
As mentioned elsewhere, it is perhaps wise to use the Windows own facility to resize itself, rather than use a non windows partition editor, since some problems seem to occur in at least some versions of Vista, not sure about windows 7.
[end edit]

When you later proceed to the install, and choose the advanced option, take care to identify your target partitions correctly (not mix up with your other ones!). 

The target system partition must be marked as to mount as  /  (that is, root). Right clicking onto the individual partition line entry will offer edit. This is how you set and change the options. 
 
The target swap partition - similar - set to swap.

Review the partitions lines, verify that th etarget  / partition is the only one set to format(!) swap will get format anyway.

Then proceed.

---

### Post by candtalan on 2010-11-10
> **erikvduyn said:**
> 
3. Create a / partition of at least 4 gigs and a /home partition with the rest.


You will need a '/'  AND a 'swap' partition as a minimum

---

### Post by erikvduyn on 2010-11-10
> **candtalan said:**
> You will need a '/'  AND a 'swap' partition as a minimum

Well, this guide:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Says this:
> If you have very little RAM (less than 512 MB) or if you plan to use hibernate (also known as suspend-to-disk), you should create what's called a swap partition, usually 1.5 or 2 times the amount of RAM you have. Swap is one of the types you can select instead of ext3 or ext4 for the Use as drop-down.

If you plan to use only sleep (also known as suspend-to-RAM) or shut down completely and you have a decent amount of RAM (1 GB or more), you don't need to bother with a swap partition.

Since I have 4 gigs of ram and only use sleep or shutdown, that guide would suggest I don't need a swap partition.

---

### Post by oldfred on 2010-11-10
Having some swap even if it is not normally used is a good idea. Some seem to think the system checks for swap and if not found it slows down a little. I have lots of applications installed and have used about 6GB in root, but if writing a DVD you may need another 4GB in tmp to store files. If really restricted you can get by with smaller system root but then have to houseclean regularly and not run processes that consume too much system.

Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up. Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM.

---

### Post by erikvduyn on 2010-11-10
> **oldfred said:**
> Having some swap even if it is not normally used is a good idea. Some seem to think the system checks for swap and if not found it slows down a little. I have lots of applications installed and have used about 6GB in root, but if writing a DVD you may need another 4GB in tmp to store files. If really restricted you can get by with smaller system root but then have to houseclean regularly and not run processes that consume too much system.

Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up. Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM.

So you'd definitely recommend a swap partition? What use does it exactly have?
Do you normally have to configure a swap partition yourself or does Ubuntu have an option in the installer to add it?

---

### Post by hobbes543 on 2010-11-10
I have a question along similar lines.  What I want to do, is get a second hard drive and install Ubuntu to that.  On that second disk would be two partitions, one for the Ubuntu install and the other as an NTFS storage space that both OSes can access. (I would also give Ubuntu read write access to my C: drive as well)

Now, I have virtually no experience with Linux and the guides that I have found reference setting up the dual boot when both OSes are on the same disk.  Since I already have Win 7 installed on my C drive and various games and other software already installed to that drive, along with documents and media files (all backed up on an external disk regularly) I want to leave that disk intact as is.  

Do you know if there is a clearly written guide to setting up a dual boot where Windows is on one disk and Linux is on a second disk?  Is the process the same with a few differences in options chosen?  If so what are those diffrences?

Thanks

---

### Post by oldfred on 2010-11-10
Only if you use one of the automatic install options will Ubuntu automatically add swap. Sometimes when using a very large drive it may put a very large swap. Just to have control over partition sizes I prefer to manually configure partitions in advance. If you have a swap partition the installer does find it and mount it. I have swaps on two different drives and it mounts both, so I have to manually remove one.

Second hard drive is just like any other install except it is better to install grub to the MBR of the second drive and in BIOS boot that drive. The only way you get the combo box to choose the second drive's MBR is to use manual install.

Look at post #10 for Maverick screens as they have changed somewhat, but the install process is the same.

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

---

### Post by erikvduyn on 2010-11-10
Well, just did it. My laptop is now running a Windows 7/Ubuntu dual-boot. Everything's getting along smoothly (I can even still boot into Windows. Look at that, I didn't even break my laptop!). Now all I need to do is learn to use Linux I guess.

Big thanks to all who helped me.

---

### Post by hobbes543 on 2010-11-10
> **oldfred said:**
> Only if you use one of the automatic install options will Ubuntu automatically add swap. Sometimes when using a very large drive it may put a very large swap. Just to have control over partition sizes I prefer to manually configure partitions in advance. If you have a swap partition the installer does find it and mount it. I have swaps on two different drives and it mounts both, so I have to manually remove one.

Second hard drive is just like any other install except it is better to install grub to the MBR of the second drive and in BIOS boot that drive. The only way you get the combo box to choose the second drive's MBR is to use manual install.

Look at post #10 for Maverick screens as they have changed somewhat, but the install process is the same.

Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")


Ok, so if I want to be more specific with my partitions on the second drive, I would have to create a primary partition at the beginning for Linux, a small partion for the SWAP and then format the last partition as NTFS so that both OSes could access the data there?

For example, say my second drive is 500 GB
I would have 
Primary 1: 100GB for Linux OS and software installs
Primary 2: 4GB for Swap partion (my computer has 4GB of memory)
Logical 1: Remainder formatted as NTFS so both my Windows and Linux installs can access it.

Is this correct?  And the Ubuntu installer will give me the option to create these partions on the disk during the install?

---

### Post by oldfred on 2010-11-10
You can do that and it will work just fine. For the first couple of years I only had root, swap and a shared (then FAT) NTFS (now) partition. The user configs and any data in Ubuntu will default into /home unless you specify otherwise.

I prefer a separate /home. You will be able to put most data into the shared NTFS partition, I still have firefox and thunderbird profiles still in my shared NTFS partition. But most of my data now goes into a /data partition as I now use windows so little.

---

### Post by hobbes543 on 2010-11-10
Ok.  Would I be able to install Linux software to NTFS partition?   I see the point of having a separate partition as a home directory though.   I still need to figure out if my wireless adapter will work as it is integrated with my motherboard.

---

### Post by sikander3786 on 2010-11-11
> Would I be able to install Linux software to NTFS partition?

Simple answer, No. Many reasons behind that. NTFS doesn't support Linux permissions. The installation on Linux is a bit different than Windows. Libraries go to one folder, docs to another, config into another etc.

> I still need to figure out if my wireless adapter will work as it is integrated with my motherboard.

Boot from a Live CD and test your wireless adapter. If it is not supported natively, you might find its drivers under System > Administration > Additional Drivers once you connect to internet by using an ethernet cable.

---

### Post by hobbes543 on 2010-11-11
I was able to connect wirelessly running from the live CD so my adapter is supported it seems.  So it seems this project is definitely a go.  I plan to get a new HDD today.

So just to verify.  If I want Linux to dual boot with the Linux install on a second disk,  When I get to the part of the installation where I have to choose the location, I should choose manual install and then the option to create partitions on the new disk.

The new disk should have a primary partition for Linux, followed by a small swap partition.  The remainder can be formatted either as a large NTFS storage drive or split into smaller drives, possibly with one being formatted using EXT-3  as a /home directory and for installations of linux software.

Then when I have the option to choose the location of Grub, I should have it install on the MBR of the second disk and then change my BIOS to boot from the second disk.  Is there any special procedure you have to do to install grub to the second disk?


Also, I know for the partition that I am installing Linux to I have to specify the mount point as / and for the home partition I need to specify the mount point as /home.  Do I need to specify the mount point for the swap partition or the partition that is going to be formatted as NTFS?

---

### Post by oldfred on 2010-11-11
If you have partitioned in advance, the installer finds an existing swap. You cannot mount the NTFS partition as part of the install, but have to do that later. 

If the windows install on the other drive is not automatically found initial as it should be, then run this from an Ubuntu command line:
sudo update-grub

To manually mount NTFS partition you need to understand fstab and mounting in Linux.
Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

---

### Post by hobbes543 on 2010-11-11
Ok, so when I am setting up Linux, I should leave the last part of the drive, which I intend to format as NTFS unallocated since I will be starting from a completely blank HDD and then format that last bit in Windows as NTFS after the Linux install?  

Also, does grub install by default to the Linux drive /partition?  And if so, all I would have to do to dual boot after the install is change the boot order in my BIOS so my second HDD is the drive my computer tries to boot from first?

---

### Post by oldfred on 2010-11-11
Grub usually default to the sda MBR. Anytime you do not want it in sda you need to specify. It is not all that difficult to reinstall but it is easier to install it as part of the install.

The Ubuntu installer does not include the NTFS driver on the liveCD install due to space limits. If you download gparted as a liveCD it does include the driver and once you have installed Ubuntu the NTFS driver is installed. You do have to be careful with any windows partitioning after Ubuntu install. Windows does not see ext partitions and sometimes erases them. Often they are still there just the partition table is missing them.

---

### Post by Mercfrog on 2010-11-11
Hi Oldfred!
It seems to work (almost) what you suggested yesterday, here's where I'm stuck now:
When setting up partitions within Ubuntu 10.10 under "Manually select ..." I am not given
the ability to give "/home" a Primary setting when following the instructions shown under
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml) 

When setting up "swap" it offers "primary" & "logical" options. 
(I tried setting up with both versions of this "radio" button)

When setting up "/" it also offers "primary & logical". 
(no problems here)

When setting up "/home" it does not offer "primary & logical" options.

I tried all "variations" of the above but with little success as when going into setup
(which it does) it always hangs on the screen "Who are you". 
The progress bar goes 85% but no further (even after 20 mins). 
The text "Ready when you are" shows up but the "Forward" button is deactivated.

Not sure what to do, I've wiped the partition 2 separate times thinking i had a bug but
no luck. Could this be because I am installing to a partition (second of 2 primarys on my
500 gb disk), as i noticed the instructions in the "link" example were for a separate drive
not a separate partition. I have not yet tried re-burning an iso CD as my copy is from
the Ubuntu website.

Any normal person would have quit by now but sometimes stuff like this is better than
call of duty :) (entertaining and interesting)

Please help if & when you can!!
I REALLY appreciate it!!

---

### Post by oldfred on 2010-11-11
You are only allowed with MBR (msdos) partitioning 4 primary partitions. When they realized that was not many, they allow one primary to be converted to an extended and hold many logical partitions. So you have to make a large extended partition to hold /home & swap and or any other additional partitions you may want. 

I always suggest to make extended the last partition on the drive as then it is somewhat easier to adjust later if desired. Do not use all the primaries it you want to install windows or possibly another windows as the first install of windows has to be in a primary and additional installs are better in a primary partition.

I prefer to use the liveCd's gparted or a download of the gparted liveCD to manually create partitions in advance. Then use manual install to choose which partiton is which and what format to use.

---

### Post by Mercfrog on 2010-11-12
Hi OldFred :)

I was praying you would write back!

I had a somewhat "nebulous" theory that there might be some kind of Primary limit to the system- 
but I had no idea if this was true or what the limitations looked like.
(I even wondered if "Bill" had something to do with it :)

Thanks for the answer- I will give it a go tomorrow (I am in Berlin, Germany, which is why there is 
always a 1 day lag before I get back to you) and let you know how it turns out.

I am/was a die-hard windows guy but after using Firefox a few years I began to see where "open 
source" software can have great advantages over what we are usually forced to use due to not 
knowing it's there or how to use it- now I am a die-hard Firefox user and have not used MSE in 
years, except in my role as webmaster for layout control reasons. (I do not "belittle" Microsoft's 
contribution to the computer age but I think he's made enough now and I am a little skeptical 
about how much "access" they really have to my PC)

When I saw Ubuntu I knew I'd found my "Firefox" of the operating systems !! :)

I'll let you know how turns out...

P.S. I find much of the info you provide, to other users, is excellent and well written- keep up the 
great work!!! It is only through people like you that people "stuck" in windows are able to "free" 
themselves.

---

### Post by oldfred on 2010-11-12
It may actually be Bill's fault. The original PC had floppy drives and hard drives were a mainframe thing. Having 2 floppy drives was a luxury. When they added hard drives 4 partitions seemed plenty. Windows typically only used one. Sometimes users would add a second D: drive (really a partition) but often that even did not always work as everything was designed for C:.

---

### Post by Mercfrog on 2010-11-12
:)

Hi Oldfred!

6 questions:

Just as curiosity; what is the deal with "Primary, Extended & Logical" partitioning options:

1.) I gather a Primary is just that- a primary, but what is the "ranking order" for the other 2 (Ext & Log) ? 

2.) I understand a logical can go into an extended, but I imagine not the other way around?

3.) What is the best use/employment for each type?

4.) Given a 250GB partition- what is the best size for each part of Ubuntu (/, /home & Swap- although I understand the swap should be close to my ram size).

5.) Why are they in need of separate partitions? 

6.) How much of that 250GB can I expect to have left over for "normal" data? (safely)

I'm having a hard time understanding because windows systems can/have everything simply on "C:".

As I plan on "Preaching" Ubuntu to other windows users I'd like to understand some of the "why" because I know questions will arise for some of this :)

Take care and have a nice weekend!!

---

### Post by oldfred on 2010-11-12
Partitioning applies to all computers. The MBR (msdos) type of partitions goes back to the original PC. They allowed up to 4 primary partitions. but soon realized that was not enough so they let you convert one of the primaries into an extended. The extended is just a container and still counts as one primary. All the logical partitions go into the extended partition. 

More info:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

A newer partitioning scheme gpt is now used by Apple, some Microsoft servers and can be used with Linux. Windows will not boot from a gpt partitioned hard drive unless it uses the newer EFI instead of BIOS to start the boot of a system.

If you plan on having windows you need to have a primary partition for the first install (and should for all) of windows. Ubuntu will work from logical partitions. Both windows & Ubuntu will read data partitions in logical partitions, but windows will only read NTFS (and FAT), Linux reads just about everything.

My original install of Ubuntu had just / (root) and swap. I also had XP on another drive and have a shared NTFS (originally FAT) for any data I want to see from both systems. I do not recommend writing from one system into another system, but to use shared data partitions. I have only written into my XP partition to make repairs and have had very few issues with it. 

Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up. Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM.

Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

My Ubuntu install with lots of software installed is about 6GB including /home which is not separate. My /home is less than 1GB but only has mostly hidden user settings for the system. I aggressively move all data into either the shared NTFS data partition or now most data is in a separate /data partition. If you have /home with all its data it will grow depending on how much and what type of data you have.

---

### Post by Mercfrog on 2010-11-14
Hi OldFred!

Ok, I've finally managed to get Ubuntu installed! :)

You will NOT beleive what had been holding me up: The page (on the current 10.10 version) called "Who are you" was not "activating" the forward button-> because I had not filled in a password.

They offer "Automatic sign in" and name & password sing in- I had assumed that since I wanted "Automatic" I did not need to fill it in. You must, or at least I had to, enter a password 

regaurdless because this password will be needed any time you install software. As an Ubuntu newbee I did not catch that.

I made the partitions with Paragon Disk Manager ahead of time and then just assigned the "/, /home & swap" areas and had them format each again within Ubuntu set up to be on the safe side :)

I'm sure my lack of knowledge of Partitions/Primarys/Extended/Logical added to my confusion to make things worse.

To people who use windows all the time this was very complicated :)

I would say this problem is to be considered "closed".


As a new and neutral user of Ubuntu my first impression (over XP) is: Faster start ups, faster browsing & faster downloads, but I've only been using it a few hours. I will definitely keep it on my PC and hope more software is made compatible- especially games. I'm 45 but not ready to quit having fun yet :)


**QUESTION:** I liked the idea of a "boot partition" for "stability" reasons, could you explain how best to set this up? (or do you maybe have this already written for someone else that you could post a copy?)

I curretly have my "windows bootloader" wherever XP puts it and my Ubuntu bootloader on my "/" partition but I'm not sure how to "point" them to my "boot patition" (I made one already).
(my "Paragon Disk Manager" has a Boot manager that takes me to a menu for xp or grub without really re-writing my MBR everytime (i think))

I read everything you sent me links of (took a whole day) but the subject is very new to me and I have a hard time understanding because the info is not always "relevant" to what I'm trying to do- you on the other hand have an excellent ability to write so even an XP softie can follow along :)

I would like to eventually install Win 7 so I am used to it when I need to work with it and to have the thrill of a multi boot system! (As a webmaster I need to use clients computers sometimes and it always looks "odd" when I seem "out of my element" in front of them :)

Thats why I'd like to go with a Boot partition.

Thanks a million so far !!!!!!!

---

### Post by oldfred on 2010-11-14
A ways back I created a boot partition for about 5 minutes then decided I did not want a boot partition but a grub only partition. Grub can be a mini-bootloader and boot many other systems. With old grub legacy that was how I booted other systems. But with grub2 and its osprober I find no reason for a grub partition anymore except on my flash drive where I use grub2 to loopmount boot my Ubuntu install and many repair ISO from one flash drive.

I find the full system is required, a /boot offers no real advantage and has to be unique to each install. It is a little more difficult to repair as you also have to mount the /boot partition to make repairs.  Herman also has lots of info on installing and separate grub or grub2 partitions on his site.

Herman on advantages/disadvantges of separate system partitions
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

Install with creating partitions screen shots
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Computers have to boot from the BIOS to the MBR to the partition with additional boot code. Not sure how Paragon Disk Manager works. It may just have its boot loader in the MBR?

To see what is installed where.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by Mercfrog on 2010-11-14
Hi Oldfred!

Ok, I'm looking at all the new info but had a little "crash" just now and could use your advice: 
somehow it seems I've corrupted the Ubuntu's Grub- when I click on my "Paragon" 
bootloader and click on "Grub" it says- 

[B][I]"Error: unknown filesystem
grub rescue"[/I][/B]

I imagine I somehow fried my grub but not sure how to fix it (other than a new installation
of everything), any tips on how to get my grub working again ??

Please help when you can ....

Thanks!

---

### Post by oldfred on 2010-11-14
Post the boot info script mentioned above.


also you can look at these threads:
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Mercfrog on 2010-11-14
ok, thanks! this should be enough to get me back on track.

Where do you suggest the Ubuntu bootloader to be installed to in my case?

**500 gb disk**

[LIST]
[*] 260 gb xp       (windows)(primary)
[/LIST]
[INDENT]
[LIST]
[*] 25 gb             (nfts shared partition)(logical)
[*] 30 gb /           (ubuntu)(logical)
[*] 20 gb /home   (ubuntu)(logical)
[*]   4 gb swap     (ubuntu)(logical)
[/LIST]
[/INDENT]

---

### Post by Mercfrog on 2010-11-14
P.S.: I would prefer to keepthe Ubuntu bootloader by Ubuntu as the curret "Paragon" bootloader provides me with the ability to still jump into windows even if something goes wrong with grub- as in this case :)

---

### Post by oldfred on 2010-11-14
Do not know about Paragon. Normally we install grub to the MBR of the Ubuntu drive or sda, not a partiiton. In fact grub2 does not like to be in a partition and will complain about it. It is less reliable as it has to use blocklists (whatever they are).

The only other way is to have another drive. I boot sdc with windows in sda. One or two users have created flash drives or CDs that they load to boot Ubuntu, otherwise it boots whatever is in sda. Grub2 finds other operating systems and lets you boot them all, so other boot loaders are not required.

---

### Post by Mercfrog on 2010-11-16
ok, thanks I'll set it up that way.

Your help to me has created at least 5 new Ubuntu users :)

---

