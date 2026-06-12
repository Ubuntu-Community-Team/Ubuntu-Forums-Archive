---
title: "operating system not found after updates"
date: 2012-10-11
forum: Installation &amp; Upgrades
---

### Post by joshalo on 2012-10-11
Hi, My computer is a Lenovo x120e AMD 64.  I have been running Ubuntu 12.04 LTS since April with no significant problems.  Today, I installed recommended security updates which is something I do regularly.  The system required restart to complete the updates and so I restarted the computer.  Upon restart, I now get the error message "Operating System not found".  I switched the bios to diagnostic mode and I see where the computer is finding my hard drive, "Fixed Disk: WDC etc."  Prior to this problem, my hard disk was operating normally with no loud noises or other indications of a problem.  

Unfortunately, I no longer have a good usb start up disk and this computer does not have a CD drive.  I do have another computer running 12.04 but I have not installed the most recent updates on that one and it works fine.  I do not, however, have a fast enough internet connection to download another copy of the operating system. 

Am I the only one having this problem?  What should I do next?

---

### Post by pqwoerituytrueiwoq on 2012-10-11
make sure the bios is set to boot the hdd, remove any sd card/usb drive and see if it boots
you can also use the boot menu and select your hdd there

---

### Post by joshalo on 2012-10-11
Thanks for the quick response.  I have tried each of your suggestions and have the boot order set to hdd first.  There are no periphery devices attached to the computer.  Same error "Operating System not found".

I opened the back of the computer, removed the hard drive and replaced it, no change.  I have an enclosure for a SATA drive so to check to make sure that the disk was good, I put it in the enclosure and mounted it on my other computer.  My files are all visible.  I ran disk utility and the disk is good with no bad sectors.  

Unless the Lenovo's controller is bad, I believe the problem must be related to the security updates that I just installed.  Is there a way to go back to the previous state of the drive before the updates? Can I do this with the disk as an external drive mounted on my working machine?

Josh

---

### Post by joshalo on 2012-10-11
So I was able to get a bootable usb start up disk and have used it to boot the Lenovo.  The WDC hard drive is visible in the file system menu.  I used disk utility to check the disk and adapter and everything is good.

---

### Post by darkod on 2012-10-11
Boot into live mode with the stick if you can, open Gparted and check whether you have the boot flag on any partition on the hdd. Some systems don't boot without any boot flag even though linux doesn't need it to work (unlike windows).

If there is no boot flag, set it on one of the partitions. If you have windows, set it on the partition where windows is.
If you have only ubuntu, set it to any partition, for example the root partition, but not to an extedned one. It has to be either primary or logical.

You set the flag by right-clicking a partition in Gparted and selecting Manage Flags.

See if that helps.

---

### Post by joshalo on 2012-10-11
Thanks for the suggestion,

I booted in using a live cd on a usb stick.  I opened GParted and saw the HDD.  A boot flag was set for sda1 with is a FAT32 100mb partition.  There were no flags on the ext partition or the swap partition.  Still, when I try and boot normally, it finds the HDD, beeps and goes to a screen that reads "Operating System not found".  Is there a way to replace the boot partition with a new version without wiping the entire disk?  What else can I try?

Josh

---

### Post by Gamanet on 2012-10-12
Hi!

I have the same problem after updating my 12.04...

It´s definatly not the disk causing the problems...

I guess the update did some changes to drivers needed for working with motherboard/chipset, etc...

Haven´t found a solution till now...

P.S: i´m also running a Lenove x121e, when i start ubuntu from cd/usb it works fine and i can access the disk... only booting from disk doesn´t work anymore... and yes, there is a boot-flag on the correct partition...

---

### Post by darkod on 2012-10-12
The thing that is confusing me is that Operating system not found is usually reported by bios, not by the bootloader or the OS itself.

If this is a bios message, what ever OS you have has nothing to do with it.

And the grub2 error messages are different, I haven't heard of this message to be part of grub2 messages.

---

### Post by Gamanet on 2012-10-12
Maybe that could lead to the right direction?

[http://askubuntu.com/questions/139394/cannot-boot-after-bios-uefi-reset-to-defaults](http://askubuntu.com/questions/139394/cannot-boot-after-bios-uefi-reset-to-defaults)

I´ve to install ubuntu on my netbook again to test by myself...


And you´re right - "Operating System not found" isn´t a grub-message..

---

### Post by joshalo on 2012-10-12
I'm glad to hear that I'm not the only one with this problem.  I followed the links suggested and followed the instructions to reload grub using the usb live disk.  This seemed to have worked as far as I could tell. However, no luck.  Still get the message "Operating System not found" when booting from the HDD.

---

### Post by Gamanet on 2012-10-12
Havew you already tried to re-install grub?

[http://wiki.ubuntuusers.de/GRUB_2/Reparatur](http://wiki.ubuntuusers.de/GRUB_2/Reparatur)

---

### Post by joshalo on 2012-10-12
Yes, I re-installed grub using the method described in the links from the previous posts.  I have also looked at the link you provided and it appears very similar to what I did.  I reinstalled grub in efi mode using a live usb stick.  Everything appeared to work fine, no error messages, etc.  Still, when I rebooted without the live usb, the error message "Operating System not found" immediately came up.

Josh

---

### Post by darkod on 2012-10-12
If you are using UEFI mode and the boot options are deleted, you will probably have to enter the bios and create new boot options. Not sure how UEFI works exactly, but I have seen it mentioned that you create entries for booting from inside bios too.

There should be some boot manager or something.

---

### Post by joshalo on 2012-10-12
The boot options in the BIOS are intact with the HDD set as first followed by the USB devices and ending with the network adapter.  I have tried various boot priority orders with no effect.

---

### Post by joshalo on 2012-10-14
I'm nearing the point wiping the hard drive and starting over.  If anyone has any more ideas about how I might rescue this system before I wipe it, please let me know.  I'm not looking forward to the hours upon hours of tweaks and downloads that will follow a fresh install.

Since this is a Lenovo x120e, more or less a suped up netbook, do any of you recommend going with another distro rather than 12.04 LTS Desktop.  Is one more stable than another so that I might not have this happen again?  Any feedback would be greatly appreciated.

Thanks,

Josh

---

### Post by Gamanet on 2012-10-15
I have already wiped the disk and reinstalled ubuntu 12.04LTS... No problems during setup, even installation of grub worked fine, but after the mandatory reboot after finishing the installation i got again "OS not found"....

Maybe it helps to NOT download updates during the installation... As far as i think, one of the last updates i causing this problem... unfortunately, as i told already, i´ve wiped my disk already, therefore i can´t check which updates was applied befor the proble arised...

---

### Post by joshalo on 2012-10-15
That sounds really frustrating.  I wonder if the netbook remix, xubuntu, or one of the other distros would avoid this problem.  How do we go about getting someone on the development side to figure out which update is causing this?  I can wait a little longer before I wipe the disk so I think I'll see if that can help figure out the problem.  Is there a way to undo the updates?

---

### Post by darkod on 2012-10-15
> **joshalo said:**
> That sounds really frustrating.  I wonder if the netbook remix, xubuntu, or one of the other distros would avoid this problem.  How do we go about getting someone on the development side to figure out which update is causing this?  I can wait a little longer before I wipe the disk so I think I'll see if that can help figure out the problem.  Is there a way to undo the updates?

First of all, did you confirm that you are not using UEFI boot? And if you are using UEFI boot that ubuntu IS installed in UEFI mode?

A lot of bootloader confusion these days is because of the UEFI that MS and Intel want to force upon users. The boot process of UEFI is quite different and it needs to be taken into account especially in dual boots.

If you are using the older, common BIOS boot, I still haven't seen a situation where some update will make your computer give the "OS not found" message since this message is usually a BIOS message, and not grub/bootloader message. This happens even before the bootloader kicks in.

So I am not 100% sure ubuntu or any update is to blame here, but I might be wrong of course.

---

### Post by Gamanet on 2012-10-15
> **joshalo said:**
> That sounds really frustrating.  I wonder if the netbook remix, xubuntu, or one of the other distros would avoid this problem.  How do we go about getting someone on the development side to figure out which update is causing this?  I can wait a little longer before I wipe the disk so I think I'll see if that can help figure out the problem.  Is there a way to undo the updates?

In "/var/log/dpkg.log" you can find informations about the last applied updates...

You can also find the last downloaded Files (via apt-get) here:

ls -lat /var/cache/apt/archives/

This should give you information about when the last updates were applied:

ls -lt --time-style="long-iso" /var/log/apt | grep -o '\([0-9]\{2,4\}[- ]\)\{3\}[0-9]\{2\}:[0-9]\{2\}' -m 1

I´m not sure, if

apt-get remove

is the right way to remove updates... I will check this...

---

### Post by joshalo on 2012-10-15
I have tried both UEFI and Legacy boot options.  I'm pretty sure that I have Ubuntu installed as UEFI and when I use the usb stick, I Know that it is loading as UEFI based on the graphical display.  It seems to me that since I have been using Ubuntu 12.04 flawlessly and with regular updates installed since April, and only after installing the latest updates and rebooting have I had this problem, that the updates are related.  Also, the fact that someone else with the same computer had the same problem after installing the same updates, twice, is further evidence that the updates are somehow related.  I don't know enough about all of this to be able to say anything definitively, but I am good at following instructions and so far, nothing has solved this.  

I'll try and look at the log of the most recent updates and see if anything jumps out that might have caused this.

J

---

### Post by darkod on 2012-10-15
But I would say there is a difference if you are using UEFI since it's too new. For example, I don't use UEFI but from has been said here, the boot entries are created in the UEFI menu, in bios. Not in grub2.

So, the message no OS found might be from UEFI, in other words no options to boot. Otherwise even if the boot files are missing, the message should be something like File not found, right?

Have you tried creating new UEFI boot entries with any kind of boot manager that might exist in the bios? Or double checking that the entries still exist there?

I'm just fishing here, but you get the point.

---

### Post by andy18 on 2013-08-16
Hi

I updated my Ubuntu yesterday and now I have the same messag when I try to start my Laptop. It says "Operation System not found"

I don't see any solutions in this thread. How did you solve the problem when even a re-installation of Ubuntu didn't help.

Any ideas?

---

