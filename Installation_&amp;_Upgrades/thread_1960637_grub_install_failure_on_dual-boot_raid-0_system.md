---
title: "grub install failure on dual-boot raid-0 system"
date: 2012-04-17
forum: Installation &amp; Upgrades
---

### Post by strask on 2012-04-17
Hi all. I'm an old-school unix guy, but it's been a few years since I messed with linux at all (I've been on MacOSX and Win7) and my googling isn't helping me much today. :(

I have a gaming laptop with two disks striped for performance (raid-0) using an intel sata raid controller. (The laptop is an MSI GT680R, in case that helps). Each disk is 500gb for a total of one tb.

It came installed with windows 7 and has a couple of small recovery partitions at the front, if I recall right the first is about 11gb and the second only 100m. Then comes the main windows partition that I resized a long time ago to something less than the whole disk, and finally 300+gb of free space.

I just tried to install Ubuntu 11.10. When it correctly detected my existing OS I told it to go ahead and install next to windows; I didn't bother specifying partitions manually or anything. The install seemed to go fine until the very end when it went to install grub; it failed and gave me three options: Specify a different device to install grub on, continue without a boot loader, or cancel the install. 

I tried specifying a different device, using /dev/mapper/Volume0 (or something like that; selected from a list) but got the same error... for all I know that's the device it tried in the first place. The other listed devices didn't seem right so I didn't try them, and instead told it to continue without a boot loader.

The install then immediately finished (I can only assume grub is the final step) and I rebooted, expecting to get into windows since grub couldn't install.

Instead I get "error: no such device: [lots of hexidecimal garbage]" and get dumped to the 'grub rescue>' prompt. I have no idea what to do with this.

'ls' gives me the list (hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)
'set' tells me that prefix=(hd0,5)/boot/grub and root=hd0,5

My assumption is that while ubuntu as a whole understands my raid controller, grub does not.

I'm hoping someone knows how to tell grub to boot to windows (which would be in the third partition) or how to re-install the default windows bootloader. Obviously since this was an initial install I don't have any important data on the linux side.

Thanks for reading this far. :)

---

### Post by oldfred on 2012-04-18
Usually the desktop installer does not have the RAID drivers, you normally need the alternative installer or the server versions.

Not sure if this had the RAID drivers or not:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

I think the issue is grub normally defaults to installing to sda, but in RAID you do not install to sda but to a mapper device.

example
For RAID reinstall
sudo mount /dev/mapper/nvidia_abjcfaad3 /mnt
Change red entries below, I think first is like partition, and second is just the drive? I do not have RAID so not 100% sure.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
[COLOR=Red]sudo mount /dev/sda5 /mnt[/COLOR]
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot [COLOR=Red]/dev/sda[/COLOR]
#If that returns any errors run:

# If no errors on previous commands reboot into working system and run this:
sudo update-grub




RAID add kpartx to LiveCD or use alternative text installer
[http://ubuntuforums.org/showthread.php?t=1811353](http://ubuntuforums.org/showthread.php?t=1811353)
[http://ubuntuforums.org/showthread.php?t=1631336](http://ubuntuforums.org/showthread.php?t=1631336)
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

---

### Post by strask on 2012-04-18
> **oldfred said:**
> Usually the desktop installer does not have the RAID drivers, you normally need the alternative installer or the server versions.
Interesting... the default desktop installer seemed to have no trouble detecting and installing to my raid device, aside from the crippling grub error. :)

> Not sure if this had the RAID drivers or not:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
I'll give it a try if I have any trouble with your other advice.

> I think the issue is grub normally defaults to installing to sda, but in RAID you do not install to sda but to a mapper device.
Yes that sounds like what happened.

Thanks for this reply you've given me an excellent starting point. I'll post back to report what I end up doing and what happens. :)

---

### Post by strask on 2012-04-18
Ok, while starting to follow your advice I noticed for the first time that my housemate had burned the 32bit version of Ubuntu, and I definitely need 64bit. So there was no sense whatsoever in trying to recover the linux install. All I needed was windows back.

Found the magic incantation for that in one of the discussions you linked (thanks also to mooseman99) and did the following:

Boot from Windows 7 DVD
Select language
Select Repair
Select my windows install from the list.
Get a command prompt
X:> bootrec 
(gives instructions)
X:> bootrec /FixMbr
(fixes everything)
Reboot, windows comes up just as it was before I broke it.

Now I will RTFM a little more and download the alternative install disk etc.

Thanks again for the rescue, oldfred.

---

