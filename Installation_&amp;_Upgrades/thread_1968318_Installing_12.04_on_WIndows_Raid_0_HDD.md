---
title: "Installing 12.04 on WIndows Raid 0 HDD"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by commiedic on 2012-04-28
Ok I am completely lost =( Here have been my problems. Sorry if I am not too detailed, but I never expected it to be this difficult and I don't know a lot of the Linux jargon. 

So I first tried the desktop installer and when I got to the installation type screen after reboot nothing would show on the partition table. Found out this doesn't work.

Tried the Live CD and it did the same thing.

Finally got the alternate CD and was able to get past that part and set up my 25GB partition to be used for Ubuntu. Then I hit another wall when I got to the Grub2 install portion. It asked me where to install to and I put in every example it gave me and every possible partition and it kept coming back with an error saying it either didn't exist or couldn't be installed to that. 

I then continued the installation without Grub2 installed. I looked up how to manual boot and someone else did the same thing. It was suggested to use a Super Grub2 disc which I made after installation complete back in Windows. After booting up with the Grub2 disc I used the function to find any OS and it found Linux and I selected it. 

This is my new error. "ALERT! /dev/disk/by-uuid  does not exist" then it goes to some cmd prompt and I have no idea what to do there. When I go back into windows, which is where I am now, I can see that the partition is filled with a 18.5GB and a 6.0GB. These were made out of the 25GB partition I made for the install. 

Any ideas what to do?

---

### Post by darkod on 2012-04-29
At the partitioning screen you needed to write down the exact device of the raid, like /dev/mapper/XXXXX_Volume0 or similar. When it asked where to install grub2 you need to enter exactly the same.

I don't know what super grub did, sometimes it makes bigger mess, sometimes it helps.

Boot into live mode of 12.04 and try this in terminal:
sudo dmraid -ay

That should activate your array. Then if you do:
sudo fdisk -l (small L)

does it list the raid device?

---

### Post by commiedic on 2012-04-29
Thanks for the reply. I am going to try a reinstall and write down the partition name this time around. I figured Grub2 would just find space and install but I guess I was wrong to assume that.

---

### Post by darkod on 2012-04-29
Be careful, you need to note the array device, not the actual partition.

So, for example, if the raid device is /dev/mapper/XXXX_Volume0
and the partitions: /dev/mapper/XXXX_Volume0p1, /dev/mapper/XXXX_Volume0p5, etc

You need to install onto Volume0, the whole device, not to a single partition. Make sure you get it right.

If you want to try, you can add grub2 without reinstalling ubuntu, but that's up to you.

---

### Post by commiedic on 2012-04-29
I went ahead and deleted the previous install and tried again. I manully made the partitions for primary and swap. The name for my Raid 0 primary partiition is md126p3, but grub will not install to that. I am getting an error: Unable to install GRUB in /dev/md126p3. Executing 'grub-install /dev/md126p3' failed. This is a fatal error

It is partition #3 for the primary Ubuntu OS and Partition #4 for swap and it says #126 above my Volume0 drive. 

On this drive it reads:

RAID0 device #126 - 600.1 GB Linux Software RAID Array
#1 Primary 104.9MB NTFS (Windows)
#2 Primary 571.7GB NTFS (Windows Storage)
#3 Primary 16.00GB K ext4 /
#4 Primary 12.30GB K swap swap


Would it be better for me to just continue the installation and repair GRUB afterwards? I am using the alternate CD since the Live/Desktop versions wouldn't detect my RAID0 at all. Do I need to load up the Live CD afterwards and repair GRUB then?

---

### Post by darkod on 2012-04-29
Something is messed up here. It says it's Linux Software RAID, not fakeraid. Windows can't install on linux software raid, it can't understand it. How would you have windows installed there?

Is it possible that this is some kind of windows software raid that ubuntu is trying to interpret as software raid also?

That's why the device is not /dev/mapper/.... because this is not fakeraid at all.

And don't try to install grub onto the partition, try it on the device, like /dev/md126. But I don't think this would work.

---

### Post by commiedic on 2012-04-29
The RAID I have is what I already have Windows installed on. I made the Raid in Bios and then installed Windows on it. I then went into disk management and partitioned ~26GB of free space on the RAID HDD's to use for Linux. 

I then put the CD in and started the installation for Ubuntu. The only thing I could find that led me up to this part is A) Use alternate install for RAID devices B) Make space on drive for Ubuntu to install on. Other then that I have pretty much been following the prompt during the install. 

It definitely isn't a "fake raid" it is a real RAID with two drives.

---

### Post by darkod on 2012-04-29
The fakeraid is the common term for bios raid (motherboard raid). This is because there is no dedicated raid card with its own cpu and memory, so it's called fake.

The fakeraid devices are named /dev/mapper/....
The linux software raid devices are named /dev/mdX but as far as I have seen, windows doesn't recognize them.

I don't know how this happened but it shouldn't be like this with bios raid. And I think this is your problem.

Is the windows device brand new or you already have data and programs on it? If it's new, are you willing to try this:
1. Go into the raid bios, and delete this array. Then create a new array again.
2. Install windows taking just the space you plan for it. Leave the rest of the raid array not partitioned.
3. Don't try to install ubuntu. Boot into live mode with the live cd and see if it recognizes the raid device there. You can check with fdisk, parted, and Gparted.

Let us know the result. The result we are looking for is a /dev/mapper/.... device, not /dev/mdX.

---

### Post by commiedic on 2012-04-29
I was afraid of having to do this, but let me back up a few more things before I do it. Will post results in a bit.

What I am using for the RAID set up is Intel matrix Storage Manager Option ROM
ICH1OR w/Raid5

I think it is part of my ASUS mobo.

---

### Post by cejack on 2012-04-29
For my machines with RAID on the motherboard, I've really never figured out Dual Boot with being able to see the RAID array in both systems.  I would dedicate a separate hard drive to install Ubuntu on or consider a Virtual machine like Virtual Box with Ubuntu running inside.  

This is on an AMD 6-Core system.  The motherboard RAID drivers are published by AMD / MOBO manufacturer (BIOSTAR).  I could find no equivalent Ubuntu RAID drivers when I checked last time.  

My suggestion would be to quit banging your head against a wall and decide to use the RAID setup in one OS or the other.  Typically, you will only be able to use the RAID in Windows if you set up the array in the BIOS and then install the Windows Drivers to see the RAID array in Windows as that is the driver base they gear the hardware for.  Many times, an equivalent Linux driver is completely missing in action.  

And these motherboard RAID controllers have been completely unreliable in RAID5,6,10 configurations and I would wholeheartedly recommend you not use such a setup in any OS without getting a beefier and more reliable PCI Express RAID 5 controller with true RAID.  

If you want to save yourself a whole bunch of time, aggravation, and problems, please buy a high quality dedicated RAID controller card and some enterprise level hard drives to go along with it.  Anything else and you are probably going to be disappointed.  

Just my two cents from having been there and done that.  Few motherboard controllers have good Linux drivers that are also compatible that have Windows equivalents.

If you're really gutsy and you have AMD motherboard with on-board RAID try here:

[http://wwwd.amd.com/AMD/devsite.nsf/oslookup/linux_chipset_drivers?opendocument](http://wwwd.amd.com/AMD/devsite.nsf/oslookup/linux_chipset_drivers?opendocument)

---

### Post by darkod on 2012-04-29
I don't know if Intel or linux (or both) are trying to change things and transition towards fakeraid to be treated as linux software raid, but if you google IMSM (Intel Matrix Storage Manager) and /dev/md126 it gives lots of hits about errors mostly with grub not installing onto the raid devices.

So far, fakeraid was used in ubuntu with the dmraid package, which is included in the live cd too, so booting into live mode should show you the device. Sometimes to activate it you need to run:
sudo dmraid -ay

But it should show it.

Linux software raid is used with the mdadm package, which is not included on the live cd, but it is on the alternate. In live mode you can also add it with:
sudo apt-get install mdadm

You might need to assemble the array under ubuntu with:
sudo mdadm --assemble --scan

That would create the /dev/mdX device.

But a fakeraid should not be /dev/mdX, that is the bottom line.

---

### Post by darkod on 2012-04-29
> **cejack said:**
> For my machines with RAID on the motherboard, I've really never figured out Dual Boot with being able to see the RAID array in both systems.

Just a quick question: Did you try with the alternate cd too?
Many people use the fact the live cd can see the fakeraid array and install like that, when the advice is clear to use the alternate cd. The live cd often fails to install grub. You can add only grub later without a full reinstall, but very few people actually take time to investigate and do this. They simply say it doesn't work and that's it.
The alternate cd is supposed to have much better raid support and not to fail in grub install.

---

### Post by commiedic on 2012-04-29
> **darkod said:**
> 

Is the windows device brand new or you already have data and programs on it? If it's new, are you willing to try this:
1. Go into the raid bios, and delete this array. Then create a new array again.
2. Install windows taking just the space you plan for it. Leave the rest of the raid array not partitioned.
3. Don't try to install ubuntu. Boot into live mode with the live cd and see if it recognizes the raid device there. You can check with fdisk, parted, and Gparted.

Let us know the result. The result we are looking for is a /dev/mapper/.... device, not /dev/mdX.

Ok, this is what I got. I left 50GB out of the raid0 setup for installing windows.

In GParted:

/dev/mapper/ddf1_raid 0 - Gparted

Unallocated 558.77GB

It says I have to create a new partition table, but it will erase everything on the drive. It doesn't see that I left 50GB off the RAID0 Setup. It would be ~600GB total seeing how it is made up of 2x 300GB drives.

---

### Post by darkod on 2012-04-29
That's little progress, at least it is showing the raid as /dev/mapper/... not.

Although I didn't expect ddf1, more like /dev/mapper/isw_blahblah

But that depends on the controller.

Try it now with the alternate cd and lets see how it goes.

---

### Post by commiedic on 2012-04-29
Getting the same thing =(

So, since it wouldn't recognize the extra space I had I went ahead and made a 50GB RAID just for Ubuntu and left it empty.

Started the installation with alternate CD and now it has two Volumes. Volume 0 (Windows) and Volume 1(Blank) I made the primary and swap partitions on Volume 1 and when it finally got to GRUB again it was back to the same thing. Just called md125p1 now, so even though this partition has nothing to do with windows I still can't install GRUB.

---

### Post by darkod on 2012-04-29
Unfortunately it seems it can't understand your raid (chipset) correctly. That would explain why it's changing device names.
I'm out of ideas, sorry. I think it's up to the board being supported or not.

---

### Post by commiedic on 2012-04-29
Yup, Guess I have no luck using this fake raid setup right now. In order to "Dual boot" do both OS's have to be on the same driver, or can I get a new small HDD and just install on that instead? This would be temporary until one day I can just get a SSD and not have to deal with RAID anymore =P

---

### Post by cejack on 2012-04-29
You have to differentiate between the ways you can do employ various Linux OS RAID or RAID-Like tactics (LVM, mdadm, etc.) and "driver-based" RAID.  They are mutually exclusive.  

If you're going to use RAID drivers to load a RAID array configured on your motherboard, you are going to have to have drivers that work with both Linux and Windows to do what you're doing.  Any problems or incompatibilities and you are toast. 

If anybody has been able to get the RAID drivers on an AMD  motherboard (SB85xx or SB95xx) for Windows and Ubuntu to co-exist peacefully with one another on a Dual Boot setup then I'd be very interested in seeing a step-by-step guide.

Personally, after having built scores of machines, servers, desktops, and what not, my only success has been with more expensive dedicated controllers that are true "hardware-based" RAID controllers.  

Anything else will generally be a disappointment for multiple OS's.  If you do happen to get it to work, prepare for only basic JBOD and RAID 0 or RAID 1 to work.  RAID 5, 6, 10, etc. will be a crap shot and I have found it generally unreliable on most AMD motherboard controllers.

---

### Post by commiedic on 2012-04-29
Well since it is my first time using Linux I would rather do it right the first time anyways. So I will either save up for a hardware Raid controller or wait to get a large SSD so I don't need the benefit of RAID 0 anymore. The only things I keep on the OS HDD's are games. Everything else like documents, music, movies go on to other storage.

---

### Post by darkod on 2012-04-30
> **commiedic said:**
> Yup, Guess I have no luck using this fake raid setup right now. In order to "Dual boot" do both OS's have to be on the same driver, or can I get a new small HDD and just install on that instead? This would be temporary until one day I can just get a SSD and not have to deal with RAID anymore =P

You can install on a third disk without any problems. Note that you might not be able to see the data on the array if that's what you want. You will have the same problem when reading the array from ubuntu so it might not be able to open it.

---

### Post by sujoe on 2012-04-30
If you're attempting to span disks (raid0) Why not just use LVM in linux and the equivalent in Windows? I want to say Logical Disk Management.

Same effect and much easier to recover and manipulate than fakeraid 0 (you can resize,move,delete partitions w/o wiping the current table). The best part is it's hardware independent. You will still need an separate boot partition that is not part of any disk array to use the LVM.

LVM in linux is pretty painless, I haven't tried the windows analog or a dual boot system with it yet so I can't expand on the subject. However, it should be possible somehow.

[http://en.wikipedia.org/wiki/Logical_volume_management](http://en.wikipedia.org/wiki/Logical_volume_management)

[http://en.wikipedia.org/wiki/Logical_Disk_Manager](http://en.wikipedia.org/wiki/Logical_Disk_Manager)

[http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29](http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29)

---

### Post by cejack on 2012-04-30
I believe LVM is awesome... Use it on my server and it is pretty easy with the LVM GUI helping you out.  

However, I don't think Windows will address an LVM volume.  AAt least not natively.  

Haven't actually tried it but to my knowledge the equivalent in most advanced Windows OS's is "Dynamic" disks and configuration with dynamic disks will not work with Linux to my knowledge.  

There are some geekier posts on this stuff but please back-up all your data before you try any of this.  

One good idea is to just set up a virtual machine.  Most virtual machines allow you to configure a share outside of the virtual machine.  Beware of the security issues but if you have a good firewall and a small or home network, you may be OK with that solution.  

Here's some ideas for further reading. 

[http://ubuntuforums.org/showthread.php?t=184934](http://ubuntuforums.org/showthread.php?t=184934)

[http://ubuntuforums.org/showthread.php?t=833653](http://ubuntuforums.org/showthread.php?t=833653)

[http://www.squidoo.com/accessing-an-lvm2-volume-in-windows](http://www.squidoo.com/accessing-an-lvm2-volume-in-windows)

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

---

### Post by udumbtu on 2012-07-19
Check out my post here:
[http://ubuntuforums.org/showthread.php?p=12113924#post12113924](http://ubuntuforums.org/showthread.php?p=12113924#post12113924)
During the first installation part (basic server) there was a choice to activate RAID. I chose yes and everything ran smoothly. I can access the RAID 1 (ntfs) from windows and ubuntu.

---

