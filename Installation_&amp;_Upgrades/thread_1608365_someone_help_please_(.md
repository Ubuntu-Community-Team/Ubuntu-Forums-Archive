---
title: "someone help please :("
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by ksharp on 2010-10-28
ok, so, after Linux Mint completely let me down, i decided to go with Ubuntu, but now the installer is stuck on detecting file systems.

im trying to install Ubuntu 10.10 netbook edition on my dell inspiron 1000. if anyone could help that would be greatly appreciated!

---

### Post by darkhelmetchris on 2010-10-28
Are you installing *only Ubuntu, or do you have multiple OS installs?  Will you have Windows here?  Please pop in your LiveCD or LiveUSB and start the Live version, and paste the contents of these 2 commands:

To list your partitions on the drive:
```
sudo fdisk -l
```

To list your hardware:
```
lspci
```

and we'll go from there

---

### Post by ksharp on 2010-10-28
only ubuntu, i completely formatted my disc.
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b0103

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3491    28041426    c  W95 FAT32 (LBA)
/dev/sda2            3492        3648     1253377    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5            3492        3648     1253376   82  Linux swap / Solaris

``````

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 80)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0a.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

```

---

### Post by darkhelmetchris on 2010-10-29
Okay, that's interesting.  I see your first partition is of type FAT32 and you then have an extended partition with your swap in it.  I suspect that Ubuntu is not liking running from a FAT32 partition, mind you, that IS a bit of a guess.  Still, I'm sure most would agree that it's generally undesirable.

If you say you are completely formatting your drive, I would suggest the following partition scheme:
1 = type primary, filesystem ext3 or ext4, mountpoint / (about 8 or 12 GB)
2 = type primary, filesystem swap (about 2x the size of your ram)
3 = type primary, filesystem ext3 or ext4, mountpoint /home (the remaining space)

Once you have done that, see if it starts up properly and post back.

---

### Post by darkhelmetchris on 2010-10-29
Also, since you are installing fresh, with no other OS, you might FIRST boot into LiveCD/LiveUSB and pull up GParted, and create a brand new partition table.  Perhaps the installer is getting stuck detecting an existing FAT32 system that may be corrupted in some way.  Creating a new partition table will start fully fresh.

---

### Post by Hakunka-Matata on 2010-10-29
ksharp,

You have sda1 formatted as FAT32.  I would reinstall Ubuntu 10.10 netbook edition and let the install process reformat your drive since you apparently are using the whole drive for this Ubuntu installation.  I don't recall if you get an option to erase the disk, if you do get that option let the install program erase and reformat and use entire disk.  It won't be formatted as FAT 32, but rather as ext 4?, I believe,

---

### Post by ksharp on 2010-10-29
the only problem is my comp wouldnt boot off of a cd/usb, so i had to use unetbootin to install off of my hard drive. so the only way i could reformat the disc is to reinstall windows, i think, and that only gives the option of fat32 or ntfs

---

### Post by Hakunka-Matata on 2010-10-29
Copied from another thread:

Re: Wanting to install Ubuntu Netbook 10.10 on Asus EEE PC 1001P
Hi,

Thanks again for the reply. According to this: [http://news.softpedia.com/news/Insta...0-160966.shtml](http://news.softpedia.com/news/Insta...0-160966.shtml)

Article describes what the headings mean with a ubuntu 10.10 install
********************
1. Install alongside other operating systems

- Choose this option ONLY if you have another OS (e.g. Windows XP) and you want a dual boot system.

Editor's Note: Remember that, after the installation, the Windows boot loader will be overwritten by the Ubuntu boot loader!

2. Erase and use the entire disk

- Choose this option if you want to delete your existing operating system, or the hard drive is already empty and you want to let the installer automatically partition the hard drive for you. This is the option recommended for all users, especially those who want a machine with a single operating system on it.

3. Specify partitions manually (advanced)

- This option is recommended ONLY for advanced users, to create special partitions or format the hard drive with other filesystems than the default one. But it can also be used to create a /home partition, which is very useful in case you reinstall the whole system.
********************

---

### Post by ksharp on 2010-10-29
well now im re re reinstalling windows xp, because when i tried to reboot my computer sat there with a blank screen. 

but i have a new idea! im going to use unetbootin to install the iso right on my comp again, then when ive rebooted into the live version of ubuntu, ill create a liveusb and try to install of of that, kind of tricking my comp maybe? let me know your ideas on this please?

-also im reformatting my disc to ntfs to see if ubuntu likes that better

---

### Post by Hakunka-Matata on 2010-10-29
t```
he only problem is my comp wouldnt boot off of a cd/usb, so i had to use unetbootin to install off of my hard drive. so the only way i could reformat the disc is to reinstall windows, i think, and that only gives the option of fat32 or ntfs
```
unetbootin, meaning you are booting off the USBHardDrive, USB Memory stick, right?  If you choose install there, it will give you the option (third step I believe) to erase and use the entire hard disk.  That option will reformat your drive properly.  I just checked that on my Asus Aspire One Netbook with a unetbootin unr 10.10 usbdrive.  Good Luck

---

### Post by ksharp on 2010-10-29
nope im booting directly off of my main drive (option 2) and i dont see an option to format :/

---

### Post by Hakunka-Matata on 2010-10-29
booting off your main drive?  What operating system?, do you have une 10.10 installed, i'm confused as to how you are setup or what you are trying to do at this point.  How are you booting to Ubuntu netbook edition 10.10?

---

### Post by darkhelmetchris on 2010-10-29
Most Dell machines will let you pick your boot device at power-up by hitting F12

---

### Post by ksharp on 2010-10-29
im currently running windows xp, then using a usb drive to transfer the iso and unetbootin from another comp to my laptop, use netbootin to boot ubuntu directly from my hard drive, and then trying to install it fully from the live version

---

### Post by Hakunka-Matata on 2010-10-29
you need to boot your laptop from the unetbootin USB Drive which has UNE10.10 image on it.  It will boot into a blue background with Highlighted options of Try, Install, etc.  Choose the Install option, that will begin installing UNE10.10 onto your hard drive.  You must configure BIOS to boot from the USB drive.  Windows XP is out of the picture at that point, are we on the same page?

---

### Post by ksharp on 2010-10-29
i tried that, with unetbootin, and the universal usb installer program, and an actual disk, but my comp wouldnt load it :/ i tried rearranging the boot order on my bios, and tried selecting what to boot from on startup but nothing worked

---

### Post by Hakunka-Matata on 2010-10-29
unetbootin is used to install une10.10 ISO file onto the usb drive.  You then have a usb drive which is a bootable drive, and if it works on your dell it will boot your dell into une10.10 Live.  I'm thinking that has not happened yet, correct?

---

### Post by ksharp on 2010-10-29
thats correct, but thats what ive tried to do, and i just tried it again and it went directly to booting from my hd

---

### Post by Hakunka-Matata on 2010-10-29
Ok, so what's wrong?  Either your dell BIOS won't recognize the usb drive as a bootable drive, or maybe unetbootin did not install une10.10 onto the usb drive correctly.  You can try booting another computer you have there using the usb drive with une10.10 on it.  If it boots correctly you know the usb drive is not the problem.

---

### Post by ksharp on 2010-10-29
i will try that. if my bios is the problem, then what do i do?

---

### Post by Hakunka-Matata on 2010-10-29
I don't really know, sometimes older BIOSes can be updated to recognise USB drives, sometimes not.  If you have or can borrow a USB CD player with a UNE10.10 ISO CD burned image, and your Dell BIOS lets you boot from CD that's another option.

---

### Post by Hakunka-Matata on 2010-10-29
One of your first posts where you ran "fdisk -l" your Terminal prompt showed > ubuntu@ubuntu:~$ sudo fdisk -l

How did you get to that point, you actually had a running ubuntu system at that time, seems you could have installed at that time???

---

### Post by darkhelmetchris on 2010-10-29
> **Hakunka-Matata said:**
> One of your first posts where you ran "fdisk -l" your Terminal prompt showed 
How did you get to that point, you actually had a running ubuntu system at that time, seems you could have installed at that time???

Hm, I'm wondering.. if he had Ubuntu running from sda1 (fat32) at that point, in which case there was no room to load a new Ubuntu system there.  The live image is usually fat32.

Perhaps what you need to do, ksharp, is create a large blank space first on your hard disk, and a second partition as fat32, placing your Ubuntu image in that second partition, the boot from there, and install Ubuntu to the free space at the start of the drive.  After you get Ubuntu up and running, you could remove the second partition containing your live image.

---

### Post by darkhelmetchris on 2010-10-29
There is something else that I don't quite follow, also.  If you have had to go back and reload Windows to get this all to come together, then how did you load Windows?  That had to be by CD I think?  Unless I missed something.  Do you have a working, bootable CD/DVD drive already?  If so, you should be using that to install Ubuntu.  Your bios should still support booting from CD.  If you're loading windows some other way, please advise and maybe we can tweak that process to get you going with Ubuntu.

---

### Post by Hakunka-Matata on 2010-10-29
good luck you guys, see you tomorrow

---

### Post by ksharp on 2010-10-29
darkhelmetchris if this works you are officially my new god

---

### Post by darkhelmetchris on 2010-10-29
I hope it's what you need.  But, if not, I'll still be around and we'll try something else.  There are some other things we can do, but they are a little more involved.

---

### Post by ksharp on 2010-10-29
it sounds like it should work, i will let you know :]

---

### Post by ksharp on 2010-10-29
ok so im back to the installer, just created a ext3 part and a swap part, and i got an error that says: 
```
the installer needs to commit changes to the partition tables, but cannot do so because partitions on the following mount points could not be unmounted:

/cdrom

please close any applications using these mount points.

would you like the installer to try to unmount these partitions again?
```

i remember getting this error before, and clicked comtinue, and thats when it froze up. what do i do?

---

### Post by ksharp on 2010-10-29
great. so i found out how to unmount the cdrom, and then the installer crashed.

---

### Post by ksharp on 2010-10-29
i give up. like seriously nothing should be this hard. im gonna try linux mint later tonight, only because i still have the iso, but if that doesnt work then im just gonna stick with windows

---

### Post by Hakunka-Matata on 2010-10-29
ksharp, it's going to be very hard indeed to install any operating system if you do not install it as it's intended to be installed.  If you can get your computer to boot using a properly burned Ubuntu Netbook Edition 10.10 CD, or a properly created UNE10.10 usb drive, it will install straight away very quickly.  So far I see no indication you have a properly created usb drive, or CD.  Are you sure you've created a boot disk?  I'm going to list the files on my working usb drive that boots my Asus Aspire One netbook.  Compare that to the your CD or usb drive files and see if they look similar.  You haven't answered if you were able to boot with the usb drive on any computer, so we still don't know if it's a working boot usb drive.

---

### Post by Hakunka-Matata on 2010-10-29
ksharp, this attachment is an image of the folder and file listing of what your usb boot drive, or Boot CD should contain.

/attachment.php?attachmentid=173933&stc=1&d=1288410638

Does this look like the contents of your boot CD, usb drive?

---

### Post by darkhelmetchris on 2010-10-30
> **Hakunka-Matata said:**
> ksharp, it's going to be very hard indeed to install any operating system if you do not install it as it's intended to be installed.

Yes, I agree with Hakunka.  Perhaps you've never installed Ubuntu the way it's intended.  I'm going to list the 2 most common methods for you.
1.  You burn your ISO to a cd and boot directly from the CD into Live mode, and click "Install" (at this point, it is not necessary to have any OS or partitions already created on your target system's hard disk)
2.  The same, but from a USB key.  Typically, for me, it has been easiest to burn the ISO to a CD, and boot any computer with that in LiveCD mode.  Once in Live mode, make a bootable USB key by going to System, Administration, USB Startup Disk Creator.  From there, you make your bootable key.  Once you have your bootable USB key, you then plug that key into your target system and boot directly from the USB key in the same fashion as starting from CD.  (as in method 1, at this point, it is not necessary to have any OS or partitions already created on your target system's hard disk)

When I mentioned before to create the large blank partition, and then use more after that, I had thought you already knew the above steps and you were trying to do something unusual on purpose.

---

### Post by Hakunka-Matata on 2010-10-30
@darkhelmetchris, thanks for concurring.  It's hard to appreciate the problems ksharp is having without knowing what exactly his problem is.  Ubuntu installs SO easily and quickly when everything is working correctly (99.9% of the time for me so far), it's a pure pleasure.  I will comment that Ubuntu's USB Startup Disk Creator, has failed me several times though, for that reason I use the unetbootin program to create usb startup discs, has never failed me yet.  I'm wondering if ksharp is maybe trying to boot with a disc that has simply a copy of the .iso file, instead of the properly burned folders and files a functional startup disc has, as I displayed. 
What about it ksharp?

---

### Post by darkhelmetchris on 2010-10-30
> **Hakunka-Matata said:**
> @darkhelmetchris ... I will comment that Ubuntu's USB Startup Disk Creator, has failed me several times though

Yes, I do have to agree with that; it has failed me several times as well.  I have nearly tracked that problem down.  I'm fairly sure it's a formatting or sync error.  I find that if I create the FAT32 partition for the USB Startup Disk Creator to use, instead of letting it do it by itself, the problem occurs far less often.  Also, after the creator makes the key, I issue "sudo sync" to sync up the write cache, and THEN unmount it.  When I do it this way, it works very well.  I think they just need to update that a bit.

> **Hakunka-Matata said:**
> @darkhelmetchris, thanks for concurring. It's hard to appreciate the problems ksharp is having without knowing what exactly his problem is. Ubuntu installs SO easily and quickly when everything is working correctly (99.9% of the time for me so far), it's a pure pleasure.

*smiles*  Hey, you're welcome.  You're right, Ubuntu is a sincere pleasure to use.  It just makes me giddy sometimes.  When I have to use someone else's computer, and they are using "the multicolored OS" I cringe sometimes and grit my teeth.. it's soooo slow that it makes me wonder why I suffered so long with it before.

---

### Post by Hakunka-Matata on 2010-11-01
@Darkhelmutchris,

> Also, after the creator makes the key, I issue "sudo sync" to sync up the write cache, and THEN unmount it.  Thanks for that tip, "sudo sync" would be issued as a cli, so I guess you start a terminal session after the creator makes the key, and issue the "sudo sync" cli there, yes?  I'll revert to using USB Startup Disk Creator again and try your method.

---

### Post by darkhelmetchris on 2010-11-01
Yes, that "sudo sync" was in the CLI.  I would be interested in your results too, as I have not really gone over this problem with anyone else.  It just seemed to work for me so I never bothered to bring it up before.

---

