---
title: "Complete Newbie and need serious help"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by blackearth99 on 2010-02-05
Today I decided to try out Ubuntu and Install it to my external hard drive. My current hard drive for my laptop is windows xp. Installation went smoothly on my external hdd but now ever since I had shutdown from ubuntu for the first time the rebooting process does not bring me back to the selection to choose between the 2 OS's, instead I get a "rescue:grub>" (which I have no clue what it is) 

I really want to boot up to windows xp and uninstall ubuntu because I feel that I'm not ready for a linux OS. So my question is how do I fix this problem and just be able boot to windows normaly before this happened?

Help will be deeply appreciated.

---

### Post by shane8002 on 2010-02-05
Dude everybody's ready for linux man its not hard at all, you might can try to boot ur computer from usb if thats the type external hardrive your using. The best thing to do is partition your hard drive.

---

### Post by blackearth99 on 2010-02-05
Ok so now I am able to get to the OS boot screen but now when I click on "microsoft windows xp professional (on /dev/mapper/nvidia_cabcadae1)" I get a "error: invalid signature" which makes no sense to me because I am able to get on ubuntu and look through my windows files. anyone know what's up?

---

### Post by realzippy on 2010-02-05
to restore your windows,you have to run fixmbr...
Google fot "XP fixmbr" and you will find tons of HowTos.It's easy.

---

### Post by blackearth99 on 2010-02-05
> **realzippy said:**
> to restore your windows,you have to run fixmbr...
Google fot "XP fixmbr" and you will find tons of HowTos.It's easy.

My cd rom is placed as the first boot loader and it starts to load the recovery disk for windows but when it asks me to press any key to continue I do press any key then my laptop stops reading the disk, yet the disk keeps spinning but not being read off of.

---

### Post by zeroseven0183 on 2010-02-05
How did you install Ubuntu? I assume you did it inside Windows and selected the external drive (whatever the drive letter is) from the selection.

Or whether it was installed inside Windows or not, you will have to adjust your BIOS to boot to the external drive first and modify your Grub (bootloader).

The reason why you can't see the Ubuntu files/partition through Windows is because Windows, by default, cannot read a different file system (ext3 or ext4 depending on your installation).

But if you really don't need the Ubuntu in your external HDD, you can just delete the partition and format it. But be sure you don't have important data stored there.

---

### Post by blackearth99 on 2010-02-05
> **zeroseven0183 said:**
> How did you install Ubuntu? I assume you did it inside Windows and selected the external drive (whatever the drive letter is) from the selection.

Or whether it was installed inside Windows or not, you will have to adjust your BIOS to boot to the external drive first and modify your Grub (bootloader).

The reason why you can't see the Ubuntu files/partition through Windows is because Windows, by default, cannot read a different file system (ext3 or ext4 depending on your installation).

But if you really don't need the Ubuntu in your external HDD, you can just delete the partition and format it. But be sure you don't have important data stored there.

I installed ubuntu through the "try it before you buy it" selection from the ubuntu cd. How do I acces grub through ubuntu desktop and modify it to boot windows?

---

### Post by blackearth99 on 2010-02-05
Now the windows xp repair disk is working but it won't give me an option to access the recovery console to fix the MBR, it just asks me if I want to set up windows xp, make a partition, and to delete the selected partition.

How do I actually get to the recovery console without being able to access windows?

---

### Post by zeroseven0183 on 2010-02-06
That's weird. You should have the Recovery Console option there. Try pressing 'R'

---

### Post by zeroseven0183 on 2010-02-06
Try this one: [http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)

Or you can download a tool, save on a CD or on a floppy drive, boot from it to fix your master boot record.
(please refer to link below)

---

### Post by zeroseven0183 on 2010-02-06
I found another one, Hiren's BootCD. A very helpful tool that includes a lot of utilities, partition tools, backup tools, recovery tools, system and hard drive testing tools, MBR tools and many more. All the programs included in the bootable CD are listed in [http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd).

You can download the 194MB file from [http://www.hirensbootcd.net](http://www.hirensbootcd.net)

I wish that information helped you to recover your MBR. Let us know if you were able to resolve the issue.

---

### Post by darkod on 2010-02-06
> **blackearth99 said:**
> Ok so now I am able to get to the OS boot screen but now when I click on "microsoft windows xp professional (on [COLOR=Red]/dev/mapper/nvidia_cabcadae1[/COLOR])" I get a "error: invalid signature" which makes no sense to me because I am able to get on ubuntu and look through my windows files. anyone know what's up?

Don't try too much tools one after the other, just creates more mess. The ubuntu cd is enough to sort everything usually.
I see no one mentioned the above: ARE YOU RUNNING A RAID ARRAY???
If you are, you DON'T install ubuntu from the standard desktop livecd, instead from the alternate install cd. And you need to read a lot about raid before starting the install. And you should also mention in your post that you are running raid because it's important.

If you are NOT running raid. It seems you have remains of raid meta data on your hdd. Windows might ignore it and work fine, but ubuntu 9.10 doesn't ignore raid meta data.

So, ONLY IF YOU ARE NOT RUNNING RAID, boot with ubuntu cd, Try Ubuntu option into the live desktop, and in terminal execute:

sudo dmraid -E -r /dev/sda (if you have only one hdd it will be named /dev/sda)
sudo apt-get remove dmraid

That should get rid of the raid settings on the hdd. Then you would need to reinstall grub2 because it wouldn't install properly with the raid data on. Run:
sudo fdisk -l

and post the result here so we can give you commands to reinstall grub2.

---

### Post by presence1960 on 2010-02-06
If you want to restore your internal disks MBR so it boot right to windows do this since you can't seem to get it with the XP install disk:

1. Boot Ubuntu Live CD. Choose "try ubuntu without any changes."
2. When the desktop loads open a terminal and run ```
sudo apt-get install lilo
``` This will install lilo to the Live Cd session. next in terminal run ```
sudo lilo -M /dev/sda mbr
``` This will fix your MBR so you can boot windows.
3. Reboot without the CD and you will boot right to windows like it was before you installed ubuntu.

---

### Post by raymondh on 2010-02-06
> **presence1960 said:**
> If you want to restore your internal disks MBR so it boot right to windows do this since you can't seem to get it with the XP install disk:

1. Boot Ubuntu Live CD. Choose "try ubuntu without any changes."
2. When the desktop loads open a terminal and run ```
sudo apt-get install lilo
``` This will install lilo to the Live Cd session. next in terminal run ```
sudo lilo -M /dev/sda mbr
``` This will fix your MBR so you can boot windows.
3. Reboot without the CD and you will boot right to windows like it was before you installed ubuntu.

+1.  Get windows running and then let's sort out the ubuntu.

Raymond

---

### Post by presence1960 on 2010-02-06
> **shane8002 said:**
> Dude everybody's ready for linux 

Just so far from the truth. Let people make their own choices. Linux is not for everyone just as Windows, Mac, BSD, etc are not for everyone. Don't be a fanatic as that tact helps no one.

---

